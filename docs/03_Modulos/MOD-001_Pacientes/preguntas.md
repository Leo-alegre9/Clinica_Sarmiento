# MOD-001 — Preguntas de refinamiento

Batería exhaustiva de preguntas para refinar el módulo Pacientes. Ninguna respuesta se asume:
todo lo que no está aquí resuelto queda `PENDIENTE_DEFINICION` en el resto de los documentos
del módulo. Formato según
[`../../00_Gobernanza/convenciones.md`](../../00_Gobernanza/convenciones.md) y estados según
[`../../00_Gobernanza/estados_requerimientos.md`](../../00_Gobernanza/estados_requerimientos.md).

**Resumen:** 53 preguntas (`Q-PAC-001` a `Q-PAC-053`). El cliente respondió las 51 preguntas
🟢 que le correspondían el 2026-09-08 (ver
[`preguntas_cliente.md`](preguntas_cliente.md)); las 3 preguntas 🔧 internas (`Q-PAC-005`,
`Q-PAC-008`, `Q-PAC-023`-interna) las resolvió el equipo con esa misma información, sin
necesidad de pregunta al cliente. Las dos contradicciones detectadas (`Q-PAC-013`/`Q-PAC-039`
sobre "dar de baja", `Q-PAC-041` sobre fallecimiento) fueron aclaradas por el cliente el
2026-09-08. **Las 54 preguntas quedaron `VALIDADA` el 2026-09-08**: se propagaron a
`requerimientos.md`, `reglas_negocio.md`, `datos.md`, `casos_uso.md`, `historias_usuario.md`,
`criterios_aceptacion.md`, `riesgos.md`, `alcance.md`, `trazabilidad.md` y a los índices
centrales en `02_Requerimientos/`, según
[`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md). Dos
excepciones parciales quedan anotadas en el propio requerimiento: `Q-PAC-030`/`Q-PAC-031`/
`Q-PAC-032` (contenido clínico específico pendiente de los médicos, `INV-004`) y `Q-PAC-016`
(la detección de duplicados está validada; la mecánica de fusión en sí, `RN-PAC-006`, nunca
tuvo pregunta propia y sigue `PROPUESTO`, ver `RIE-PAC-007`).

**Actualización 2026-09-24:** la excepción de contenido clínico se cerró. Las respuestas de los
médicos (`Q-HCL-006`/`Q-HCL-007`, `INV-004`) confirman las tres categorías de antecedentes y el
aviso destacado. Se agregaron 16 preguntas de cierre (`Q-PAC-054` a `Q-PAC-069`, sección 24),
todas MEDIA o BAJA con hipótesis de trabajo, entre ellas las de la mecánica de fusión.

---

## 1. Identificación

### Q-PAC-001

**Categoría:** Datos / Reglas de negocio · **Criticidad:** ALTA

**Pregunta:** ¿Puede existir más de un paciente con el mismo DNI en el sistema?

**Motivo:** Define una restricción estructural del modelo de datos (¿el DNI es clave única o
solo un campo más?) y condiciona toda la lógica de detección de duplicados.

**Impacta en:** RF-PAC-003, RN-PAC-001, CU-PAC-001

**Respuesta:** No, el DNI debe ser único. Resuelve `DECP-002` (ver
[`../../08_Pendientes/decisiones_pendientes.md`](../../08_Pendientes/decisiones_pendientes.md)).
**Estado:** VALIDADA

---

### Q-PAC-002

**Categoría:** Reglas de negocio · **Criticidad:** ALTA

**Pregunta:** Si el DNI no es único, ¿qué combinación de datos determina que dos registros son
"la misma persona" (DNI + fecha de nacimiento, DNI + apellido, otro criterio)?

**Motivo:** Sin esta regla no se puede implementar ninguna validación de alta ni detección de
duplicados de forma confiable.

**Impacta en:** RF-PAC-003, RN-PAC-001, CU-PAC-001, CU-PAC-003

**Respuesta:** La premisa cambia con `Q-PAC-001` (el DNI sí es único, no puede haber dos
registros con el mismo). La pregunta reformulada al cliente fue distinta ("¿qué datos usa
recepción para confirmar que es la misma persona ante una posible coincidencia?"): **Otro:
número de afiliado de obra social**, como criterio adicional a los estándar (nombre, fecha de
nacimiento, teléfono) para la detección de duplicados de `Q-PAC-016`.
**Estado:** VALIDADA

---

### Q-PAC-003

**Categoría:** Datos · **Criticidad:** MEDIA

**Pregunta:** ¿Qué tipos de documento deben soportarse además del DNI argentino (pasaporte,
cédula de identidad extranjera, libreta cívica/enrolamiento para adultos mayores, otro)?

**Motivo:** Afecta el diseño del campo de identificación (¿tipo + número, o solo número?).

**Impacta en:** RF-PAC-013, datos.md (sección Identificación)

**Respuesta:** Cédula de identidad extranjera (único tipo adicional mencionado; no marcó
pasaporte, libreta cívica ni "ninguno otro").
**Estado:** VALIDADA

---

### Q-PAC-004

**Categoría:** Datos · **Criticidad:** ALTA

**Pregunta:** ¿Cómo se identifica en el sistema a un recién nacido que todavía no tiene DNI
tramitado, pero que ya requiere atención (por ejemplo, control oftalmológico neonatal)?

**Motivo:** Caso real y frecuente en un sistema de salud; sin resolverlo, la recepción no
podría dar de alta a estos pacientes.

**Impacta en:** RF-PAC-001, RF-PAC-013, RN-PAC-002

**Respuesta:** Con un número o código provisorio interno.
**Estado:** VALIDADA

---

### Q-PAC-005

**Categoría:** Datos / Validación · **Criticidad:** BAJA

**Pregunta:** ¿Debe validarse el formato del DNI argentino (solo dígitos, longitud), o el
campo debe aceptar cualquier cadena para no bloquear casos no previstos (extranjeros,
documentos con letras)?

**Motivo:** Afecta el nivel de validación en el formulario de alta.

**Impacta en:** RF-PAC-001, datos.md

**Respuesta (EQUIPO, informada por `Q-PAC-003/006/007`):** No debe exigirse un formato
numérico estricto de DNI argentino. El campo debe aceptar cédulas extranjeras (`Q-PAC-003`),
pacientes sin ningún documento (`Q-PAC-006`: "Sí, siempre" se les debe poder atender) y
cualquiera de pasaporte/DNI extranjero/CUIL-CUIT (`Q-PAC-007`: "todos los anteriores"). Se
modela como tipo de documento + valor libre, con el campo opcional.
**Estado:** VALIDADA — origen EQUIPO, no cliente.

---

## 2. Pacientes sin DNI y extranjeros

### Q-PAC-006

**Categoría:** Datos / Reglas de negocio · **Criticidad:** ALTA

**Pregunta:** ¿Debe permitirse dar de alta y operar (turnos, historia clínica) a un paciente
adulto sin ningún documento de identidad?

**Motivo:** Determina si la identificación es estrictamente obligatoria o si el sistema debe
tolerar la ausencia total de documento.

**Impacta en:** RF-PAC-001, RF-PAC-013, RN-PAC-002

**Respuesta:** Sí, siempre.
**Estado:** VALIDADA

---

### Q-PAC-007

**Categoría:** Datos · **Criticidad:** MEDIA

**Pregunta:** Para pacientes extranjeros, ¿qué documento se acepta como identificación
principal (pasaporte, DNI de su país, CUIL/CUIT si lo tramitaron)?

**Motivo:** Define el modelo de identificación para un segmento de pacientes ya anticipado por
el propio pedido del cliente.

**Impacta en:** RF-PAC-013, datos.md

**Respuesta:** Otro: "Todos los anteriores" — se acepta pasaporte, DNI de su país de origen o
CUIL/CUIT indistintamente.
**Estado:** VALIDADA

---

### Q-PAC-008

**Categoría:** Reglas de negocio · **Criticidad:** ALTA

**Pregunta:** Cuando un paciente sin DNI (recién nacido u otro caso) posteriormente obtiene su
documento, ¿cómo se completa ese dato sin perder el historial ya generado bajo el identificador
provisorio?

**Motivo:** Sin esta regla, se corre el riesgo de crear una ficha nueva y duplicar la historia
clínica del paciente.

**Impacta en:** RF-PAC-017, RN-PAC-002, CU-PAC-003

**Respuesta (EQUIPO, informada por `Q-PAC-004/009`):** Se completa editando el mismo registro
creado con el código provisorio interno (`Q-PAC-004`), nunca creando una ficha nueva; recepción
hace seguimiento activo del dato pendiente (`Q-PAC-009`).
**Estado:** VALIDADA — origen EQUIPO, no cliente.

---

### Q-PAC-009

**Categoría:** UX / Operativa · **Criticidad:** MEDIA

**Pregunta:** ¿Quién completa el DNI provisorio de un recién nacido en la práctica: la
recepción, o se deja explícitamente pendiente hasta que la familia lo aporte?

**Motivo:** Afecta el diseño del flujo de alta y si el campo puede quedar vacío
temporalmente sin bloquear otras operaciones.

**Impacta en:** RF-PAC-001, CU-PAC-001

**Respuesta:** La recepción hace seguimiento y lo pide.
**Estado:** VALIDADA

---

### Q-PAC-010

**Categoría:** Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** ¿Se necesita distinguir explícitamente en el sistema entre "paciente sin
documento" y "paciente con documento en trámite", o alcanza con un único estado de
identificación incompleta?

**Motivo:** Afecta el modelo de datos (¿un campo de estado de identificación, o alcanza con
DNI nulo?).

**Impacta en:** datos.md, RN-PAC-002

**Respuesta:** Sí, necesitamos distinguir ambos casos.
**Estado:** VALIDADA

---

## 3. Alta de paciente

### Q-PAC-011

**Categoría:** Datos / UX · **Criticidad:** ALTA

**Pregunta:** ¿Cuáles son los campos realmente obligatorios para completar un alta en
recepción, considerando que suele hacerse bajo presión de tiempo (paciente esperando)?

**Motivo:** Un alta con demasiados campos obligatorios frena la operación diaria; muy pocos
campos obligatorios generan fichas incompletas e inconsistentes. Es la base del diseño del
formulario de alta.

**Impacta en:** RF-PAC-001, CU-PAC-001, criterios_aceptacion.md

**Respuesta:** DNI, Obra social, Nombre y apellido, Fecha de nacimiento, Teléfono, Domicilio
(no marcó Email). Coherente con `Q-PAC-043` (domicilio obligatorio).
**Estado:** VALIDADA

---

### Q-PAC-012

**Categoría:** UX / Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** ¿El alta puede hacerse en dos pasos — un alta "rápida" con datos mínimos seguida
de completar el resto más tarde — o el sistema debe exigir la ficha completa desde el primer
momento?

**Motivo:** Afecta directamente la experiencia de recepción y el diseño del formulario.

**Impacta en:** RF-PAC-001, HU-PAC-001

**Respuesta:** Ficha completa siempre.
**Estado:** VALIDADA

---

## 4. Modificación

### Q-PAC-017

**Categoría:** Reglas de negocio / Auditoría · **Criticidad:** MEDIA

**Pregunta:** ¿Debe conservarse un historial visible de cambios sobre el DNI de un paciente
(por ejemplo, corrección de un error de carga vs. cambio real de documento), y quién puede
consultarlo?

**Motivo:** Un DNI mal cargado es un error operativo común; distinguirlo de un cambio real
afecta la confianza en los datos históricos.

**Impacta en:** RF-PAC-017, RN-PAC-008, MOD-028 (Auditoría)

**Respuesta:** Sí, siempre (historial visible, sin restringirlo a un rol específico). Coherente
con `Q-PAC-040` (auditar todos los cambios).
**Estado:** VALIDADA

---

### Q-PAC-037

**Categoría:** Permisos · **Criticidad:** MEDIA

**Pregunta:** ¿Cualquier usuario con acceso a la ficha del paciente puede modificar cualquier
campo, o hay campos que solo puede editar un rol específico (por ejemplo, solo un médico puede
editar antecedentes clínicos)?

**Motivo:** Determina si los permisos se controlan a nivel de pantalla completa o a nivel de
campo/sección.

**Impacta en:** RF-PAC-004, RF-PAC-014, RN-PAC-007

**Respuesta:** Otro: "Médico y un perfil o dos que sería el mío y el de Nadia, para corregir
cualquier cosa. Y si se puede, [una ventana de] 12 o 24h que nos permita modificar." Es decir:
ciertos campos (antecedentes/datos clínicos) solo los edita un médico, salvo dos perfiles
directivos con permiso de corrección total; además pide una ventana de 12-24h de edición
abierta tras crear el registro. Mismo pedido que `Q-HCL-002` de la Ronda 2.
**Estado:** VALIDADA — la ventana de 12-24h es un requisito funcional nuevo, no una simple
regla de permisos; agregar a `requerimientos.md` como funcionalidad a diseñar.

---

## 5. Baja y reactivación

### Q-PAC-013

**Categoría:** Reglas de negocio · **Criticidad:** ALTA

**Pregunta:** ¿Qué significa exactamente "dar de baja" a un paciente? ¿Impide agendarle
turnos, lo oculta de las búsquedas por defecto, ambas cosas, o algo distinto? ¿Existe también
un estado "bloqueado" distinto de "inactivo"?

**Motivo:** Sin esta definición no puede diseñarse el estado del paciente ni el flujo de
baja/reactivación (ver hipótesis en `diagramas.md`).

**Impacta en:** RF-PAC-005, RN-PAC-005, HU-PAC-004

**Respuesta (aclarada 2026-09-08):** "Dar de baja" y "eliminar" son conceptos distintos. Se
permite que usuarios específicos den de baja a un paciente cuando se requiera, **de forma
lógica únicamente** (marca de estado inactivo/bloqueado) — nunca se elimina físicamente de la
base de datos, precisamente por la obligación legal de conservar la historia clínica 10 años.
Quién puede hacerlo: ver `Q-PAC-039`.
**Estado:** VALIDADA — contradicción resuelta, lista para propagar a `RN-PAC-005`.

---

## 6. Búsqueda

### Q-PAC-014

**Categoría:** UX / Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** ¿La búsqueda de pacientes debe incluir por defecto a los pacientes inactivos/de
baja, o solo debe mostrarlos bajo un filtro explícito ("incluir inactivos")?

**Motivo:** Afecta tanto la usabilidad diaria (evitar ruido) como el riesgo de no encontrar un
paciente real (reactivación).

**Impacta en:** RF-PAC-002, CU-PAC-002

**Respuesta:** Mostrar todos siempre. Coherente con `Q-PAC-051` (los inactivos deben verse
siempre, sin ocultarse por tiempo transcurrido).
**Estado:** VALIDADA

---

### Q-PAC-015

**Categoría:** Datos / UX · **Criticidad:** MEDIA

**Pregunta:** Además de DNI y nombre/apellido, ¿qué otros criterios de búsqueda se necesitan en
la práctica (teléfono, fecha de nacimiento, número de afiliado de obra social)?

**Motivo:** Recepción suele buscar por teléfono cuando el paciente llama sin tener el DNI a
mano; define el alcance del buscador.

**Impacta en:** RF-PAC-002, CU-PAC-002

**Respuesta:** N.º de afiliado de obra social (no marcó teléfono ni fecha de nacimiento).
**Estado:** VALIDADA

---

## 7. Duplicados

### Q-PAC-016

**Categoría:** Reglas de negocio / UX · **Criticidad:** ALTA

**Pregunta:** Cuando el sistema detecta un posible duplicado al momento del alta (mismo DNI, o
nombre y fecha de nacimiento coincidentes), ¿debe bloquear el alta, solo advertir y permitir
continuar, o depende del tipo de coincidencia?

**Motivo:** Es la regla central para prevenir el riesgo `RIE-PAC-001` (historias clínicas
fragmentadas por duplicados) sin frenar la operación en casos legítimos (p. ej. dos personas
distintas con el mismo nombre).

**Impacta en:** RF-PAC-003, RF-PAC-012, RN-PAC-001, RN-PAC-006, CU-PAC-001, CU-PAC-003

**Respuesta:** Advertir pero permitir continuar si recepción confirma que son personas
distintas. Ver `Q-PAC-002` para el criterio adicional de confirmación (número de afiliado).
**Estado:** VALIDADA

---

## 8. Obra social

### Q-PAC-018

**Categoría:** Reglas de negocio · **Criticidad:** ALTA

**Pregunta:** ¿Un paciente puede tener más de una obra social asociada al mismo tiempo? Si es
así, ¿existe el concepto de obra social "principal" a efectos de facturación/turnos?

**Motivo:** Define la cardinalidad de la relación paciente↔obra social en el modelo de datos —
es una de las decisiones estructurales más importantes del módulo.

**Impacta en:** RF-PAC-007, RN-PAC-003, HU-PAC-006, modelo_dominio

**Respuesta:** Sí, y una debe marcarse como principal.
**Estado:** VALIDADA

---

### Q-PAC-019

**Categoría:** Datos · **Criticidad:** ALTA

**Pregunta:** ¿Qué información exacta se necesita registrar por cada afiliación (número de
afiliado, plan, condición de titular o familiar a cargo, vigencia, parentesco con el titular)?

**Motivo:** Determina el detalle del modelo de datos de afiliación y su relación con el futuro
`MOD-019`/`MOD-020`.

**Impacta en:** RF-PAC-007, MOD-019, MOD-020

**Respuesta:** N.º de afiliado, Plan o categoría, Titular o familiar a cargo (no marcó vigencia
ni parentesco con el titular).
**Estado:** VALIDADA

---

### Q-PAC-020

**Categoría:** Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** Cuando un paciente cambia de obra social, ¿debe conservarse el historial de
coberturas anteriores (por ejemplo, para justificar una consulta pasada ante una auditoría de
obra social)?

**Motivo:** Afecta si la relación paciente↔obra social se modela como reemplazable o como
histórico versionado.

**Impacta en:** RF-PAC-007, RF-PAC-017, MOD-019

**Respuesta:** Sí.
**Estado:** VALIDADA

---

### Q-PAC-021

**Categoría:** Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** ¿Puede un paciente con obra social vigente optar por atenderse como particular en
una consulta puntual? ¿Eso se registra a nivel del turno/consulta o requiere "desactivar"
temporalmente la obra social del paciente?

**Motivo:** Caso frecuente en clínicas privadas (paciente prefiere pagar particular por
rapidez); afecta el diseño de la relación entre paciente, obra social y consulta.

**Impacta en:** RF-PAC-007, MOD-003, MOD-022 (Caja)

**Respuesta:** Sí.
**Estado:** VALIDADA

---

## 9. Responsables / tutores / menores

### Q-PAC-022

**Categoría:** Reglas de negocio · **Criticidad:** ALTA

**Pregunta:** ¿A partir de qué edad se considera "menor" a los efectos de requerir un
responsable en el sistema? ¿Coincide con la mayoría de edad legal (18 años) o hay un umbral
distinto para ciertos actos (por ejemplo, consentir una práctica)?

**Motivo:** Sin este umbral no puede implementarse la regla `RN-PAC-004` (menor requiere
responsable) ni el flujo de `HU-PAC-007`.

**Impacta en:** RF-PAC-008, RN-PAC-004, HU-PAC-007

**Respuesta:** 18 años (mayoría de edad legal).
**Estado:** VALIDADA

---

### Q-PAC-023

**Categoría:** Datos / Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** ¿Un responsable/tutor debe existir como un registro de paciente en el sistema
(por si él mismo también se atiende), o es una entidad distinta que solo sirve como dato de
contacto del menor?

**Motivo:** Decisión estructural: modelar "Responsable" como una entidad propia vs. reutilizar
"Paciente" con un rol adicional.

**Impacta en:** RF-PAC-008, modelo_dominio

**Respuesta (cliente, versión reformulada):** Sí, frecuentemente un responsable/tutor es
también paciente de la clínica.
**Decisión de EQUIPO derivada:** dado que es frecuente, "Responsable" se modela como una
referencia a un registro de `Paciente` existente (rol adicional), no como una entidad
independiente. Evita duplicar datos de la misma persona en dos tablas.
**Estado:** VALIDADA — origen mixto (premisa CLIENTE, modelado EQUIPO).

---

### Q-PAC-024

**Categoría:** Datos · **Criticidad:** MEDIA

**Pregunta:** ¿Puede haber más de un responsable registrado para un mismo menor (por ejemplo,
madre y padre)? ¿Deben registrarse todos o alcanza con uno como contacto principal?

**Motivo:** Afecta la cardinalidad de la relación paciente↔responsable.

**Impacta en:** RF-PAC-008, HU-PAC-007

**Respuesta:** Sí, todos los que correspondan.
**Estado:** VALIDADA

---

### Q-PAC-025

**Categoría:** Reglas de negocio · **Criticidad:** BAJA

**Pregunta:** ¿Qué sucede con la relación responsable↔paciente cuando el paciente alcanza la
mayoría de edad? ¿Se desvincula automáticamente, se conserva como dato histórico, o requiere
una acción manual?

**Motivo:** Evita que el sistema siga mostrando como "menor" a un paciente que ya no lo es.

**Impacta en:** RF-PAC-008, RN-PAC-004

**Respuesta:** Conservarse como dato histórico.
**Estado:** VALIDADA

---

## 10. Contacto y emergencia

### Q-PAC-026

**Categoría:** Datos · **Criticidad:** MEDIA

**Pregunta:** De los datos de contacto (teléfono, WhatsApp, email), ¿cuáles son obligatorios y
cuáles opcionales? ¿El WhatsApp se considera siempre igual al teléfono, o puede ser un número
distinto?

**Motivo:** Afecta el formulario de alta y es prerrequisito para `MOD-014` (recordatorios) y
`MOD-030` (WhatsApp).

**Impacta en:** RF-PAC-009, MOD-014, MOD-030

**Respuesta:** WhatsApp (si es distinto al teléfono), Teléfono — ambos obligatorios (no marcó
Email ni "ninguno obligatorio").
**Estado:** VALIDADA

---

### Q-PAC-027

**Categoría:** Datos / Reglas de negocio · **Criticidad:** BAJA

**Pregunta:** ¿El contacto de emergencia es obligatorio para todos los pacientes, o solo para
ciertos casos (pacientes quirúrgicos, menores, adultos mayores)?

**Motivo:** Un campo obligatorio para todos podría ser excesivo; limitarlo a ciertos casos
requiere una regla de activación condicional.

**Impacta en:** RF-PAC-009, MOD-013 (Cirugías)

**Respuesta:** Siempre.
**Estado:** VALIDADA

---

## 11. Fotografías, documentación y archivos

### Q-PAC-028

**Categoría:** Datos / Seguridad · **Criticidad:** MEDIA

**Pregunta:** ¿Se necesita fotografía del paciente para identificación visual en recepción, o
solo se planteó como posibilidad? ¿Quién la toma/carga y con qué consentimiento?

**Motivo:** Afecta el alcance del módulo y genera requisitos de almacenamiento seguro de
imágenes.

**Impacta en:** RF-PAC-010, RNF-PRI-001

**Respuesta:** Podría ser útil, pero no es prioridad.
**Estado:** VALIDADA

---

### Q-PAC-029

**Categoría:** Datos · **Criticidad:** BAJA

**Pregunta:** Además de la fotografía, ¿qué otros documentos deben poder adjuntarse a la ficha
del paciente (DNI escaneado, carnet de obra social, consentimientos firmados)?

**Motivo:** Define el alcance de la gestión documental del paciente frente a la de `MOD-007`
(estudios/documentación clínica).

**Impacta en:** RF-PAC-010, MOD-007

**Respuesta:** DNI escaneado, Carnet de obra social, Consentimientos firmados (los tres).
**Estado:** VALIDADA

---

## 12. Antecedentes, alergias y alertas clínicas

### Q-PAC-030

**Categoría:** Datos / Clínica · **Criticidad:** ALTA

**Pregunta:** ¿Qué antecedentes y alergias deben registrarse a nivel de la ficha del paciente
(visibles siempre) frente a los que se registran dentro de cada consulta en la historia
clínica (`MOD-002`/`MOD-003`)?

**Motivo:** Define el límite funcional entre Pacientes y Historia Clínica; sin esta distinción
se corre el riesgo de duplicar o de no tener visible una alerta crítica al momento de atender.

**Impacta en:** RF-PAC-011, MOD-002, MOD-003, alcance.md

**Respuesta:** Alergias a medicamentos, Antecedentes quirúrgicos relevantes, Enfermedades
crónicas (los tres, no "ninguno").
**Estado:** VALIDADA

---

### Q-PAC-031

**Categoría:** UX / Clínica · **Criticidad:** ALTA

**Pregunta:** ¿Cómo debe mostrarse una alerta clínica crítica (por ejemplo, alergia grave) al
abrir la ficha del paciente, para garantizar que no pase desapercibida?

**Motivo:** Tiene implicancia directa en seguridad del paciente, no solo en diseño de UI.

**Impacta en:** RF-PAC-011, HU-PAC-009

**Respuesta:** Ambas (aviso destacado siempre visible arriba de la ficha + ventana emergente al
abrir la ficha).
**Estado:** VALIDADA

---

### Q-PAC-032

**Categoría:** Permisos · **Criticidad:** MEDIA

**Pregunta:** ¿Quién puede cargar o editar antecedentes/alertas clínicas: solo un profesional
médico, o también administración/recepción con supervisión posterior?

**Motivo:** Afecta el modelo de permisos por campo (ver `Q-PAC-037`) y la calidad/confiabilidad
de la información clínica.

**Impacta en:** RF-PAC-011, RF-PAC-014, RN-PAC-007

**Respuesta:** También administración/recepción, con supervisión posterior.
**Estado:** VALIDADA

---

## 13. Exportación e impresión

### Q-PAC-033

**Categoría:** Funcional · **Criticidad:** BAJA

**Pregunta:** ¿Qué formato de ficha impresa/exportada del paciente se necesita (para
entregar al paciente, para una obra social, para un trámite)?

**Motivo:** Determina si se necesita una plantilla de impresión específica o alcanza con una
vista de solo lectura.

**Impacta en:** RF-PAC-016

**Respuesta:** Para entregársela al paciente, Para una obra social, Para un trámite (los tres
motivos).
**Estado:** VALIDADA

---

### Q-PAC-034

**Categoría:** Seguridad · **Criticidad:** MEDIA

**Pregunta:** ¿La exportación/impresión de la ficha del paciente debe quedar auditada (quién
exportó, cuándo, qué paciente)?

**Motivo:** Una ficha impresa/exportada sale del control del sistema; su trazabilidad es
relevante para `RNF-AUD-001`.

**Impacta en:** RF-PAC-016, RNF-AUD-001, MOD-028

**Respuesta:** Sí.
**Estado:** VALIDADA

---

## 14. Datos personales adicionales

### Q-PAC-035

**Categoría:** Datos · **Criticidad:** MEDIA

**Pregunta:** ¿El sistema debe distinguir "sexo" (biológico, relevante clínicamente) de
"género" (autopercibido), como dos campos separados? ¿Con qué opciones/catálogo en cada caso?

**Motivo:** Tiene relevancia clínica (sexo) y de trato/legal (género); definirlo mal puede ser
tanto un problema técnico como de respeto al paciente.

**Impacta en:** RF-PAC-001, datos.md

**Respuesta:** No, alcanza con uno solo.
**Estado:** VALIDADA

---

## 15. Privacidad, permisos y auditoría

### Q-PAC-036

**Categoría:** Permisos / Privacidad · **Criticidad:** ALTA

**Pregunta:** ¿Qué información del paciente puede ver cada rol (secretario/a, médico,
administrador)? En particular, ¿toda la clínica ve la historia clínica de todos los pacientes,
o solo el/los profesional/es que lo atienden?

**Motivo:** Requisito de seguridad central del sistema; condiciona el diseño de `MOD-027`
(Roles y permisos) y de toda pantalla que muestre datos de paciente.

**Impacta en:** RF-PAC-014, RN-PAC-007, MOD-027

**Respuesta:** Todo el personal (puede ver la historia clínica de cualquier paciente, sin
restringirla a quienes lo atienden). **Nota de riesgo:** simplifica el modelo de permisos pero
amplía la superficie de acceso a datos clínicos sensibles; considerar como riesgo de privacidad
a documentar en `riesgos.md`, no solo como regla de negocio.
**Estado:** VALIDADA

---

### Q-PAC-038

**Categoría:** Permisos / Privacidad · **Criticidad:** ALTA

**Pregunta:** ¿Los datos administrativos (contacto, obra social) y los datos clínicos
(antecedentes, alertas) requieren permisos distintos, o un usuario con acceso a la ficha ve
todo por igual?

**Motivo:** Determina si el modelo de permisos necesita granularidad por sección dentro de la
ficha del paciente.

**Impacta en:** RF-PAC-014, RN-PAC-007, MOD-027

**Respuesta:** No, quien accede a la ficha ve todo por igual. Coherente con `Q-PAC-036`. Nota:
esto es sobre **visualización**; `Q-PAC-037` sí establece una restricción de **edición** de
ciertos campos clínicos a médico + 1-2 perfiles directivos — ambas respuestas son compatibles
(ver todos, editar no todos).
**Estado:** VALIDADA

---

### Q-PAC-039

**Categoría:** Permisos · **Criticidad:** MEDIA

**Pregunta:** ¿Quién puede eliminar/dar de baja un paciente? ¿Es una acción exclusiva de
administradores, o cualquier secretario/a puede hacerlo?

**Motivo:** Es una acción de alto impacto (afecta turnos, historia clínica); su permiso debe
quedar explícito.

**Impacta en:** RF-PAC-005, RF-PAC-014

**Respuesta (aclarada 2026-09-08):** El administrador puede dar de baja (baja lógica) a un
paciente, y también un médico específico designado para ese caso (a detallar más adelante qué
médicos y bajo qué criterio). No es una acción abierta a cualquier secretario/a.
**Estado:** VALIDADA — contradicción con `Q-PAC-013` resuelta.

---

### Q-PAC-040

**Categoría:** Auditoría · **Criticidad:** ALTA

**Pregunta:** ¿Qué cambios sobre la ficha del paciente deben quedar auditados obligatoriamente
(todos los campos, o solo los sensibles: DNI, obra social, estado, datos clínicos)?

**Motivo:** Define el alcance real de `RN-PAC-008`/`RNF-AUD-001` aplicado a este módulo, para
no sobre-auditar (ruido) ni sub-auditar (riesgo).

**Impacta en:** RF-PAC-015, RN-PAC-008, MOD-028

**Respuesta:** Todos los cambios.
**Estado:** VALIDADA

---

## 16. Fallecimiento

### Q-PAC-041

**Categoría:** Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** Al registrar el fallecimiento de un paciente, ¿qué debe suceder automáticamente
con sus turnos futuros, recordatorios pendientes y obra social vigente?

**Motivo:** Evita que el sistema siga generando recordatorios o mostrando turnos activos para
un paciente fallecido, lo cual sería un error operativo grave y de mal gusto hacia la familia.

**Impacta en:** RF-PAC-006, HU-PAC-005, MOD-010, MOD-014

**Respuesta (aclarada 2026-09-08):** Ninguna acción automática — cada caso se revisa
manualmente (turnos futuros, recordatorios y obra social vigente incluidos).
**Estado:** VALIDADA — contradicción resuelta.

---

### Q-PAC-042

**Categoría:** Permisos · **Criticidad:** BAJA

**Pregunta:** ¿Quién puede registrar el fallecimiento de un paciente (cualquier usuario,
solo administración, solo un médico)?

**Motivo:** Es una acción sensible que probablemente requiera un permiso específico.

**Impacta en:** RF-PAC-006, RF-PAC-014

**Respuesta:** Solo administración.
**Estado:** VALIDADA

---

## 17. Domicilio

### Q-PAC-043

**Categoría:** Datos · **Criticidad:** BAJA

**Pregunta:** ¿El domicilio del paciente es obligatorio, o solo se registra si el paciente lo
provee espontáneamente?

**Motivo:** Afecta el formulario de alta; el domicilio suele ser un dato de baja urgencia
operativa frente al contacto telefónico.

**Impacta en:** RF-PAC-001, datos.md

**Respuesta:** Sí (obligatorio). Coherente con `Q-PAC-011` (domicilio entre los campos
obligatorios del alta).
**Estado:** VALIDADA

---

### Q-PAC-044

**Categoría:** Datos · **Criticidad:** BAJA

**Pregunta:** ¿Se necesita el domicilio estructurado (calle, número, localidad, provincia por
separado) o alcanza con un campo de texto libre?

**Motivo:** Afecta si el domicilio se usa para algo más que mostrarlo (por ejemplo, filtrar
pacientes por zona, o si es puramente informativo).

**Impacta en:** datos.md

**Respuesta:** Sí (necesitan poder buscar/filtrar por zona o localidad). **Implicancia de
diseño:** si se necesita filtrar por zona, el domicilio no puede ser un único campo de texto
libre — como mínimo necesita un subcampo de localidad/zona estructurado.
**Estado:** VALIDADA

---

## 18. Consentimiento y tratamiento de datos

### Q-PAC-045

**Categoría:** Legal / Privacidad · **Criticidad:** ALTA

**Pregunta:** ¿Se necesita registrar el consentimiento informado del paciente para el
tratamiento de sus datos personales y clínicos (Ley de Protección de Datos Personales)? ¿En
qué momento se solicita y cómo se deja constancia?

**Motivo:** Aplica especialmente al alta desde recepción y al formulario público de turnos
(`RC-012`); es un requisito potencialmente legal, no solo de producto.

**Impacta en:** RF-PAC-001, RNF-PRI-001, MOD-033

**Respuesta:** Sí, en el alta presencial (no marcó que también se pida en el formulario de
turnos online).
**Estado:** VALIDADA

---

### Q-PAC-046

**Categoría:** Legal / Privacidad · **Criticidad:** MEDIA

**Pregunta:** ¿Se necesita un consentimiento específico y separado para el uso de fotografías
del paciente (distinto del consentimiento general de tratamiento de datos)?

**Motivo:** El uso de imagen suele requerir consentimiento explícito diferenciado en el ámbito
de salud.

**Impacta en:** RF-PAC-010, Q-PAC-028

**Respuesta:** Sí.
**Estado:** VALIDADA

---

## 19. Comunicación

### Q-PAC-047

**Categoría:** Funcional / UX · **Criticidad:** MEDIA

**Pregunta:** ¿El paciente puede indicar un canal de comunicación preferido (llamada,
WhatsApp, email) y/o un horario en que prefiere no ser contactado?

**Motivo:** Insumo directo para `MOD-014` (recordatorios) y `MOD-029`-`MOD-031`
(notificaciones).

**Impacta en:** RF-PAC-009, MOD-014, MOD-029

**Respuesta:** Sí.
**Estado:** VALIDADA

---

### Q-PAC-048

**Categoría:** Legal / Privacidad · **Criticidad:** MEDIA

**Pregunta:** ¿El paciente puede oponerse a recibir comunicaciones no estrictamente necesarias
(por ejemplo, recordatorios promocionales, si los hubiera), manteniendo igualmente los avisos
de turno?

**Motivo:** Buenas prácticas de comunicación y potencial requisito legal de opt-out.

**Impacta en:** MOD-014, MOD-029

**Respuesta:** Sí.
**Estado:** VALIDADA

---

## 20. Portal del paciente (hipotético / futuro)

### Q-PAC-049

**Categoría:** Alcance · **Criticidad:** BAJA

**Pregunta:** ¿Existe intención, aunque sea a futuro, de que el paciente acceda directamente a
su propia ficha o historia clínica (portal de autogestión), más allá de solicitar un turno?

**Motivo:** No fue pedido explícitamente (ver
[`../../01_Proyecto/fuera_de_alcance.md`](../../01_Proyecto/fuera_de_alcance.md)), pero
condiciona si conviene dejar preparada la separación entre "datos que el paciente podría ver
de sí mismo" y "datos internos de la clínica" desde ahora.

**Impacta en:** alcance.md, fuera_de_alcance.md

**Respuesta:** No está en los planes.
**Estado:** VALIDADA

---

## 21. Importación y datos históricos

### Q-PAC-050

**Categoría:** Datos / Migración · **Criticidad:** MEDIA

**Pregunta:** ¿Existen pacientes registrados en el sistema anterior de la clínica (o en
planillas/Ampina) que deban migrarse a este sistema, o el sistema arranca con una base de
pacientes vacía?

**Motivo:** Condiciona directamente si se necesita un proceso de importación (`MOD-040`) antes
de poder operar el módulo en producción.

**Impacta en:** MOD-040, SUP-002

**Respuesta:** Sí, tenemos datos que migrar. Ver también `Q-IMP-001` de la Ronda 2 (también
estudios a migrar).
**Estado:** VALIDADA

---

### Q-PAC-051

**Categoría:** Datos / Retención · **Criticidad:** BAJA

**Pregunta:** ¿Hay un plazo a partir del cual un paciente inactivo (sin turnos ni consultas)
deja de mostrarse por defecto, o los pacientes inactivos se conservan indefinidamente visibles
bajo demanda?

**Motivo:** Afecta el diseño de búsqueda/listado y eventualmente la política de retención de
datos (`MOD-037`, `RNF-PRI-001`).

**Impacta en:** RF-PAC-002, RNF-PRI-001

**Respuesta:** No, deben verse siempre. Coherente con `Q-PAC-014`.
**Estado:** VALIDADA

---

## 22. Multisede (si aplica)

### Q-PAC-052

**Categoría:** Alcance / Datos · **Criticidad:** BAJA

**Pregunta:** Si en el futuro la clínica opera más de una sede (`SUP-001`), ¿un paciente es una
única ficha compartida entre sedes, o puede haber una ficha por sede?

**Motivo:** Afecta si conviene dejar el modelo preparado para un identificador de paciente
global desde ahora, aunque hoy exista una sola sede.

**Impacta en:** MOD-018, RNF-ESC-001

**Respuesta:** Una única ficha compartida. **Ya no es hipotético**: la Ronda 2 confirmó
(`Q-SED-001`) que la clínica opera más de una sede hoy mismo — ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-018`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-018).
**Estado:** VALIDADA

