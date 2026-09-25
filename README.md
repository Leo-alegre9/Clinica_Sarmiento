# 🏥 Clínica Sarmiento

Sistema integral de gestión desarrollado para **Clínica Sarmiento**, orientado a centralizar y optimizar la administración de pacientes, turnos, historias clínicas, profesionales, caja, operaciones y documentación médica.

El proyecto busca reemplazar procesos manuales y sistemas anteriores mediante una plataforma web moderna, escalable y preparada para acompañar el crecimiento de la clínica.

---

## 📌 Descripción

**Clínica Sarmiento** es una aplicación web de gestión médica desarrollada principalmente para una clínica oftalmológica.

El sistema permite administrar desde una única plataforma diferentes áreas de la institución, facilitando el trabajo del personal administrativo y de los profesionales médicos.

Entre sus principales objetivos se encuentran:

- Centralizar la información de los pacientes.
- Digitalizar las historias clínicas.
- Mejorar la gestión de turnos.
- Facilitar el seguimiento de consultas y tratamientos.
- Administrar ingresos, gastos y movimientos de caja.
- Gestionar documentación y archivos médicos.
- Organizar operaciones y procedimientos.
- Proporcionar interfaces específicas según el rol del usuario.

---

## 🚀 Tecnologías utilizadas

### Backend

- **PHP 8.4**
- **Laravel**
- **Laravel Fortify**
- **Inertia.js**
- **Pest / PHPUnit**
- **Larastan**
- **Laravel Pint**

### Frontend

- **React**
- **TypeScript**
- **Tailwind CSS**
- **shadcn/ui**
- **Radix UI**
- **Vite**

### Base de datos

Actualmente el proyecto utiliza:

- **SQLite** para el entorno inicial de desarrollo.

La arquitectura está preparada para trabajar posteriormente con una base de datos relacional destinada al entorno productivo.

### Herramientas

- Git
- GitHub
- Composer
- Node.js
- npm
- Docker
- Laravel Herd
- WSL

---

## 🧩 Módulos principales

### 👤 Gestión de pacientes

Permite registrar y administrar la información de los pacientes de la clínica.

Incluye funcionalidades como:

- Alta de pacientes.
- Modificación de datos.
- Consulta de información.
- Historial de atención.
- Información de contacto.
- Documentación asociada.

---

### 📅 Gestión de turnos

Sistema de agenda destinado a organizar las consultas de los profesionales.

Contempla:

- Creación de turnos.
- Reprogramación.
- Cancelación.
- Agenda por profesional.
- Estados de los turnos.
- Control de llegada de pacientes.
- Reorganización de la agenda.
- Automatización de avisos y recordatorios.

---

### 🩺 Historia clínica

Cada paciente dispone de una historia clínica digital.

Los profesionales podrán registrar:

- Consultas.
- Diagnósticos.
- Observaciones.
- Estudios.
- Tratamientos.
- Evolución del paciente.
- Indicaciones médicas.

---

### 📄 Archivos del paciente

El sistema permitirá adjuntar y administrar documentación relacionada con cada paciente.

Por ejemplo:

- Estudios.
- Informes.
- Resultados.
- Imágenes.
- Documentación médica.
- Archivos complementarios.

---

### 💊 Recetas

Los profesionales podrán generar y registrar recetas asociadas a las consultas de los pacientes.

Las recetas quedarán vinculadas a la historia clínica correspondiente.

---

### 👨‍⚕️ Gestión de profesionales

El sistema contará con diferentes médicos que podrán acceder a funcionalidades específicas.

Cada profesional podrá administrar:

- Su agenda.
- Sus pacientes.
- Historias clínicas.
- Consultas.
- Recetas.
- Estudios.
- Procedimientos.

---

### 💰 Caja

Módulo destinado al registro y control de movimientos económicos.

Permitirá gestionar:

- Ingresos.
- Egresos.
- Pagos de consultas.
- Gastos.
- Movimientos diarios.
- Control de caja.

---

### 💵 Valores de consultas

El sistema permitirá configurar los diferentes valores correspondientes a las consultas y prestaciones realizadas dentro de la clínica.

---

### 🏥 Operaciones y procedimientos

Permitirá registrar procedimientos u operaciones médicas.

Se podrá administrar:

- Paciente.
- Profesional responsable.
- Tipo de operación.
- Fecha.
- Estado.
- Observaciones.
- Información relacionada al procedimiento.

---

### 📊 Administración general

Los usuarios administrativos dispondrán de herramientas para supervisar la actividad general de la clínica.

Entre ellas:

- Gestión de profesionales.
- Gestión de pacientes.
- Control de gastos.
- Gastos asociados por médico.
- Valores de consultas.
- Movimientos económicos.
- Operaciones.
- Reportes generales.

---

## 👥 Roles del sistema

La aplicación está diseñada para trabajar con diferentes niveles de acceso.

### Administrador

Acceso general al sistema y a la configuración de la clínica.

### Administrativo

Gestión de:

- Pacientes.
- Turnos.
- Caja.
- Pagos.
- Documentación.
- Operaciones.

