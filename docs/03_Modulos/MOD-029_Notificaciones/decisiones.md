# MOD-029 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-NOT-001 | Para avisar al profesional sobre cambios en su propia agenda (cancelaciones, turnos nuevos, recordatorio de cirugía próxima), el canal preferido es WhatsApp y notificación dentro del sistema. No se marcó email ni "no hace falta avisarme" | MÉDICOS (`Q-NOT-003`) | 2026-09-15 | `alcance.md`, `requerimientos.md` (a crear) |

`DEC-NOT-001` salió de las respuestas de Cecilia Portillo Rivero. Eduardo Peña eligió solo
WhatsApp. Hipótesis de análisis (`Requiere validación: SÍ`): el canal de aviso debería poder
configurarlo cada profesional, en vez de ser fijo para todos.

Nota: esto es la preferencia del profesional sobre avisos de su propia agenda, distinto de
`Q-NOT-001` (Ronda 2, canal preferido para avisos a pacientes), que también eligió WhatsApp como
canal principal — coherente entre sí, no hay contradicción.

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