---

## 23. Accesibilidad y necesidades especiales

### Q-PAC-053

**Categoría:** UX / Clínica · **Criticidad:** MEDIA

**Pregunta:** ¿Es necesario registrar si un paciente tiene alguna necesidad especial relevante
para su atención (discapacidad visual/auditiva, movilidad reducida, necesidad de intérprete),
más allá de las alertas clínicas propiamente dichas?

**Motivo:** Especialmente relevante en una clínica oftalmológica, donde la discapacidad visual
del propio paciente puede condicionar cómo se lo atiende y comunica.

**Impacta en:** RF-PAC-011, MOD-011 (Recepción)

**Respuesta:** Sí.
**Estado:** VALIDADA

---

## 24. Cierre para validación (Ronda 3, 2026-09-24)

Preguntas surgidas al revisar el módulo completo para `LISTO_PARA_VALIDACION`. Salen de tres
fuentes: huecos que nunca se habían preguntado (fusión de duplicados), contradicciones internas
entre respuestas ya dadas, y la respuesta de los médicos sobre "procedencia". Respondidas el 2026-09-26 por Leonel Alegre, responsable del proyecto: 15 confirman la
hipótesis y `Q-PAC-064` la corrige (`CR-001`). Ninguna es de
criticidad ALTA: cada una tiene una **hipótesis de trabajo** (origen `ANÁLISIS`, `Requiere
validación: SÍ`) que ya se volcó al resto de los documentos marcada como tal. Se envían al
cliente en
[`../../08_Pendientes/cuestionario_cliente_ronda_3.md`](../../08_Pendientes/cuestionario_cliente_ronda_3.md),
bloque 1.

