# MOD-001 — Requerimientos funcionales

Estado por requerimiento según
[`../../00_Gobernanza/estados_requerimientos.md`](../../00_Gobernanza/estados_requerimientos.md).
La mayoría pasó de `PROPUESTO` a `CONFIRMADO` tras la Ronda 1 respondida por el cliente el
2026-09-08 (ver [`preguntas.md`](preguntas.md), [`decisiones.md`](decisiones.md)). Origen
`ANÁLISIS` salvo donde se cite un `RC-###`/`Q-PAC-###` explícito de origen `CLIENTE`, o
`EQUIPO` para las 3 preguntas internas resueltas sin el cliente.

| ID | Requerimiento | Origen | Estado | Preguntas relacionadas |
|---|---|---|---|---|
| RF-PAC-001 | El sistema debe permitir dar de alta un paciente nuevo, siempre con la ficha completa (sin alta rápida en dos pasos). Campos obligatorios: DNI (o tipo de documento alternativo), obra social, nombre y apellido, fecha de nacimiento, teléfono, domicilio (con subcampo de localidad/zona estructurado). Requiere registrar el consentimiento de tratamiento de datos en el alta presencial. | CLIENTE | CONFIRMADO | Q-PAC-001 a Q-PAC-012, Q-PAC-035, Q-PAC-043 a Q-PAC-045 |
| RF-PAC-002 | El sistema debe permitir buscar pacientes por DNI, nombre/apellido y número de afiliado de obra social, mostrando siempre tanto activos como inactivos (sin ocultar estos últimos por defecto ni por antigüedad). | CLIENTE | CONFIRMADO | Q-PAC-014, Q-PAC-015, Q-PAC-051 |
| RF-PAC-003 | Al dar de alta, el sistema debe detectar posibles duplicados. (a) Si coincide **exactamente el tipo y número de documento** con otro paciente, **impide** el alta y ofrece abrir la ficha existente o corregir el documento mal cargado (`RN-PAC-001`). (b) Si coinciden nombre y fecha de nacimiento, o el número de afiliado de obra social, **advierte** mostrando la ficha existente y permite continuar si recepción confirma que son personas distintas. El número de afiliado sirve como dato adicional para confirmar la identidad. | CLIENTE + ANÁLISIS (resolución de la contradicción `Q-PAC-001`/`Q-PAC-016`) | CONFIRMADO | Q-PAC-001, Q-PAC-002, Q-PAC-016, Q-PAC-057 |
| RF-PAC-004 | El sistema debe permitir modificar los datos de un paciente existente, con auditoría de todos los cambios (`RF-PAC-015`). | CLIENTE | CONFIRMADO | Q-PAC-017, Q-PAC-037 |
| RF-PAC-005 | El sistema debe permitir dar de baja **lógicamente** a un paciente (nunca eliminación física, por la obligación legal de conservar la historia clínica) y reactivarlo posteriormente. Ejecutan la baja el administrador o un médico específico designado para ese caso. Al dar de baja a un paciente con turnos futuros, el sistema lo avisa y lista esos turnos, sin cancelarlos automáticamente; un paciente dado de baja no recibe turnos nuevos hasta que se lo reactive (`Q-PAC-062`). El permiso de baja para médicos lo asigna Dirección (`Q-PAC-061`). | CLIENTE | CONFIRMADO | Q-PAC-013, Q-PAC-039, Q-PAC-061, Q-PAC-062 |
| RF-PAC-006 | El sistema debe permitir registrar el fallecimiento de un paciente (solo administración puede hacerlo). Al registrarlo, el sistema **no** ejecuta ninguna acción automática sobre turnos futuros, recordatorios u obra social vigente: cada caso se revisa manualmente. Un fallecimiento registrado por error solo puede revertirlo administración, con motivo obligatorio (`Q-PAC-063`). | CLIENTE | CONFIRMADO | Q-PAC-041, Q-PAC-042, Q-PAC-063 |
| RF-PAC-007 | El sistema debe permitir asociar a un paciente una o más obras sociales, marcando cuál es la principal, conservando el historial de coberturas anteriores al cambiar de obra social. Por cada afiliación se registra: número de afiliado, plan/categoría, titular o familiar a cargo. Un paciente con obra social vigente puede optar por atenderse como particular en una consulta puntual. | CLIENTE | CONFIRMADO | Q-PAC-018 a Q-PAC-021 |
| RF-PAC-008 | El sistema debe permitir registrar uno o más responsables/tutores para pacientes menores de 18 años. Un responsable se modela como referencia a un registro de `Paciente` existente (no como entidad aparte), dado que frecuentemente también es paciente de la clínica. Al alcanzar la mayoría de edad, el vínculo se conserva como dato histórico (no se desvincula automáticamente). | CLIENTE | CONFIRMADO | Q-PAC-022 a Q-PAC-025 |
| RF-PAC-009 | El sistema debe permitir registrar datos de contacto del paciente (teléfono y WhatsApp obligatorios, si son distintos entre sí) y un contacto de emergencia, obligatorio siempre. El paciente puede indicar un canal de contacto preferido y optar por no recibir comunicaciones que no sean el aviso de su turno. | CLIENTE | CONFIRMADO | Q-PAC-026, Q-PAC-027, Q-PAC-047, Q-PAC-048 |
| RF-PAC-010 | El sistema debe permitir adjuntar a la ficha del paciente: DNI escaneado, carnet de obra social y consentimientos firmados. La fotografía del paciente es deseable pero no prioritaria, y su uso requiere un consentimiento separado del consentimiento general de tratamiento de datos. | CLIENTE | CONFIRMADO | Q-PAC-028, Q-PAC-029, Q-PAC-046 |
| RF-PAC-011 | El sistema debe permitir registrar antecedentes y alertas clínicas visibles siempre en la ficha del paciente (no solo dentro de cada consulta): alergias a medicamentos, antecedentes quirúrgicos relevantes, enfermedades crónicas. Las alertas críticas se muestran con un aviso destacado permanente **y** una ventana emergente al abrir la ficha. Administración/recepción también pueden **agregar** antecedentes y alertas; quedan marcados "pendiente de revisión médica" (y se muestran igual) hasta que un médico los confirma. **Modificar o eliminar** uno existente queda reservado al médico y a los perfiles directivos designados (`RF-PAC-018`; `Q-PAC-060` concilia `Q-PAC-032` con `Q-PAC-037`). Los médicos confirmaron las tres categorías y el aviso destacado (`Q-HCL-006`, `Q-HCL-007`, `INV-004`, 2026-09-24). | CLIENTE + MÉDICOS | CONFIRMADO | Q-PAC-030 a Q-PAC-032, Q-HCL-006, Q-HCL-007, Q-PAC-060 |
| RF-PAC-012 | El sistema debe permitir unificar dos fichas que resultan ser la misma persona, detectadas después del alta. Solo Dirección/administración; se elige la ficha que queda; todo lo del otro registro (historia clínica, turnos, pagos, coberturas, adjuntos, responsables) pasa a la ficha que queda; antecedentes y alertas se suman sin descartar ninguno; el otro registro queda `Fusionado`, sin borrarse; sin deshacer automático; todo auditado. | ANÁLISIS, confirmado por CLIENTE | CONFIRMADO (2026-09-26, `Q-PAC-054` a `Q-PAC-056`). Se construye en un incremento posterior al primero (`DEC-PAC-025`) | Q-PAC-016, Q-PAC-054, Q-PAC-055, Q-PAC-056 |
| RF-PAC-013 | El sistema debe permitir registrar y atender a pacientes sin ningún documento de identidad, extranjeros (pasaporte, DNI de su país, CUIL/CUIT, o cédula de identidad extranjera) o recién nacidos sin DNI tramitado (identificados con un código provisorio interno, editando el mismo registro cuando se obtenga el documento real). El sistema distingue explícitamente "sin documento" de "documento en trámite". El campo de documento no exige formato de DNI argentino. | CLIENTE + EQUIPO (`Q-PAC-005`, `Q-PAC-008`) | CONFIRMADO | Q-PAC-003, Q-PAC-004, Q-PAC-005 a Q-PAC-010 |
| RF-PAC-014 | El sistema debe permitir que todo el personal autenticado vea la historia clínica y todos los datos de cualquier paciente, sin distinción de permisos entre datos administrativos y clínicos a nivel de **visualización**. La **edición** de ciertos campos clínicos (antecedentes) está restringida a un médico y a 1-2 perfiles directivos designados (`RF-PAC-018`). Dar de baja a un paciente y registrar su fallecimiento tienen permisos específicos (ver `RF-PAC-005`, `RF-PAC-006`). | CLIENTE | CONFIRMADO — ver nota de riesgo de privacidad en `decisiones.md` | Q-PAC-036 a Q-PAC-040 |
| RF-PAC-015 | El sistema debe registrar auditoría (usuario, fecha, valor anterior/nuevo) sobre **todos** los cambios a la ficha del paciente, no solo los sensibles. El historial de cambios de DNI es visible sin restringirlo a un rol específico. | CLIENTE | CONFIRMADO | Q-PAC-017, Q-PAC-040 |
| RF-PAC-016 | El sistema debe permitir exportar/imprimir la ficha del paciente (para entregársela al paciente, para una obra social o para un trámite), dejando auditado quién la exportó/imprimió y cuándo. | CLIENTE | CONFIRMADO | Q-PAC-033, Q-PAC-034 |
| RF-PAC-017 | El sistema debe registrar el historial de coberturas de obra social anteriores y de cambios de DNI de un paciente. | CLIENTE | CONFIRMADO | Q-PAC-017, Q-PAC-020 |
| RF-PAC-018 | El sistema debe permitir que el médico corrija libremente un antecedente clínico durante una ventana de tiempo después de cargarlo (24 h, configurable por Dirección en `MOD-036`, `Q-PAC-058`). Pasada la ventana, solo pueden corregirlo los perfiles directivos designados, **sin límite de tiempo** (`Q-PAC-059`, que concilia `Q-PAC-037` con `Q-HCL-002`). "Perfil directivo designado" es un permiso asignable (`MOD-027`), no una lista fija de personas. Toda corrección queda auditada. | CLIENTE | CONFIRMADO | Q-PAC-037, Q-HCL-002, Q-PAC-058, Q-PAC-059 |
| RF-PAC-019 | El sistema debe modelar al paciente como una ficha única compartida entre sedes (no una ficha distinta por sede), en línea con que la clínica ya opera más de una sede. | CLIENTE | CONFIRMADO | Q-PAC-052 |
| RF-PAC-020 | El sistema debe permitir buscar/filtrar pacientes por zona o localidad de domicilio. | CLIENTE | CONFIRMADO | Q-PAC-044 |
| RF-PAC-021 | El sistema debe permitir registrar si un paciente tiene una necesidad especial relevante para su atención (discapacidad visual/auditiva, movilidad reducida, necesidad de intérprete). | CLIENTE | CONFIRMADO | Q-PAC-053 |
| RF-PAC-022 | El sistema debe permitir registrar, como dato opcional, quién derivó al paciente (médico o institución, texto libre), y mostrarlo en el encabezado de la ficha junto con la localidad ("procedencia"). | CLIENTE (`CR-001`) | CONFIRMADO (2026-09-26) | Q-HCL-003, Q-PAC-064 |

