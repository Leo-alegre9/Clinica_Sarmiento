# Prompt — Cuestionarios Clínica Sarmiento (Ronda 2 + Médicos)

Prompt autocontenido para pasar a otra herramienta/proyecto que arma cuestionarios. Contiene
las dos baterías de preguntas que todavía faltan armar: la **Ronda 2** para el cliente (resto
de los módulos) y la consulta a los **médicos**, tal como están hoy en
`docs/08_Pendientes/cuestionario_cliente_ronda_2.md` y
`docs/08_Pendientes/cuestionario_medicos_ronda_1.md`. El cuestionario de Pacientes (Ronda 1) ya
está armado aparte y no va en este prompt.

---

## Instrucciones para quien arme el cuestionario

Sos parte del equipo que releva requerimientos para un sistema de gestión de una clínica
oftalmológica en Argentina (Clínica Sarmiento). Necesito que generes dos cuestionarios web
interactivos a partir del contenido de más abajo, uno por cada bloque ("Cuestionario 1 — Ronda
2" y "Cuestionario 2 — Médicos").

**Audiencias — son distintas entre sí, no las mezcles:**
- **Cuestionario 1 (Ronda 2):** el dueño/interlocutor administrativo de la clínica. Sin
  conocimientos técnicos — el lenguaje ya está pensado para esa audiencia, no lo tecnifiques.
- **Cuestionario 2 (Médicos):** profesionales de la clínica (médicos). Está redactado en
  segunda persona ("vos"/"necesitás") porque se los completa cada profesional individualmente,
  a diferencia del primero. Pensalo también como guía de entrevista, no solo como formulario:
  muchas respuestas van a ser de texto libre y pueden disparar una repregunta en el momento.

**Idioma:** español (Argentina). Mantené el texto de las preguntas y opciones exactamente como
está.

**Formato por pregunta**, tal como aparece abajo:
- Un ID estable (por ejemplo `Q-MED-001`) — no lo cambies ni lo renumeres, se usa para trazar la
  respuesta de vuelta a la documentación de origen. Una pregunta del cierre del cuestionario de
  médicos no tiene ID de módulo (`CIERRE-001`) porque es exploratoria a propósito.
- Una criticidad: `Alta`, `Media` o `Baja` — Alta significa que bloquea el avance del proyecto
  hasta tener respuesta; mostralo como badge o indicador visual.
- Un tipo:
  - `single` → selección única (radio buttons).
  - `multi` → selección múltiple (checkboxes).
  - `open` → respuesta abierta de texto libre (no tiene opciones). El cuestionario de médicos
    tiene bastantes más preguntas de este tipo que el de Ronda 2 — es intencional, no lo
    conviertas a opciones cerradas.
- El texto de la pregunta.
- Una lista de opciones (cuando el tipo es `single`/`multi`). **Toda lista de opciones termina
  en "Otro"**, que al marcarse debe desplegar un campo de texto libre para que la persona
  especifique — nunca lo trates como una opción de texto fijo más.

**Comportamiento esperado de la interfaz** (replicar en ambos cuestionarios):
- Progreso visible (cuántas preguntas respondidas sobre el total, idealmente también por
  sección).
- Guardado automático mientras se completa, sin necesidad de un botón "guardar"; la persona
  debe poder cerrar y volver más tarde sin perder lo ya cargado.
- Un resumen antes de enviar que priorice mostrar qué preguntas de criticidad **Alta** quedan
  sin responder (son las que más importan resolver).
- Dos campos libres al inicio, antes de las preguntas: en el Cuestionario 1, nombre de quien
  completa y su rol en la clínica; en el Cuestionario 2, nombre del profesional y su
  especialidad — y como lo va a completar más de un médico, cada uno necesita que su progreso
  se guarde por separado (identificado por su nombre), no todos pisando el mismo registro.
- Los dos cuestionarios son de contenido independiente (temas y audiencias distintas) pero
  deberían compartir una misma identidad visual si conviven en el mismo lugar — son parte de la
  misma serie de relevamiento (la Ronda 1 de Pacientes, ya armada, es la tercera pieza de esa
  serie).

No agregues preguntas nuevas, no fusiones preguntas entre sí, y no reformules el texto: el
contenido ya pasó por un proceso de validación de lenguaje simple y alcance.

## CUESTIONARIO 1 — Ronda 2 (resto de los módulos)

77 preguntas, 12 bloques temáticos, cubriendo 38 módulos del sistema (todos menos Pacientes).

### Bloque 1 — Personal, especialidades y espacios físicos

**Q-MED-001** (Alta, multi) — Además del nombre, ¿qué datos necesitan tener cargados de cada profesional para que el sistema funcione?
Opciones: Matrícula profesional / Especialidad(es) / Datos para firmar recetas / Teléfono y email / Horarios habituales / Otro.

**Q-MED-002** (Alta, single) — ¿Un mismo profesional puede tener más de una especialidad?
Opciones: Sí, frecuentemente / Puede pasar, pero es poco común / No, cada profesional tiene una sola especialidad / Otro.

**Q-MED-003** (Media, single) — ¿Un profesional puede atender en más de un consultorio o, a futuro, en más de una sede?
Opciones: Sí / No / Depende del profesional / Otro.

**Q-MED-004** (Baja, single) — ¿Necesitan poder marcar a un profesional como "de licencia" temporalmente (vacaciones, enfermedad) sin borrar su información ni su historial?
Opciones: Sí / No, alcanza con vaciar su agenda manualmente / Otro.

**Q-ESC-001** (Alta, open) — ¿Cuáles son las especialidades médicas que ofrece hoy la clínica? (para cargarlas como listado inicial)

**Q-ESC-002** (Media, single) — ¿Necesitan agrupar especialidades relacionadas (por ejemplo, "Oftalmología general" y "Oftalmología pediátrica" bajo un mismo grupo "Oftalmología")?
Opciones: Sí / No, cada una es independiente / Otro.

**Q-CTO-001** (Alta, open) — ¿Cuántos consultorios o salas de atención tienen hoy en uso?

**Q-CTO-002** (Media, single) — ¿Cada consultorio está reservado para un tipo específico de práctica (por ejemplo, uno solo para procedimientos), o son intercambiables entre profesionales?
Opciones: Específicos por tipo de práctica / Intercambiables / Depende del consultorio / Otro.

**Q-SED-001** (Alta, single) — ¿Cuántas sedes/sucursales tiene la clínica en funcionamiento hoy?
Opciones: Una sola / Más de una / Otro.

**Q-SED-002** (Media, single) — ¿Tienen planeado abrir otra sede en los próximos 1-2 años?
Opciones: Sí / No / Todavía no lo sabemos / Otro.

### Bloque 2 — Agenda, turnos y recepción

**Q-AGE-001** (Alta, single) — ¿Cómo arman hoy la agenda de cada profesional?
Opciones: Horarios fijos semanales (por ejemplo, lunes y miércoles de 9 a 13) / Se cargan turnos variables semana a semana / Combinación de ambas / Otro.

**Q-AGE-002** (Alta, single) — ¿Cuánto dura habitualmente un turno de consulta?
Opciones: Una duración fija para todos / Varía según el tipo de consulta o práctica / Lo decide cada profesional / Otro.

**Q-AGE-003** (Media, single) — ¿Un profesional necesita poder bloquear horarios de su agenda para tareas que no son atención al público (cirugías, tareas administrativas)?
Opciones: Sí / No es necesario / Otro.

**Q-AGE-004** (Media, single) — ¿Cómo manejan hoy los feriados y días no laborables en la agenda?
Opciones: Se cierran manualmente cada vez que corresponde / Preferiríamos un calendario de feriados que los bloquee automáticamente / Otro.

**Q-TUR-001** (Alta, single) — ¿Qué pasa hoy cuando un paciente no se presenta a su turno ("ausente")?
Opciones: No pasa nada especial / Queda registrado como antecedente / Se limitan sus próximos turnos si se repite / Otro.

**Q-TUR-002** (Alta, single) — ¿Con cuánta anticipación mínima se puede cancelar o reprogramar un turno sin inconvenientes?
Opciones: Sin límite de tiempo / Hasta una cierta cantidad de horas/días antes / Hoy no hay una política definida / Otro.

**Q-TUR-003** (Media, single) — ¿Necesitan una lista de espera para turnos ya completos, por si se libera un lugar?
Opciones: Sí / No es necesario / Otro.

**Q-TUR-004** (Media, single) — ¿Reciben pacientes sin turno previo ("por orden de llegada") que se atienden si hay lugar disponible?
Opciones: Sí, habitualmente / Solo en casos de urgencia / No, todo es con turno previo / Otro.

**Q-REC-001** (Alta, multi) — Cuando el paciente llega a la clínica, ¿qué hace hoy recepción antes de que pase con el médico?
Opciones: Confirma datos personales / Confirma o cobra la cobertura/obra social / Entrega un comprobante o número / Avisa al consultorio que el paciente llegó / Otro.

**Q-REC-002** (Media, single) — ¿Necesitan imprimir algún comprobante de check-in para el paciente?
Opciones: Sí / No / Otro.

**Q-ESP-001** (Alta, single) — En la sala de espera, ¿en qué orden se llama habitualmente a los pacientes?
Opciones: Por orden de llegada / Por el horario de turno asignado / El profesional decide a quién llama / Hay excepciones por urgencia médica sobre el orden normal / Otro.

**Q-ESP-002** (Media, single) — ¿Existen criterios que hacen "saltar" el orden normal (embarazadas, adultos mayores, urgencias)?
Opciones: Sí (detallar cuáles en "Otro") / No / Otro.

**Q-ESP-003** (Baja, single) — ¿Necesitan una pantalla o cartel que muestre a qué paciente se está llamando?
Opciones: Sí / No, alcanza con avisar verbalmente / Otro.

### Bloque 3 — Cirugías y recordatorios

**Q-CIR-001** (Alta, multi) — Para programar una cirugía, ¿qué información necesitan registrar además de la fecha y el paciente?
Opciones: Profesional(es) que intervienen / Consultorio o quirófano / Tipo de cirugía / Consentimiento informado firmado / Indicaciones prequirúrgicas / Otro.

**Q-CIR-002** (Alta, single) — ¿Necesitan que quede registrado en el sistema un consentimiento informado firmado antes de la cirugía?
Opciones: Sí, es obligatorio / Hoy se maneja en papel, aparte del sistema / No aplica / Otro.

**Q-CIR-003** (Media, single) — ¿Una cirugía puede tener más de un profesional o asistente asociado?
Opciones: Sí / No, un solo responsable por cirugía / Otro.

**Q-CIR-004** (Media, single) — Al programar una cirugía, ¿debe bloquearse automáticamente el consultorio/quirófano y la agenda normal del profesional en ese horario?
Opciones: Sí / No es necesario, se coordina aparte / Otro.

**Q-RCD-001** (Alta, single) — ¿Con cuánta anticipación debe enviarse un recordatorio de turno o cirugía?
Opciones: 24 horas antes / 48 horas antes / Más de un recordatorio (por ejemplo, una semana y un día antes) / Otro.

**Q-RCD-002** (Alta, single) — ¿Necesitan que el paciente pueda confirmar o cancelar el turno respondiendo directamente al recordatorio?
Opciones: Sí / No, el recordatorio es solo informativo / Otro.

**Q-RCD-003** (Media, single) — Si el paciente no responde al recordatorio, ¿qué debería pasar?
Opciones: Nada, el turno se mantiene / Se lo vuelve a contactar por otro medio / El turno se libera automáticamente / Otro.

### Bloque 4 — Comunicaciones

**Q-NOT-001** (Alta, multi) — ¿Por qué medio prefieren que se envíen los recordatorios y avisos a los pacientes?
Opciones: WhatsApp / SMS / Email / Llamado telefónico / Otro.

**Q-NOT-002** (Media, multi) — Además de los recordatorios de turno, ¿qué otros avisos automáticos necesitan enviar a los pacientes?
Opciones: Resultados de estudios disponibles / Cambios de horario del profesional / Confirmación de una solicitud de turno online / Novedades generales de la clínica / Ninguno otro por ahora / Otro.

**Q-WHA-001** (Alta, single) — ¿La clínica ya tiene un número de WhatsApp Business oficial/verificado para comunicarse con pacientes?
Opciones: Sí, ya lo tenemos / No, habría que gestionarlo / No estoy seguro/a / Otro.

**Q-MAI-001** (Media, single) — ¿Tienen un dominio de email propio de la clínica (por ejemplo, @clinicasarmiento.com), o usan un correo genérico?
Opciones: Sí, tenemos dominio propio / No, usamos un correo genérico (Gmail u otro) / Otro.

**Q-PLT-001** (Baja, single) — Para los mensajes que reciben los pacientes, ¿necesitan poder editar ustedes mismos el texto más adelante, o alcanza con un texto acordado una vez con el equipo de desarrollo?
Opciones: Necesitamos poder editarlo nosotros mismos / Alcanza con un texto fijo acordado una vez / Otro.

### Bloque 5 — Portal público de turnos

**Q-PUB-001** (Alta, multi) — ¿Qué datos mínimos debería pedir el formulario público para solicitar un turno?
Opciones: Nombre y apellido / DNI / Teléfono / Email / Obra social / Especialidad o motivo de consulta / Otro.

**Q-PUB-002** (Alta, single) — Cuando alguien pide un turno desde la web, ¿queda confirmado automáticamente (si hay lugar disponible) o siempre necesita que alguien de recepción lo revise y confirme antes?
Opciones: Se confirma automáticamente si hay lugar / Siempre requiere confirmación manual de recepción / Depende del profesional o la especialidad / Otro.

**Q-DIS-001** (Alta, single) — ¿Todos los profesionales y especialidades deberían mostrar sus horarios disponibles públicamente en la web, o solo algunos?
Opciones: Todos / Solo algunos (indicar cuáles en "Otro") / Ninguno por ahora, se decide más adelante / Otro.

**Q-DIS-002** (Media, single) — ¿Con cuánta anticipación hacia adelante debería mostrarse la disponibilidad en el portal público?
Opciones: Una semana / Dos semanas / Un mes / Otro.

**Q-SOL-001** (Media, single) — Si una solicitud de turno público queda pendiente de confirmación, ¿en cuánto tiempo esperan que recepción la revise?
Opciones: El mismo día / Dentro de 24-48 horas / Hoy no hay un plazo definido / Otro.

**Q-SOL-002** (Baja, single) — ¿El paciente debería poder consultar el estado de su solicitud por sí mismo, o se entera solo cuando lo contactan?
Opciones: Sí, debería poder consultarlo / No es necesario, alcanza con que lo contacten / Otro.

### Bloque 6 — Obras sociales y coberturas

**Q-OSO-001** (Alta, open) — ¿Con qué obras sociales y prepagas trabaja hoy la clínica?

**Q-OSO-002** (Alta, single) — ¿Necesitan validar la cobertura antes de la consulta (por ejemplo, con un portal de la obra social o un llamado), o alcanza con la credencial que presenta el paciente?
Opciones: Se valida antes por algún medio / Alcanza con la credencial presentada / Depende de la obra social / Otro.

**Q-OSO-003** (Media, single) — ¿El paciente paga habitualmente algo de su bolsillo además de lo que cubre la obra social (copago/coseguro)?
Opciones: Sí, según la obra social y la práctica / No, la obra social cubre todo / Otro.

**Q-PLA-001** (Media, single) — Dentro de una misma obra social, ¿existen distintos planes o categorías que cambian lo que cubren?
Opciones: Sí / No / Depende de la obra social / Otro.

**Q-AUT-001** (Alta, single) — ¿Hay prácticas o estudios que necesitan autorización previa de la obra social antes de realizarse?
Opciones: Sí, para ciertas prácticas / No manejamos autorizaciones previas / No estoy seguro/a / Otro.

**Q-AUT-002** (Media, single) — Cuando se necesita esa autorización previa, ¿quién la gestiona hoy?
Opciones: La clínica / El propio paciente / Depende del caso / Otro.

### Bloque 7 — Administración financiera

**Q-CAJ-001** (Alta, single) — ¿Cómo manejan hoy la caja: una única por día, una por persona/turno de trabajo, o una por sede?
Opciones: Única por día / Una por persona o turno de trabajo / Una por sede / Otro.

**Q-CAJ-002** (Alta, single) — ¿Necesitan un cierre de caja diario que compare lo que debería haber contra lo efectivamente contado (arqueo)?
Opciones: Sí / No es necesario / Otro.

**Q-PAG-001** (Alta, multi) — ¿Qué medios de pago aceptan hoy?
Opciones: Efectivo / Tarjeta de débito o crédito / Transferencia bancaria / Mercado Pago u otra billetera virtual / Otro.

**Q-PAG-002** (Media, single) — ¿Aceptan pagos parciales o en cuotas para un mismo servicio?
Opciones: Sí / No, se paga completo / Otro.

**Q-PAG-003** (Alta, single) — ¿Necesitan emitir la factura electrónica (AFIP) directamente desde este sistema, o eso se maneja aparte con un sistema contable?
Opciones: Necesitamos emitirla desde el sistema / Se maneja aparte, con otro sistema / No emitimos factura hoy / Otro.

**Q-GAS-001** (Media, single) — ¿Necesitan registrar en este sistema los gastos de la clínica (insumos, servicios, sueldos), o eso ya lo llevan en otro lado?
Opciones: Sí, queremos registrarlos acá / No, se maneja aparte / Otro.

**Q-RAD-001** (Media, multi) — De los reportes administrativos, ¿cuáles consultan con más frecuencia hoy o les gustaría tener?
Opciones: Ingresos por día/período / Ingresos por profesional / Ingresos por obra social / Turnos atendidos vs. ausentes / Otro.

### Bloque 8 — Usuarios, roles y auditoría

**Q-USR-001** (Alta, multi) — ¿Qué tipos de usuarios del sistema tienen hoy, según su función (más allá de "médico" y "recepción")?
Opciones: Recepción/administrativo / Médico o profesional / Dirección/administración / Caja / Otro.

**Q-USR-002** (Alta, single) — ¿Cada persona tiene (o debería tener) su propio usuario y contraseña, o hoy se comparte un usuario por puesto de trabajo?
Opciones: Cada persona con su propio usuario / Se comparte por puesto de trabajo / Otro.

**Q-ROL-001** (Media, single) — ¿Quién debería poder crear o dar de baja usuarios del sistema?
Opciones: Solo una persona administradora general / Cualquier directivo / Otro.

**Q-AUD-001** (Media, multi) — Ante un problema o reclamo, ¿qué tipo de acciones necesitan poder rastrear ("quién hizo qué y cuándo")?
Opciones: Cambios en datos de pacientes / Cambios en turnos / Movimientos de caja/pagos / Accesos al sistema / Todo lo anterior / Otro.

### Bloque 9 — Historia clínica y atención (costado administrativo/legal)

**Q-HCL-001** (Alta, single) — ¿Durante cuánto tiempo debe conservarse el registro de historia clínica de un paciente (por norma legal o política propia)?
Opciones: Indefinidamente / Un plazo específico (indicar cuál en "Otro") / No lo sabemos, hay que confirmarlo / Otro.

**Q-HCL-002** (Media, single) — ¿El paciente puede pedir una copia de su historia clínica? ¿Cómo se maneja hoy ese pedido?
Opciones: Sí, se le entrega copia impresa o digital / Hoy no se maneja ese pedido / Otro.

**Q-CON-001** (Media, single) — ¿Existen distintos "tipos" de consulta que cambian la duración o el precio (por ejemplo, primera vez vs. control)?
Opciones: Sí / No, todas las consultas son iguales a estos efectos / Otro.

**Q-RET-001** (Alta, single) — ¿Las recetas necesitan imprimirse con un membrete o formato específico de la clínica o del profesional?
Opciones: Sí / No, alcanza con un formato genérico / Otro.

**Q-RET-002** (Media, single) — ¿Manejan recetas de medicamentos controlados (psicofármacos, estupefacientes) que requieran un circuito especial?
Opciones: Sí / No / Otro.

**Q-EST-001** (Alta, multi) — ¿Qué tipos de estudios o resultados necesitan poder adjuntar a la ficha del paciente?
Opciones: Imágenes o fotos / PDFs de laboratorio / Estudios de centros externos / Otro.

**Q-EST-002** (Media, single) — ¿Trabajan con laboratorios o centros de diagnóstico externos que debieran poder enviar resultados directamente al sistema?
Opciones: Sí / No, todo se sube manualmente / Otro.

**Q-EVO-001** (Media, single) — Una vez guardada una nota de evolución del paciente, ¿debería poder modificarse libremente después, o solo corregirse dejando constancia del cambio original?
Opciones: Puede modificarse libremente / Solo corregirse dejando registro del cambio / No debería poder modificarse nunca / Otro.

### Bloque 10 — Fórmulas oftalmológicas (solo para destrabar una investigación pendiente)

**Q-FOR-001** (Alta, single) — ¿Podrían compartirnos el documento/PDF de fórmulas oftalmológicas que mencionaron como referencia?
Opciones: Sí, lo enviamos / No lo tenemos disponible / Otro.

**Q-FOR-002** (Alta, single) — ¿Usan hoy Ampina y/o Treelan para las fórmulas oftalmológicas?
Opciones: Solo Ampina / Solo Treelan / Ambos / Ninguno, se hace en papel / Otro.

**Q-FOR-003** (Media, single) — ¿Podrían darnos acceso, o una exportación/captura de ejemplo, de ese sistema (Ampina/Treelan) para entender qué calcula automáticamente?
Opciones: Sí / No es posible / Otro.

### Bloque 11 — Configuración general

**Q-CFG-001** (Media, open) — ¿Cuál es el horario general de atención de la clínica (días y horas)?

**Q-CFG-002** (Baja, single) — ¿Necesitan que el sistema pueda personalizarse con el logo y los colores de la clínica?
Opciones: Sí / No es prioridad / Otro.

### Bloque 12 — Infraestructura, continuidad de datos y migración

**Q-BCK-001** (Alta, single) — Si el sistema quedara caído, o se perdiera la información de un día completo, ¿qué tan grave sería para la operación de la clínica?
Opciones: Muy grave, no podríamos operar / Grave, pero podríamos seguir en papel temporalmente / Manejable / Otro.

**Q-BCK-002** (Media, single) — ¿Cuentan con presupuesto para un servicio de hosting/respaldo en la nube de forma recurrente, o prefieren invertir una sola vez en equipamiento propio?
Opciones: Preferimos un servicio en la nube recurrente / Preferimos invertir en equipo propio / Todavía no lo definimos / Otro.

**Q-INTG-001** (Media, multi) — Más allá de Ampina/Treelan, ¿usan hoy algún otro sistema que el nuevo software debería seguir permitiendo usar en paralelo?
Opciones: Sistema contable / Sistema de facturación / Portal de alguna obra social / Ninguno otro / Otro.

**Q-IMP-001** (Alta, single) — Además de los pacientes, ¿tienen otra información existente que deba migrarse al nuevo sistema (turnos ya agendados, historial de pagos, etc.)?
Opciones: Sí (indicar cuál en "Otro") / No, arrancamos desde cero en todo lo demás / Otro.

**Q-DEP-001** (Alta, single) — Si internet se cortara en la clínica, ¿hoy podrían seguir atendiendo pacientes de alguna forma (por ejemplo, en papel), o la atención se detendría?
Opciones: Podemos seguir en papel temporalmente / La atención se vería muy afectada / Otro.

**Q-DEP-002** (Media, single) — ¿La clínica ya cuenta con algún servidor o computadora dedicada exclusivamente para este sistema, o se partiría de cero?
Opciones: Ya contamos con equipo dedicado / Partiríamos de cero / No estoy seguro/a / Otro.

---

## CUESTIONARIO 2 — Médicos (Ronda 1)

28 preguntas (27 con ID de módulo + 1 de cierre exploratoria), 12 bloques. A diferencia del
Cuestionario 1, esto no es para el dueño/administración de la clínica sino para cada médico
individualmente — de ahí que muchas preguntas estén en segunda persona y que casi la mitad sean
de respuesta abierta. Pensalo como guion de entrevista tanto como formulario.

### Bloque 1 — Historia clínica: qué necesitan ver de un paciente

**Q-HCL-003** (Alta, open) — Al abrir la ficha de un paciente, antes de atenderlo, ¿qué necesitan ver de entrada, sin tener que buscarlo?

**Q-HCL-004** (Media, single) — ¿Necesitan el historial completo de consultas anteriores siempre visible, o alcanza con un resumen de lo más relevante y poder expandirlo si hace falta?
Opciones: Historial completo siempre visible / Resumen con opción de ver el detalle / Otro.

**Q-HCL-005** (Media, single) — Cuando un paciente fue atendido por más de una especialidad, ¿cada profesional debería ver todo lo que registraron las otras especialidades, o solo lo propio?
Opciones: Todo visible para cualquier profesional tratante / Cada especialidad ve solo lo propio / Depende del caso (indicar cuál en "Otro") / Otro.

**Q-HCL-006** (Alta, open) — ¿Qué antecedentes o alergias consideran indispensable que estén siempre visibles al abrir la ficha, sin tener que revisar consultas viejas una por una?

**Q-HCL-007** (Alta, single) — ¿Cómo debería mostrarse una alerta crítica (por ejemplo, alergia grave a un medicamento) para que nadie la pase por alto?
Opciones: Un aviso destacado siempre visible arriba de la ficha / Una ventana emergente al abrirla / Ambas / Otro.

### Bloque 2 — Consultas médicas

**Q-CON-002** (Alta, multi) — ¿Qué registran (o necesitarían poder registrar) en cada consulta, más allá del motivo de consulta?
Opciones: Examen físico/oftalmológico / Diagnóstico / Indicaciones o tratamiento / Próximo control sugerido / Otro.

**Q-CON-003** (Media, single) — ¿La estructura de una consulta cambia según la especialidad, o hay un formato común a todas?
Opciones: Formato común para todas / Cambia según la especialidad (indicar en qué) / Otro.

**Q-CON-004** (Media, open) — ¿Necesitan registrar mediciones o signos específicos durante la consulta (agudeza visual, presión intraocular, tensión arterial, peso, etc.)? ¿Cuáles, según su especialidad?

### Bloque 3 — Diagnósticos

**Q-DIA-001** (Media, single) — ¿Usan hoy algún código estándar de diagnóstico (por ejemplo, CIE-10), o lo registran en texto libre?
Opciones: Código estándar / Texto libre / Una combinación de ambos / Otro.

**Q-DIA-002** (Media, single) — ¿Un paciente puede tener más de un diagnóstico activo al mismo tiempo?
Opciones: Sí / No / Otro.

**Q-DIA-003** (Media, single) — ¿Necesitan diferenciar un diagnóstico "presuntivo" (a confirmar) de uno ya confirmado?
Opciones: Sí / No, se registra directamente el diagnóstico / Otro.

### Bloque 4 — Recetas / prescripciones

**Q-RET-003** (Alta, multi) — ¿Qué datos no pueden faltar en una receta para que sea válida?
Opciones: Nombre genérico y/o comercial del medicamento / Dosis y frecuencia / Duración del tratamiento / Diagnóstico asociado / Firma y matrícula del profesional / Otro.

**Q-RET-004** (Media, open) — Para recetas ópticas (anteojos, lentes de contacto), ¿qué datos específicos necesitan además de lo anterior (graduación, distancia pupilar, tipo de cristal, etc.)?

**Q-RET-005** (Media, single) — ¿Necesitan poder repetir o renovar una receta anterior del mismo paciente rápidamente, sin cargar todo de nuevo?
Opciones: Sí / No es necesario / Otro.

### Bloque 5 — Fórmulas oftalmológicas (insumo directo para destrabar una investigación pendiente)

**Q-FOR-004** (Alta, single) — ¿Con qué frecuencia usan fórmulas oftalmológicas en la práctica diaria?
Opciones: Todos los días / Algunas veces por semana / Rara vez / Otro.

**Q-FOR-005** (Alta, open) — De lo que calcula o completa automáticamente Ampina o Treelan hoy, ¿qué les resulta realmente útil y les gustaría conservar en el sistema nuevo? (si pueden, muestren un caso real)

**Q-FOR-006** (Media, open) — ¿Hay algo de esos sistemas actuales que consideren que funciona mal, que sea incómodo, o que no usarían en el sistema nuevo?

### Bloque 6 — Estudios y documentación clínica

**Q-EST-003** (Media, open) — ¿Qué estudios solicitan u ordenan con más frecuencia?

**Q-EST-004** (Media, single) — Cuando llega el resultado de un estudio, ¿necesitan poder agregar un comentario o interpretación propia dentro del sistema, o alcanza con tener el archivo adjunto?
Opciones: Sí, necesitamos poder comentarlo/interpretarlo / No, alcanza con el archivo adjunto / Otro.

### Bloque 7 — Evoluciones / seguimiento del paciente

**Q-EVO-002** (Media, multi) — ¿En qué momentos registran (o deberían registrar) una nota de evolución, más allá de cada consulta presencial?
Opciones: Llamados telefónicos de seguimiento / Cambios de indicación entre consultas / Resultados de un estudio que llega después / Otro.

**Q-EVO-003** (Baja, single) — Para revisar cómo evolucionó un paciente en el tiempo, ¿prefieren una vista tipo línea de tiempo, o alcanza con la lista de consultas en orden cronológico?
Opciones: Línea de tiempo visual / Alcanza con la lista en orden / Otro.

### Bloque 8 — Agenda: desde la mirada del profesional

**Q-AGE-005** (Media, multi) — Para organizar tu día, ¿qué necesitás ver de tu agenda además del nombre y el horario del paciente?
Opciones: Motivo de la consulta / Si es primera vez o control / Obra social / Alertas clínicas del paciente / Otro.

**Q-AGE-006** (Media, single) — ¿Necesitás ver la agenda de otros profesionales o consultorios para coordinar, o te alcanza con ver la propia?
Opciones: Solo la propia / También la de otros, para coordinar casos / Otro.

### Bloque 9 — Cirugías

**Q-CIR-005** (Alta, open) — ¿Qué necesitan tener chequeado o preparado antes de una cirugía (checklist prequirúrgico)?

**Q-CIR-006** (Alta, open) — El día de la cirugía, ¿qué información del paciente es crítica tener a mano de forma inmediata?

### Bloque 10 — Reportes de la propia actividad

**Q-RES-001** (Baja, open) — ¿Qué te gustaría poder consultar sobre tu propia actividad (cantidad de consultas, cirugías realizadas, pacientes atendidos por período, etc.)?

### Bloque 11 — Notificaciones para el profesional

**Q-NOT-003** (Media, multi) — ¿Cómo preferís que te avisen sobre cambios en tu propia agenda (cancelaciones, turnos nuevos, recordatorio de una cirugía próxima)?
Opciones: WhatsApp / Email / Notificación dentro del sistema / No hace falta avisarme, lo reviso yo mismo/a / Otro.

### Bloque 12 — Descubrimiento abierto (sin módulo específico, exploratoria)

**CIERRE-001** (Media, open) — ¿Existen prácticas, estudios o procedimientos que realicen habitualmente en la clínica y que no vean reflejados en ninguno de los módulos de este relevamiento?
