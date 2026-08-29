# 🏥 Clínica Sarmiento

Sistema de gestión clínica orientado a la administración integral de una clínica y consultorio oftalmológico.

> 🚧 **Proyecto en desarrollo**  
> Esta nueva versión se está construyendo desde cero utilizando una arquitectura moderna, escalable y mantenible.

---

## 📋 Acerca del proyecto

**Clínica Sarmiento** tiene como objetivo centralizar la gestión clínica y administrativa de pacientes, profesionales y consultas oftalmológicas en una única plataforma.

El sistema será desarrollado progresivamente por módulos, priorizando:

- 🔐 Seguridad de la información
- 🩺 Trazabilidad de la historia clínica
- ⚡ Rendimiento
- 📈 Escalabilidad
- 🎨 Buena experiencia de usuario
- 🧩 Arquitectura mantenible
- 🧪 Testing automatizado
- 🐳 Facilidad de despliegue
- 📚 Documentación técnica

---

## 🚧 Estado del proyecto

**Fase actual:** Preparación inicial del entorno y arquitectura.

Este repositorio corresponde a una nueva implementación de **Clínica Sarmiento**, desarrollada completamente desde cero.

La versión anterior del sistema se conservará únicamente como **referencia funcional**, sin reutilizar directamente su arquitectura ni código.

---

## 🧱 Stack tecnológico

### Backend

- PHP 8.4+
- Laravel 13

### Frontend

- React
- TypeScript
- Inertia
- Tailwind CSS
- shadcn/ui
- Vite

### Base de datos

- PostgreSQL

### Infraestructura

- Docker
- Docker Compose
- Nginx
- Redis
- VPS Linux

### Desarrollo y calidad

- Git
- GitHub
- Laravel Pint
- ESLint
- Testing automatizado
- CI/CD

---

## 🏗️ Arquitectura prevista

```text
Usuario
   │
   ▼
React + TypeScript
   │
   ▼
Inertia
   │
   ▼
Laravel
   │
   ├── Autenticación
   ├── Autorización
   ├── Lógica de negocio
   ├── Validaciones
   ├── Servicios
   ├── Jobs
   └── Notificaciones
   │
   ▼
PostgreSQL
```

Posteriormente la infraestructura será complementada con:

```text
Docker Compose
│
├── Laravel / PHP
├── Nginx
├── PostgreSQL
├── Redis
└── Queue Worker
```

---

## 🧩 Módulos previstos

El sistema será construido progresivamente e incluirá módulos como:

### 👤 Usuarios

- Gestión de usuarios
- Autenticación
- Roles
- Permisos
- Control de acceso

### 👨‍⚕️ Profesionales

- Médicos
- Especialidades
- Disponibilidad
- Horarios de atención

### 🧑 Pacientes

- Alta de pacientes
- Datos personales
- Datos de contacto
- Información clínica
- Antecedentes
- Búsqueda y filtros

### 📅 Turnos

- Agenda
- Calendario
- Asignación de turnos
- Estados
- Reprogramaciones
- Cancelaciones
- Historial

### 🩺 Consultas oftalmológicas

- Motivo de consulta
- Antecedentes
- Evaluación oftalmológica
- Evoluciones
- Diagnósticos
- Indicaciones
- Conductas médicas

### 📖 Historia clínica

- Historial de consultas
- Diagnósticos
- Antecedentes
- Recetas
- Estudios
- Archivos
- Evolución clínica

### 💊 Recetas

- Recetas médicas
- Recetas ópticas
- Generación de documentos
- Impresión
- Exportación PDF

### 🔬 Estudios

- Registro de estudios
- Resultados
- Imágenes
- Documentación adjunta
- Seguimiento

### 📊 Administración

- Dashboard
- Estadísticas
- Reportes
- Auditoría
- Configuración general

### 🔔 Notificaciones

- Recordatorios
- Avisos de turnos
- Email
- Integraciones futuras

---

# 🗺️ Roadmap

## ✅ Fase 0 — Preparación

Configuración del entorno de desarrollo.

- PHP
- Composer
- Node.js
- NPM
- Git
- GitHub
- Claude Code
- Entorno Laravel

---

## 🔄 Fase 1 — Base del proyecto

Creación de la aplicación utilizando:

- Laravel
- React
- TypeScript
- Inertia
- Tailwind CSS
- shadcn/ui
- Vite

También se configurarán:

- estructura inicial;
- variables de entorno;
- testing;
- linting;
- documentación;
- Git.

---

## 🗄️ Fase 2 — PostgreSQL

Configuración del motor de base de datos.

Se definirán:

- conexión con Laravel;
- entorno local;
- convenciones;
- migraciones;
- claves;
- índices;
- restricciones.

---

## 🧠 Fase 3 — Arquitectura del dominio clínico

Se diseñará el modelo de negocio antes de comenzar los módulos principales.

Entidades iniciales:

```text
Usuario
Médico
Paciente
Turno
Consulta
Historia Clínica
Diagnóstico
Receta
Antecedente
Estudio
Archivo
```

También se definirán:

- relaciones;
- cardinalidades;
- claves foráneas;
- restricciones;
- índices;
- auditoría;
- timestamps;
- estrategia de eliminación.

