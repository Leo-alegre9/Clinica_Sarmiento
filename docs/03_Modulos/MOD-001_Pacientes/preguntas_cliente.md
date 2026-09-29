# MOD-001 — Preguntas reformuladas para el cliente

**Estado: RESPONDIDA el 2026-09-08.** El cliente contestó las 51 preguntas 🟢 de este
documento. Las respuestas completas, con el detalle de motivo/impacto de cada una, están
volcadas en [`preguntas.md`](preguntas.md) (formato `**Respuesta:**` / `**Estado:**` por
pregunta) — no se duplican aquí para evitar que queden dos fuentes de verdad. Las decisiones
derivadas están en [`decisiones.md`](decisiones.md). Dos respuestas quedaron contradictorias
entre sí (`Q-PAC-013`/`Q-PAC-039` y `Q-PAC-041`) y están pendientes de repregunta — ver
[`../../08_Pendientes/decisiones_pendientes.md`](../../08_Pendientes/decisiones_pendientes.md).

Este documento separa las 53 preguntas de refinamiento de
[`preguntas.md`](preguntas.md) en dos grupos, sin eliminar ninguna:

- 🟢 **Preguntas para el cliente** — requieren conocimiento de negocio, operativo, legal o
  clínico que solo tiene Clínica Sarmiento. Se reformulan aquí en lenguaje simple, sin jerga de
  requerimientos (`RF-`, `RN-`, `CU-`), con opciones de respuesta cerradas y, cuando la pregunta
  no admite un catálogo cerrado de respuestas, una opción "Otro" abierta. Estas son las que se
  llevan al cuestionario interactivo (ver artefacto adjunto).
- 🔧 **Preguntas internas del sistema** — decisiones de arquitectura/modelo de datos que el
  equipo de desarrollo puede resolver sin depender de una respuesta del cliente (aunque el
  resultado de la decisión pueda luego mostrarse al cliente como parte de la solución). No se
  incluyen en el cuestionario para no pedirle al cliente que opine sobre implementación.

El criterio de separación: si la respuesta depende de cómo trabaja la clínica hoy, de una
política que quieren aplicar, o de una obligación legal/clínica → es del cliente. Si la
respuesta no cambia el comportamiento visible del sistema y es puramente una decisión de cómo
se modela o implementa internamente → es del equipo.

Cada pregunta reformulada conserva su ID original (`Q-PAC-0XX`) para trazabilidad con
`preguntas.md` y `decisiones.md`. Las respuestas que el cliente complete en el cuestionario se
vuelcan a este documento (o a `decisiones.md`) una vez recibidas.

**Resumen:** 50 preguntas 🟢 para el cliente, 3 🔧 internas (`Q-PAC-005`, `Q-PAC-008`,
`Q-PAC-023`).

---

## 🔧 Preguntas internas del sistema (no se le piden al cliente)

| ID | Motivo por el que queda en el equipo técnico |
| --- | --- |
| `Q-PAC-005` | Validar o no el formato del DNI es una consecuencia técnica de cómo se respondan `Q-PAC-003`, `Q-PAC-006` y `Q-PAC-007` (qué documentos y con qué formato se aceptan); no requiere una decisión de negocio aparte. |
| `Q-PAC-008` | Cómo completar el DNI de un paciente ya cargado sin duplicar su historia clínica es una garantía de implementación (edición del mismo registro), no una elección que dependa de la clínica. |
| `Q-PAC-023` | Modelar "Responsable/tutor" como una entidad propia o reutilizar "Paciente" es una decisión de diseño de base de datos. El hecho de negocio del que depende (si un tutor puede también ser paciente) sí se le pregunta al cliente, ver `Q-PAC-023` reformulada abajo. |

---

## 🟢 Preguntas reformuladas para el cliente

### 1. Identificación

**Q-PAC-001** (Alta) — En la práctica, ¿podría darse que dos pacientes distintos queden
registrados con el mismo número de DNI (por ejemplo, por un error de carga)?
Opciones: *No, el DNI debe ser único* / *Sí, puede pasar por error* / *No estoy seguro/a* / Otro.

**Q-PAC-002** (Alta) — Si dos fichas tuvieran el mismo DNI pero pudieran ser personas distintas
(o al revés), ¿qué datos usa recepción hoy para confirmar que es la misma persona?
Opciones (selección múltiple): DNI / Nombre y apellido / Fecha de nacimiento / Teléfono /
Dirección / Otro.

**Q-PAC-003** (Media) — Además del DNI argentino, ¿qué otros documentos de identidad reciben
habitualmente?
Opciones (múltiple): Pasaporte / Cédula de identidad extranjera / Libreta cívica o de
enrolamiento / Ninguno otro / Otro.

