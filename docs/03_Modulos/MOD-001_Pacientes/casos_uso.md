# MOD-001 — Casos de uso

Se documentan en detalle los flujos de mayor complejidad. Los flujos simples de
CRUD quedan cubiertos por sus historias de usuario en
[`historias_usuario.md`](historias_usuario.md) sin caso de uso propio, salvo que el
refinamiento posterior revele complejidad adicional.

---

## CU-PAC-001 — Alta de paciente

- **Objetivo:** registrar un paciente nuevo en el sistema, evitando duplicados evidentes.
- **Actor principal:** Secretario/a de recepción.
- **Actores secundarios:** Sistema (validación de duplicados).
- **Disparador:** un paciente se presenta o llama por primera vez, o se solicita un turno a su
  nombre.
- **Precondiciones:** el usuario está autenticado y tiene permiso de alta de pacientes.
- **Postcondiciones:** existe un registro de paciente activo, buscable por DNI y nombre.

**Flujo principal (confirmado 2026-09-08):**

1. El usuario busca al paciente por DNI, nombre o número de afiliado (ver `CU-PAC-002`) para
   verificar que no existe.
2. El sistema no encuentra coincidencias exactas.
3. El usuario completa la ficha **completa** del paciente (no hay alta rápida en dos pasos,
   `Q-PAC-012`): DNI (o tipo de documento alternativo), nombre y apellido, fecha de nacimiento,
   teléfono, domicilio con localidad, y obra social (`Q-PAC-011`).
4. El usuario asocia la obra social del paciente, marcando cuál es la principal si tiene más de
   una (`HU-PAC-006`).
5. El usuario deja constancia del consentimiento de tratamiento de datos personales y clínicos
   (`Q-PAC-045`).
6. El sistema valida los datos y guarda el paciente como `Activo`.
7. El sistema muestra la ficha del paciente recién creado.

**Flujos alternativos:**

- 3a. El paciente no tiene DNI (recién nacido, extranjero, indocumentado) → el sistema permite
  continuar el alta con un código provisorio interno, distinguiendo explícitamente el estado
  "sin documento" de "documento en trámite" (`Q-PAC-004`, `Q-PAC-006` a `Q-PAC-010`). No se
  valida un formato estricto de DNI argentino (`Q-PAC-005`).
- 4a. El paciente no tiene obra social → se registra como particular.

**Excepciones:**

- 6a. El tipo y número de documento coinciden exactamente con otro paciente → el sistema
  **impide** el alta y ofrece abrir la ficha existente (`RN-PAC-001`; hipótesis `Q-PAC-057`,
  que resuelve la contradicción con `Q-PAC-016`).
- 6b. Coinciden nombre y fecha de nacimiento, o el número de afiliado de obra social → el
  sistema **advierte y permite continuar** si recepción confirma que son personas distintas
  (`Q-PAC-002`, `Q-PAC-016`).
- 6c. Falta un dato obligatorio → el sistema indica cuál y no guarda.
- 3b. El paciente es menor de 18 años → el sistema exige al menos un responsable
  (`HU-PAC-007`).

**Reglas de negocio:** RN-PAC-001, RN-PAC-002, RN-PAC-003.
**Datos involucrados:** ver [`datos.md`](datos.md).
**Requisitos relacionados:** RF-PAC-001, RF-PAC-003, RF-PAC-007, RF-PAC-013.
**Historias relacionadas:** HU-PAC-001, HU-PAC-006, HU-PAC-007.

---

## CU-PAC-002 — Búsqueda de paciente

- **Objetivo:** localizar un paciente existente para operar sobre su ficha.
- **Actor principal:** cualquier usuario autenticado con acceso al módulo.
- **Disparador:** necesidad de abrir la ficha de un paciente (turno, consulta, caja).
- **Precondiciones:** el usuario está autenticado.
- **Postcondiciones:** se muestra la ficha del paciente seleccionado, o un resultado vacío.

**Flujo principal (confirmado 2026-09-08):**

1. El usuario ingresa un criterio de búsqueda: DNI, nombre y/o apellido, o número de afiliado
   de obra social (`Q-PAC-015`).
2. El sistema devuelve coincidencias, **mostrando siempre tanto pacientes activos como
   inactivos** por defecto, sin necesidad de un filtro explícito (`Q-PAC-014`, `Q-PAC-051`).
3. El usuario selecciona un resultado.
4. El sistema muestra la ficha completa del paciente — todo el personal autenticado ve por
   igual los datos administrativos y clínicos (`RN-PAC-007`); la edición de ciertos campos
   clínicos sigue restringida (`RF-PAC-018`).

**Flujos alternativos:**

- 2a. No hay coincidencias exactas pero sí aproximadas (nombre similar) →
  `PENDIENTE_DEFINICION` (no preguntado; queda como detalle de UX a definir en el diseño).

**Excepciones:** ninguna identificada todavía.

**Reglas de negocio:** RN-PAC-007.
**Requisitos relacionados:** RF-PAC-002.
**Historias relacionadas:** HU-PAC-002.

---

## CU-PAC-003 — Fusión de pacientes duplicados

- **Objetivo:** unificar dos registros de paciente que representan a la misma persona.
**Estado:** `PROPUESTO` — hipótesis completa, pendiente de `Q-PAC-054` a `Q-PAC-056`. Fuera
del primer incremento de construcción (`DEC-PAC-022`).

- **Actor principal:** Dirección/administración (hipótesis `Q-PAC-054`).
- **Disparador:** se detecta que dos fichas corresponden al mismo paciente. El caso típico es
  un paciente cargado con código provisorio que después aparece con DNI en otra ficha.
