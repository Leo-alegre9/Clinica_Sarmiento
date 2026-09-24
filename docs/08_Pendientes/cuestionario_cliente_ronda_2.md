# Cuestionario para el cliente — Ronda 2 (todos los módulos que ya se pueden preguntar)

Este documento reúne, para enviarse **una sola vez** al cliente, las preguntas de todos los
módulos que **no dependen de las respuestas todavía pendientes de `MOD-001 — Pacientes`** (ver
[`../03_Modulos/MOD-001_Pacientes/preguntas_cliente.md`](../03_Modulos/MOD-001_Pacientes/preguntas_cliente.md),
que sigue siendo la Ronda 1 y continúa sin respuesta completa).

**Estado: RESPONDIDA el 2026-09-08.** El cliente contestó las 89 preguntas de esta ronda. Cada
pregunta abajo incluye su `**Respuesta:**` y `**Estado:** RESPONDIDA`. Ver
[`decisiones_pendientes.md`](decisiones_pendientes.md) para las `DECP-###` que estas respuestas
resuelven o informan, y [`investigaciones.md`](investigaciones.md) para las `INV-###` afectadas.
La propagación formal a `requerimientos.md` / `reglas_negocio.md` / `decisiones.md` de cada
módulo ocurre recién cuando a ese módulo le toque su refinamiento profundo (ver
[`../03_Modulos/README.md`](../03_Modulos/README.md)); mientras tanto, este documento es la
fuente de verdad de lo respondido.

## Criterio de armado

- **Solo preguntas de negocio.** Nada de términos técnicos, nombres de tablas ni opciones de
  arquitectura. Si una decisión es puramente de implementación (equivalente a lo que en
  `MOD-001` se clasificó como pregunta 🔧 interna), no está acá.
- **Solo lo necesario para construir**, no un relevamiento exhaustivo por módulo. Los módulos
  grandes tendrán una ronda 2 más profunda (equivalente al detalle que sí tuvo `MOD-001`)
  recién cuando les toque su refinamiento completo, uno por vez, según
  [`../03_Modulos/README.md`](../03_Modulos/README.md). Esto es un primer relevamiento
  estructural para no bloquear el diseño de datos ni hacerle al cliente múltiples rondas
  separadas.
- **Sin duplicar entre módulos.** Cuando varios módulos comparten la misma pregunta de fondo
  (por ejemplo, canal de recordatorios), se pregunta una sola vez y se aclara a qué módulos
  alimenta.
- **Escalable.** Cada pregunta conserva el prefijo del módulo al que pertenece
  (`Q-XXX-###`, ver [`../00_Gobernanza/convenciones.md`](../00_Gobernanza/convenciones.md)) para
  poder propagarse después a `decisiones.md` de cada módulo exactamente igual que en `MOD-001`.
  Rondas futuras (`ronda_3`, etc.) se agregan como archivos nuevos, sin reabrir este.

## Qué NO está en esta ronda (y por qué)

| Excluido | Motivo |
|---|---|
| `MOD-001` (Pacientes) | Ronda 1, ya enviada, todavía sin responder completa. Es la base de la que dependen varias preguntas de otros módulos (ver tabla de diferidas más abajo). |
| Contenido **clínico** de `MOD-002, 003, 004, 005, 007, 008` (qué se examina, cómo se redacta una evolución, qué campos clínicos lleva una consulta) | Por pedido explícito del cliente (`RC-006`), esto se releva **con los médicos**, no con el cliente/dueño. Ver [`preguntas_medicos.md`](preguntas_medicos.md) e `INV-004`. Esta ronda solo incluye el costado administrativo/legal de esos módulos, que sí puede responder el cliente. |
| `MOD-006` (Fórmulas oftalmológicas) — funcionalidad completa | Bloqueado por `INV-001/002/003` (falta el documento y el acceso a Ampina/Treelan). Esta ronda solo incluye las 3 preguntas necesarias para destrabar esa investigación. |
| `MOD-038` (Logs y monitoreo) | Es enteramente una decisión técnica del equipo de desarrollo (qué y cuánto tiempo loguear a nivel de sistema), no depende de una decisión de negocio del cliente. |

## Preguntas diferidas a después de `MOD-001`

Estas preguntas de otros módulos existen, pero su redacción final depende de cómo se responda
`MOD-001` (identificación de pacientes, obra social principal, visibilidad de datos). Para no
hacerle una pregunta al cliente que quizás haya que reformular en dos semanas, se posponen a una
ronda 3 posterior a `MOD-001`:

| Tema diferido | Depende de | Módulos que alimenta |
|---|---|---|
| Qué pasa si dos personas que sacan turno público parecen ser el mismo paciente | `Q-PAC-001`, `Q-PAC-016` | `MOD-010`, `MOD-011`, `MOD-033` |
| Cómo se guarda la obra social "principal" de un paciente con varias coberturas | `Q-PAC-018`, `Q-PAC-019` | `MOD-019`, `MOD-020`, `MOD-023` |
| Quién ve qué datos clínicos vs. administrativos, en detalle por rol | `Q-PAC-036`, `Q-PAC-038` | `MOD-027`, `MOD-028`, módulos clínicos |

---

## 1. Personal, especialidades y espacios físicos (`MOD-015`, `MOD-016`, `MOD-017`, `MOD-018`)

<a id="mod-015"></a>

### Médicos / Profesionales (`MOD-015`)

**Q-MED-001** (Alta) — Además del nombre, ¿qué datos necesitan tener cargados de cada
profesional para que el sistema funcione?
Opciones (múltiple): Matrícula profesional / Especialidad(es) / Datos para firmar recetas /
Teléfono y email / Horarios habituales / Otro.
**Respuesta:** Matrícula profesional, Especialidad(es), Datos para firmar recetas, Otro: "estaría
bueno que den como un aproximado de la mayoría de días y horarios que está cada profesional".
**Estado:** RESPONDIDA

