# MOD-006 — Decisiones tomadas

Registro de decisiones ya adoptadas para este módulo, con origen y fecha. El módulo sigue
bloqueado (ver `README.md`) por `RN-CLI-001`: ningún cálculo clínico se implementa sin
documentación validada por un profesional. Lo de acá son hechos ya confirmados por los médicos,
no habilitan todavía el diseño del cálculo en sí.

Origen de esta primera tanda: entrevista a médicos `INV-004`, ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

| ID | Decisión | Origen | Fecha | Documentos afectados |
|---|---|---|---|---|
| DEC-FOR-001 | Los médicos usan fórmulas oftalmológicas todos los días (uso diario, no ocasional); esto eleva la prioridad de destrabar el módulo | MÉDICOS (`Q-FOR-004`) | 2026-09-15 | `README.md` |
| DEC-FOR-002 | La clínica sí usa Treelan para calcular la adición de lentes de cerca. Resuelve a favor de los médicos (`Q-FOR-005`) la contradicción con `Q-FOR-002` de la Ronda 2 del cliente ("ninguno, se hace en papel"), que queda marcada como desactualizada en `cuestionario_cliente_ronda_2.md` | EQUIPO — confirmación directa del responsable del proyecto, sin nueva ronda formal al cliente | 2026-09-15 | `README.md`, `INV-002` en `investigaciones.md` |

## Investigación todavía pendiente

Confirmado el uso de Treelan, `INV-002` se reabre como investigación real (no como contradicción
sin resolver): falta conseguir acceso o un ejemplo/documentación de Treelan (retomar `Q-FOR-003`
del cliente, que vuelve a aplicar) para entender exactamente qué calcula, antes de poder diseñar
algo similar — sigue rigiendo `RN-CLI-001` (ningún cálculo clínico sin documentación validada por
un profesional). Ver
[`../../08_Pendientes/investigaciones.md`](../../08_Pendientes/investigaciones.md).

"Adicción" en la respuesta de `Q-FOR-005` se mantiene sin confirmar si era error de tipeo por
"adición" (término óptico de la graduación de cerca); no bloquea nada mientras tanto.

**Actualización 2026-09-24:** el segundo profesional que respondió, Eduardo Peña, contestó
"Ampina" a `Q-FOR-005` (Portillo Rivero había respondido Treelan). Por eso se **reabre
`INV-003`**: es posible que cada profesional use una herramienta distinta. `DEC-FOR-002` se
mantiene. Se pregunta al cliente en `Q-FOR-007` (Ronda 3) y se amplía el pedido de acceso de
`Q-FOR-003` a ambas herramientas. La respuesta de Peña a `Q-FOR-006` ("La base de datos. Lente
respuesta del proveedor") no se interpreta sin aclarar (`Q-FOR-008`).

El módulo sigue `IDENTIFICADO — BLOQUEADO por investigación documental` hasta conseguir esa
documentación de Treelan; no pasa a `EN_DESCUBRIMIENTO` todavía.

Ver [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md) para
cómo se gestionan cambios sobre decisiones ya tomadas después de que el módulo esté `APROBADO`.
