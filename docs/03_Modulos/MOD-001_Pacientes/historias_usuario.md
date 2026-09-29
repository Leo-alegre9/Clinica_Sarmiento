# MOD-001 — Historias de usuario

**Estado del documento:** actualizado el 2026-09-24 para el pase a `LISTO_PARA_VALIDACION`. Cada
requerimiento `RF-PAC-###` tiene al menos una historia, y cada historia tiene criterios de
aceptación en [`criterios_aceptacion.md`](criterios_aceptacion.md). Las hipótesis de trabajo
quedaron confirmadas en la Ronda 3 (2026-09-26, `Q-PAC-054` a `Q-PAC-069`).

Roles según `Q-USR-001`: recepción/administrativo, médico, Dirección/administración, más el
permiso de perfil directivo designado (ver
[`reglas_negocio.md`](reglas_negocio.md#permisos-por-rol-y-acción)).

---

### HU-PAC-001 — Alta de paciente

Como **secretario/a de recepción**
quiero **registrar un paciente nuevo con su ficha completa**
para **poder asignarle un turno o iniciar su historia clínica**.

- **Prioridad:** Alta
- **Requerimiento origen:** RF-PAC-001, RF-PAC-003, RF-PAC-013, RF-PAC-022 (`CR-001`)
- **Precondiciones:** el usuario está autenticado (todo el personal puede dar de alta,
  `RF-PAC-014`).
- **Reglas de negocio relacionadas:** RN-PAC-001, RN-PAC-002
- **Dependencias:** MOD-019 (obra social, obligatoria en el alta)
- **Casos excepcionales:** paciente sin DNI (código provisorio interno, `RF-PAC-013`); documento
  idéntico a otro paciente (se impide y se ofrece abrir la ficha existente,
  `Q-PAC-057`); coincidencia de nombre y fecha de nacimiento o de número de afiliado (se advierte
  y se deja continuar, `RF-PAC-003`).
- **Estado:** RESPONDIDA — lista para criterios de aceptación.

---

### HU-PAC-002 — Búsqueda de paciente

Como **usuario del sistema (recepción, médico, administración)**
quiero **buscar un paciente por DNI, nombre/apellido o número de afiliado**
para **acceder rápidamente a su ficha sin crear un duplicado**.

- **Prioridad:** Alta
- **Requerimiento origen:** RF-PAC-002, RF-PAC-014, RF-PAC-019
- **Precondiciones:** estar autenticado, en cualquier sede.
- **Reglas de negocio relacionadas:** RN-PAC-007, RN-PAC-009
- **Dependencias:** —
- **Casos excepcionales:** búsqueda sin resultados (ofrece crear paciente); múltiples
  coincidencias por nombre; paciente cargado en otra sede (aparece igual: la ficha es única).
- **Estado:** RESPONDIDA — `Q-PAC-014`, `Q-PAC-015`, `Q-PAC-052` confirmadas.

---

### HU-PAC-003 — Modificación de datos del paciente

Como **secretario/a de recepción**
quiero **actualizar los datos de un paciente existente**
para **mantener su información de contacto y cobertura al día**.

- **Prioridad:** Alta
- **Requerimiento origen:** RF-PAC-004, RF-PAC-017
- **Precondiciones:** el paciente existe.
- **Reglas de negocio relacionadas:** RN-PAC-001, RN-PAC-008 (auditoría de todos los cambios)
- **Dependencias:** MOD-028 (auditoría)
- **Casos excepcionales:** cambio de DNI (queda en el historial, visible sin restricción de rol);
  el nuevo DNI ya pertenece a otro paciente (se impide, `RN-PAC-001`); edición de antecedentes
  clínicos (se rige por `HU-PAC-010`, no por esta historia).
- **Estado:** RESPONDIDA — `Q-PAC-017`, `Q-PAC-037` confirmadas.

---

### HU-PAC-004 — Baja y reactivación de paciente

Como **administrador o médico con permiso de baja**
quiero **dar de baja (lógica) a un paciente y poder reactivarlo**
para **reflejar que ya no se atiende en la clínica sin perder su historia**.

- **Prioridad:** Media
- **Requerimiento origen:** RF-PAC-005
- **Precondiciones:** el paciente existe; el usuario es de Dirección/administración o es un
  médico con el permiso asignado (`Q-PAC-061`).
- **Reglas de negocio relacionadas:** RN-PAC-005 (baja siempre lógica, nunca elimina el
  registro)
- **Dependencias:** MOD-010 (turnos futuros)
- **Casos excepcionales:** paciente con turnos futuros: el sistema los lista para revisión manual
  y no los cancela solo; mientras esté dado de baja no se le pueden dar turnos nuevos
  (`Q-PAC-062`).
- **Estado:** RESPONDIDA — `Q-PAC-013`, `Q-PAC-039`, `Q-PAC-061` y `Q-PAC-062`
  confirmadas. Ver `CU-PAC-005`.

---

### HU-PAC-005 — Registro de fallecimiento

Como **administración**
quiero **marcar a un paciente como fallecido**
para **reflejar su estado real, dejando que cada caso (turnos, recordatorios, obra social) se
revise manualmente**.

- **Prioridad:** Media
- **Requerimiento origen:** RF-PAC-006
- **Precondiciones:** el paciente existe; el usuario pertenece a administración.
- **Reglas de negocio relacionadas:** RN-PAC-005
- **Dependencias:** MOD-010 (turnos), MOD-014 (recordatorios): revisión manual, no automática
- **Casos excepcionales:** ninguna acción automática se dispara; fallecimiento cargado por error
  (solo administración lo revierte, con motivo, `Q-PAC-063`).
- **Estado:** RESPONDIDA — `Q-PAC-041`, `Q-PAC-042` confirmadas.

---

### HU-PAC-006 — Asociar obra social a un paciente

Como **secretario/a de recepción**
quiero **asociar una o más obras sociales a un paciente, marcando cuál es la principal**
para **facturar y verificar cobertura correctamente**.

- **Prioridad:** Alta
- **Requerimiento origen:** RF-PAC-007, RF-PAC-017
- **Precondiciones:** el paciente existe; la obra social existe en el catálogo (`MOD-019`).
- **Reglas de negocio relacionadas:** RN-PAC-003
- **Dependencias:** MOD-019, MOD-020
- **Casos excepcionales:** paciente sin obra social (particular); paciente que opta por
  atenderse particular pese a tener obra social vigente; cambio de obra social (conserva
  historial).
- **Estado:** RESPONDIDA — `Q-PAC-018` a `Q-PAC-021` confirmadas.

---

### HU-PAC-007 — Registrar responsable/tutor de un menor

Como **secretario/a de recepción**
quiero **asociar uno o más responsables/tutores a un paciente menor de 18 años**
para **poder contactarlos y dejar constancia de quién autoriza la atención**.

- **Prioridad:** Alta
- **Requerimiento origen:** RF-PAC-008
- **Precondiciones:** el paciente es menor de 18 años.
- **Reglas de negocio relacionadas:** RN-PAC-004
- **Dependencias:** el responsable se modela como referencia a un registro de `Paciente`
  existente (frecuentemente es también paciente de la clínica).
- **Casos excepcionales:** menor con más de un responsable (madre y padre, por ejemplo); el
  paciente alcanza la mayoría de edad (el vínculo se conserva como histórico).
- **Estado:** RESPONDIDA — `Q-PAC-022` a `Q-PAC-025` confirmadas.

---

### HU-PAC-008 — Unificar fichas duplicadas

Como **Dirección/administración**
quiero **unificar dos fichas de paciente que en realidad son la misma persona**
para **que su historia clínica, turnos y pagos queden en un solo lugar**.

- **Prioridad:** Media
- **Requerimiento origen:** RF-PAC-012
- **Precondiciones:** existen dos registros del mismo paciente (por ejemplo, uno con código
  provisorio y otro con DNI).
- **Reglas de negocio relacionadas:** RN-PAC-006
- **Dependencias:** MOD-002, MOD-010, MOD-022/MOD-023
- **Casos excepcionales:** antecedentes distintos en cada ficha (se suman); obras sociales
  distintas (se conservan ambas); una de las fichas tiene turnos futuros (pasan a la que queda).
- **Estado:** RESPONDIDA — confirmada el 2026-09-26 (`Q-PAC-054` a `Q-PAC-056`). Se construye en
  un incremento posterior al primero (`DEC-PAC-025`). Ver
  `CU-PAC-003`.

---

### HU-PAC-009 — Registrar y ver alertas clínicas

Como **médico**
quiero **ver alertas clínicas relevantes del paciente (alergias, antecedentes críticos) al
abrir su ficha**
para **atenderlo de forma segura**.

- **Prioridad:** Alta (impacto en seguridad clínica)
- **Requerimiento origen:** RF-PAC-011
- **Precondiciones:** el paciente tiene alertas registradas.
- **Reglas de negocio relacionadas:** RN-PAC-007
- **Dependencias:** MOD-002, MOD-003
- **Casos excepcionales:** alerta cargada por recepción/administración (se muestra igual, marcada
  "pendiente de revisión médica" hasta que un médico la confirme, `Q-PAC-060`); alerta
  cargada por error (se corrige según `HU-PAC-010`).
- **Estado:** RESPONDIDA — el cliente (`Q-PAC-030` a `Q-PAC-032`) y los médicos (`Q-HCL-006`,
  `Q-HCL-007`, 2026-09-24) confirmaron las tres categorías y el aviso destacado. Ver `CU-PAC-004`.

---

### HU-PAC-010 — Corrección de antecedentes clínicos

Como **médico, o persona con perfil directivo designado**
quiero **poder corregir un antecedente clínico ya cargado**
para **arreglar errores de carga sin perder la trazabilidad**.

- **Prioridad:** Media
- **Requerimiento origen:** RF-PAC-018
- **Precondiciones:** el usuario es médico y el antecedente está dentro de la ventana de
  corrección (24 h configurables, `Q-PAC-058`), o el usuario tiene el perfil directivo
  designado (sin límite de tiempo, `Q-PAC-059`).
- **Reglas de negocio relacionadas:** RN-PAC-007, RN-PAC-008
- **Dependencias:** MOD-027 (permiso de perfil directivo), MOD-028 (auditoría), MOD-036
  (parámetro de la ventana)
- **Casos excepcionales:** médico que intenta corregir fuera de la ventana (se rechaza);
  recepción que intenta modificar o eliminar un antecedente existente (se rechaza).
- **Estado:** RESPONDIDA — requerimiento surgido de `Q-PAC-037`/`Q-HCL-002`; valor de la ventana
  y alcance de los directivos confirmados en `Q-PAC-058`/`Q-PAC-059`.

---

### HU-PAC-011 — Datos de contacto y contacto de emergencia

Como **secretario/a de recepción**
quiero **registrar teléfono, WhatsApp, canal preferido y contacto de emergencia del paciente**
para **poder avisarle de sus turnos y ubicar a alguien ante una urgencia**.

- **Prioridad:** Alta
- **Requerimiento origen:** RF-PAC-009
- **Precondiciones:** alta o edición de un paciente.
- **Reglas de negocio relacionadas:** RN-PAC-008
- **Dependencias:** MOD-014, MOD-029, MOD-030 (usan el canal preferido y el opt-out)
- **Casos excepcionales:** WhatsApp igual al teléfono (se carga una sola vez); paciente que no
  quiere comunicaciones salvo el aviso de turno (opt-out).
- **Estado:** RESPONDIDA — `Q-PAC-026`, `Q-PAC-027`, `Q-PAC-047`, `Q-PAC-048`; opciones de canal
  confirmadas en `Q-PAC-067`.

---

### HU-PAC-012 — Adjuntos y consentimientos

Como **secretario/a de recepción**
quiero **adjuntar a la ficha el DNI escaneado, el carnet de obra social y los consentimientos
firmados, y registrar si el paciente autorizó el uso de su foto**
para **tener la documentación a mano y respaldar el tratamiento de sus datos**.

- **Prioridad:** Media
- **Requerimiento origen:** RF-PAC-001 (consentimiento en el alta), RF-PAC-010
- **Precondiciones:** el paciente existe o se está dando de alta.
- **Reglas de negocio relacionadas:** RN-PAC-008, RN-PAC-010
- **Dependencias:** MOD-007 (almacenamiento de archivos)
- **Casos excepcionales:** paciente que no autoriza el uso de su foto (no se puede cargar
  fotografía, el resto de la ficha sigue igual).
- **Estado:** RESPONDIDA — `Q-PAC-028`, `Q-PAC-029`, `Q-PAC-045`, `Q-PAC-046`; visibilidad de
  adjuntos confirmada en `Q-PAC-069`.

---

### HU-PAC-013 — Exportar o imprimir la ficha

Como **usuario del sistema**
quiero **exportar o imprimir la ficha de un paciente**
para **entregársela al paciente, a una obra social o para un trámite**.

- **Prioridad:** Baja
- **Requerimiento origen:** RF-PAC-016
- **Precondiciones:** el paciente existe.
- **Reglas de negocio relacionadas:** RN-PAC-008
- **Dependencias:** MOD-028
- **Casos excepcionales:** ninguno identificado.
- **Estado:** RESPONDIDA — `Q-PAC-033`, `Q-PAC-034`.

---

### HU-PAC-014 — Consultar el historial de cambios de la ficha

Como **usuario del sistema**
quiero **ver quién cambió qué dato de la ficha y cuándo**
para **resolver dudas o reclamos sobre datos del paciente**.

- **Prioridad:** Media
- **Requerimiento origen:** RF-PAC-015, RF-PAC-017
- **Precondiciones:** el paciente existe.
- **Reglas de negocio relacionadas:** RN-PAC-008
- **Dependencias:** MOD-028
- **Casos excepcionales:** ninguno identificado.
- **Estado:** RESPONDIDA — `Q-PAC-017`, `Q-PAC-040`.

---

### HU-PAC-015 — Filtrar pacientes por localidad

Como **Dirección/administración**
quiero **listar pacientes por zona o localidad**
para **conocer de dónde vienen y organizar la atención**.

- **Prioridad:** Baja
- **Requerimiento origen:** RF-PAC-020
- **Precondiciones:** los pacientes tienen localidad cargada (obligatoria en el alta).
- **Reglas de negocio relacionadas:** —
- **Dependencias:** MOD-041 (reportes)
- **Casos excepcionales:** pacientes migrados del sistema anterior sin localidad (se listan como
  "sin localidad", `MOD-040`).
- **Estado:** RESPONDIDA — `Q-PAC-044`.

---

### HU-PAC-016 — Necesidad especial de atención

Como **secretario/a de recepción**
quiero **registrar si el paciente tiene una necesidad especial (discapacidad visual o auditiva,
movilidad reducida, intérprete)**
para **que quien lo atienda lo sepa de antemano**.

- **Prioridad:** Media
- **Requerimiento origen:** RF-PAC-021
- **Precondiciones:** alta o edición de un paciente.
- **Reglas de negocio relacionadas:** —
- **Dependencias:** MOD-011 (recepción), MOD-012 (prioridades en sala de espera)
- **Casos excepcionales:** ninguno identificado.
- **Estado:** RESPONDIDA — `Q-PAC-053`.

---

La lista se amplía si el refinamiento de módulos dependientes (`MOD-019`, `MOD-026`/`MOD-027`,
`MOD-033`) revela nuevas necesidades sobre la ficha del paciente. Después de `APROBADO`, eso se
gestiona como Change Request.
