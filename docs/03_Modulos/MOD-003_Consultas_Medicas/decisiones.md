# MOD-003 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-CON-001 | Cada consulta registra, más allá del motivo de consulta: examen físico/oftalmológico, diagnóstico, e indicaciones o tratamiento. No se marcó "próximo control sugerido" como necesario | MÉDICOS (`Q-CON-002`) | 2026-09-15 | `alcance.md`, `requerimientos.md` (a crear) |
| DEC-CON-002 | La estructura de la consulta cambia según la especialidad (no hay un formato común único) | MÉDICOS (`Q-CON-003`) | 2026-09-15 | `alcance.md`, modelo de dominio |
| DEC-CON-003 | Para Oftalmología específicamente, la consulta registra: agudeza visual con y sin corrección; presión intraocular (indicando con qué aparato se mide); y, opcional, medición de ARM (autorrefractómetro) | MÉDICOS (`Q-CON-004`) | 2026-09-15 | `datos.md` (a crear), diseño de plantilla de consulta oftalmológica |
| DEC-CON-004 | Cada consulta también debe poder registrar el **próximo control sugerido**. Complementa `DEC-CON-001` (Portillo Rivero no lo había marcado; Peña sí) | MÉDICOS (`Q-CON-002`, Eduardo Peña) | 2026-09-24 | `alcance.md`, `requerimientos.md` (a crear) |

## Divergencia entre profesionales (2026-09-24)

`DEC-CON-001` a `DEC-CON-003` salieron de las respuestas de Cecilia Portillo Rivero. Eduardo Peña
respondió que la consulta tiene un **formato común para todas las especialidades** (`Q-CON-003`)
y que **no** necesita registrar mediciones específicas (`Q-CON-004`). `DEC-CON-002`/`DEC-CON-003`
se mantienen hasta que el cliente resuelva en `Q-CON-005` (Ronda 3). La diferencia podría
explicarse porque atienden especialidades distintas (`Q-MED-005`).

## Nota

Solo se relevó el detalle de estructura de consulta (`Q-CON-004`) para Oftalmología. El contenido
concreto para el resto de las especialidades que ofrezca la clínica (ver `Q-ESC-001`, Ronda 2 del
cliente, para el listado) se releva más adelante, cuando esas especialidades se incorporen al
sistema — decisión del responsable del proyecto, 2026-09-15. No bloquea el refinamiento de este
módulo para Oftalmología.

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
