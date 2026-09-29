# Glosario

Términos usados de forma consistente en toda la documentación de `/Docs`. Se amplía a medida
que se refinan módulos.

| Término | Significado en este proyecto |
|---|---|
| **Paciente** | Persona sujeto de atención clínica en la clínica. Ver `MOD-001`. |
| **Profesional / Médico** | Persona que brinda atención clínica. Se modela como "profesional" con una o más especialidades, para no acoplar el sistema únicamente a oftalmología. Ver [`vision.md`](vision.md). |
| **Especialidad** | Área de práctica de un profesional (p. ej. Oftalmología). Permite escalar a otras especialidades en el futuro. |
| **Turno** | Reserva de un horario de agenda para una consulta u otra práctica. |
| **Agenda** | Conjunto de horarios disponibles/ocupados de un profesional (o consultorio) en un período. Puede haber agendas diferenciadas por tipo (consultas, cirugías) — ver `RC-001`, `RC-002`. |
| **Consulta** | Atención médica común, no quirúrgica. |
| **Cirugía** | Práctica quirúrgica programada, con agenda y necesidades de recordatorio propias — ver `RC-002`. |
| **Historia clínica** | Registro longitudinal de la atención de un paciente: consultas, diagnósticos, recetas, estudios, evoluciones. |
| **Fórmula oftalmológica** | Documento/registro específico de oftalmología (graduación de lentes u otro valor clínico), pendiente de especificación — ver `RC-005`, `INV-001`, `INV-002`, `INV-003`. |
| **Obra social** | Entidad de cobertura médica de un paciente. Alcance funcional pendiente de definir — ver `RC-004`. |
| **Afiliación** | Relación entre un paciente y una obra social/plan, con número de afiliado y vigencia. |
| **Caja** | Registro de movimientos de dinero (cobros, egresos) de la clínica, con apertura y cierre — ver `RC-008`. |
| **Check-in / Recepción** | Registro de la llegada efectiva de un paciente a la clínica, distinto de la hora programada del turno — ver `RC-007`. |
| **Cola de espera / prioridad** | Orden en que se atiende a los pacientes presentes, no necesariamente por orden de llegada — ver `RC-007`. |
| **Rol** | Conjunto de permisos asignable a un usuario. No atado a personas específicas — ver `RC-009`. |
| **Sede** | Ubicación física de la clínica. Hoy se asume una sola sede; el modelo debe permitir más de una en el futuro — ver `MOD-018`. |
| **Consultorio** | Espacio físico dentro de una sede donde se atiende. |
| **Requerimiento crudo (`RC-###`)** | Apunte textual, sin refinar, tomado de una reunión con el cliente. Ver [`../02_Requerimientos/requerimientos_cliente_raw.md`](../02_Requerimientos/requerimientos_cliente_raw.md). |
| **Módulo (`MOD-###`)** | Agrupación funcional cohesiva del sistema, con su propio ciclo de refinamiento y aprobación. |
| **Definition of Ready (documental)** | Checklist mínima para que un módulo pueda presentarse a validación. Ver [`../00_Gobernanza/definition_of_ready.md`](../00_Gobernanza/definition_of_ready.md). |
| **PENDIENTE_DEFINICION** | Marcador explícito de que una decisión no fue tomada y no debe asumirse. |

Este glosario se actualiza cada vez que un módulo introduce un término de negocio nuevo o
redefine uno existente (registrar el cambio en `decisiones.md` del módulo correspondiente).