## Fuera de alcance confirmado

- Portal de autogestión del paciente: **no está en los planes** del cliente (`Q-PAC-049`). Se
  mantiene fuera de alcance, ver [`alcance.md`](alcance.md).

## Requisitos no funcionales aplicables

Definidos en
[`../../02_Requerimientos/requerimientos_no_funcionales.md`](../../02_Requerimientos/requerimientos_no_funcionales.md):

| RNF | Aplicación en este módulo |
|---|---|
| RNF-SEG-001 | Solo usuarios autenticados acceden a fichas de pacientes (Fortify, Fase 1). |
| RNF-SEG-002 | Las acciones restringidas (baja, fallecimiento, edición clínica, unificación) se controlan con permisos asignables a roles, no con nombres de personas. Ver la matriz de permisos en [`reglas_negocio.md`](reglas_negocio.md). |
| RNF-PRI-001 | La ficha contiene datos personales y de salud. El alcance legal exacto sigue `PENDIENTE_DEFINICION` a nivel proyecto. |
| RNF-PRI-002 | **Descartado para este módulo**: todo el personal ve toda la ficha (`Q-PAC-038`, `RIE-PAC-004`). |
| RNF-AUD-001 | Se auditan **todos** los cambios de la ficha, además de exportaciones, impresiones y descargas de adjuntos (`RN-PAC-008`). |
| RNF-INC-001 | Ningún paciente ni antecedente se elimina físicamente (`RN-PAC-005`). |
| RNF-USA-001 | El alta y la búsqueda deben ser operables por recepción sin conocimientos técnicos. |
| RNF-ESC-001 | La ficha no asume una especialidad ni una sede (`DEC-PAC-002`, `RN-PAC-009`). |
| RNF-BCK-001 | Los datos de pacientes son parte central del respaldo (`MOD-037`). |

## Estado de completitud

Los 22 requerimientos están `CONFIRMADO` (2026-09-26). La Ronda 3 confirmó todas las hipótesis de
trabajo (`Q-PAC-054` a `Q-PAC-069`) salvo `Q-PAC-064`, que agregó `RF-PAC-022` por `CR-001`.

`RF-PAC-012` (unificar fichas duplicadas) quedó confirmado, pero se construye en un incremento
posterior al primero (`DEC-PAC-025`).

Ninguno pasa a `VALIDADO` (implementado y verificado) hasta `EN_CONSTRUCCION`.