**Q-MED-002** (Alta) — ¿Un mismo profesional puede tener más de una especialidad?
Opciones: Sí, frecuentemente / Puede pasar, pero es poco común / No, cada profesional tiene una
sola especialidad / Otro.
**Respuesta:** Puede pasar, pero es poco común.
**Estado:** RESPONDIDA

**Q-MED-003** (Media) — ¿Un profesional puede atender en más de un consultorio o, a futuro, en
más de una sede?
Opciones: Sí / No / Depende del profesional / Otro.
**Respuesta:** Depende del profesional.
**Estado:** RESPONDIDA

**Q-MED-004** (Baja) — ¿Necesitan poder marcar a un profesional como "de licencia" temporalmente
(vacaciones, enfermedad) sin borrar su información ni su historial?
Opciones: Sí / No, alcanza con vaciar su agenda manualmente / Otro.
**Respuesta:** No, alcanza con vaciar su agenda manualmente.
**Estado:** RESPONDIDA

<a id="mod-016"></a>

### Especialidades (`MOD-016`)

**Q-ESC-001** (Alta) — ¿Cuáles son las especialidades médicas que ofrece hoy la clínica? (para
cargarlas como listado inicial)
Respuesta abierta (listado).
**Respuesta:** Oftalmología, Diabetología, Pediatría, Endocrinología, Cirugía general, Cirugía
general/especialista en cabeza y cuello, Oncología, Otorrinolaringología, Neurocirujano/especialista
en columna, Neumonología, Cardiología, Traumatología, Medicina clínica. Aclaración del cliente:
este es el listado **a futuro**; lo inmediato/actual es solo Oftalmología y ORL (otorrinos).
**Estado:** RESPONDIDA

**Q-ESC-002** (Media) — ¿Necesitan agrupar especialidades relacionadas (por ejemplo,
"Oftalmología general" y "Oftalmología pediátrica" bajo un mismo grupo "Oftalmología")?
Opciones: Sí / No, cada una es independiente / Otro.
**Respuesta:** No, cada una es independiente.
**Estado:** RESPONDIDA

<a id="mod-017"></a>

### Consultorios (`MOD-017`)

**Q-CTO-001** (Alta) — ¿Cuántos consultorios o salas de atención tienen hoy en uso?
Respuesta abierta (número).
**Respuesta:** 2 para oftalmología, 1 para ORL (total 3 hoy).
**Estado:** RESPONDIDA

**Q-CTO-002** (Media) — ¿Cada consultorio está reservado para un tipo específico de práctica
(por ejemplo, uno solo para procedimientos), o son intercambiables entre profesionales?
Opciones: Específicos por tipo de práctica / Intercambiables / Depende del consultorio / Otro.
**Respuesta:** Intercambiables.
**Estado:** RESPONDIDA

<a id="mod-018"></a>

### Sedes (`MOD-018`)

**Q-SED-001** (Alta) — ¿Cuántas sedes/sucursales tiene la clínica en funcionamiento hoy?
Opciones: Una sola / Más de una / Otro.
**Respuesta:** Más de una. **⚠️ Corrige un supuesto del inventario**: `MOD-018` estaba clasificado
como prioridad "Baja (hoy 1 sede)" asumiendo sede única — ver nota en
[`../03_Modulos/README.md`](../03_Modulos/README.md).
**Estado:** RESPONDIDA

**Q-SED-002** (Media) — ¿Tienen planeado abrir otra sede en los próximos 1-2 años?
Opciones: Sí / No / Todavía no lo sabemos / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

---

## 2. Agenda, turnos y recepción (`MOD-009`, `MOD-010`, `MOD-011`, `MOD-012`)

<a id="mod-009"></a>

### Agenda médica (`MOD-009`)

**Q-AGE-001** (Alta) — ¿Cómo arman hoy la agenda de cada profesional?
Opciones: Horarios fijos semanales (por ejemplo, lunes y miércoles de 9 a 13) / Se cargan
turnos variables semana a semana / Combinación de ambas / Otro.
**Respuesta:** Combinación de ambas.
**Estado:** RESPONDIDA

**Q-AGE-002** (Alta) — ¿Cuánto dura habitualmente un turno de consulta?
Opciones: Una duración fija para todos / Varía según el tipo de consulta o práctica / Lo decide
cada profesional / Otro.
**Respuesta:** Lo decide cada profesional.
**Estado:** RESPONDIDA

**Q-AGE-003** (Media) — ¿Un profesional necesita poder bloquear horarios de su agenda para
tareas que no son atención al público (cirugías, tareas administrativas)?
Opciones: Sí / No es necesario / Otro.
**Respuesta:** Otro: "es ambiguo, sí y no. Debería tener yo como administrador una opción de sacar
[el bloqueo], y dependiendo el médico [él también]". **Aclarado 2026-09-08:** el administrador
puede bloquear/gestionar la agenda de cualquier profesional; adicionalmente, un médico
específico puede hacerlo también en su propia agenda cuando la administración se lo habilite
(a definir más adelante qué médicos y bajo qué criterio, en línea con `Q-PAC-037`).
**Estado:** VALIDADA

**Q-AGE-004** (Media) — ¿Cómo manejan hoy los feriados y días no laborables en la agenda?
Opciones: Se cierran manualmente cada vez que corresponde / Preferiríamos un calendario de
feriados que los bloquee automáticamente / Otro.
**Respuesta:** Se cierran manualmente cada vez que corresponde.
**Estado:** RESPONDIDA

