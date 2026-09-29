# Fase 1 — Creación de la base tecnológica

**Fecha:** 2026-09-01
**Rama:** `setup/fase-1-laravel`
**Estado:** Completada. Sin commits ni push (según instrucción explícita).

## Objetivo de la fase

Crear, directamente en la raíz del repositorio existente
(`E:\Proyectos\Clinica-Sarmiento`), una aplicación Laravel funcional con
React + TypeScript + Inertia + Tailwind + shadcn/ui + Vite, autenticación
estándar del Starter Kit oficial, SQLite temporal y Laravel Boost — sin
desarrollar módulos clínicos ni tocar infraestructura de producción.

## Verificación previa del entorno

```
php -v            → PHP 8.4.24 (NTS, Visual C++ 2022 x64)
composer --version → Composer 2.10.2
laravel --version  → Laravel Installer 5.31.1
node --version     → v24.15.0
npm --version      → 11.12.1
git --version      → git version 2.54.0.windows.1
git status         → working tree limpio, rama setup/fase-1-laravel
git branch         → main, * setup/fase-1-laravel
git remote -v      → origin → github.com/leo-alegre9/clinica_sarmiento.git
```

PHP 8.4 es compatible con Laravel 13 (requiere PHP ^8.3). No se detectaron
incompatibilidades críticas.

## Versiones instaladas (resultado final)

| Paquete | Versión |
|---|---|
| PHP | 8.4.24 |
| Laravel Framework | 13.29.0 |
| Laravel Fortify | 1.39.0 |
| Laravel Wayfinder | 0.1.21 |
| Laravel Boost | 2.7.0 |
| Inertia (Laravel adapter) | 3.3.1 |
| Inertia (React adapter) | 3.7.0 |
| React / React DOM | 19.2.8 |
| TypeScript | 5.9.3 |
| Tailwind CSS | 4.3.3 |
| Vite | 8.2.2 (vía `vite-plus` / `vp`) |
| Node.js | 24.15.0 |
| npm | 11.12.1 |
| shadcn/ui | estilo "new-york" (componentes en `resources/js/components/ui`) |

## Dependencias principales

**Backend (`composer.json`):** `laravel/framework`, `inertiajs/inertia-laravel`,
`laravel/fortify`, `laravel/wayfinder`, `laravel/tinker`; dev:
`laravel/pint`, `laravel/sail`, `laravel/pail`, `laravel/pao`, `larastan/larastan`,
`pestphp/pest` (vía phpunit/pest bridge), `laravel/boost`.

**Frontend (`package.json`):** `react`, `react-dom`, `@inertiajs/react`,
`@inertiajs/vite`, `@tailwindcss/vite`, `tailwindcss`, `typescript`, `vite`,
componentes Radix UI (base de shadcn/ui), `lucide-react`, `@laravel/passkeys`,
`class-variance-authority`, `clsx`, `tailwind-merge`; dev:
`@laravel/vite-plugin-wayfinder`, `vite-plus`.

## Comandos utilizados (resumen cronológico)

```bash
# 1. Verificación de entorno
php -v && composer --version && laravel --version && node --version \
  && npm --version && git --version && git status && git branch && git remote -v

# 2. Scaffold temporal en carpeta hermana (el instalador requiere directorio vacío)
laravel new clinica-sarmiento-scaffold --react --database=sqlite --pest \
  --no-node --no-interaction

# 3. Selección de features de autenticación (ver "Problemas encontrados")
php artisan install:features --no-interaction \
  --answers='{"auth_features":["email-verification","registration","2fa","passkeys","password-confirmation"]}'
composer lint
php artisan wayfinder:generate --with-form --no-interaction
rm chisel.php chisel-paths.php app/Console/Commands/InstallFeaturesCommand.php
npm run check:fix

# 4. Validación del scaffold antes de integrarlo
php artisan migrate:fresh
npm run build
php artisan test   # 39/39 passed

# 5. Integración cuidadosa dentro del repositorio real (preservando .git y README.md)
robocopy "E:\Proyectos\clinica-sarmiento-scaffold" "E:\Proyectos\Clinica-Sarmiento" /E \
  /XD ".git" "vendor" "node_modules" "public\build" "resources\js\actions" \
      "resources\js\routes" "resources\js\wayfinder" \
  /XF "README.md" ".env"

# 6. Instalación de dependencias en el repositorio real
cp .env.example .env
composer install
php artisan key:generate
npm install
php artisan wayfinder:generate --with-form --no-interaction

# 7. Configuración (APP_NAME, APP_URL, locale, timezone) — ver sección Configuración

# 8. Base de datos SQLite
touch database/database.sqlite
php artisan migrate --graceful

# 9. Laravel Boost
composer require laravel/boost --dev
php artisan boost:install --guidelines --skills --mcp --no-interaction

# 10. Calidad
php artisan about
php artisan migrate
php artisan test
npm run build
npm run check        # (no existe script "lint"; equivalente más cercano)
npm run types:check
composer lint:check   # Pint

# 11. Limpieza del scaffold temporal
rm -rf "E:/Proyectos/clinica-sarmiento-scaffold"

# 12. Herd
herd paths
herd parked
herd restart          # necesario para que resolviera el dominio .test
```