**Q-PAC-004** (Alta) — ¿Cómo identifican hoy a un recién nacido que todavía no tiene DNI pero ya
necesita atención?
Opciones: Con los datos de la madre o padre + fecha de nacimiento del bebé / Con un número o
código provisorio interno / No se atienden recién nacidos sin DNI / Otro.

### 2. Pacientes sin DNI y extranjeros

**Q-PAC-006** (Alta) — ¿Debe poder atenderse (turnos, historia clínica) a un paciente adulto que
no tiene ningún documento de identidad?
Opciones: Sí, siempre / Solo en casos excepcionales con autorización / No, es requisito
indispensable / Otro.

**Q-PAC-007** (Media) — Para pacientes extranjeros, ¿qué documento aceptan como identificación
principal?
Opciones (múltiple): Pasaporte / DNI de su país de origen / CUIL o CUIT si lo tienen /
Cualquiera de los anteriores / Otro.

**Q-PAC-009** (Media) — Cuando nace un bebé y aún no tiene DNI, ¿quién se espera que complete
ese dato más adelante en el sistema?
Opciones: La recepción hace seguimiento y lo pide / Se deja pendiente hasta que la familia lo
traiga espontáneamente / Otro.

**Q-PAC-010** (Media) — ¿Necesitan poder identificar en el sistema si un paciente "ya tiene el
DNI en trámite" (para hacerle seguimiento), o alcanza con saber que "todavía no lo cargó"?
Opciones: Sí, necesitamos distinguir ambos casos / No, alcanza con saber si está cargado o no /
Otro.

### 3. Alta de paciente

**Q-PAC-011** (Alta) — Pensando en que recepción suele completar el alta con el paciente
esperando, ¿qué datos consideran imprescindibles para registrar a un paciente nuevo?
Opciones (múltiple): Nombre y apellido / DNI / Fecha de nacimiento / Teléfono / Obra social /
Domicilio / Email / Otro.

**Q-PAC-012** (Media) — ¿Prefieren poder hacer un alta rápida con datos mínimos y completar el
resto después, o siempre debe cargarse la ficha completa desde el inicio?
Opciones: Alta rápida y completar después / Ficha completa siempre / Depende del caso / Otro.

### 4. Modificación

**Q-PAC-017** (Media) — Si se corrige un DNI mal cargado, ¿necesitan poder consultar después qué
decía antes y quién hizo el cambio?
Opciones: Sí, siempre / Solo el personal administrativo o directivo / No es necesario / Otro.

**Q-PAC-037** (Media) — ¿Debe haber datos de la ficha que solo un médico pueda editar (por
ejemplo, antecedentes clínicos), fuera del alcance de recepción/administración?
Opciones: Sí / No, cualquiera con acceso a la ficha puede editar todo / Otro.

### 5. Baja y reactivación

**Q-PAC-013** (Alta) — Para ustedes, ¿qué debería significar "dar de baja" a un paciente?
Opciones (múltiple): No se le pueden sacar turnos nuevos / Deja de aparecer en las búsquedas
normales / Ambas cosas / Debería existir además un estado de "bloqueado" distinto de "inactivo"
/ Otro.

### 6. Búsqueda

**Q-PAC-014** (Media) — Al buscar un paciente, ¿deben aparecer también los inactivos/dados de
baja por defecto, o solo si se pide expresamente?
Opciones: Mostrar solo activos por defecto / Mostrar todos siempre / Otro.

**Q-PAC-015** (Media) — Además de DNI y nombre, ¿por qué otros datos necesitan poder buscar a un
paciente?
Opciones (múltiple): Teléfono / Fecha de nacimiento / N.º de afiliado de obra social / Otro.

### 7. Duplicados

**Q-PAC-016** (Alta) — Cuando el sistema detecta un posible duplicado al dar de alta (mismo DNI,
o nombre y fecha de nacimiento iguales), ¿qué debería pasar?
Opciones: Bloquear el alta hasta resolver la duda / Advertir pero permitir continuar si
recepción confirma que son personas distintas / Depende del tipo de coincidencia / Otro.

### 8. Obra social

**Q-PAC-018** (Alta) — ¿Un paciente puede tener más de una obra social a la vez?
Opciones: No, solo una / Sí, puede tener varias / Sí, y una debe marcarse como principal / Otro.

**Q-PAC-019** (Alta) — Por cada obra social del paciente, ¿qué datos necesitan registrar?
Opciones (múltiple): N.º de afiliado / Plan o categoría / Titular o familiar a cargo / Vigencia
o vencimiento / Parentesco con el titular / Otro.