### Q-PAC-054

**Categoría:** Reglas de negocio / Permisos · **Criticidad:** MEDIA

**Pregunta:** Si se descubre que dos fichas corresponden a la misma persona (por ejemplo, una
cargada con código provisorio y otra con DNI), ¿quién puede unificarlas y qué debe pasar con cada
una?

**Motivo:** `RN-PAC-006` nunca tuvo pregunta propia (`RIE-PAC-007`). Unificar mal dos fichas
puede perder historia clínica, turnos o pagos.

**Impacta en:** RF-PAC-012, RN-PAC-006, HU-PAC-008, CU-PAC-003

**Hipótesis de trabajo:** solo Dirección/administración puede unificar. Elige cuál ficha queda;
todo lo del otro registro (historia clínica, turnos, pagos, coberturas, adjuntos, responsables)
pasa a la ficha que queda; el otro registro no se borra, queda en estado `Fusionado` apuntando a
la ficha que queda, y toda la operación se audita.

**Respuesta:** Sí, así. Solo Dirección/administración unifica. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-055

**Categoría:** Reglas de negocio / Clínica · **Criticidad:** MEDIA

**Pregunta:** Al unificar dos fichas con datos distintos (por ejemplo, alergias diferentes u
obras sociales distintas), ¿cómo se decide qué queda?

