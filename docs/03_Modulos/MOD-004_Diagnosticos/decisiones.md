# MOD-004 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-DIA-001 | El diagnóstico se registra con una combinación de código estándar (tipo CIE-10) y texto libre, no solo con uno de los dos | MÉDICOS (`Q-DIA-001`) | 2026-09-15 | `alcance.md`, `datos.md` (a crear) |
| DEC-DIA-002 | Un paciente puede tener más de un diagnóstico activo al mismo tiempo | MÉDICOS (`Q-DIA-002`) | 2026-09-15 | modelo de dominio |
| DEC-DIA-003 | El sistema debe diferenciar un diagnóstico "presuntivo" (a confirmar) de uno ya confirmado | MÉDICOS (`Q-DIA-003`) | 2026-09-15 | `datos.md` (a crear), `reglas_negocio.md` (a crear) |

## Divergencia entre profesionales (2026-09-24)

Las decisiones de arriba salieron de las respuestas de Cecilia Portillo Rivero. Eduardo Peña
respondió distinto en dos puntos: registra el diagnóstico solo en **texto libre** (`Q-DIA-001`) y
**no** diferencia presuntivo de confirmado (`Q-DIA-003`). `DEC-DIA-001` y `DEC-DIA-003` se
mantienen hasta que el cliente resuelva en `Q-DIA-004` (Ronda 3). `DEC-DIA-002` coincide.

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