<a id="mod-010"></a>

### Turnos (`MOD-010`)

**Q-TUR-001** (Alta) — ¿Qué pasa hoy cuando un paciente no se presenta a su turno ("ausente")?
Opciones: No pasa nada especial / Queda registrado como antecedente / Se limitan sus próximos
turnos si se repite / Otro.
**Respuesta:** Otro: "estaría bueno que si al finalizar el día ese paciente no tiene una evolución
[cargada], el sistema aclare que faltó a su turno". Es un pedido de funcionalidad (detección
automática de ausentismo por falta de evolución), no una descripción de la práctica actual.
**Estado:** RESPONDIDA

**Q-TUR-002** (Alta) — ¿Con cuánta anticipación mínima se puede cancelar o reprogramar un turno
sin inconvenientes?
Opciones: Sin límite de tiempo / Hasta una cierta cantidad de horas/días antes (indicar cuál) /
Hoy no hay una política definida / Otro.
**Respuesta:** Sin límite de tiempo.
**Estado:** RESPONDIDA

**Q-TUR-003** (Media) — ¿Necesitan una lista de espera para turnos ya completos, por si se
libera un lugar?
Opciones: Sí / No es necesario / Otro.
**Respuesta:** Otro: "para los turnos de Eduardo sería genial: poner una lista de espera y que
cuando el sistema abre agenda para él, avise automáticamente a los pacientes — sería un golazo".
Confirma que sí la necesitan, con aviso automático al liberarse agenda (no solo lista pasiva).
**Estado:** RESPONDIDA

**Q-TUR-004** (Media) — ¿Reciben pacientes sin turno previo ("por orden de llegada") que se
atienden si hay lugar disponible?
Opciones: Sí, habitualmente / Solo en casos de urgencia / No, todo es con turno previo / Otro.
**Respuesta:** Otro: "tengo como directiva que todos los pacientes que van se atienden, no suele
ser muchos pero se atienden, y si son del interior más aún". Es una política de la dirección, no
una excepción ocasional.
**Estado:** RESPONDIDA

<a id="mod-011"></a>

### Recepción / Check-in (`MOD-011`)

**Q-REC-001** (Alta) — Cuando el paciente llega a la clínica, ¿qué hace hoy recepción antes de
que pase con el médico?
Opciones (múltiple): Confirma datos personales / Confirma o cobra la cobertura/obra social /
Entrega un comprobante o número / Avisa al consultorio que el paciente llegó / Otro.
**Respuesta:** Confirma datos personales, Confirma o cobra la cobertura/obra social, Entrega un
comprobante o número, Avisa al consultorio que el paciente llegó (las cuatro).
**Estado:** RESPONDIDA

**Q-REC-002** (Media) — ¿Necesitan imprimir algún comprobante de check-in para el paciente?
Opciones: Sí / No / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

<a id="mod-012"></a>

### Sala de espera / prioridades (`MOD-012`)

**Q-ESP-001** (Alta) — En la sala de espera, ¿en qué orden se llama habitualmente a los
pacientes?
Opciones: Por orden de llegada / Por el horario de turno asignado / El profesional decide a
quién llama / Hay excepciones por urgencia médica sobre el orden normal / Otro.
**Respuesta:** Otro: combinación de "por el horario de turno asignado" y "el profesional decide a
quién llama". Textual: "si yo subo y pido atención rápida para tal paciente el médico lo atiende,
y el médico también decide como quiera atender, pero los turnos que se dan son con horarios".
**Estado:** RESPONDIDA

**Q-ESP-002** (Media) — ¿Existen criterios que hacen "saltar" el orden normal (embarazadas,
adultos mayores, urgencias)? ¿Cuáles?
Opciones: Sí (detallar cuáles) / No / Otro.
**Respuesta:** Sí — embarazadas, niños, pacientes en sillas de ruedas o adultos mayores.
**Estado:** RESPONDIDA

**Q-ESP-003** (Baja) — ¿Necesitan una pantalla o cartel que muestre a qué paciente se está
llamando?
Opciones: Sí / No, alcanza con avisar verbalmente / Otro.
**Respuesta:** Otro: "no es necesario, porque según Eduardo el paciente que va ahí no ve jaja, pero
estaría bueno inclusive que lo llamen [por voz/nombre]". En la práctica: no priorizado, aviso
verbal alcanza.
**Estado:** RESPONDIDA

---

## 3. Cirugías y recordatorios (`MOD-013`, `MOD-014`)

<a id="mod-013"></a>

### Cirugías (`MOD-013`)

**Q-CIR-001** (Alta) — Para programar una cirugía, ¿qué información necesitan registrar además
de la fecha y el paciente?
Opciones (múltiple): Profesional(es) que intervienen / Consultorio o quirófano / Tipo de
cirugía / Consentimiento informado firmado / Indicaciones prequirúrgicas / Otro.
**Respuesta:** Profesional(es) que intervienen, Tipo de cirugía, Consentimiento informado
firmado, Indicaciones prequirúrgicas (no marcó "Consultorio o quirófano").
**Estado:** RESPONDIDA

**Q-CIR-002** (Alta) — ¿Necesitan que quede registrado en el sistema un consentimiento
informado firmado antes de la cirugía?
Opciones: Sí, es obligatorio / Hoy se maneja en papel, aparte del sistema / No aplica / Otro.
**Respuesta:** Hoy se maneja en papel, aparte del sistema.
**Estado:** RESPONDIDA

**Q-CIR-003** (Media) — ¿Una cirugía puede tener más de un profesional o asistente asociado?
Opciones: Sí / No, un solo responsable por cirugía / Otro.
**Respuesta:** No, un solo responsable por cirugía.
**Estado:** RESPONDIDA