- **Precondiciones:** existen al menos dos registros de paciente candidatos a fusión.
- **Postcondiciones:** un único registro de paciente concentra la historia clínica, turnos y
  facturación de ambos; el registro perdedor queda marcado como `Fusionado`, referenciando al
  ganador.

**Flujo principal (hipótesis):**

1. El usuario identifica las dos fichas.
2. El sistema muestra ambas lado a lado.
3. El usuario elige cuál ficha queda y, campo por campo, qué dato administrativo conservar
   (`Q-PAC-055`).
4. El usuario confirma la unificación.
5. El sistema pasa a la ficha que queda la historia clínica, turnos, pagos, coberturas,
   adjuntos y responsables de la otra, y suma los antecedentes y alertas de ambas.
6. El sistema marca la otra ficha como `Fusionado`, apuntando a la que queda, y registra en
   auditoría qué se movió.

**Flujos alternativos:**

- 3a. Las dos fichas tienen obras sociales distintas → se conservan ambas y el usuario elige la
  principal.

**Excepciones:**

- 4a. Una de las fichas está `Fusionado` → no puede unificarse de nuevo; se opera sobre la ficha
  a la que apunta.
- 5a. Una de las fichas tiene turnos futuros → pasan a la ficha que queda, no se pierden.
- Unificación hecha por error → no hay deshacer automático; se corrige a mano con la auditoría
  (`Q-PAC-056`).

**Reglas de negocio:** RN-PAC-006.
**Requisitos relacionados:** RF-PAC-012.
**Historias relacionadas:** HU-PAC-008.
**Riesgo asociado:** ver `RIE-PAC-001` en [`riesgos.md`](riesgos.md) — esta funcionalidad es en
sí misma una mitigación de ese riesgo, pero introduce complejidad y requiere definición
cuidadosa antes de construirse.

---

## CU-PAC-004 — Carga y revisión de antecedentes y alertas clínicas

- **Objetivo:** que las alergias y antecedentes relevantes estén siempre visibles en la ficha,
  aunque los cargue alguien que no es médico, sin perder confiabilidad.
- **Actor principal:** médico, recepción o administración.
- **Actores secundarios:** médico revisor; perfil directivo designado.
- **Disparador:** el paciente informa una alergia o antecedente, o el médico lo detecta en la
  consulta.
- **Precondiciones:** el paciente existe.
- **Postcondiciones:** el antecedente queda en la ficha y, si es alerta crítica, se muestra en el
  aviso destacado y en la ventana emergente al abrirla.

**Flujo principal (usuario médico):**

1. El médico abre la ficha y agrega un antecedente: categoría (alergia a medicamentos,
   antecedente quirúrgico relevante, enfermedad crónica), descripción, y si es alerta crítica.
2. El sistema lo guarda como `confirmado`, con autor y fecha.
3. Si es alerta crítica, aparece desde ese momento en el aviso destacado de la ficha.

**Flujos alternativos:**

- 1a. Lo carga recepción o administración (`Q-PAC-032`) → el sistema lo guarda como
  `pendiente de revisión médica` y lo muestra igual (hipótesis `Q-PAC-060`). Cuando un médico
  abre la ficha, ve la marca y puede confirmarlo.
- 1b. El médico necesita corregir un antecedente propio dentro de la ventana de corrección → lo
  edita libremente, con auditoría (`HU-PAC-010`).
- 1c. Hay que corregirlo fuera de la ventana → solo puede hacerlo un perfil directivo designado
  (hipótesis `Q-PAC-059`).

**Excepciones:**

- 1d. Un usuario no médico intenta modificar o eliminar un antecedente existente → el sistema lo
  rechaza (hipótesis `Q-PAC-060`).
- Un antecedente nunca se borra físicamente: "eliminar" lo marca como anulado, con motivo, y
  queda en auditoría (`RNF-INC-001`).

**Reglas de negocio:** RN-PAC-007, RN-PAC-008.
**Requisitos relacionados:** RF-PAC-011, RF-PAC-018.
**Historias relacionadas:** HU-PAC-009, HU-PAC-010.

---

## CU-PAC-005 — Baja lógica y reactivación

- **Objetivo:** marcar que un paciente dejó de atenderse, sin perder nada de su información.
- **Actor principal:** Dirección/administración, o un médico con el permiso asignado.
- **Disparador:** decisión administrativa o clínica de dar de baja al paciente.
- **Precondiciones:** el paciente está `Activo` (para la baja) o `Inactivo` (para reactivar).
- **Postcondiciones:** el paciente queda `Inactivo` (o `Activo`), con motivo y auditoría.

**Flujo principal (baja):**

1. El usuario abre la ficha y elige "dar de baja".
2. El sistema pide el motivo.
3. Si el paciente tiene turnos futuros, el sistema los lista y avisa que no se cancelan solos
   (hipótesis `Q-PAC-062`).
4. El usuario confirma.
5. El sistema marca al paciente como `Inactivo`. Sigue apareciendo en las búsquedas, identificado
   como inactivo.

**Flujos alternativos:**

- Reactivación: el usuario con permiso elige "reactivar" en un paciente inactivo; el sistema lo
  marca `Activo` y vuelve a permitir asignarle turnos.

**Excepciones:**

- 1a. El usuario no tiene permiso de baja → el sistema rechaza la acción.
- Mientras está inactivo, un intento de asignarle un turno nuevo se rechaza, indicando que debe
  reactivarse primero (hipótesis `Q-PAC-062`).

**Reglas de negocio:** RN-PAC-005, RN-PAC-008.
**Requisitos relacionados:** RF-PAC-005.
**Historias relacionadas:** HU-PAC-004.

---

El resto de los flujos (fallecimiento, edición de datos administrativos, contacto, adjuntos,
exportación, filtro por localidad) son simples y quedan cubiertos por sus historias de usuario y
criterios de aceptación, sin caso de uso propio.
