# MOD-001 — Reglas de negocio

Estado por regla según
[`../../00_Gobernanza/estados_requerimientos.md`](../../00_Gobernanza/estados_requerimientos.md).
Confirmadas por el cliente el 2026-09-08 (ver [`preguntas.md`](preguntas.md),
[`decisiones.md`](decisiones.md)) salvo indicación contraria. Revisadas el 2026-09-24 para el pase a
`LISTO_PARA_VALIDACION`: lo marcado como **hipótesis** tiene origen `ANÁLISIS`, `Requiere
validación: SÍ`, y se pregunta en la Ronda 3.

| ID | Regla | Estado | Depende de |
|---|---|---|---|
| RN-PAC-001 | El documento, cuando existe, es único entre todos los pacientes (no solo entre activos): no puede haber dos pacientes con el mismo tipo y número de documento. Un alta con documento idéntico a uno existente se impide y se ofrece abrir la ficha existente (hipótesis que resuelve la contradicción con `Q-PAC-016`). Las coincidencias que no son de documento (nombre + fecha de nacimiento, número de afiliado) solo generan una advertencia. | CONFIRMADO — el tratamiento del documento idéntico es hipótesis hasta `Q-PAC-057` | Q-PAC-001, Q-PAC-016, Q-PAC-057 |
| RN-PAC-002 | Un paciente puede no tener DNI al momento del alta (recién nacido, indocumentado, extranjero sin trámite). Se identifica con un código provisorio interno y se distingue explícitamente el estado "sin documento" de "documento en trámite". Al completarse el documento real, se edita el mismo registro, nunca se crea uno nuevo. | CONFIRMADO | Q-PAC-004, Q-PAC-006, Q-PAC-008, Q-PAC-009, Q-PAC-010 |
| RN-PAC-003 | Un paciente puede tener más de una obra social simultánea, pero solo una puede marcarse como principal a la vez. Se conserva el historial de coberturas anteriores. Un paciente con obra social vigente puede optar por atenderse como particular en una consulta puntual. | CONFIRMADO | Q-PAC-018, Q-PAC-020, Q-PAC-021 |
| RN-PAC-004 | Un paciente menor de 18 años requiere al menos un responsable/tutor asociado; puede tener más de uno registrado. Al alcanzar la mayoría de edad, el vínculo se conserva como dato histórico (no se desvincula automáticamente). | CONFIRMADO | Q-PAC-022, Q-PAC-024, Q-PAC-025 |
| RN-PAC-005 | Un paciente nunca se elimina físicamente. La historia clínica se conserva **indefinidamente** (`Q-HCL-001`, Ronda 2), lo que cubre el mínimo legal de 10 años citado en `Q-PAC-013`. Se da de baja de forma **lógica** (marca de estado), ejecutada por un administrador o por un médico con el permiso asignado, o se marca como fallecido. Ni la baja ni el fallecimiento ejecutan acciones automáticas sobre turnos, recordatorios u obra social: el sistema avisa y lista los turnos futuros para revisarlos a mano. Un paciente inactivo no recibe turnos nuevos hasta que se lo reactive (hipótesis, `Q-PAC-062`). Un fallecimiento cargado por error solo lo revierte administración, con motivo (hipótesis, `Q-PAC-063`). | CONFIRMADO — los puntos marcados son hipótesis | Q-PAC-013, Q-PAC-039, Q-PAC-041, Q-PAC-042, Q-HCL-001, Q-PAC-062, Q-PAC-063 |
| RN-PAC-006 | Unificar fichas duplicadas: la ficha que queda recibe toda la historia clínica, turnos, pagos, coberturas, adjuntos y responsables de la otra. Los antecedentes y alertas clínicas de ambas se suman, sin descartar ninguno. La otra ficha queda en estado `Fusionado` apuntando a la que queda, sin borrarse. La unificación no se deshace automáticamente y queda auditada. | PROPUESTO — hipótesis completa, pendiente de `Q-PAC-054` a `Q-PAC-056`. Fuera del primer incremento de construcción (`DEC-PAC-022`) | Q-PAC-016, Q-PAC-054, Q-PAC-055, Q-PAC-056 |
| RN-PAC-007 | Todo el personal autenticado ve por igual los datos administrativos y clínicos de la ficha, sin restricción por tipo de dato ni por rol. Los antecedentes clínicos siguen estas reglas de edición: cualquier usuario puede **agregar** uno (si no es médico, queda "pendiente de revisión médica", hipótesis `Q-PAC-060`); **modificar o eliminar** uno existente puede hacerlo el médico dentro de la ventana de corrección (`RF-PAC-018`) o un perfil directivo designado sin límite de tiempo (hipótesis `Q-PAC-059`). | CONFIRMADO — ver nota de riesgo de privacidad en `decisiones.md`; el detalle de edición es hipótesis hasta `Q-PAC-058` a `Q-PAC-060` | Q-PAC-032, Q-PAC-036, Q-PAC-037, Q-PAC-038, Q-HCL-002 |
| RN-PAC-008 | Todo cambio sobre la ficha del paciente (no solo DNI, obra social o estado) queda auditado con usuario, fecha y valores anterior/nuevo. También se auditan exportaciones, impresiones y descargas de adjuntos. El historial de cambios de DNI es consultable sin restricción de rol. | CONFIRMADO | Q-PAC-017, Q-PAC-034, Q-PAC-040 |
| RN-PAC-009 | El paciente es una ficha única compartida entre sedes; no existe una ficha distinta por sede. | CONFIRMADO | Q-PAC-052 |
| RN-PAC-010 | El uso de la fotografía del paciente requiere un consentimiento específico, distinto del consentimiento general de tratamiento de datos personales y clínicos (exigido en el alta presencial). | CONFIRMADO | Q-PAC-045, Q-PAC-046 |
| RN-PAC-011 | La solicitud de turno web o por WhatsApp no crea ni modifica fichas de pacientes. Si el DNI ya existe, el turno se vincula a esa ficha y recepción revisa las diferencias. Si no existe, el turno queda con datos provisorios y la ficha completa se da de alta en recepción. | PROPUESTO — hipótesis hasta `Q-PAC-068` | Q-PAC-012, Q-PUB-001, Q-PAC-068 |