**Q-CIR-004** (Media) — Al programar una cirugía, ¿debe bloquearse automáticamente el
consultorio/quirófano y la agenda normal del profesional en ese horario?
Opciones: Sí / No es necesario, se coordina aparte / Otro.
**Respuesta:** No es necesario, se coordina aparte.
**Estado:** RESPONDIDA

<a id="mod-014"></a>

### Recordatorios y confirmaciones (`MOD-014`)

**Q-RCD-001** (Alta) — ¿Con cuánta anticipación debe enviarse un recordatorio de turno o
cirugía?
Opciones: 24 horas antes / 48 horas antes / Más de un recordatorio (por ejemplo, una semana y
un día antes) / Otro.
**Respuesta:** 48 horas antes.
**Estado:** RESPONDIDA

**Q-RCD-002** (Alta) — ¿Necesitan que el paciente pueda confirmar o cancelar el turno
respondiendo directamente al recordatorio?
Opciones: Sí / No, el recordatorio es solo informativo / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

**Q-RCD-003** (Media) — Si el paciente no responde al recordatorio, ¿qué debería pasar?
Opciones: Nada, el turno se mantiene / Se lo vuelve a contactar por otro medio / El turno se
libera automáticamente / Otro.
**Respuesta:** Nada, el turno se mantiene.
**Estado:** RESPONDIDA

*(El canal de envío del recordatorio —WhatsApp, SMS, email, llamado— se pregunta una sola vez
en la sección 4, "Comunicaciones", porque es compartido con otros módulos.)*

---

## 4. Comunicaciones (`MOD-029`, `MOD-030`, `MOD-031`, `MOD-032`)

<a id="mod-029"></a><a id="mod-030"></a><a id="mod-031"></a><a id="mod-032"></a>

Estas cuatro preguntas alimentan en conjunto Notificaciones (`MOD-029`), WhatsApp/mensajería
(`MOD-030`), Email (`MOD-031`) y Plantillas de comunicación (`MOD-032`), además del canal de
Recordatorios (`MOD-014`).

**Q-NOT-001** (Alta) — ¿Por qué medio prefieren que se envíen los recordatorios y avisos a los
pacientes?
Opciones (múltiple): WhatsApp / SMS / Email / Llamado telefónico / Otro.
**Respuesta:** WhatsApp, Llamado telefónico, SMS (no marcó Email).
**Estado:** RESPONDIDA

**Q-NOT-002** (Media) — Además de los recordatorios de turno, ¿qué otros avisos automáticos
necesitan enviar a los pacientes?
Opciones (múltiple): Resultados de estudios disponibles / Cambios de horario del profesional /
Confirmación de una solicitud de turno online / Novedades generales de la clínica / Ninguno
otro por ahora / Otro.
**Respuesta:** Cambios de horario del profesional, Confirmación de una solicitud de turno online.
**Estado:** RESPONDIDA

**Q-WHA-001** (Alta) — ¿La clínica ya tiene un número de WhatsApp Business oficial/verificado
para comunicarse con pacientes?
Opciones: Sí, ya lo tenemos / No, habría que gestionarlo / No estoy seguro/a / Otro.
**Respuesta (aclarada 2026-09-08):** Tienen un número de WhatsApp general de la clínica (no un
número de WhatsApp Business verificado). También aclaran que los administradores usan números
propios para comunicarse con pacientes. **Recomendación técnica:** un número de WhatsApp
"normal" no puede integrarse de forma soportada para enviar mensajes automáticos (recordatorios)
ni para el agendamiento de turnos por WhatsApp que el cliente pidió explícitamente (ver
`sistema nuevo.pdf`, punto 1) — Meta no permite automatizar WhatsApp personal. Para eso hace
falta migrar el número general de la clínica a la **WhatsApp Business Platform (Cloud API)**;
es un cambio de plataforma sobre el mismo número, no necesariamente un número nuevo. Esto es
independiente de que cada administrador siga usando su propio WhatsApp para conversaciones
manuales con pacientes — son dos canales distintos que pueden convivir (uno automatizado desde
el sistema con el número general, otro manual y humano con los números individuales).
**Confirmado 2026-09-08:** el cliente decidió avanzar con la migración del número general de la
clínica a WhatsApp Business Platform (Cloud API).
**Estado:** VALIDADA

**Q-MAI-001** (Media) — ¿Tienen un dominio de email propio de la clínica (por ejemplo,
`@clinicasarmiento.com`) desde el cual enviar correos, o usan un correo genérico?
Opciones: Sí, tenemos dominio propio / No, usamos un correo genérico (Gmail u otro) / Otro.
**Respuesta:** No, usamos un correo genérico (Gmail u otro).
**Estado:** RESPONDIDA

**Q-PLT-001** (Baja) — Para los mensajes que reciben los pacientes, ¿necesitan poder editar
ustedes mismos el texto más adelante, o alcanza con un texto acordado una vez con el equipo de
desarrollo?
Opciones: Necesitamos poder editarlo nosotros mismos / Alcanza con un texto fijo acordado una
vez / Otro.
**Respuesta:** Necesitamos poder editarlo nosotros mismos.
**Estado:** RESPONDIDA

---

## 5. Portal público de turnos (`MOD-033`, `MOD-034`, `MOD-035`)

<a id="mod-033"></a><a id="mod-034"></a><a id="mod-035"></a>

**Q-PUB-001** (Alta) — ¿Qué datos mínimos debería pedir el formulario público para solicitar un
turno?
Opciones (múltiple): Nombre y apellido / DNI / Teléfono / Email / Obra social / Especialidad o
motivo de consulta / Otro.
**Respuesta:** Nombre y apellido, DNI, Teléfono, Obra social, Especialidad o motivo de consulta
(no marcó Email).
**Estado:** RESPONDIDA

