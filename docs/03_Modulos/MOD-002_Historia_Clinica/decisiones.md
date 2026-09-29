# MOD-002 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-HCL-001 | Al abrir la ficha de un paciente, antes de atenderlo, deben verse sin buscarlos: nombre, edad, obra social, procedencia (localidad y quién lo derivó, `Q-PAC-064`, `CR-001` de `MOD-001`) | MÉDICOS (`Q-HCL-003`) | 2026-09-15 | `alcance.md`, `requerimientos.md` (a crear) |
| DEC-HCL-002 | El historial de consultas anteriores se muestra como un resumen con opción de expandir el detalle; no se mantiene el historial completo siempre visible | MÉDICOS (`Q-HCL-004`) | 2026-09-15 | `alcance.md`, diseño de UI |
| DEC-HCL-003 | Las alertas críticas (por ejemplo, alergia grave a un medicamento) se muestran como un aviso destacado siempre visible arriba de la ficha. Coincide con `DEC-PAC-012` (cliente pidió aviso destacado + ventana emergente); lo respondido acá es subconjunto, no contradice — se mantiene `DEC-PAC-012` completa | MÉDICOS (`Q-HCL-007`) | 2026-09-15 | `reglas_negocio.md` (a crear) |
| DEC-HCL-004 | La visibilidad de lo registrado por otras especialidades no sigue una regla fija ("todo visible" o "solo lo propio"): se decide caso por caso, a criterio clínico. El sistema necesita un mecanismo para compartir puntualmente un registro con otras especialidades cuando corresponda, no un permiso global por especialidad | EQUIPO — aclaración del responsable del proyecto sobre `Q-HCL-005` | 2026-09-15 | `alcance.md`, `reglas_negocio.md` (a crear), modelo de permisos |
| DEC-HCL-005 | Antecedentes/alergias que deben estar siempre visibles al abrir la ficha: alergias medicamentosas, antecedentes quirúrgicos relevantes, enfermedades crónicas. Coincide exactamente con `DEC-PAC-012` ya definida con el cliente, sin contradicción | EQUIPO — aclaración del responsable del proyecto sobre `Q-HCL-006` | 2026-09-15 | `alcance.md`, `reglas_negocio.md` (a crear) |
| DEC-HCL-006 | Cada médico elige cómo ver el historial de consultas anteriores: resumen con opción de ver el detalle, o historial completo siempre visible. Es una preferencia por usuario. Reemplaza `DEC-HCL-002` | CLIENTE (`Q-HCL-008`, Ronda 3) | 2026-09-26 | `alcance.md`, diseño de UI, preferencias de usuario |
| DEC-HCL-007 | Lo que registra cada especialidad en la historia clínica lo ve esa especialidad; el médico comparte puntualmente lo que haga falta con otras. Confirma y precisa `DEC-HCL-004`: la regla por defecto es "cada especialidad ve lo suyo", y compartir es una acción explícita del médico. No alcanza a la ficha del paciente (`MOD-001`), que ve todo el personal (`Q-PAC-069`). Queda para el refinamiento de este módulo qué ve recepción de las consultas, porque `DEC-PAC-013` dice que todo el personal ve la historia clínica | CLIENTE (`Q-HCL-009`, Ronda 3) | 2026-09-26 | `alcance.md`, `reglas_negocio.md` (a crear), modelo de permisos |
| DEC-HCL-008 | Se mantiene el aviso destacado de alergias, cirugías previas y enfermedades crónicas para todos los médicos. Confirma `DEC-HCL-005` y `DEC-PAC-012` | CLIENTE (`Q-HCL-010`, Ronda 3) | 2026-09-26 | `reglas_negocio.md` (a crear) |

## Respuestas de un segundo profesional (2026-09-24)

Las decisiones de arriba salieron de las respuestas de Cecilia Portillo Rivero. Eduardo Peña
respondió el mismo cuestionario (ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md#respuestas-de-eduardo-peña`](../../08_Pendientes/cuestionario_medicos_ronda_1.md#respuestas-de-eduardo-peña)).
Las divergencias se resolvieron en la Ronda 3 (2026-09-26). Los dos médicos son oftalmólogos
(`Q-MED-005`), así que las diferencias no se explican por especialidad:

| Decisión | Divergencia | Resolución |
|---|---|---|
| DEC-HCL-002 | Peña pide el historial completo siempre visible, no un resumen | `Q-HCL-008`: cada médico elige → `DEC-HCL-006` (reemplaza a `DEC-HCL-002`) |
| DEC-HCL-004 | Peña: todo visible para cualquier profesional tratante (coincide con `Q-PAC-038` del cliente); Portillo Rivero: caso por caso | `Q-HCL-009`: cada especialidad ve lo suyo y el médico comparte → `DEC-HCL-007` |
| DEC-HCL-005 | Peña respondió "Ninguna" sobre antecedentes siempre visibles. No cambia la regla, que la fijó el cliente (`DEC-PAC-012`) | `Q-HCL-010`: se mantiene → `DEC-HCL-008` |

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
