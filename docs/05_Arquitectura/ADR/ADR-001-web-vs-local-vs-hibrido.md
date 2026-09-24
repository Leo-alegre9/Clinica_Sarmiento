# ADR-001 — Modelo de despliegue: web centralizada vs. local vs. híbrida

## Estado

`PROPUESTO / PENDIENTE` — no decidido. Origen del requerimiento: `CLIENTE` (`RC-013`).

## Contexto

El cliente pidió explícitamente **no tomar todavía** una decisión de despliegue, y analizar
formalmente las alternativas antes de decidir. La Fase 1 ya construida usa SQLite local sobre
Laravel Herd en un entorno de desarrollo Windows, lo cual no prejuzga la arquitectura de
producción.

## Problema

Definir si el sistema de producción será:

- **Web centralizada**: un servidor (propio o en la nube) accesible por Internet, con la
  clínica operando como cliente remoto.
- **Instalación local**: el sistema corre en un servidor/PC dentro de la clínica, sin depender
  de Internet para operar día a día.
- **Híbrida**: combinación (por ejemplo, operación local con sincronización periódica a la
  nube, o base local con exposición controlada para el portal público de turnos).

## Alternativas y dimensiones a comparar (ninguna evaluada todavía)

| Dimensión | Web centralizada | Local | Híbrida |
|---|---|---|---|
| Funcionamiento ante caída de Internet | Se interrumpe (o degrada) | No afectado | Depende del diseño |
| Seguridad | Responsabilidad del proveedor de hosting + la app | Responsabilidad total de la clínica | Mixta |
| Backups | Más simple de centralizar | Requiere infraestructura propia | Mixta |
| Mantenimiento/actualizaciones | Centralizado, más simple | Requiere visita/acceso remoto por sitio | Mixta |
| Acceso remoto (multi-sede futura) | Nativo | Requiere VPN u otra solución | Depende |
| Costos | Hosting recurrente | Hardware propio, sin costo recurrente de hosting | Ambos |
| Escalabilidad (más sedes, más usuarios) | Más simple | Limitada por hardware local | Depende |
| Portal público de turnos (`MOD-033`/`MOD-034`) | Natural (ya expuesto a Internet) | Requiere exponer selectivamente el sistema local | Requiere diseño explícito |

## Información faltante para decidir

- ¿La clínica ya cuenta con infraestructura de servidor propio, o partiría de cero?
- ¿Cuál es la tolerancia real a que el sistema no funcione ante una caída de Internet (¿la
  clínica sigue atendiendo en papel en ese caso, o se detiene la operación)?
- ¿Existe presupuesto para hosting recurrente, o se prefiere una inversión única en hardware
  local?
- ¿Quién sería responsable técnico del mantenimiento en cada escenario?
- Ver también `INV-005` en
  [`../../08_Pendientes/investigaciones.md`](../../08_Pendientes/investigaciones.md).

## Decisión

No tomada. Pendiente de la información anterior.

## Consecuencias

Mientras este ADR esté `PENDIENTE`, quedan también pendientes: la política de backups
(`MOD-037`, `RIE-007`), los requisitos de disponibilidad (`RNF-DIS-001`, `RNF-DIS-002`) y el
diseño de exposición del portal público (`MOD-033`, `MOD-034`).