**Q-PUB-002** (Alta) — Cuando alguien pide un turno desde la web, ¿queda confirmado
automáticamente (si hay lugar disponible) o siempre necesita que alguien de recepción lo revise
y confirme antes?
Opciones: Se confirma automáticamente si hay lugar / Siempre requiere confirmación manual de
recepción / Depende del profesional o la especialidad / Otro.
**Respuesta:** Se confirma automáticamente si hay lugar. **Resuelve `DECP-001`** (alternativa A:
reserva automática) — ver [`decisiones_pendientes.md`](decisiones_pendientes.md).
**Estado:** RESPONDIDA

**Q-DIS-001** (Alta) — ¿Todos los profesionales y especialidades deberían mostrar sus horarios
disponibles públicamente en la web, o solo algunos?
Opciones: Todos / Solo algunos (indicar cuáles, si ya lo saben) / Ninguno por ahora, se decide
más adelante / Otro.
**Respuesta:** Ninguno por ahora, se decide más adelante.
**Estado:** RESPONDIDA

**Q-DIS-002** (Media) — ¿Con cuánta anticipación hacia adelante debería mostrarse la
disponibilidad en el portal público?
Opciones: Una semana / Dos semanas / Un mes / Otro.
**Respuesta:** Una semana.
**Estado:** RESPONDIDA

**Q-SOL-001** (Media) — Si una solicitud de turno público queda pendiente de confirmación,
¿en cuánto tiempo esperan que recepción la revise?
Opciones: El mismo día / Dentro de 24-48 horas / Hoy no hay un plazo definido / Otro.
**Respuesta:** Hoy no hay un plazo definido.
**Estado:** RESPONDIDA

**Q-SOL-002** (Baja) — ¿El paciente debería poder consultar el estado de su solicitud
(pendiente/confirmada/rechazada) por sí mismo, o se entera solo cuando lo contactan?
Opciones: Sí, debería poder consultarlo / No es necesario, alcanza con que lo contacten / Otro.
**Respuesta:** Sí, debería poder consultarlo.
**Estado:** RESPONDIDA

---

## 6. Obras sociales y coberturas (`MOD-019`, `MOD-020`, `MOD-021`)

<a id="mod-019"></a><a id="mod-020"></a><a id="mod-021"></a>

*(Ver también `INV-007`. Lo que depende de cómo se guarda la obra social del paciente queda
diferido, ver tabla al inicio del documento.)*

**Q-OSO-001** (Alta) — ¿Con qué obras sociales y prepagas trabaja hoy la clínica?
Respuesta abierta (listado).
**Respuesta:** IASEP, Medicus, AMP, PAMI, Salud Integral, Prevención Salud, OSDE, TV Salud,
Sancor Salud, OSFATUN, OSPEDYC, OPSTACA, OSPECON, OSPRERA, Avalian, Galeno, OSCAC, SPF, OSUTHGRA,
Swiss Medical, SADAIC, OMINT S.A., OSPAGA, Visitar Salud, Poder Judicial (25 obras
sociales/prepagas).
**Estado:** RESPONDIDA

**Q-OSO-002** (Alta) — ¿Necesitan validar la cobertura antes de la consulta (por ejemplo, con un
portal de la obra social o un llamado), o alcanza con la credencial que presenta el paciente?
Opciones: Se valida antes por algún medio / Alcanza con la credencial presentada / Depende de
la obra social / Otro.
**Respuesta:** Depende de la obra social.
**Estado:** RESPONDIDA

**Q-OSO-003** (Media) — ¿El paciente paga habitualmente algo de su bolsillo además de lo que
cubre la obra social (copago/coseguro)?
Opciones: Sí, según la obra social y la práctica / No, la obra social cubre todo / Otro.
**Respuesta:** Sí, según la obra social y la práctica.
**Estado:** RESPONDIDA

**Q-PLA-001** (Media) — Dentro de una misma obra social, ¿existen distintos planes o categorías
que cambian lo que cubren?
Opciones: Sí / No / Depende de la obra social / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

**Q-AUT-001** (Alta) — ¿Hay prácticas o estudios que necesitan autorización previa de la obra
social antes de realizarse?
Opciones: Sí, para ciertas prácticas (indicar cuáles si ya lo saben) / No manejamos
autorizaciones previas / No estoy seguro/a / Otro.
**Respuesta:** Sí, para ciertas prácticas. **Aclarado 2026-09-08:** se difiere el detalle de
cuáles son esas prácticas hasta que `MOD-021` (Autorizaciones) entre en refinamiento profundo —
no es necesario especificarlas ahora, no bloquea el avance actual.
**Estado:** RESPONDIDA — detalle diferido a `MOD-021`, no bloqueante.

**Q-AUT-002** (Media) — Cuando se necesita esa autorización previa, ¿quién la gestiona hoy?
Opciones: La clínica / El propio paciente / Depende del caso / Otro.
**Respuesta:** La clínica.
**Estado:** RESPONDIDA

---

## 7. Administración financiera (`MOD-022`, `MOD-023`, `MOD-024`, `MOD-025`, `MOD-041`)

<a id="mod-022"></a><a id="mod-023"></a><a id="mod-024"></a><a id="mod-025"></a><a id="mod-041"></a>

