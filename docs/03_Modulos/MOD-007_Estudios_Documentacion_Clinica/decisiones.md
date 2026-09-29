# MOD-007 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-EST-001 | Los estudios que se solicitan con más frecuencia son: OCT (tomografía de coherencia óptica) de mácula o de nervio, retinografía, campo visual, e IOL (biometría para cálculo de lente intraocular) | MÉDICOS (`Q-EST-003`) | 2026-09-15 | `alcance.md` |
| DEC-EST-002 | Al llegar el resultado de un estudio, debe poder agregarse un comentario/interpretación propia dentro del sistema; no alcanza con tener solo el archivo adjunto | MÉDICOS (`Q-EST-004`) | 2026-09-15 | `requerimientos.md` (a crear) |
| DEC-EST-003 | Se suma a los estudios frecuentes de `DEC-EST-001` la **ecografía ocular**. Peña nombra el campo visual como "CVC" (campo visual computarizado), que es el mismo estudio ya listado | MÉDICOS (`Q-EST-003`, Eduardo Peña) | 2026-09-24 | `alcance.md` |

`DEC-EST-001` y `DEC-EST-002` salieron de las respuestas de Cecilia Portillo Rivero; Eduardo Peña
coincide en `Q-EST-004`.

Nota sobre `DEC-EST-001`: "IOL" en la respuesta se interpretó como biometría para cálculo de
lente intraocular, la lectura estándar del término en oftalmología; no se confirmó
explícitamente con el médico que respondió.

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