**Motivo:** Descartar una alergia al unificar sería un riesgo clínico directo.

**Impacta en:** RF-PAC-012, RN-PAC-006, CU-PAC-003

**Hipótesis de trabajo:** antecedentes y alertas clínicas **se suman siempre**, nunca se
descarta ninguno. Los datos administrativos (teléfono, domicilio, etc.) los elige campo por campo
quien unifica. Las coberturas de ambas fichas se conservan (la principal la elige quien unifica).

**Respuesta:** Sí, así. Antecedentes y alertas se suman siempre; el resto lo elige quien unifica. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-056

**Categoría:** Reglas de negocio · **Criticidad:** BAJA

**Pregunta:** ¿Hace falta poder deshacer una unificación hecha por error?

**Motivo:** Deshacer automáticamente es muy costoso de construir. Conviene saber si hace falta
antes de diseñarlo.

**Impacta en:** RF-PAC-012, CU-PAC-003

**Hipótesis de trabajo:** no se deshace automáticamente. Un error se corrige a mano con ayuda de
la auditoría, que conserva qué se movió de una ficha a otra.

**Respuesta:** Alcanza con corregirlo a mano. No se construye un "deshacer" automático. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-057

**Categoría:** Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** Si alguien intenta dar de alta a un paciente con **exactamente el mismo número de
documento** que otro ya cargado, ¿el sistema debe impedirlo y ofrecer abrir la ficha existente, o
solo advertir y dejar continuar?