**Q-CAJ-001** (Alta) — ¿Cómo manejan hoy la caja: una única por día, una por persona/turno de
trabajo, o una por sede?
Opciones: Única por día / Una por persona o turno de trabajo / Una por sede / Otro.
**Respuesta (aclarada 2026-09-08):** Por sede, contabilizada por día. La clínica ya opera más de
una sede (`Q-SED-001`), pero el sistema se pondrá en marcha dado de alta con una sola sede; el
registro de caja arranca desde que esa sede empieza a operar en el sistema, y la segunda sede se
incorpora más adelante con el mismo esquema.
**Estado:** VALIDADA

**Q-CAJ-002** (Alta) — ¿Necesitan un cierre de caja diario que compare lo que debería haber
contra lo efectivamente contado (arqueo)?
Opciones: Sí / No es necesario / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

**Q-PAG-001** (Alta) — ¿Qué medios de pago aceptan hoy?
Opciones (múltiple): Efectivo / Tarjeta de débito o crédito / Transferencia bancaria / Mercado
Pago u otra billetera virtual / Otro.
**Respuesta:** Efectivo, Tarjeta de débito o crédito, Transferencia bancaria, Mercado Pago u otra
billetera virtual (los cuatro).
**Estado:** RESPONDIDA

**Q-PAG-002** (Media) — ¿Aceptan pagos parciales o en cuotas para un mismo servicio?
Opciones: Sí / No, se paga completo / Otro.
**Respuesta:** Otro: "sí, pero es más un arreglo de la gerencia con el paciente" (no es una
política sistematizada, es caso a caso por decisión de gerencia).
**Estado:** RESPONDIDA

**Q-PAG-003** (Alta) — ¿Necesitan emitir la factura electrónica (AFIP) directamente desde este
sistema, o eso se maneja aparte con un sistema contable?
Opciones: Necesitamos emitirla desde el sistema / Se maneja aparte, con otro sistema / No
emitimos factura hoy / Otro.
**Respuesta:** Se maneja aparte, con otro sistema.
**Estado:** RESPONDIDA

**Q-GAS-001** (Media) — ¿Necesitan registrar en este sistema los gastos de la clínica (insumos,
servicios, sueldos), o eso ya lo llevan en otro lado?
Opciones: Sí, queremos registrarlos acá / No, se maneja aparte / Otro.
**Respuesta:** No, se maneja aparte.
**Estado:** RESPONDIDA

**Q-RAD-001** (Media) — De los reportes administrativos, ¿cuáles consultan con más frecuencia
hoy o les gustaría tener?
Opciones (múltiple): Ingresos por día/período / Ingresos por profesional / Ingresos por obra
social / Turnos atendidos vs. ausentes / Otro.
**Respuesta:** Ingresos por día/período, Ingresos por obra social, Turnos atendidos vs. ausentes
(no marcó "Ingresos por profesional").
**Estado:** RESPONDIDA

---

## 8. Usuarios, roles y auditoría (`MOD-026`, `MOD-027`, `MOD-028`)

<a id="mod-026"></a><a id="mod-027"></a><a id="mod-028"></a>

*(La parte fina de "quién ve exactamente qué dato clínico" queda diferida a después de
`MOD-001`, ver tabla al inicio. Acá solo se pregunta la estructura general de usuarios y
roles.)*

**Q-USR-001** (Alta) — ¿Qué tipos de usuarios del sistema tienen hoy, según su función (más
allá de "médico" y "recepción")?
Opciones (múltiple): Recepción/administrativo / Médico o profesional / Dirección/administración
/ Caja / Otro.
**Respuesta:** Recepción/administrativo, Médico o profesional, Dirección/administración (no
marcó "Caja" como tipo de usuario separado).
**Estado:** RESPONDIDA

**Q-USR-002** (Alta) — ¿Cada persona tiene (o debería tener) su propio usuario y contraseña, o
hoy se comparte un usuario por puesto de trabajo (por ejemplo, "recepción")?
Opciones: Cada persona con su propio usuario / Se comparte por puesto de trabajo / Otro.
**Respuesta:** Cada persona con su propio usuario.
**Estado:** RESPONDIDA

**Q-ROL-001** (Media) — ¿Quién debería poder crear o dar de baja usuarios del sistema?
Opciones: Solo una persona administradora general / Cualquier directivo / Otro.
**Respuesta:** Cualquier directivo.
**Estado:** RESPONDIDA

**Q-AUD-001** (Media) — Ante un problema o reclamo, ¿qué tipo de acciones necesitan poder
rastrear ("quién hizo qué y cuándo")?
Opciones (múltiple): Cambios en datos de pacientes / Cambios en turnos / Movimientos de
caja/pagos / Accesos al sistema / Todo lo anterior / Otro.
**Respuesta:** Todo lo anterior.
**Estado:** RESPONDIDA

---

## 9. Historia clínica y atención médica — solo el costado administrativo/legal (`MOD-002`, `MOD-003`, `MOD-004`, `MOD-005`, `MOD-007`, `MOD-008`)

<a id="mod-002"></a><a id="mod-003"></a><a id="mod-004"></a><a id="mod-005"></a><a id="mod-007"></a><a id="mod-008"></a>

**El contenido clínico de estos módulos (qué campos lleva una consulta, cómo se redacta una
evolución, qué antecedentes son relevantes) se releva directamente con los médicos, no acá —
ver [`preguntas_medicos.md`](preguntas_medicos.md).** Las siguientes son las únicas preguntas
de estos módulos que le corresponden al cliente/dueño por ser decisiones administrativas o
legales, no clínicas.

**Q-HCL-001** (Alta) — ¿Durante cuánto tiempo debe conservarse el registro de historia clínica
de un paciente (por norma legal o política propia)?
Opciones: Indefinidamente / Un plazo específico (indicar cuál) / No lo sabemos, hay que
confirmarlo / Otro.
**Respuesta:** Indefinidamente.
**Estado:** RESPONDIDA

