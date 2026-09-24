# MOD-001 — Alcance

**Estado del documento:** confirmado tras la Ronda 1 respondida por el cliente el 2026-09-08 y
las respuestas de los médicos (`INV-004`, 2026-09-24). Ver [`preguntas.md`](preguntas.md) y
[`decisiones.md`](decisiones.md). Los detalles que dependen de la Ronda 3 están marcados como
hipótesis en cada documento.

## Alcance confirmado

- Gestión de pacientes de una clínica multiespecialidad, con ficha **única compartida entre
  sedes** (la clínica ya opera más de una sede) — sin ningún campo o regla que asuma
  implícitamente "paciente oftalmológico" salvo lo intrínsecamente oftalmológico (que
  pertenece a `MOD-006`).
- Identificación del paciente por DNI (único, sin duplicados), cédula extranjera, pasaporte,
  DNI extranjero o CUIL/CUIT — o sin ningún documento, mediante código provisorio interno
  (recién nacidos, indocumentados).
- Datos personales (nombre, apellido, fecha de nacimiento, un solo campo de sexo/género,
  nacionalidad, necesidad especial de atención), domicilio obligatorio con localidad
  estructurada, contacto (teléfono y WhatsApp obligatorios, canal preferido, opt-out de
  comunicaciones no esenciales) y contacto de emergencia obligatorio.
- Responsables/tutores para menores de 18 años, modelados como referencia a un registro de
  `Paciente` existente (no como entidad aparte).
- Asociación con una o más obras sociales, con una principal, historial de coberturas
  anteriores y opción de atenderse particular puntualmente (relación con `MOD-019`).
- Alta (siempre con ficha completa, sin alta rápida), modificación, búsqueda (siempre incluye
  activos e inactivos), baja lógica (nunca elimina el registro) y reactivación.
- Estado del paciente: activo, inactivo (baja lógica), fallecido, fusionado.
- Antecedentes y alertas clínicas visibles siempre en la ficha (alergias a medicamentos,
  antecedentes quirúrgicos relevantes, enfermedades crónicas), con alerta destacada + ventana
  emergente. Confirmado también por los médicos (`INV-004`, `DEC-PAC-020`).
- Encabezado de la ficha con nombre, edad, obra social principal y procedencia (`Q-HCL-003`).
- Permisos por rol y acción según la matriz de [`reglas_negocio.md`](reglas_negocio.md).
- Fotografía (no prioritaria) y documentación adjunta (DNI escaneado, carnet de obra social,
  consentimientos firmados), cada una con su consentimiento correspondiente.
- Reglas de privacidad: todo el personal ve todos los datos por igual (decisión explícita del
  cliente, ver nota de riesgo en `decisiones.md`); la edición de antecedentes clínicos sí
  está restringida: recepción puede agregarlos (quedan pendientes de revisión médica), y
  modificarlos solo puede hacerlo el médico dentro de una ventana de corrección o un perfil
  directivo designado (hipótesis `Q-PAC-058` a `Q-PAC-060`).
- Auditoría de todos los cambios sobre la ficha, sin excepciones.
- Exportación/impresión de la ficha, auditada.
- Migración de pacientes desde el sistema anterior de la clínica (confirmado que hay datos a
  migrar, `Q-PAC-050`) — diseño del proceso corresponde a `MOD-040`.

## Fuera de alcance confirmado

- El diagnóstico, la evolución clínica detallada y las recetas **no** viven en este módulo:
  pertenecen a `MOD-002` (Historia Clínica), `MOD-003` (Consultas) y `MOD-005` (Recetas). Este
  módulo sostiene la ficha del paciente, no el contenido clínico de cada atención.
- La gestión de planes/afiliaciones detallada de obra social (vigencias, convenios) es de
  `MOD-019`/`MOD-020`; este módulo sostiene solo la referencia paciente↔obra social con los
  campos confirmados en `datos.md`.
- Un portal de autogestión del paciente **no está en los planes** del cliente (`Q-PAC-049`,
  confirmado 2026-09-08) — se mantiene fuera de alcance, ver
  [`../../01_Proyecto/fuera_de_alcance.md`](../../01_Proyecto/fuera_de_alcance.md).
- La solicitud pública de turnos no crea ni modifica fichas (hipótesis `RN-PAC-011`,
  `Q-PAC-068`); el alta completa se hace en recepción.

## En alcance, fuera del primer incremento de construcción

- Unificación de fichas duplicadas (`RF-PAC-012`, `RN-PAC-006`): hipótesis completa
  documentada, pero no se construye hasta que el cliente confirme `Q-PAC-054` a `Q-PAC-056`
  (`DEC-PAC-022`).

## Decisión de diseño (confirmada)

Este módulo se piensa para una clínica con múltiples pacientes atendidos por múltiples
profesionales de distintas especialidades, evitando cualquier campo o regla que asuma
implícitamente "paciente oftalmológico" salvo donde el dato sea intrínsecamente oftalmológico
(en cuyo caso pertenece a `MOD-006`, no a este módulo). Ver
[`../../01_Proyecto/vision.md`](../../01_Proyecto/vision.md).