**Motivo:** Contradicción entre dos respuestas ya dadas. `Q-PAC-001` dice que el DNI es único
("no puede haber dos pacientes con el mismo DNI"), mientras que `Q-PAC-016`, cuya pregunta
incluía el caso "mismo DNI", dice "advertir pero permitir continuar". Las dos no pueden cumplirse
a la vez para un DNI idéntico.

**Impacta en:** RF-PAC-003, RN-PAC-001, CU-PAC-001, criterios de `HU-PAC-001`

**Hipótesis de trabajo:** se aplica `Q-PAC-001`. Con el mismo tipo y número de documento, el
sistema **impide** el alta y ofrece abrir la ficha existente, o corregir el documento si estaba
mal cargado (queda en auditoría). `Q-PAC-016` (advertir y dejar continuar) se aplica a las
coincidencias que no son de documento: mismo nombre y fecha de nacimiento, o mismo número de
afiliado.

**Respuesta:** Sí, así. Con el mismo tipo y número de documento se impide el alta y se ofrece abrir la ficha existente; las demás coincidencias advierten y dejan continuar. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-058

**Categoría:** Permisos · **Criticidad:** MEDIA

**Pregunta:** La ventana de tiempo para corregir libremente un antecedente clínico después de
cargarlo, ¿es de 12 o de 24 horas?