**Q-HCL-002** (Media) — ¿El paciente puede pedir una copia de su historia clínica? ¿Cómo se
maneja hoy ese pedido?
Opciones: Sí, se le entrega copia impresa o digital / Hoy no se maneja ese pedido / Otro.
**Respuesta:** Otro: "nos encargamos nosotros; ustedes podrían darnos la opción de editar sin
tiempo de caducidad, por lo menos a un perfil de los directivos — al mío o al de Nadia, que somos
los que más estamos ahí". Pide un permiso de edición sin límite de tiempo para un perfil
directivo específico, más que describir el circuito de entrega de copias al paciente.
**Estado:** RESPONDIDA

**Q-CON-001** (Media) — ¿Existen distintos "tipos" de consulta que cambian la duración o el
precio (por ejemplo, primera vez vs. control)?
Opciones: Sí / No, todas las consultas son iguales a estos efectos / Otro.
**Respuesta:** No, todas las consultas son iguales a estos efectos.
**Estado:** RESPONDIDA

**Q-RET-001** (Alta) — ¿Las recetas necesitan imprimirse con un membrete o formato específico de
la clínica o del profesional?
Opciones: Sí / No, alcanza con un formato genérico / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

**Q-RET-002** (Media) — ¿Manejan recetas de medicamentos controlados (psicofármacos,
estupefacientes) que requieran un circuito especial?
Opciones: Sí / No / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

**Q-EST-001** (Alta) — ¿Qué tipos de estudios o resultados necesitan poder adjuntar a la ficha
del paciente?
Opciones (múltiple): Imágenes o fotos / PDFs de laboratorio / Estudios de centros externos /
Otro.
**Respuesta:** Imágenes o fotos, PDFs de laboratorio, Estudios de centros externos (los tres).
**Estado:** RESPONDIDA

**Q-EST-002** (Media) — ¿Trabajan con laboratorios o centros de diagnóstico externos que
debieran poder enviar resultados directamente al sistema?
Opciones: Sí / No, todo se sube manualmente / Otro.
**Respuesta:** No, todo se sube manualmente.
**Estado:** RESPONDIDA

**Q-EVO-001** (Media) — Una vez guardada una nota de evolución del paciente, ¿debería poder
modificarse libremente después, o solo corregirse dejando constancia del cambio original?
Opciones: Puede modificarse libremente / Solo corregirse dejando registro del cambio / No
debería poder modificarse nunca / Otro.
**Respuesta:** Solo corregirse dejando registro del cambio.
**Estado:** RESPONDIDA

---

## 10. Fórmulas oftalmológicas — solo para destrabar la investigación (`MOD-006`)

<a id="mod-006"></a>

Estas tres preguntas no reemplazan el relevamiento funcional de `MOD-006` (que sigue
bloqueado), pero son necesarias para poder avanzar con `INV-001`, `INV-002` e `INV-003`.

**Q-FOR-001** (Alta) — ¿Podrían compartirnos el documento/PDF de fórmulas oftalmológicas que
mencionaron como referencia?
Opciones: Sí, lo enviamos / No lo tenemos disponible / Otro.
**Respuesta:** Sí, lo enviamos. **Documento recibido el 2026-09-08** (`sistema nuevo.pdf`) — ver
[`investigaciones.md`](investigaciones.md) (`INV-001`) para el detalle de qué cubre y qué falta
todavía (la fórmula de combinación lejos/cerca requiere consulta directa con los médicos, ya
señalado en el propio documento).
**Estado:** RESPONDIDA

**Q-FOR-002** (Alta) — ¿Usan hoy Ampina y/o Treelan para las fórmulas oftalmológicas?
Opciones: Solo Ampina / Solo Treelan / Ambos / Ninguno, se hace en papel / Otro.
**Respuesta:** Ninguno, se hace en papel.
**Estado:** RESPONDIDA — **DESACTUALIZADA (2026-09-15).** Contradice la Ronda 1 de médicos
(`Q-FOR-005`), que sí menciona el uso de Treelan para la adición de cerca. El responsable del
proyecto confirmó directamente que sí lo usan; queda como dato vigente que la clínica **sí usa
Treelan**, y esta respuesta original del cliente no se toma como válida. Ver `INV-002` en
[`investigaciones.md`](investigaciones.md).

**Q-FOR-003** (Media) — ¿Podrían darnos acceso, o una exportación/captura de ejemplo, de ese
sistema (Ampina/Treelan) para entender qué calcula automáticamente?
Opciones: Sí / No es posible / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA — **vuelve a aplicar (2026-09-15)**, ya no está sin objeto: dado que sí
usan Treelan (ver `Q-FOR-002` actualizado), falta todavía conseguir ese acceso/ejemplo para poder
avanzar `INV-002`.

---

## 11. Configuración general (`MOD-036`)

<a id="mod-036"></a>

**Q-CFG-001** (Media) — ¿Cuál es el horario general de atención de la clínica (días y horas)?
Respuesta abierta.
**Respuesta:** Lunes a viernes de 7:30 a 20:00. Sábados de 8:00 a 12:30, solo Oftalmología.
**Estado:** RESPONDIDA

**Q-CFG-002** (Baja) — ¿Necesitan que el sistema pueda personalizarse con el logo y los colores
de la clínica?
Opciones: Sí / No es prioridad / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

---

## 12. Infraestructura, continuidad de datos y migración (`MOD-037`, `MOD-039`, `MOD-040`, más insumo para `ADR-001`)

<a id="mod-037"></a><a id="mod-039"></a><a id="mod-040"></a>

*(Estas preguntas no cierran `MOD-037` —que sigue bloqueado por `INV-006`— ni `ADR-001`
—`INV-005`—, pero son la información de negocio que falta para poder avanzar esas decisiones,
que son técnicas.)*

