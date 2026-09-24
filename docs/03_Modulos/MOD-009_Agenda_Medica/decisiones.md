# MOD-009 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md)
(bloque "Agenda — desde la mirada del profesional").

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-AGE-001 | Para organizar el día, el profesional necesita ver en su agenda, además del nombre y horario del paciente: motivo de la consulta y obra social. No se marcó "si es primera vez o control" ni "alertas clínicas del paciente" como necesarios | MÉDICOS (`Q-AGE-005`) | 2026-09-15 | `alcance.md`, diseño de UI |
| DEC-AGE-002 | Cada profesional necesita ver solo su propia agenda, no la de otros profesionales o consultorios | MÉDICOS (`Q-AGE-006`) | 2026-09-15 | `alcance.md`, `reglas_negocio.md` (a crear) |
| DEC-AGE-003 | La agenda del profesional también debe mostrar **si el turno es primera vez o control**. Complementa `DEC-AGE-001`: Portillo Rivero no lo había marcado y Peña sí | MÉDICOS (`Q-AGE-005`, Eduardo Peña) | 2026-09-24 | `alcance.md`, diseño de UI |

`DEC-AGE-001` y `DEC-AGE-002` salieron de las respuestas de Cecilia Portillo Rivero; Eduardo Peña
coincide en `Q-AGE-006` (solo la agenda propia).

## Nota

La pregunta de cierre exploratoria del cuestionario de médicos (`CIERRE-001`) pidió una "agenda
quirúrgica" separada de la agenda general. Se resolvió (`INV-008`, 2026-09-15) que es una
**extensión de `MOD-013`** (Cirugías), que ya preveía una agenda diferenciada de este módulo
según `RC-002` — no cambia el alcance de `MOD-009`. Ver
[`../MOD-013_Cirugias/decisiones.md`](../MOD-013_Cirugias/decisiones.md).

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
