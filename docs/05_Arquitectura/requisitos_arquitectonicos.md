# Requisitos arquitectónicos

Origen: `ANÁLISIS` sobre la base de la Fase 1 ya construida y de los requerimientos crudos.
Ninguno de estos requisitos es una decisión nueva; documentan lo ya definido y lo que queda
pendiente.

## Ya definido (Fase 1, confirmado)

- Arquitectura monolítica: Laravel + Inertia + React, sin API REST pública separada para el
  frontend propio. Ver [`../../docs/architecture.md`](../../docs/architecture.md).
- Autenticación vía Laravel Fortify (Starter Kit oficial).
- Base de datos SQLite temporal; PostgreSQL previsto sin fecha definida.

## Pendiente de definir

- **Modelo de despliegue** — ver [`ADR/ADR-001-web-vs-local-vs-hibrido.md`](ADR/ADR-001-web-vs-local-vs-hibrido.md).
- **Necesidad de API pública** — el `README.md` original menciona APIs "cuando sean
  necesarias para aplicaciones móviles, integraciones externas, WhatsApp, otros sistemas". No
  hay compromiso de construir una todavía; se evalúa módulo por módulo (por ejemplo,
  `MOD-033`/`MOD-034` para el portal público podrían no necesitar una API pública si el portal
  se sirve desde el mismo monolito Inertia).
- **Colas/trabajos en segundo plano** — probablemente necesarios para `MOD-014`
  (recordatorios) y `MOD-029`-`MOD-031` (notificaciones), no implementados todavía.
- **Almacenamiento de archivos** — necesario para `MOD-001` (documentación/fotos),
  `MOD-007` (estudios) y `MOD-005` (recetas en PDF); proveedor y estrategia
  `PENDIENTE_DEFINICION`, depende de `ADR-001`.

Ver también [`seguridad.md`](seguridad.md), [`escalabilidad.md`](escalabilidad.md) e
[`integraciones.md`](integraciones.md).
