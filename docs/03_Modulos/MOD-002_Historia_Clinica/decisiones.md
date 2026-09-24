# MOD-002 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-HCL-001 | Al abrir la ficha de un paciente, antes de atenderlo, deben verse sin buscarlos: nombre, edad, obra social, procedencia | MÉDICOS (`Q-HCL-003`) | 2026-09-15 | `alcance.md`, `requerimientos.md` (a crear) |
| DEC-HCL-002 | El historial de consultas anteriores se muestra como un resumen con opción de expandir el detalle; no se mantiene el historial completo siempre visible | MÉDICOS (`Q-HCL-004`) | 2026-09-15 | `alcance.md`, diseño de UI |
| DEC-HCL-003 | Las alertas críticas (por ejemplo, alergia grave a un medicamento) se muestran como un aviso destacado siempre visible arriba de la ficha. Coincide con `DEC-PAC-012` (cliente pidió aviso destacado + ventana emergente); lo respondido acá es subconjunto, no contradice — se mantiene `DEC-PAC-012` completa | MÉDICOS (`Q-HCL-007`) | 2026-09-15 | `reglas_negocio.md` (a crear) |
| DEC-HCL-004 | La visibilidad de lo registrado por otras especialidades no sigue una regla fija ("todo visible" o "solo lo propio"): se decide caso por caso, a criterio clínico. El sistema necesita un mecanismo para compartir puntualmente un registro con otras especialidades cuando corresponda, no un permiso global por especialidad | EQUIPO — aclaración del responsable del proyecto sobre `Q-HCL-005` | 2026-09-15 | `alcance.md`, `reglas_negocio.md` (a crear), modelo de permisos |
| DEC-HCL-005 | Antecedentes/alergias que deben estar siempre visibles al abrir la ficha: alergias medicamentosas, antecedentes quirúrgicos relevantes, enfermedades crónicas. Coincide exactamente con `DEC-PAC-012` ya definida con el cliente, sin contradicción | EQUIPO — aclaración del responsable del proyecto sobre `Q-HCL-006` | 2026-09-15 | `alcance.md`, `reglas_negocio.md` (a crear) |

## Respuestas de un segundo profesional (2026-09-24)

Las decisiones de arriba salieron de las respuestas de Cecilia Portillo Rivero. Eduardo Peña
respondió el mismo cuestionario (ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md#respuestas-de-eduardo-peña`](../../08_Pendientes/cuestionario_medicos_ronda_1.md#respuestas-de-eduardo-peña)).
Donde las respuestas se contradicen, las decisiones vigentes **no se modifican** hasta que el
cliente resuelva (Ronda 3):

| Decisión | Divergencia | Pregunta de resolución |
|---|---|---|
| DEC-HCL-002 | Peña pide el historial completo siempre visible, no un resumen | `Q-HCL-008` |
| DEC-HCL-004 | Peña: todo visible para cualquier profesional tratante (coincide con `Q-PAC-038` del cliente); Portillo Rivero: caso por caso | `Q-HCL-009` |
| DEC-HCL-005 | Peña respondió "Ninguna" sobre antecedentes siempre visibles. No cambia la regla, que la fijó el cliente (`DEC-PAC-012`) | `Q-HCL-010` (confirmación) |

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
