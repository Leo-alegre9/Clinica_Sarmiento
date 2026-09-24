# Cuestionario para el cliente — Ronda 3

**Estado: ARMADO el 2026-09-24, pendiente de envío.** Versión interactiva: https://claude.ai/artifact/Brjz6CJvDBumjYfFqVNVx6
(las respuestas se guardan en su base de datos, documento `respuestas/ronda-3-cliente`). 29 preguntas en 4 bloques, más una lista
de documentos a pedir (bloque 5).

Esta ronda junta, en un solo envío, todo lo que falta relevar hoy:

1. **Cierre de Pacientes (`MOD-001`)**: el módulo ya está aprobado con estas propuestas; las
   preguntas confirman **lo que proponemos**, para que baste con marcar "sí"
   o corregirlo.
2. **Temas diferidos hasta cerrar `MOD-001`**: los que la
   [Ronda 2](cuestionario_cliente_ronda_2.md#preguntas-diferidas-a-después-de-mod-001) dejó
   para después, sobre obra social y duplicados. La visibilidad por rol quedó cubierta en el
   bloque 3.
3. **Diferencias entre los médicos**: puntos donde Cecilia Portillo Rivero y Eduardo Peña
   respondieron distinto el cuestionario de médicos (ver
   [`cuestionario_medicos_ronda_1.md`](cuestionario_medicos_ronda_1.md#respuestas-de-eduardo-peña)).
   Según la regla del proyecto, no las decide el equipo: las resuelve la clínica.
4. **Otros pendientes**: investigaciones abiertas (`INV-003`, `INV-005`) y quién aprueba.
5. **Documentos que necesitamos**: lista de
   [`documentos_pendientes.md`](documentos_pendientes.md).

## Criterio de armado

Es el mismo de la Ronda 2: solo preguntas de negocio, en lenguaje simple, sin términos técnicos.
Cada pregunta conserva su ID (`Q-XXX-###`) para volcar la respuesta al documento de origen. Toda
lista de opciones termina en "Otro", que habilita un texto libre.

**Cómo se usan las respuestas:** si confirman una propuesta del bloque 1, la hipótesis pasa a
`CONFIRMADO` en los documentos de `MOD-001`. Si la corrigen, se registra un Change Request
(`CR-###`) sobre el módulo aprobado.

## Antes de empezar

- Nombre de quien responde: ____________
- Rol en la clínica: ____________
- Para el bloque 3 conviene responder junto con los dos médicos que completaron el cuestionario
  anterior, o con quien la clínica designe para decidir temas clínicos.

---

## Bloque 1 — Pacientes: confirmación de propuestas (`MOD-001`)

### Fichas duplicadas

**Q-PAC-054** (Media) — A veces un mismo paciente termina con dos fichas (por ejemplo, un bebé
cargado sin DNI y después vuelto a cargar con DNI). Proponemos que **solo Dirección/administración**
pueda unificarlas: se elige cuál ficha queda, todo lo de la otra (consultas, turnos, pagos,
obras sociales, documentos) pasa a la que queda, y la otra no se borra: queda marcada como
"unificada". ¿Está bien así?
Opciones: Sí, así / Sí, pero también debería poder hacerlo recepción / Sí, pero también debería
poder hacerlo un médico / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-055** (Media) — Si las dos fichas tienen datos distintos, proponemos que **las alergias
y antecedentes se sumen siempre** (nunca se descarta ninguno) y que el resto de los datos
(teléfono, domicilio, etc.) los elija quien unifica. ¿Está bien así?
Opciones: Sí, así / No, un médico debería revisar las alergias antes de unificar / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-056** (Baja) — Si se unifican dos fichas por error, ¿hace falta un botón para deshacerlo,
o alcanza con corregirlo a mano (el sistema guarda qué se movió)?
Opciones: Alcanza con corregirlo a mano / Hace falta poder deshacerlo / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-057** (Media) — En la Ronda 1 nos dijeron que **no puede haber dos pacientes con el
mismo DNI**, y también que ante un posible duplicado el sistema **avise pero deje continuar**.
Para que las dos cosas se cumplan, proponemos: si el DNI es **exactamente el mismo**, el sistema
no deja crear otra ficha y ofrece abrir la que ya existe; si solo coinciden nombre y fecha de
nacimiento (o el número de afiliado), avisa y deja continuar. ¿Está bien así?
Opciones: Sí, así / No, con el mismo DNI también debe dejar continuar / Otro.
**Respuesta:** —
**Estado:** ABIERTA

### Corrección de antecedentes clínicos

**Q-PAC-058** (Media) — Nos pidieron un plazo de "12 o 24 horas" para corregir libremente un
antecedente (por ejemplo, una alergia) después de cargarlo. Proponemos **24 horas**, con la
posibilidad de que Dirección lo cambie más adelante sin tocar el sistema. ¿Está bien así?
Opciones: 24 horas / 12 horas / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-059** (Media) — También nos pidieron que un perfil directivo ("el mío y el de Nadia")
pueda corregir cualquier cosa, y en otra respuesta, que sea **sin límite de tiempo**. Proponemos:
el médico corrige dentro del plazo de la pregunta anterior; los perfiles directivos corrigen **en
cualquier momento**; y quiénes tienen ese perfil lo decide Dirección desde el sistema (no queda
fijo a dos personas). ¿Está bien así?
Opciones: Sí, así / Los directivos también deberían tener el mismo plazo que el médico / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-060** (Media) — Recepción puede cargar alergias y antecedentes "con supervisión
posterior". Proponemos: recepción puede **agregar** antecedentes; se ven enseguida en la ficha,
marcados "pendiente de revisión médica", hasta que un médico los confirma. **Modificar o borrar**
uno ya cargado solo pueden hacerlo el médico (dentro del plazo) o un perfil directivo. ¿Está
bien así?
Opciones: Sí, así / Recepción también debería poder modificar o borrar / Lo que carga recepción
no necesita revisión médica / Otro.
**Respuesta:** —
**Estado:** ABIERTA

### Baja y fallecimiento

**Q-PAC-061** (Baja) — Nos dijeron que un médico designado también puede dar de baja a un
paciente. Proponemos que Dirección le asigne ese permiso a los médicos que decida. ¿Está bien
así, o ya saben qué médicos y en qué casos?
Opciones: Sí, Dirección lo asigna / Ya sabemos cuáles (indicar en "Otro") / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-062** (Media) — Si se da de baja a un paciente que tiene turnos futuros, proponemos lo
mismo que para el fallecimiento: el sistema **avisa y muestra esos turnos**, pero no los cancela
solo. Además, mientras esté dado de baja **no se le pueden dar turnos nuevos**, hasta que se lo
reactive. ¿Está bien así?
Opciones: Sí, así / Sí, pero que igual se le puedan dar turnos nuevos / Los turnos futuros se
deberían cancelar solos / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-063** (Baja) — Si se marca a un paciente como fallecido por error, proponemos que solo
administración pueda revertirlo, indicando el motivo. ¿Está bien así?
Opciones: Sí / No debería poder revertirse / Otro.
**Respuesta:** —
**Estado:** ABIERTA

### Datos de la ficha

**Q-PAC-064** (Media) — Los médicos pidieron ver la **"procedencia"** del paciente al abrir la
ficha. ¿A qué se refiere?
Opciones: La localidad donde vive / Quién lo derivó (otro médico o institución) / Ambas / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-065** (Baja) — De la obra social del paciente, ¿quieren poder anotar también la fecha de
vencimiento de la credencial y el parentesco con el titular? Proponemos dejarlos como datos
opcionales.
Opciones: Sí, como opcionales / Sí, como obligatorios / No hacen falta / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-066** (Baja) — Del domicilio, proponemos: calle y número obligatorios; piso/departamento
y código postal opcionales; localidad y provincia elegidas de una lista. ¿Está bien así?
Opciones: Sí / Alcanza con localidad y una dirección escrita libre / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-067** (Baja) — Como "medio de contacto preferido" del paciente, proponemos ofrecer
WhatsApp, llamada o SMS, que son los medios que eligieron para los avisos. El email se guarda
solo como dato. ¿Está bien así?
Opciones: Sí / El email también debe poder elegirse como preferido / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-PAC-069** (Baja) — Los documentos adjuntos a la ficha (DNI escaneado, carnet,
consentimientos), ¿los puede ver todo el personal, como el resto de la ficha?
Opciones: Sí, todo el personal / Solo algunos (indicar quiénes en "Otro") / Otro.
**Respuesta:** —
**Estado:** ABIERTA

---

## Bloque 2 — Temas diferidos hasta cerrar Pacientes

**Q-PAC-068** (Media) — Cuando alguien pide un turno por la web o por WhatsApp, el formulario
pide pocos datos (nombre, DNI, teléfono, obra social, motivo), pero el alta de un paciente se
hace siempre con la ficha completa. Proponemos: el pedido web **no crea ni cambia fichas**. Si el
DNI ya existe, el turno se asocia a ese paciente y recepción revisa si algún dato cambió; si no
existe, el turno queda con esos datos y la ficha completa se hace en recepción cuando el
paciente llega. ¿Está bien así?
Opciones: Sí, así / Si el DNI no existe, el pedido web debería crear la ficha igual / Si el
paciente escribe otro teléfono, debería actualizarse solo / Otro.
Alimenta: `MOD-001`, `MOD-010`, `MOD-011`, `MOD-033`.
**Respuesta:** —
**Estado:** ABIERTA

**Q-OSO-004** (Media) — Si un paciente tiene más de una obra social, ¿con cuál se registra cada
atención?
Opciones: Siempre con la principal / Recepción elige en cada atención (la principal viene
marcada) / Depende de la práctica / Otro.
Alimenta: `MOD-019`, `MOD-020`, `MOD-023`.
**Respuesta:** —
**Estado:** ABIERTA

**Q-OSO-005** (Alta para `MOD-019`, no para `MOD-001`) — Con las obras sociales, ¿el sistema
tiene que ayudarlos a **armar la presentación o liquidación** que se manda a cada obra social
(qué se atendió, a quién y cuánto se cobra), o alcanza con registrar qué obra social tiene cada
paciente y qué se le hizo?
Opciones: Tiene que armar la presentación/liquidación / Alcanza con registrar / Todavía no lo
sabemos / Otro.
Alimenta: `MOD-019`, `MOD-020`, `MOD-021`; resuelve `DECP-005` e `INV-007`.
**Respuesta:** —
**Estado:** ABIERTA

---

## Bloque 3 — Diferencias entre los médicos

Cecilia Portillo Rivero y Eduardo Peña respondieron distinto en los puntos siguientes. En varios,
la diferencia puede deberse a que atienden especialidades distintas, por eso la primera pregunta.

**Q-MED-005** (Alta para este bloque) — ¿Qué especialidad atiende cada uno? Y Eduardo Peña, ¿es
el mismo Eduardo que figura como administrador con acceso a caja?
Respuesta abierta: especialidad de Cecilia Portillo Rivero, especialidad de Eduardo Peña, y si
Eduardo también es administrador.
**Respuesta:** —
**Estado:** ABIERTA

**Q-HCL-008** (Media) — Al ver las consultas anteriores de un paciente, Cecilia prefiere **un
resumen con opción de ver el detalle** y Eduardo prefiere **el historial completo siempre a la
vista**. ¿Cómo lo resolvemos?
Opciones: Resumen con opción de ver el detalle / Historial completo siempre visible / Que cada
médico elija cómo verlo / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-HCL-009** (Alta para `MOD-002`) — Sobre lo que registran otras especialidades, Cecilia
respondió que depende del caso y Eduardo que todo debería ser visible para cualquier profesional
que atienda al paciente. Además, en la Ronda 1 ustedes decidieron que **todo el personal ve toda
la ficha**. ¿Cuál es la regla?
Opciones: Todo visible para todos los profesionales (como la ficha) / Cada especialidad ve lo
suyo, y el médico comparte lo que haga falta / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-HCL-010** (Baja) — Ustedes y Cecilia pidieron que alergias, cirugías previas y enfermedades
crónicas estén siempre visibles en la ficha, con un aviso destacado. Eduardo respondió
"Ninguna". Proponemos mantener el aviso (a quien no lo necesite no le molesta). ¿Confirman?
Opciones: Sí, se mantiene / No hace falta / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-CON-005** (Media) — Cecilia dice que la consulta **cambia según la especialidad** y que en
oftalmología se registran agudeza visual, presión intraocular y opcionalmente ARM. Eduardo dice
que hay **un formato común** y que no necesita mediciones específicas. ¿Cómo lo resolvemos?
Opciones: Formato común para todos, con las mediciones de oftalmología como opcionales / Un
formato por especialidad / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-DIA-004** (Media) — Sobre el diagnóstico: Cecilia lo registra con **código y texto libre**, y
necesita marcar si es **presuntivo o confirmado**; Eduardo usa **solo texto libre** y no
distingue presuntivo. Proponemos que el código y la marca de "presuntivo" existan pero sean
**opcionales**. ¿Está bien así?
Opciones: Sí, opcionales / El código debe ser obligatorio / Solo texto libre, sin código ni
presuntivo / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-RET-006** (Media) — En una receta de medicamentos, Cecilia marcó como indispensables también
**dosis, frecuencia y duración del tratamiento**; Eduardo no. ¿Son obligatorios? Y la opción de
**repetir una receta anterior** (Cecilia la pidió, Eduardo dijo que no la necesita), ¿la
incluimos como algo opcional?
Opciones: Dosis, frecuencia y duración obligatorias, y repetir receta opcional / Dosis,
frecuencia y duración opcionales, y repetir receta opcional / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-FOR-007** (Alta para `MOD-006`) — Para calcular las fórmulas, Cecilia usa **Treelan** y
Eduardo respondió **Ampina**. En la Ronda 2 ustedes habían respondido que no usaban ninguno.
¿Qué usa cada médico hoy? ¿Y pueden darnos acceso o un ejemplo de cada uno?
Opciones: Cada uno usa uno distinto (aclarar cuál) / Todos usan los dos / Otro.
Resuelve `INV-002` e `INV-003`.
**Respuesta:** —
**Estado:** ABIERTA

**Q-FOR-008** (Baja) — Ante la pregunta sobre qué funciona mal de esos sistemas, Eduardo
respondió "La base de datos. Lente respuesta del proveedor". ¿Qué quiso decir?
Respuesta abierta.
**Respuesta:** —
**Estado:** ABIERTA

---

## Bloque 4 — Otros pendientes

**Q-PRY-001** (Alta para aprobar módulos) — ¿Quién aprueba formalmente cada parte del sistema
antes de que la construyamos? Pacientes ya la aprobó el responsable del proyecto; falta definirlo para las siguientes.
Opciones: Quien respondió estos cuestionarios / Dirección (indicar quién) / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-DEP-003** (Media) — ¿Quién se ocupa hoy de las computadoras y la conexión a internet de la
clínica? (Retoma `Q-DEP-002`, que quedó en "no estoy seguro/a".)
Opciones: Un técnico propio / Un técnico o empresa externa / Nadie en particular / Otro.
Alimenta: `INV-005`, `INV-006`, `ADR-001`.
**Respuesta:** —
**Estado:** ABIERTA

---

## Bloque 5 — Documentos que necesitamos

No son preguntas: es la lista de lo que falta recibir. Tildar lo que se envía.

- [ ] Acceso o ejemplos (capturas de un caso real) de **Treelan** y de **Ampina** — `MOD-006`
      (`INV-002`, `INV-003`).
- [ ] **Datos de cada médico**: matrícula, teléfono o email, y días y horarios aproximados.
      Incluir a Cecilia Portillo Rivero y Eduardo Peña, que no estaban en el listado recibido
      (Arkwright, Coppini, Rivera del Toro) — `MOD-015`.
- [ ] **Convenios y planes** que maneja la clínica con cada obra social — `MOD-019` a `MOD-021`.
- [ ] **Ejemplos de recetas** actuales (medicamentos y anteojos) — `MOD-005`.
- [ ] **Formularios actuales** de alta de paciente y de pedido de turno (papel o digital) —
      `MOD-001`, `MOD-033`.
- [ ] Cómo se maneja hoy **una cirugía**: agenda, checklist, consentimientos — `MOD-013`.
- [ ] Cómo se maneja hoy **la caja** — `MOD-022` a `MOD-024`.
- [ ] **Circuitos administrativos** actuales (quién hace qué, desde que llega el paciente hasta
      que se va) — varios módulos.
- [ ] **Planillas o sistema actual**, incluida una exportación de los pacientes a migrar —
      `MOD-040`.

---

## Resumen por criticidad

| Criticidad | Preguntas |
|---|---|
| Alta (para otros módulos o para aprobar; **ninguna bloquea `MOD-001`**) | Q-OSO-005, Q-MED-005, Q-HCL-009, Q-FOR-007, Q-PRY-001 |
| Media | Q-PAC-054, Q-PAC-055, Q-PAC-057, Q-PAC-058, Q-PAC-059, Q-PAC-060, Q-PAC-062, Q-PAC-064, Q-PAC-068, Q-OSO-004, Q-HCL-008, Q-CON-005, Q-DIA-004, Q-RET-006, Q-DEP-003 |
| Baja | Q-PAC-056, Q-PAC-061, Q-PAC-063, Q-PAC-065, Q-PAC-066, Q-PAC-067, Q-PAC-069, Q-HCL-010, Q-FOR-008 |

Q-PRY-001 no tiene módulo: es una pregunta transversal de gobierno del proyecto.
