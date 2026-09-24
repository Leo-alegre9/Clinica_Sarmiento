# Supuestos

Origen: `ANÁLISIS`. Todo supuesto listado aquí **requiere validación** y no debe usarse como
base de una decisión de diseño irreversible sin confirmarlo primero con el cliente.

| ID | Supuesto | Impacta en | Requiere validación |
|---|---|---|---|
| SUP-001 | La clínica opera en una única sede física por el momento, pero el modelo debe soportar más de una sede en el futuro. | `MOD-017`, `MOD-018`, `MOD-009` | SÍ |
| SUP-002 | El "sistema anterior" mencionado en el `README.md` original (versión previa de Clínica Sarmiento) contiene datos históricos que eventualmente deberán migrarse o consultarse como referencia. | `MOD-040` (Importación/exportación), `01_Proyecto/vision.md` | SÍ |
| SUP-003 | Ampina y Treelan son sistemas de terceros ya utilizados por la clínica o por los médicos, no sistemas a construir. | `MOD-006`, `INV-002`, `INV-003` | SÍ |
| SUP-004 | Los administradores nombrados (Hernán, Eduardo, Melisa, Noelia) no son necesariamente los únicos usuarios del sistema; hay al menos secretarios/as y médicos adicionales sin nombrar todavía. | `MOD-026`, `MOD-027`, `01_Proyecto/stakeholders.md` | SÍ |
| SUP-005 | La clínica factura/gestiona obras sociales de forma manual o semi-manual actualmente (no se mencionó un sistema de liquidación existente). | `MOD-019`, `MOD-020`, `MOD-021` | SÍ |
| SUP-006 | El dominio institucional de la página pública ya existe o está definido fuera de este sistema; el módulo de solicitud pública de turnos se integra a un sitio existente o futuro, no lo reemplaza. | `MOD-033`, `MOD-034` | SÍ |
| SUP-007 | El horario de atención de la clínica es diurno/comercial, sin urgencias 24 h (no se mencionaron guardias). | `RNF` de disponibilidad, `MOD-009` | SÍ |
| SUP-008 | Los recordatorios de turnos/cirugías se enviarán preferentemente por WhatsApp y/o SMS/email, dado que el cliente mencionó explícitamente "avisar" sin especificar medio. | `MOD-014`, `MOD-030`, `MOD-031` | SÍ |

Cada supuesto que se confirme se mueve a "Información confirmada" del módulo correspondiente y
se elimina de esta tabla (o se marca `CONFIRMADO` con fecha). Cada supuesto que se refute se
marca `DESCARTADO` con el motivo, sin borrarse del historial.
