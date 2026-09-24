# MOD-013 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. Una decisión listada
aquí **ya se aplicó** en el resto de los documentos del módulo; una hipótesis todavía no
confirmada vive en `alcance.md`/`preguntas.md` (a crear cuando el módulo entre en refinamiento
completo), no aquí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-CIR-001 | Checklist prequirúrgico, a completar antes de que el paciente ingrese: prequirúrgicos completos, exámenes oftalmológicos, y consentimiento informado firmado (obligatorio, sin excepción). Consistente con `Q-CIR-002` de la Ronda 2 del cliente (consentimiento ya definido como obligatorio) | MÉDICOS (`Q-CIR-005`) | 2026-09-15 | `alcance.md`, `criterios_aceptacion.md` (a crear) |
| DEC-CIR-002 | El día de la cirugía, la información crítica que debe estar a mano de forma inmediata es: motivo de la cirugía y antecedentes del paciente | MÉDICOS (`Q-CIR-006`) | 2026-09-15 | diseño de UI (vista del día de cirugía) |
| DEC-CIR-003 | La "agenda quirúrgica" pedida en la pregunta de cierre del cuestionario de médicos (`CIERRE-001`) es una extensión de este módulo, no un módulo/vista nueva ni parte de `MOD-009` | EQUIPO — resolución directa del responsable del proyecto sobre `INV-008` | 2026-09-15 | `alcance.md` |
| DEC-CIR-004 | Detalle de los prequirúrgicos de `DEC-CIR-001`: exámenes de laboratorio y ECG, y estudios oftalmológicos (ecografía, más ecometría y/o IOL Master) | MÉDICOS (`Q-CIR-005`, Eduardo Peña) | 2026-09-24 | `alcance.md`, `criterios_aceptacion.md` (a crear) |
| DEC-CIR-005 | El día de la cirugía, además del motivo y los antecedentes (`DEC-CIR-002`), deben estar a mano la ecometría, el OCT y el IOL (biometría) | MÉDICOS (`Q-CIR-006`, Eduardo Peña) | 2026-09-24 | diseño de UI (vista del día de cirugía) |

`DEC-CIR-001` y `DEC-CIR-002` salieron de las respuestas de Cecilia Portillo Rivero; lo aportado
por Eduardo Peña las complementa, no las contradice. Peña no propuso nada nuevo en la pregunta de
cierre.

Consistente con lo ya previsto para `MOD-013` (agenda de cirugías diferenciada de la agenda de
consultas comunes, según `RC-002`) — ver
[`../../08_Pendientes/investigaciones.md`](../../08_Pendientes/investigaciones.md) (`INV-008`,
resuelta).

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