**Motivo:** `Q-PAC-037` pidió "12 o 24h" sin elegir un valor (`RIE-PAC-008`).

**Impacta en:** RF-PAC-018, HU-PAC-010

**Hipótesis de trabajo:** 24 horas, configurable por Dirección (`MOD-036`), para poder
ajustarlo sin cambiar el sistema.

**Respuesta:** 24 horas. Confirma la hipótesis (configurable por Dirección en `MOD-036`). (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-059

**Categoría:** Permisos · **Criticidad:** MEDIA

**Pregunta:** Los perfiles directivos que pueden corregir cualquier dato (`Q-PAC-037`: "el mío
y el de Nadia"), ¿están sujetos también a esa ventana de 12-24 h, o pueden corregir sin límite de
tiempo?

**Motivo:** Dos respuestas del cliente no coinciden. En `Q-PAC-037` pidió una ventana de 12-24
h, y en `Q-HCL-002` (Ronda 2) pidió "editar sin tiempo de caducidad, por lo menos a un perfil de
los directivos".

**Impacta en:** RF-PAC-018, RN-PAC-007, HU-PAC-010

**Hipótesis de trabajo:** la ventana se aplica al médico. Los perfiles directivos designados
corrigen **sin límite de tiempo**, con auditoría. "Perfil directivo designado" es un permiso que
Dirección asigna a las personas que decida (`MOD-027`), no una lista fija de nombres.

**Respuesta:** Sí, así. Los perfiles directivos designados corrigen sin límite de tiempo; el perfil es un permiso asignable. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-060

**Categoría:** Permisos / Clínica · **Criticidad:** MEDIA

**Pregunta:** Recepción puede cargar antecedentes y alertas "con supervisión posterior"
(`Q-PAC-032`). ¿Puede también **modificar o borrar** uno ya cargado, o solo agregar nuevos? ¿Y
cómo se hace esa supervisión?

**Motivo:** Hay tensión entre `Q-PAC-032` (recepción carga, con supervisión posterior) y
`Q-PAC-037` (solo el médico y los directivos editan los campos clínicos).

**Impacta en:** RF-PAC-011, RF-PAC-014, RN-PAC-007, CU-PAC-004

**Hipótesis de trabajo:** recepción y administración pueden **agregar** antecedentes y alertas,
que quedan marcados "pendiente de revisión médica" (y se muestran igual, porque una alergia sin
revisar sigue siendo una alerta). Un médico los revisa y confirma. **Modificar o eliminar** un
antecedente existente queda reservado al médico (dentro de la ventana, `Q-PAC-058`) y a los
perfiles directivos (`Q-PAC-059`).

**Respuesta:** Sí, así. Recepción agrega (pendiente de revisión médica); modificar o borrar queda para el médico o un perfil directivo. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-061

**Categoría:** Permisos · **Criticidad:** BAJA

**Pregunta:** ¿Qué médicos pueden dar de baja a un paciente, y en qué casos?

**Motivo:** `Q-PAC-039` dejó "a detallar más adelante qué médicos y bajo qué criterio".

**Impacta en:** RF-PAC-005, HU-PAC-004

**Hipótesis de trabajo:** "dar de baja pacientes" es un permiso que Dirección le asigna a los
médicos que decida. Por defecto solo lo tiene Dirección/administración.

**Respuesta:** Sí, Dirección lo asigna. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-062

**Categoría:** Reglas de negocio · **Criticidad:** MEDIA

**Pregunta:** Al dar de baja a un paciente que tiene turnos futuros, ¿qué pasa con esos turnos?
¿Y se le pueden seguir dando turnos nuevos mientras está dado de baja?

**Motivo:** Para fallecimiento se definió "nada automático" (`Q-PAC-041`), pero para la baja no
se preguntó.

**Impacta en:** RF-PAC-005, HU-PAC-004, MOD-010

**Hipótesis de trabajo:** igual que con el fallecimiento, **nada automático**. Al dar de baja,
el sistema avisa que el paciente tiene turnos futuros y los lista, para revisarlos a mano. Un
paciente dado de baja no puede recibir turnos nuevos hasta que se lo reactive.

**Respuesta:** Sí, así. Se avisa y se listan los turnos futuros, sin cancelarlos; un paciente dado de baja no recibe turnos nuevos. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-063

**Categoría:** Reglas de negocio · **Criticidad:** BAJA

**Pregunta:** Si se registra un fallecimiento por error, ¿se puede revertir? ¿Quién puede
hacerlo?

**Motivo:** Hoy el estado `Fallecido` no tiene salida (`diagramas.md`).

**Impacta en:** RF-PAC-006, HU-PAC-005

**Hipótesis de trabajo:** solo administración puede revertirlo, con un motivo obligatorio y
auditoría.

**Respuesta:** Sí. Solo administración revierte un fallecimiento cargado por error, con motivo. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-064

**Categoría:** Datos · **Criticidad:** MEDIA

**Pregunta:** Los médicos pidieron ver la "procedencia" del paciente al abrir la ficha
(`Q-HCL-003`). ¿Qué quiere decir: la localidad donde vive, quién lo derivó (otro médico u otra
institución), o algo distinto?

**Motivo:** Si es quién lo derivó, hace falta un dato nuevo en la ficha. Si es la localidad, ya
existe.

**Impacta en:** `datos.md`, `DEC-HCL-001`

**Hipótesis de trabajo:** es la localidad del domicilio, que ya es obligatoria. No se agrega
ningún campo nuevo.

**Respuesta:** Ambas: la localidad donde vive **y** quién lo derivó (otro médico o institución). **Contradice la hipótesis** (solo localidad): se agrega el campo "derivado por" mediante [`CR-001`](../../00_Gobernanza/control_cambios.md#cr-001). (Ronda 3, 2026-09-26)
**Estado:** VALIDADA (con CR-001)

---

### Q-PAC-065

**Categoría:** Datos · **Criticidad:** BAJA

**Pregunta:** De la cobertura, ¿hace falta registrar la fecha de vencimiento de la credencial y
el parentesco con el titular?

**Motivo:** `Q-PAC-019` no los marcó, y en `datos.md` quedaron como `PENDIENTE_DEFINICION`.

**Impacta en:** `datos.md`, RF-PAC-007

**Hipótesis de trabajo:** los dos datos existen como **opcionales**.

**Respuesta:** Sí, como opcionales. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-066

**Categoría:** Datos · **Criticidad:** BAJA

**Pregunta:** Del domicilio, además de la localidad, ¿qué datos se cargan: calle, número,
piso/departamento, código postal?

**Motivo:** Solo se confirmó que la localidad debe permitir filtrar (`Q-PAC-044`).

**Impacta en:** `datos.md`

**Hipótesis de trabajo:** calle y número obligatorios; piso/departamento y código postal
opcionales; localidad y provincia elegidas de un listado.

**Respuesta:** Sí. Calle y número obligatorios; piso/departamento y código postal opcionales; localidad y provincia de un listado. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-067

**Categoría:** Datos / Comunicación · **Criticidad:** BAJA

**Pregunta:** Como canal de contacto preferido del paciente, ¿el email es una opción válida?

**Motivo:** `Q-PAC-047` listó llamada/WhatsApp/email, pero la Ronda 2 definió que los avisos a
pacientes van por WhatsApp, llamado y SMS, **no email** (`Q-NOT-001`).

**Impacta en:** `datos.md`, RF-PAC-009, MOD-014

**Hipótesis de trabajo:** canal preferido entre WhatsApp, llamada o SMS. El email se guarda solo
como dato de contacto.

**Respuesta:** Sí. Canal preferido entre WhatsApp, llamada o SMS; el email se guarda solo como dato. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-068

**Categoría:** Reglas de negocio / Alcance · **Criticidad:** MEDIA

**Pregunta:** Cuando alguien pide un turno por la web o por WhatsApp, ¿qué pasa con su ficha? Si
es un paciente nuevo, el formulario solo pide nombre, DNI, teléfono, obra social y motivo
(`Q-PUB-001`), pero el alta de un paciente siempre se hace con la ficha completa (`Q-PAC-012`).
Si ya es paciente y escribe un dato distinto (por ejemplo, otro teléfono), ¿se actualiza la
ficha?

**Motivo:** Es la pregunta que había quedado diferida hasta cerrar `MOD-001` (duplicados en
turno público), y además hay una tensión entre dos respuestas.

**Impacta en:** RF-PAC-001, RF-PAC-003, MOD-033, MOD-011

**Hipótesis de trabajo:** la solicitud web **no crea ni modifica fichas**. Si el DNI ya existe,
el turno se vincula a esa ficha y recepción revisa las diferencias. Si no existe, el turno queda
con datos provisorios y la ficha completa se da de alta en recepción cuando el paciente llega.

**Respuesta:** Sí, así. La solicitud web no crea ni modifica fichas. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

### Q-PAC-069

**Categoría:** Permisos · **Criticidad:** BAJA

**Pregunta:** Los documentos adjuntos (DNI escaneado, carnet, consentimientos), ¿los puede ver
todo el personal, como el resto de la ficha?

**Motivo:** `datos.md` los dejó como `PENDIENTE_DEFINICION`.

**Impacta en:** `datos.md`, RF-PAC-010

**Hipótesis de trabajo:** sí, igual que el resto de la ficha (`Q-PAC-038`), con auditoría de
cada descarga.

**Respuesta:** Sí, todo el personal. Confirma la hipótesis. (Ronda 3, 2026-09-26)
**Estado:** VALIDADA

---

## Índice de preguntas por criticidad ALTA (bloquean `LISTO_PARA_VALIDACION`)

Q-PAC-001, Q-PAC-002, Q-PAC-004, Q-PAC-006, Q-PAC-008, Q-PAC-011, Q-PAC-013, Q-PAC-016,
Q-PAC-018, Q-PAC-019, Q-PAC-022, Q-PAC-030, Q-PAC-031, Q-PAC-036, Q-PAC-038, Q-PAC-040,
Q-PAC-045 — 17 preguntas ALTA (el resto son MEDIA o BAJA; total 53 preguntas numeradas de
Q-PAC-001 a Q-PAC-053, con dos secciones de referencia cruzada sin numeración propia).

**Las 17 quedaron `VALIDADA`** el 2026-09-08. El contenido clínico de los médicos llegó
(`INV-004`, respondido por Portillo Rivero y Peña), y la fusión de duplicados tiene ahora sus
propias preguntas (`Q-PAC-054` a `Q-PAC-056`). Las 16 preguntas nuevas de la sección 24
(`Q-PAC-054` a `Q-PAC-069`) son MEDIA o BAJA y tienen hipótesis de trabajo documentada, como
permite la Definition of Ready. El módulo pasó a **`LISTO_PARA_VALIDACION` y fue `APROBADO` el 2026-09-24**
(ver [`README.md`](README.md)). Las 16 de la sección 24 quedaron `VALIDADA` el 2026-09-26
(Ronda 3); `Q-PAC-064` generó `CR-001`.

Ver el detalle de decisiones que se toman a medida que estas preguntas se responden en
[`decisiones.md`](decisiones.md), y la propagación obligatoria a todos los documentos listados
en `Impacta en:` según
[`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md).
