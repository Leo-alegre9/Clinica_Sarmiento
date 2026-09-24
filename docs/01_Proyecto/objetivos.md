# Objetivos

## Objetivos de esta fase (Ingeniería de Requisitos)

Origen: `CLIENTE` (instrucción explícita de abrir esta etapa antes de construir).

1. Producir una fuente única de verdad funcional y técnica (`/Docs`) con trazabilidad completa
   entre necesidad del cliente → requerimiento → módulo → historia de usuario → caso de uso →
   regla de negocio → criterio de aceptación → implementación → prueba.
2. Levantar un inventario de módulos y clasificar qué existe hoy en el código, qué está
   planificado y qué es nuevo.
3. Refinar el primer módulo (Pacientes) hasta `LISTO_PARA_VALIDACION` mediante preguntas
   explícitas al cliente, sin asumir respuestas.
4. Dejar registradas las investigaciones y decisiones pendientes que condicionan otros módulos
   (fórmulas oftalmológicas, Treelan, obras sociales, arquitectura web/local, backups).

## Objetivos del sistema (a validar progresivamente, módulo por módulo)

Estos objetivos son una síntesis de los requerimientos crudos (`RC-001` a `RC-013`, ver
[`../02_Requerimientos/requerimientos_cliente_raw.md`](../02_Requerimientos/requerimientos_cliente_raw.md))
y **no** deben leerse como alcance cerrado:

- Agendar consultas y cirugías en agendas diferenciadas, con recordatorios automáticos para
  cirugías.
- Permitir la solicitud pública de turnos desde la página institucional, con un modelo de
  confirmación aún por definir (`RC-003`).
- Gestionar la cobertura de obras sociales de los pacientes con alcance por determinar
  (`RC-004`).
- Registrar y, eventualmente, asistir con fórmulas oftalmológicas, sujeto a investigación
  documental previa (`RC-005`).
- Gestionar la llegada de pacientes y una posible cola de espera con prioridades (`RC-007`).
- Operar una caja con apertura/cierre, cobros y egresos, con roles de acceso configurables
  (`RC-008`, `RC-009`).
- Sostener backups con política a definir (`RC-011`).

## Objetivos no funcionales transversales (hipótesis de análisis, a validar)

Origen: `ANÁLISIS`. Ver detalle en
[`../02_Requerimientos/requerimientos_no_funcionales.md`](../02_Requerimientos/requerimientos_no_funcionales.md).

- Seguridad y confidencialidad de información clínica y financiera.
- Auditoría de cambios sobre datos sensibles.
- Disponibilidad razonable durante el horario de atención de la clínica.
- Extensibilidad hacia nuevas especialidades, profesionales y sedes sin reescritura del modelo.

## No son objetivos de esta fase

- Escribir código de producción de módulos clínicos o administrativos.
- Tomar decisiones de arquitectura de despliegue (web/local/híbrida) — queda como
  [`ADR-001`](../05_Arquitectura/ADR/ADR-001-web-vs-local-vs-hibrido.md), `PROPUESTO/PENDIENTE`.
- Definir lógica clínica u oftalmológica sin la documentación de referencia del cliente.