---

## 🔐 Fase 4 — Seguridad

Implementación de:

- autenticación;
- roles;
- permisos;
- Laravel Policies;
- Middleware;
- validaciones;
- sesiones;
- auditoría.

---

## 👤 Fase 5 — Pacientes

Desarrollo completo del módulo de pacientes.

---

## 📅 Fase 6 — Turnos

Desarrollo de agenda, calendario y administración de turnos.

---

## 🩺 Fase 7 — Consulta oftalmológica

Implementación del flujo clínico para la atención de pacientes.

---

## 📖 Fase 8 — Historia clínica

Construcción de la historia clínica longitudinal del paciente.

---

## 💊 Fase 9 — Recetas y documentos

Implementación de recetas, órdenes, informes e impresión.

---

## 🎨 Fase 10 — UX/UI avanzada

Desarrollo de una interfaz moderna y profesional.

Se trabajará en:

- Dashboard
- Sidebar
- Navegación
- Tablas
- Formularios
- Filtros
- Buscadores
- Calendarios
- Modales
- Notificaciones visuales
- Responsive Design
- Dark Mode

---

## ⚙️ Fase 11 — Procesos en segundo plano

Implementación de:

- Redis
- Queues
- Jobs
- Laravel Scheduler
- Emails
- Notificaciones
- Recordatorios

---

## 📁 Fase 12 — Gestión de archivos

Administración segura de:

- imágenes;
- estudios;
- documentos;
- PDFs;
- archivos clínicos.

---

## 🐳 Fase 13 — Docker

Contenerización de la aplicación utilizando:

- Docker
- Docker Compose
- Laravel / PHP
- PostgreSQL
- Redis
- Nginx
- Workers

---

## 🧪 Fase 14 — Testing y seguridad avanzada

Implementación de:

- Unit Tests
- Feature Tests
- Tests de autorización
- Tests de reglas de negocio
- Seguridad de archivos
- Rate Limiting
- Logs
- Auditoría

---

## 🚀 Fase 15 — Producción

Despliegue definitivo mediante:

- VPS Linux
- Docker
- Nginx
- HTTPS
- Dominio
- DNS
- Firewall
- Backups
- Monitoreo
- Logs
- GitHub
- CI/CD

---

# 🌐 Comunicación Frontend / Backend

La aplicación web utilizará:

```text
React
   │
   ▼
Inertia
   │
   ▼
Laravel
```

Por lo tanto, inicialmente no será necesario crear una API REST exclusivamente para comunicar React con Laravel.

Las APIs serán incorporadas cuando sean necesarias para:

- aplicaciones móviles;
- integraciones externas;
- servicios de terceros;
- automatizaciones;
- WhatsApp;
- otros sistemas.

---

# 🔐 Seguridad

Debido a que el sistema administrará información clínica, la seguridad será considerada desde el diseño.

Entre las medidas previstas se encuentran:

- autenticación segura;
- autorización basada en roles;
- Laravel Policies;
- validación de información;
- protección de datos sensibles;
- auditoría de acciones;
- protección de archivos;
- gestión segura de sesiones;
- logs;
- backups;
- HTTPS;
- variables de entorno.

> ⚠️ Nunca deben almacenarse contraseñas, credenciales, tokens, claves API ni archivos `.env` dentro del repositorio.

---

# 📂 Documentación

La documentación técnica será almacenada progresivamente dentro del directorio:

```text
docs/
```

La estructura prevista será similar a:

```text
docs/
├── architecture/
├── database/
├── development/
├── deployment/
├── security/
└── phases/
```

Se documentarán:

- decisiones arquitectónicas;
- modelo de datos;
- fases de implementación;
- infraestructura;
- seguridad;
- deployment;
- integraciones;
- procedimientos técnicos.

---

# 🧪 Testing

Se incorporarán pruebas automatizadas progresivamente.

Las áreas críticas tendrán especial cobertura:

- autenticación;
- autorización;
- pacientes;
- turnos;
- consultas;
- historia clínica;
- recetas;
- reglas de negocio;
- seguridad.

---

# 📌 Principios de desarrollo

Durante todo el proyecto se priorizarán:

- Clean Code
- Convenciones oficiales de Laravel
- Código mantenible
- TypeScript
- Componentes React reutilizables
- Separación de responsabilidades
- Commits descriptivos
- Documentación técnica
- Testing automatizado
- Seguridad por diseño
- Variables sensibles mediante `.env`
- Evitar abstracciones innecesarias

---

# ⚙️ Instalación

Las instrucciones para instalar y ejecutar el proyecto serán agregadas una vez finalizada la configuración inicial de Laravel.

---

# 📈 Estado

```text
Fase 0     ██████████ Preparación
Fase 1     ░░░░░░░░░░ Laravel
Fase 2     ░░░░░░░░░░ PostgreSQL
Fase 3     ░░░░░░░░░░ Arquitectura clínica
Fase 4     ░░░░░░░░░░ Seguridad
Fase 5+    ░░░░░░░░░░ Módulos
```

---

## 📄 Licencia

Proyecto privado.

**Clínica Sarmiento — Todos los derechos reservados.**