## Decisiones técnicas

- **Starter Kit React con TypeScript por defecto**: el flag `--react` del
  instalador de Laravel 13 ya provee TypeScript, Inertia, Tailwind y
  shadcn/ui integrados; no existe un flag separado `--typescript`.
- **Testing con Pest** (`--pest`), por ser el framework de testing por
  defecto de los starter kits actuales de Laravel.
- **Todas las features de autenticación del Starter Kit habilitadas**
  (registro, verificación de email, 2FA, passkeys, confirmación de
  contraseña), para reflejar la autenticación "estándar" completa pedida,
  sin recortes.
- **Scaffold temporal en carpeta hermana** (`E:\Proyectos\clinica-sarmiento-scaffold`),
  integrado luego mediante `robocopy` con exclusiones explícitas
  (`.git`, `vendor`, `node_modules`, artefactos generados, `.env`, `README.md`),
  preservando el `.git` y el `README.md` originales del repositorio.
  El scaffold temporal fue eliminado al finalizar la integración.
- **`vendor/` y `node_modules/` no se copiaron** desde el scaffold: se
  reinstalaron desde cero (`composer install`, `npm install`) directamente
  en `E:\Proyectos\Clinica-Sarmiento` para evitar artefactos con rutas
  absolutas de la carpeta temporal.
- **Locale `es` con fallback `en`**: dado que la aplicación es para una
  clínica argentina (Córdoba), se configuró español como locale principal
  (`APP_LOCALE=es`) manteniendo inglés como fallback de traducciones
  (`APP_FALLBACK_LOCALE=en`), y `es_AR` como locale de Faker.
- **Timezone `America/Argentina/Cordoba`**: configurado directamente en
  `config/app.php` (no vía variable de entorno), siguiendo la convención
  actual de Laravel para este valor.
- **`APP_URL=http://clinica-sarmiento.test`**: alineado con el dominio
  local servido por Herd.
- **Laravel Boost instalado con integración completa para Claude Code**
  (`--guidelines --skills --mcp`), generando `CLAUDE.md`, `.claude/skills/`
  y `.mcp.json`.

## Configuración realizada

`.env` y `.env.example`:

```
APP_NAME="Clínica Sarmiento"
APP_ENV=local
APP_DEBUG=true
APP_URL=http://clinica-sarmiento.test

APP_LOCALE=es
APP_FALLBACK_LOCALE=en
APP_FAKER_LOCALE=es_AR

DB_CONNECTION=sqlite
```

`config/app.php`:

```php
'timezone' => 'America/Argentina/Cordoba',
```

Ningún secreto ni credencial real fue incluido en archivos versionados;
`.env` permanece fuera de Git (ya excluido por `.gitignore` del propio
starter kit) y `.env.example` está documentado sin valores sensibles
(`APP_KEY` vacío).

## Problemas encontrados y solución

1. **`laravel new --no-interaction` no evitó un prompt interactivo**
   (`install:features`, selección de funcionalidades de autenticación) al
   ejecutarse como script de Composer dentro del propio proyecto generado.
   El comando `install:features` sí admite `--answers='<json>'` y
   `--no-interaction` de forma directa. Se ejecutó manualmente con las
   respuestas explícitas (todas las features habilitadas).

2. **Fallo de subprocesos (`composer lint`, `wayfinder:generate`) lanzados
   internamente por `install:features` vía `Symfony\Process` en Windows**,
   con el error `"C:\Users\LEONEL" no se reconoce como un comando interno o
   externo...` — causado por el espacio en la ruta de perfil de usuario
   (`C:\Users\LEONEL ALEGRE`) al resolverse el ejecutable de Composer sin
   pasar por una shell. Los pasos de transformación de archivos (selección
   de features) ya se habían aplicado correctamente antes de este punto, por
   lo que se completaron manualmente los pasos finales
   (`composer lint`, `php artisan wayfinder:generate --with-form`, borrado
   de `chisel.php` / `chisel-paths.php` / `InstallFeaturesCommand.php`,
   `npm run check:fix`), todos ejecutados con éxito desde Bash directamente.