**Q-PAC-020** (Media) — Cuando un paciente cambia de obra social, ¿necesitan conservar el
historial de las coberturas anteriores?
Opciones: Sí / No, alcanza con la vigente / Otro.

**Q-PAC-021** (Media) — ¿Un paciente con obra social vigente puede elegir atenderse como
particular en una consulta puntual?
Opciones: Sí / No / Otro.

### 9. Responsables / tutores / menores

**Q-PAC-022** (Alta) — ¿A partir de qué edad deja de requerirse un responsable/tutor para
atender a un paciente?
Opciones: 18 años (mayoría de edad legal) / Otra edad / Depende del tipo de práctica.

**Q-PAC-023** (Media, reformulada) — ¿Un responsable/tutor de un menor podría, en algún caso,
ser también paciente de la clínica?
Opciones: Sí, frecuentemente / Podría pasar / No, son roles siempre separados / Otro.

**Q-PAC-024** (Media) — ¿Puede haber más de un responsable registrado para un mismo menor (por
ejemplo, madre y padre)?
Opciones: Sí, todos los que correspondan / Alcanza con uno como contacto principal / Otro.

**Q-PAC-025** (Baja) — Cuando el paciente cumple la mayoría de edad, ¿qué debe pasar con el
vínculo con su responsable?
Opciones: Desvincularse automáticamente / Conservarse como dato histórico / Requiere una acción
manual del personal / Otro.

### 10. Contacto y emergencia

**Q-PAC-026** (Media) — De los datos de contacto, ¿cuáles son obligatorios?
Opciones (múltiple): Teléfono / WhatsApp (si es distinto al teléfono) / Email / Ninguno es
obligatorio / Otro.

**Q-PAC-027** (Baja) — ¿El contacto de emergencia debe pedirse siempre, o solo en ciertos casos?
Opciones (múltiple): Siempre / Solo en cirugías / Solo en menores / Solo en adultos mayores / No
es necesario / Otro.

### 11. Fotografías y documentación

**Q-PAC-028** (Media) — ¿Necesitan una fotografía del paciente para identificarlo visualmente en
recepción?
Opciones: Sí / No / Podría ser útil, pero no es prioridad.

**Q-PAC-029** (Baja) — Además de una foto, ¿qué otros documentos necesitan poder adjuntar a la
ficha del paciente?
Opciones (múltiple): DNI escaneado / Carnet de obra social / Consentimientos firmados / Ninguno
/ Otro.

### 12. Antecedentes, alergias y alertas clínicas

**Q-PAC-030** (Alta) — ¿Qué antecedentes o alergias deberían verse siempre en la ficha del
paciente (no solo dentro de cada consulta)?
Opciones (múltiple): Alergias a medicamentos / Antecedentes quirúrgicos relevantes /
Enfermedades crónicas / Ninguno, todo debe estar dentro de cada consulta / Otro.

**Q-PAC-031** (Alta) — ¿Qué tan visible debe ser una alerta crítica (por ejemplo, alergia grave)
al abrir la ficha del paciente?
Opciones: Un aviso destacado siempre visible arriba de la ficha / Una ventana emergente al abrir
la ficha / Ambas / Otro.

**Q-PAC-032** (Media) — ¿Quién puede cargar o editar antecedentes/alertas clínicas?
Opciones: Solo profesionales médicos / También administración/recepción, con supervisión
posterior / Otro.

### 13. Exportación e impresión

**Q-PAC-033** (Baja) — ¿Para qué necesitan imprimir o exportar la ficha de un paciente?
Opciones (múltiple): Para entregársela al paciente / Para una obra social / Para un trámite / No
es necesario / Otro.

**Q-PAC-034** (Media) — ¿Debe quedar registro de quién exportó o imprimió la ficha de un
paciente, y cuándo?
Opciones: Sí / No / Otro.

### 14. Datos personales adicionales

**Q-PAC-035** (Media) — ¿Necesitan registrar "sexo" y "género" como dos datos separados?
Opciones: Sí, son cosas distintas y ambas importan / No, alcanza con uno solo / Otro.

### 15. Privacidad, permisos y auditoría

**Q-PAC-036** (Alta) — ¿Todo el personal debe poder ver la historia clínica de cualquier
paciente, o solo los profesionales que lo atienden?
Opciones: Todo el personal / Solo quienes lo atienden / Depende del rol / Otro.

**Q-PAC-038** (Alta) — ¿Los datos administrativos (contacto, obra social) deberían tener
permisos distintos a los datos clínicos (antecedentes, alergias)?
Opciones: Sí / No, quien accede a la ficha ve todo por igual / Otro.

