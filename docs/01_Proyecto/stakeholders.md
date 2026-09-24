# Stakeholders

Origen: `CLIENTE` (nombres y roles mencionados en las reuniones) + `ANÁLISIS` (roles inferidos
por tipo de sistema, pendientes de confirmación). No se infieren responsabilidades exactas sin
confirmar — cualquier alcance de rol abajo es hipótesis hasta validarse.

## Personas nombradas explícitamente por el cliente

| Nombre | Rol mencionado | Fuente | Estado |
|---|---|---|---|
| Hernán | Administrador (acceso a caja); contacto para datos de médicos (`RC-010`) | `RC-009`, `RC-010` | A confirmar rol exacto |
| Eduardo | Administrador (acceso a caja) | `RC-009` | A confirmar rol exacto |
| Melisa | Administrador (acceso a caja) | `RC-009` | A confirmar rol exacto |
| Noelia | Administrador (acceso a caja) | `RC-009` | A confirmar rol exacto |

**Importante:** estos nombres son usuarios iniciales candidatos a recibir un rol, no el
diseño del sistema de permisos. Los roles deben ser configurables y no estar atados a personas
específicas. Ver [`RC-009`](../02_Requerimientos/requerimientos_cliente_raw.md) y el futuro
`MOD-027 — Roles y permisos`.

## Grupos de stakeholders (a completar / confirmar)

| Grupo | Interés / rol esperado | Confirmado |
|---|---|---|
| Dirección / administración de la clínica | Define alcance, aprueba módulos, es la voz "CLIENTE" en esta documentación | Parcial — se desconoce si hay más de una persona con autoridad de aprobación además de quien da los requerimientos |
| Médicos / profesionales | Usuarios de agenda, historia clínica, cirugías, recetas, fórmulas; sus necesidades específicas **todavía no fueron relevadas** (`RC-006`) | No |
| Secretarios/as | Usuarios de agenda, turnos, recepción, caja, solicitudes públicas | No |
| Administración / caja | Usuarios de caja, pagos, reportes administrativos (probablemente Hernán/Eduardo/Melisa/Noelia) | Parcial |
| Pacientes | Usuarios externos del portal público de turnos; sujetos de la historia clínica | No |
| Responsable técnico / desarrollo | Mantiene el sistema, ejecuta esta fase de requisitos | Sí (este equipo) |
| Responsable de sistemas/IT de la clínica (si existe) | Backups, infraestructura, continuidad | Desconocido — registrar como pregunta |

## Pendiente

- Confirmar si existe un responsable de sistemas/IT en la clínica distinto de Hernán.
- Relevar necesidades de "los demás médicos" (`RC-006`) — ver
  [`INV-004`](../08_Pendientes/investigaciones.md) y
  [`../08_Pendientes/preguntas_medicos.md`](../08_Pendientes/preguntas_medicos.md).
- Confirmar quién tiene autoridad final para mover un módulo a `APROBADO` (¿el mismo
  interlocutor de estos requerimientos, o Dirección?).
