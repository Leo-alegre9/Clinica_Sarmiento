# Documentos pendientes a obtener del cliente

| Documento | Motivo | Módulo(s) afectado(s) | Fuente | Estado |
|---|---|---|---|---|
| PDF de fórmulas oftalmológicas | Base para diseñar `MOD-006` sin inventar lógica clínica | MOD-006 | Cliente (`RC-005`) | **RECIBIDO 2026-09-08** ([`anexos/sistema_nuevo.pdf`](anexos/sistema_nuevo.pdf)) — parcial, ver `INV-001`: falta la fórmula de combinación lejos/cerca, a relevar con los médicos |
| Información/documentación de Treelan | Entender qué automatiza ese sistema | MOD-006 | Cliente (`RC-005`) | **CONFIRMADO EL USO 2026-09-15** — `INV-002` había cerrado como no aplica por respuesta del cliente, pero se confirmó que sí lo usan (contradicción resuelta a favor de los médicos, `Q-FOR-005`). Sigue faltando el acceso/documentación en sí para poder avanzar |
| Información de Ampina (si corresponde) | Comparar capacidades actuales | MOD-006 | Cliente (`RC-005`) | **PENDIENTE de nuevo (2026-09-24)**: se había descartado, pero Eduardo Peña menciona que usa Ampina (`Q-FOR-005`). `INV-003` reabierta |
| Datos de contacto de los médicos | Completar `MOD-015` y coordinar `INV-004` | MOD-015 | Hernán (`RC-010`) | PARCIAL — nombres conocidos (`sistema nuevo.pdf`, 2026-09-08): oftalmólogos Arkwright Ayelen, Coppini Emiliano, Rivera del Toro Luz; faltan matrícula, teléfono/email y horarios de cada uno |
| Requerimientos de los demás médicos | Completar el descubrimiento de módulos clínicos | Todos los clínicos | Médicos de la clínica (`RC-006`) | **RESPONDIDO 2026-09-15** (`INV-004`) — propagado a `decisiones.md` de cada módulo. Respondieron Cecilia Portillo Rivero y Eduardo Peña (identificados 2026-09-24); las divergencias entre ambos están en `cuestionario_cliente_ronda_3.md` |
| Estructura actual de obras sociales (convenios, planes que maneja la clínica) | Definir alcance real de `MOD-019` | MOD-019, MOD-020, MOD-021 | Cliente/administración | PENDIENTE |
| Ejemplos de recetas actuales | Diseñar `MOD-005` sin inventar formato | MOD-005 | Cliente/médicos | PENDIENTE |
| Ejemplos de formularios actuales (papel o digital) | Insumo para formularios de alta de paciente y solicitud de turnos | MOD-001, MOD-033 | Cliente | PENDIENTE |
| Circuitos administrativos actuales | Entender el proceso real antes de digitalizarlo | Varios | Cliente/administración | PENDIENTE |
| Forma actual de manejar cirugías (agenda, checklist, consentimientos) | Diseñar `MOD-013` con base real | MOD-013 | Cliente/médicos | PENDIENTE |
| Forma actual de manejar caja | Diseñar `MOD-022` con base real, dado que el cliente mismo señaló que necesita refinamiento importante | MOD-022, MOD-023, MOD-024 | Cliente/administración (Hernán, Eduardo, Melisa, Noelia) | PENDIENTE |
| Cualquier planilla o sistema actualmente utilizado | Evitar perder funcionalidad válida ya en uso al migrar | Todos | Cliente | PENDIENTE |

Ningún módulo que dependa de un documento listado aquí como `PENDIENTE` puede considerarse
`LISTO_PARA_VALIDACION` en las áreas que ese documento condiciona.
