# MOD-005 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-RET-001 | Datos obligatorios de toda receta, sin excepción: nombre genérico y/o comercial del medicamento, dosis y frecuencia, duración del tratamiento, diagnóstico asociado, firma y matrícula del profesional | MÉDICOS (`Q-RET-003`) | 2026-09-15 | `requerimientos.md` (a crear), `criterios_aceptacion.md` (a crear) |
| DEC-RET-002 | Las recetas ópticas registran esférico, cilíndrico y eje (ángulo); además puede especificarse filtro sugerido, tipo de vidrio, o si son lentes de contacto (lo que puede cambiar la receta original) | MÉDICOS (`Q-RET-004`) | 2026-09-15 | `datos.md` (a crear); insumo directo también para `MOD-006` |
| DEC-RET-003 | Debe poder repetirse/renovarse rápidamente una receta anterior del mismo paciente, sin recargar todos los datos de nuevo | MÉDICOS (`Q-RET-005`) | 2026-09-15 | `requerimientos.md` (a crear) |

## Divergencia entre profesionales (2026-09-24)

Las decisiones de arriba salieron de las respuestas de Cecilia Portillo Rivero. Eduardo Peña
marcó como indispensables en una receta solo el medicamento, el diagnóstico asociado y la firma y
matrícula (no dosis/frecuencia ni duración, `Q-RET-003`), no pidió datos ópticos adicionales
(`Q-RET-004`) y respondió que no necesita renovar recetas rápidamente (`Q-RET-005`). `DEC-RET-001`
y `DEC-RET-003` se mantienen hasta que el cliente resuelva en `Q-RET-006` (Ronda 3); `DEC-RET-002`
no se ve afectada.

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
