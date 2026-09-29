# Arquitectura — Clínica Sarmiento

Este documento describe la arquitectura técnica de la aplicación tal como quedó
establecida al finalizar la **Fase 1 (base tecnológica)**. No incluye módulos
clínicos: solo la base sobre la que se construirán en fases posteriores.

## Visión general

Clínica Sarmiento es una aplicación **monolítica** construida con Laravel e
Inertia.js. No existe una API REST separada para comunicar frontend y
backend: el frontend en React se renderiza a través de Inertia, que actúa
como puente entre las rutas de Laravel y los componentes de React, sin pasar
por JSON expuesto públicamente como una API tradicional.

```
React (TypeScript)
       ↓
   Inertia.js
       ↓
 Laravel (PHP)
       ↓
   SQLite (temporal)
```

Todo el ciclo de vida de una petición ocurre dentro de un mismo proyecto,
desplegado como una sola aplicación.

## Stack tecnológico

### Backend

| Componente | Versión | Notas |
|---|---|---|
| PHP | 8.4.24 | Herd (Windows), NTS |
| Laravel Framework | 13.29.0 | |
| Laravel Fortify | 1.39.0 | Backend de autenticación |
| Laravel Wayfinder | 0.1.21 | Genera helpers TypeScript para rutas/acciones |
| Laravel Boost | 2.7.0 | Herramientas de asistencia IA (dev only) |
| Inertia (adaptador Laravel) | 3.3.1 | |
| Base de datos | SQLite | Temporal — PostgreSQL llega en Fase 2 |
| Testing | Pest / PHPUnit 12 | `php artisan test` |
| Estilo de código | Laravel Pint | `composer lint` / `composer lint:check` |
| Análisis estático | Larastan (PHPStan) | `composer types:check` |

### Frontend

| Componente | Versión | Notas |
|---|---|---|
| React | 19.2.8 | |
| React DOM | 19.2.8 | |
| TypeScript | 5.9.3 | |
| Inertia (adaptador React) | 3.7.0 | |
| Tailwind CSS | 4.3.3 | vía `@tailwindcss/vite` |
| shadcn/ui | estilo "new-york" | componentes en `resources/js/components/ui` |
| Vite | 8.2.2 | mediante `vite-plus` (`vp`) |
| Node.js | 24.15.0 | |
| npm | 11.12.1 | |

### Autenticación

Provista por el **Starter Kit oficial de React de Laravel**, que internamente
usa **Laravel Fortify**. Se habilitaron todas las funcionalidades estándar
del kit:

- Registro de usuarios
- Verificación de email
- Autenticación de dos factores (2FA)
- Passkeys (WebAuthn)
- Confirmación de contraseña

No se agregaron roles ni permisos clínicos: la autenticación es la
provista "de fábrica" por el starter kit, sin personalización de dominio.

## Estructura general del proyecto

```
Clinica-Sarmiento/
├── app/                    # Backend Laravel (Models, Http, Providers, Actions)
├── bootstrap/
├── config/                 # Configuración (app, database, fortify, etc.)
├── database/
│   ├── database.sqlite     # Base de datos temporal SQLite
│   ├── factories/
│   ├── migrations/
│   └── seeders/
├── docs/                   # Esta documentación
├── public/
│   └── build/               # Assets compilados por Vite (generado, no versionado)
├── resources/
│   ├── css/                # app.css (Tailwind)
│   └── js/
│       ├── actions/         # Generado por Wayfinder (no versionado)
│       ├── routes/          # Generado por Wayfinder (no versionado)
│       ├── wayfinder/       # Generado por Wayfinder (no versionado)
│       ├── components/
│       │   └── ui/          # Componentes shadcn/ui
│       ├── hooks/
│       ├── layouts/
│       ├── lib/
│       ├── pages/           # Páginas Inertia (equivalentes a "vistas" React)
│       └── app.tsx           # Punto de entrada de Inertia/React
├── routes/
│   ├── web.php
│   ├── settings.php
│   └── console.php
├── storage/
├── tests/
│   └── Feature / Unit        # Pest
├── .env / .env.example
├── composer.json
├── package.json
├── vite.config.ts
└── components.json           # Configuración shadcn/ui
```

## Entorno local

- **Servidor local**: Laravel Herd (Windows), sirviendo la carpeta parqueada
  `E:\Proyectos`.
- **Dominio local**: `http://clinica-sarmiento.test` (servido automáticamente
  por Herd al estar el proyecto dentro de una ruta parqueada — no requiere
  `herd link` individual).
- **PHP servido por Herd**: 8.4.
- **Base de datos**: SQLite en `database/database.sqlite` (temporal, hasta
  Fase 2).
- **Zona horaria**: `America/Argentina/Cordoba` (`config/app.php`).
- **Locale**: `es` (`APP_LOCALE`), con `en` como fallback (`APP_FALLBACK_LOCALE`).

## Herramientas de desarrollo asistido por IA

Se instaló **Laravel Boost** (`laravel/boost`, dependencia de desarrollo) con
integración para Claude Code:

- Guías (`guidelines`) específicas de Laravel/Inertia/React/Pint/PHPUnit/etc.
- Skills de Claude Code en `.claude/skills/`.
- Servidor MCP (`.mcp.json`) que expone `php artisan boost:mcp`.

Esto no afecta el comportamiento de la aplicación en producción; es
únicamente una herramienta de asistencia para el desarrollo.

## Fuera de alcance de esta fase

Explícitamente no forman parte de esta base tecnológica (se abordarán en
fases posteriores):

- PostgreSQL, Redis, Docker.
- Configuración de servidor (Nginx, VPS).
- Módulos clínicos: pacientes, médicos, turnos, historias clínicas,
  diagnósticos, recetas.
- Roles y permisos específicos del dominio clínico.
- Diseño definitivo de interfaz/dashboard.

Ver [`docs/phases/phase-01-foundation.md`](phases/phase-01-foundation.md)
para el detalle de lo realizado en esta fase.