**Q-BCK-001** (Alta) — Si el sistema quedara caído, o se perdiera la información de un día
completo, ¿qué tan grave sería para la operación de la clínica?
Opciones: Muy grave, no podríamos operar / Grave, pero podríamos seguir en papel
temporalmente / Manejable / Otro.
**Respuesta:** Grave, pero podríamos seguir en papel temporalmente.
**Estado:** RESPONDIDA — informa `INV-006`, no lo cierra (falta presupuesto/responsable técnico).

**Q-BCK-002** (Media) — ¿Cuentan con presupuesto para un servicio de hosting/respaldo en la nube
de forma recurrente, o prefieren invertir una sola vez en equipamiento propio?
Opciones: Preferimos un servicio en la nube recurrente / Preferimos invertir en equipo propio /
Todavía no lo definimos / Otro.
**Respuesta (aclarada 2026-09-08):** Empiezan con hosting en la nube (servicio recurrente). No
descartan pasar a equipo propio más adelante — queda documentado como opción futura, sin
compromiso de fecha.
**Estado:** VALIDADA

**Q-INTG-001** (Media) — Más allá de Ampina/Treelan (ya preguntado en la sección 10), ¿usan hoy
algún otro sistema que el nuevo software debería seguir permitiendo usar en paralelo (contable,
facturación, portal de alguna obra social)?
Opciones (múltiple): Sistema contable / Sistema de facturación / Portal de alguna obra social /
Ninguno otro / Otro.
**Respuesta (aclarada 2026-09-08):** Ninguno otro. No hay contradicción real con `Q-PAG-003`: la
factura electrónica (AFIP) la gestionan directamente desde el sitio oficial de AFIP, que no es
un "sistema" de terceros a integrar, sino el trámite ante el organismo — de ahí que no lo hayan
marcado como un sistema externo a mantener en paralelo.
**Estado:** VALIDADA

**Q-IMP-001** (Alta) — Además de los pacientes (ya preguntado en `MOD-001`, `Q-PAC-050`),
¿tienen otra información existente que deba migrarse al nuevo sistema (turnos ya agendados,
historial de pagos, etc.)?
Opciones: Sí (indicar cuál) / No, arrancamos desde cero en todo lo demás / Otro.
**Respuesta:** Otro: "también estudios" (estudios/resultados existentes a migrar, además de
pacientes).
**Estado:** RESPONDIDA

**Q-DEP-001** (Alta, transversal — insumo para `ADR-001`) — Si internet se cortara en la
clínica, ¿hoy podrían seguir atendiendo pacientes de alguna forma (por ejemplo, en papel), o la
atención se detendría?
Opciones: Podemos seguir en papel temporalmente / La atención se vería muy afectada / Otro.
**Respuesta:** La atención se vería muy afectada.
**Estado:** RESPONDIDA — informa `ADR-001`/`INV-005` (pesa a favor de tolerancia a fallos de
conectividad en el diseño, ej. modo local/híbrido u offline parcial).

**Q-DEP-002** (Media, transversal — insumo para `ADR-001`) — ¿La clínica ya cuenta con algún
servidor o computadora dedicada exclusivamente para este sistema, o se partiría de cero?
Opciones: Ya contamos con equipo dedicado / Partiríamos de cero / No estoy seguro/a / Otro.
**Respuesta:** No estoy seguro/a.
**Estado:** RESPONDIDA — `INV-005`/`ADR-001` siguen abiertos en este punto (falta el dato con
el responsable técnico).

---

## Resumen de módulos que quedan fuera de esta ronda

| Módulo | Motivo | Dónde se retoma |
|---|---|---|
| `MOD-001` Pacientes | Ronda 1, en curso | `03_Modulos/MOD-001_Pacientes/preguntas_cliente.md` |
| `MOD-038` Logs y monitoreo | Decisión técnica interna | Se resuelve en el equipo, sin pregunta al cliente |

## Próximos pasos

1. ~~Convertir este archivo en el cuestionario interactivo (artefacto) para que el cliente
   responda todo de una sola vez, igual que se hizo con la Ronda 1 de `MOD-001`.~~ Hecho —
   respondida el 2026-09-08 (respuestas recibidas por otro canal, no por artifact interactivo).
2. ~~Repreguntar los puntos que quedaron ambiguos o contradictorios...~~ Hecho — `Q-AGE-003`,
   `Q-CAJ-001` y `Q-INTG-001`/`Q-PAG-003` aclarados el 2026-09-08 (ver respuestas arriba).
3. Actualizar el estado de cada módulo en
   [`../03_Modulos/README.md`](../03_Modulos/README.md); en particular, corregir el supuesto de
   sede única de `MOD-018` (`Q-SED-001`) — hecho.
4. ~~Cerrar `INV-002`/`INV-003`...~~ Hecho. `INV-001`: documento recibido el 2026-09-08, ver
   `investigaciones.md` para lo que todavía falta (fórmula de combinación lejos/cerca, a
   consultar con los médicos).
5. Definir con el cliente si avanza la migración del número general de WhatsApp a la Business
   Platform (Cloud API) — necesaria para automatizar recordatorios y el agendamiento de turnos
   por WhatsApp que pidieron explícitamente (`Q-WHA-001`).
6. ~~Una vez respondida `MOD-001`, armar la ronda 3 con las preguntas diferidas~~ — hecho el
   2026-09-24: [`cuestionario_cliente_ronda_3.md`](cuestionario_cliente_ronda_3.md) (bloque 2
   para los temas diferidos; la visibilidad por rol quedó en `Q-HCL-009`, bloque 3).