3. **`robocopy` mal interpretado por Git Bash (MSYS)**: los flags que
   empiezan con `/` (p. ej. `/E`, `/XD`) fueron reescritos como rutas de
   archivo por la capa de conversión de rutas de MSYS, provocando un error
   de parámetro inválido. Se resolvió ejecutando el comando con
   `MSYS_NO_PATHCONV=1`.

4. **El dominio `http://clinica-sarmiento.test` no resolvía inicialmente**
   (`No se puede resolver el nombre remoto`), pese a que
   `E:\Proyectos` ya estaba parqueado en Herd y el sitio aparecía
   correctamente listado en `herd parked`. Se resolvió con `herd restart`
   (recarga de los servicios/DNS de Herd); tras el reinicio, el sitio
   respondió `HTTP 200`. No fue necesario ningún cambio de configuración
   global de Herd.

5. **Corrección menor propia**: al probar `herd park` desde dentro de
   `E:\Proyectos\Clinica-Sarmiento` (para diagnosticar el punto 4) se agregó
   por error esa carpeta como una ruta parqueada independiente. Se revirtió
   de inmediato con `herd unpark`, dejando la configuración de Herd
   exactamente como estaba (solo `E:\Proyectos` parqueado).

## Base de datos

SQLite, archivo `database/database.sqlite`. Migraciones aplicadas:

```
0001_01_01_000000_create_users_table
0001_01_01_000001_create_cache_table
0001_01_01_000002_create_jobs_table
2024_01_01_000000_create_passkeys_table
2025_08_14_170933_add_two_factor_columns_to_users_table
```

PostgreSQL queda pendiente para la Fase 2, según lo indicado.

## Resultados de calidad

- **`php artisan test`** → `39 passed (136 assertions)`, 0 fallos.
- **`npm run build`** → build exitoso (`✓ built in ~9s` la primera vez,
  `~2.7s` en rebuilds incrementales), manifest y assets generados en
  `public/build/`.
- **`npm run check`** (equivalente más cercano a "lint"; no existe un
  script llamado `lint` en `package.json`) → sin errores en el código de
  la aplicación. Señaló un problema de formato únicamente en el
  `README.md` original (raíz del repo); no se modificó ese archivo por
  instrucción explícita de preservarlo.
- **`npm run types:check`** (`tsc --noEmit`) → sin errores.
- **`composer lint:check`** (Laravel Pint) → `{"tool":"pint","result":"passed"}`.

## Laravel Boost

Instalado como dependencia de desarrollo (`composer require laravel/boost --dev`,
v2.7.0) y configurado con `php artisan boost:install --guidelines --skills --mcp --no-interaction`.
Generó:

- `CLAUDE.md` (guías de Laravel/Inertia/React/Pint/PHPUnit/Wayfinder/etc.)
- `.claude/skills/` (7 skills: fortify-development, inertia-react-development,
  infer-conventions, laravel-best-practices, tailwindcss-development,
  testing-best-practices, wayfinder-development)
- `.mcp.json` (servidor MCP `laravel-boost` vía `php artisan boost:mcp`)
- `AGENTS.md` / `.agents/` / `opencode.json` / `boost.json` (integración
  adicional para OpenCode, generada automáticamente por el instalador)

## Herd

- `E:\Proyectos` ya se encontraba parqueado en Herd.
- El proyecto es servido automáticamente como sitio dentro de esa ruta
  parqueada (no requirió `herd link` individual).
- URL local verificada: **http://clinica-sarmiento.test** → `HTTP 200`.
- PHP servido por Herd para el sitio: 8.4.
- No se realizaron cambios globales de configuración de Herd (el único
  cambio accidental —punto 5 de "Problemas encontrados"— fue revertido).

## URL local

**http://clinica-sarmiento.test**

## Alcance respetado

No se crearon módulos clínicos (pacientes, médicos, turnos, historias
clínicas, diagnósticos, recetas) ni roles/permisos de dominio. No se
instaló PostgreSQL, Redis ni Docker. No se configuró Nginx manualmente ni
VPS. No se realizaron commits ni push. No se inició la Fase 2.