`RN-PAC-006` y `RN-PAC-011` siguen `PROPUESTO`; el resto está `CONFIRMADO`. `RN-PAC-005` (no
eliminación física) está referenciada desde
[`../../02_Requerimientos/reglas_negocio.md`](../../02_Requerimientos/reglas_negocio.md) por su
alcance transversal.

## Permisos por rol y acción

Roles tomados de `Q-USR-001` (Ronda 2): **Recepción/administrativo**, **Médico/profesional** y
**Dirección/administración**. Además, **perfil directivo designado** es un permiso adicional que
Dirección asigna a personas concretas (`Q-PAC-037`, `Q-HCL-002`). Como pide `RNF-SEG-002`, cada
celda es un permiso configurable en `MOD-027`, no una regla atada a personas. Todas las acciones
quedan auditadas (`RN-PAC-008`).

| Acción | Recepción / administrativo | Médico | Dirección / administración | Perfil directivo designado | Fuente |
|---|---|---|---|---|---|
| Buscar y ver la ficha completa (incluidos datos clínicos) | ✅ | ✅ | ✅ | ✅ | Q-PAC-036, Q-PAC-038 |
| Dar de alta un paciente | ✅ | ✅ | ✅ | ✅ | RF-PAC-014 |
| Modificar datos administrativos (identificación, contacto, domicilio, cobertura, responsables, adjuntos) | ✅ | ✅ | ✅ | ✅ | Q-PAC-037 |
| Agregar un antecedente o alerta clínica | ✅ (queda pendiente de revisión médica, hipótesis) | ✅ | ✅ (queda pendiente de revisión médica, hipótesis) | ✅ | Q-PAC-032, Q-PAC-060 |
| Confirmar un antecedente cargado por no médicos | — | ✅ | — | ✅ | Q-PAC-060 (hipótesis) |
| Modificar o eliminar un antecedente existente | — | ✅ dentro de la ventana de corrección | — | ✅ sin límite de tiempo (hipótesis) | Q-PAC-037, Q-PAC-058, Q-PAC-059 |
| Dar de baja (lógica) y reactivar | — | Solo con permiso asignado | ✅ | ✅ | Q-PAC-039, Q-PAC-061 |
| Registrar fallecimiento / revertirlo | — | — | ✅ | ✅ (si además es de administración) | Q-PAC-042, Q-PAC-063 |
| Unificar fichas duplicadas | — | — | ✅ (hipótesis) | ✅ (hipótesis) | Q-PAC-054 |
| Exportar / imprimir la ficha | ✅ | ✅ | ✅ | ✅ | Q-PAC-033, Q-PAC-034 (quién puede hacerlo no se preguntó; se deriva de Q-PAC-038) |
| Consultar el historial de cambios (auditoría) de la ficha | ✅ | ✅ | ✅ | ✅ | Q-PAC-017 |
