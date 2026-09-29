# Actores del sistema

Actores identificados hasta ahora, a partir de los requerimientos crudos y del análisis del
inventario de módulos. Se amplía a medida que se refina cada módulo.

| Actor | Descripción | Interactúa principalmente con |
|---|---|---|
| **Paciente** | Persona atendida por la clínica. Actor externo (no autenticado) en el portal público; sujeto de datos en el resto del sistema. | MOD-001, MOD-033, MOD-034, MOD-010 |
| **Secretario/a de recepción** | Usuario interno que gestiona agenda, turnos, pacientes, check-in y, potencialmente, caja. | MOD-001, MOD-009, MOD-010, MOD-011, MOD-012 |
| **Médico / Profesional** | Usuario interno que atiende consultas y cirugías, registra historia clínica, diagnósticos, recetas y fórmulas. | MOD-002 a MOD-008, MOD-013 |
| **Administrador** | Usuario interno con acceso ampliado, incluida caja y configuración. Los administradores nombrados por el cliente (Hernán, Eduardo, Melisa, Noelia) son candidatos a este rol, no el rol en sí. | MOD-022 a MOD-028, MOD-036 |
| **Sistema (automatizado)** | Actor no humano: envía recordatorios, detecta duplicados, aplica reglas de auditoría. | MOD-014, MOD-028, MOD-029 |
| **Obra social (externa)** | Entidad externa referenciada por el sistema, no un usuario del sistema (salvo integración futura). | MOD-019 a MOD-021 |

## Pendiente de confirmar

- ¿Existen roles adicionales no mencionados (por ejemplo, "enfermero/a" o "técnico" para
  estudios)? Ver `RC-006` e [`INV-004`](../08_Pendientes/investigaciones.md).
- ¿El "administrador" y el "médico" pueden ser la misma persona en distintos momentos (un
  médico dueño de la clínica que también administra la caja)? Afecta si los roles son
  excluyentes o combinables — ver `MOD-027`.