**Q-PAC-039** (Media) — ¿Quién puede dar de baja a un paciente?
Opciones: Solo administradores / Cualquier secretario/a / Otro.

**Q-PAC-040** (Alta) — ¿Qué cambios sobre la ficha de un paciente necesitan quedar registrados
(auditados) obligatoriamente?
Opciones (múltiple): Todos los cambios / Solo los sensibles (DNI, obra social, estado) / Solo
los datos clínicos / No es necesario auditar / Otro.

### 16. Fallecimiento

**Q-PAC-041** (Media) — Al registrar el fallecimiento de un paciente, ¿qué debería pasar
automáticamente con sus turnos futuros y recordatorios pendientes?
Opciones (múltiple): Cancelar turnos futuros automáticamente / Detener recordatorios
automáticos / Dar de baja la obra social vigente / Ninguna acción automática, revisar caso por
caso / Otro.

**Q-PAC-042** (Baja) — ¿Quién puede registrar el fallecimiento de un paciente?
Opciones: Cualquier usuario / Solo administración / Solo un médico / Otro.

### 17. Domicilio

**Q-PAC-043** (Baja) — ¿El domicilio del paciente es un dato obligatorio?
Opciones: Sí / No, solo si el paciente lo da espontáneamente / Otro.

**Q-PAC-044** (Baja) — ¿Necesitan poder buscar o filtrar pacientes por zona o localidad?
Opciones: Sí / No, el domicilio es solo informativo / Otro.

### 18. Consentimiento y tratamiento de datos

**Q-PAC-045** (Alta) — ¿Necesitan que el paciente acepte un consentimiento para el tratamiento
de sus datos personales y clínicos?
Opciones: Sí, en el alta presencial / Sí, también en el formulario de turnos online / No es
necesario / Otro.

**Q-PAC-046** (Media) — ¿El uso de la fotografía del paciente necesita un consentimiento aparte,
distinto del consentimiento general de datos?
Opciones: Sí / No, alcanza con el general / No aplica, no se usan fotos / Otro.

### 19. Comunicación

**Q-PAC-047** (Media) — ¿El paciente debería poder indicar cuál es su canal de contacto
preferido (llamada, WhatsApp, email)?
Opciones: Sí / No es necesario / Otro.

**Q-PAC-048** (Media) — ¿El paciente debería poder optar por no recibir comunicaciones que no
sean estrictamente el aviso de su turno?
Opciones: Sí / No, todas las comunicaciones son igual de necesarias / Otro.

### 20. Portal del paciente (futuro)

**Q-PAC-049** (Baja) — ¿Están pensando, aunque sea a futuro, en que el paciente pueda ver
directamente su propia ficha o historia clínica desde una web/app?
Opciones: Sí, es un objetivo a futuro / No está en los planes / No lo habíamos pensado, pero
podría interesarnos / Otro.

### 21. Importación y datos históricos

**Q-PAC-050** (Media) — ¿Tienen pacientes ya registrados en un sistema anterior, planillas u
otro medio, que deban pasarse a este nuevo sistema?
Opciones: Sí, tenemos datos que migrar / No, arrancamos desde cero / No estoy seguro/a, hay que
revisarlo / Otro.

**Q-PAC-051** (Baja) — ¿Debe existir un tiempo a partir del cual un paciente sin turnos ni
consultas deja de mostrarse por defecto?
Opciones: Sí / No, deben verse siempre / Otro.

### 22. Multisede

**Q-PAC-052** (Baja) — Si en el futuro abren otra sede, ¿un paciente debería ser una única ficha
compartida entre sedes, o una ficha distinta por sede?
Opciones: Una única ficha compartida / Una ficha por sede / No aplica, no planeamos más sedes /
Otro.

### 23. Accesibilidad y necesidades especiales

**Q-PAC-053** (Media) — ¿Necesitan registrar si un paciente tiene alguna necesidad especial para
su atención (discapacidad visual/auditiva, movilidad reducida, necesidad de intérprete)?
Opciones: Sí / No / Otro.

---

## Próximos pasos

1. Presentar el cuestionario interactivo (artefacto Claude) al cliente para que seleccione las
   respuestas.
2. Volcar cada respuesta recibida a `Q-PAC-0XX` en [`preguntas.md`](preguntas.md) (`Estado:
   RESPONDIDA`) y registrar la decisión derivada en [`decisiones.md`](decisiones.md).
3. Resolver las 3 preguntas 🔧 internas dentro del equipo técnico, documentando la decisión de
   igual manera.
4. Propagar los cambios a los documentos listados en `Impacta en:` de cada pregunta, según
   [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md).