### Médico

Acceso principalmente a:

- Agenda.
- Pacientes.
- Historias clínicas.
- Consultas.
- Recetas.
- Estudios.
- Procedimientos.

Los permisos específicos serán controlados según el rol asignado a cada usuario.

---

## 🏗️ Arquitectura

El proyecto utiliza una arquitectura web moderna basada en:

```text
Laravel
   │
   ├── Backend
   │
   ├── API / lógica de negocio
   │
   └── Persistencia
          │
       Base de datos

Laravel + Inertia
          │
        React
          │
      TypeScript
          │
      Tailwind CSS
```

Laravel se encarga principalmente de la lógica de negocio, autenticación, persistencia y seguridad.

React junto con TypeScript proporciona una interfaz de usuario dinámica y mantenible.

Inertia.js permite integrar Laravel y React sin necesidad de mantener una API REST independiente para toda la aplicación.

---

## 📂 Estructura general

```text
clinica_sarmiento/
│
├── app/
│   ├── Http/
│   ├── Models/
│   ├── Services/
│   └── ...
│
├── database/
│   ├── factories/
│   ├── migrations/
│   └── seeders/
│
├── resources/
│   ├── css/
│   └── js/
│       ├── components/
│       ├── layouts/
│       ├── pages/
│       └── ...
│
├── routes/
│
├── tests/
│
├── public/
│
├── Docs/
│
├── composer.json
├── package.json
└── README.md
```

---

## 📚 Documentación

El proyecto mantiene documentación adicional dentro del directorio:

```text
/Docs
```

Allí se documentan aspectos como:

- Alcance del sistema.
- Requisitos funcionales.
- Requisitos no funcionales.
- Historias de usuario.
- Casos de uso.
- Reglas de negocio.
- Diagramas.
- Arquitectura.
- Decisiones técnicas.
- Trazabilidad de requerimientos.
- Planificación por fases.

---

## 🔄 Metodología de desarrollo

El proyecto se desarrolla de manera incremental mediante diferentes fases.

Cada fase puede incluir:

1. Definición de alcance.
2. Diseño funcional.
3. Modelado de datos.
4. Implementación.
5. Pruebas.
6. Documentación.
7. Integración.
8. Revisión.

También se utilizan ramas de Git para separar diferentes etapas del desarrollo.

Ejemplo:

```bash
setup/fase-1-laravel
```

---

## ⚙️ Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/leo-alegre9/clinica_sarmiento.git
```

### 2. Ingresar al proyecto

```bash
cd clinica_sarmiento
```

### 3. Instalar dependencias de PHP

```bash
composer install
```

### 4. Instalar dependencias de JavaScript

```bash
npm install
```

### 5. Crear archivo de entorno

```bash
cp .env.example .env
```

### 6. Generar la clave de Laravel

```bash
php artisan key:generate
```

### 7. Configurar la base de datos

Modificar las variables correspondientes dentro del archivo:

```text
.env
```

### 8. Ejecutar migraciones

```bash
php artisan migrate
```

### 9. Iniciar el frontend

```bash
npm run dev
```

### 10. Iniciar Laravel

```bash
php artisan serve
```

---

## 🧪 Verificaciones

### TypeScript

```bash
npx tsc --noEmit
```

### Build de producción

```bash
npm run build
```

### Tests

```bash
php artisan test
```

### Formateo de código PHP

```bash
./vendor/bin/pint
```

---

## 🎯 Objetivo del proyecto

Construir una solución moderna y centralizada que permita mejorar la gestión diaria de **Clínica Sarmiento**, reducir tareas manuales y proporcionar una plataforma preparada para incorporar nuevas funcionalidades en el futuro.

El sistema está pensado para evolucionar progresivamente hacia una solución integral de gestión clínica.

---

## 🔮 Funcionalidades futuras

Algunas funcionalidades previstas para futuras fases incluyen:

- Notificaciones automáticas de turnos.
- Recordatorios a pacientes.
- Reportes administrativos.
- Estadísticas.
- Dashboard de indicadores.
- Auditoría de operaciones.
- Gestión avanzada de permisos.
- Exportación de reportes.
- Integración con servicios externos.
- Mejoras en seguridad.
- Backups automáticos.
- Monitoreo del sistema.

---

## 🔐 Seguridad

El proyecto contempla buenas prácticas relacionadas con:

- Autenticación de usuarios.
- Autorización basada en roles.
- Validación de datos.
- Protección de rutas.
- Gestión segura de sesiones.
- Control de acceso a información médica.
- Registro de acciones sensibles.

Debido a la naturaleza de la información administrada, la seguridad y privacidad de los datos constituyen uno de los principales aspectos del sistema.

---

## 📄 Estado del proyecto

> 🚧 **Proyecto actualmente en desarrollo**

La arquitectura, funcionalidades y documentación pueden modificarse a medida que avance la implementación de las diferentes fases.

---

## 📄 Licencia

Este proyecto fue desarrollado para **Clínica Sarmiento**.

Su código y documentación son de uso privado salvo autorización expresa del propietario del proyecto.
