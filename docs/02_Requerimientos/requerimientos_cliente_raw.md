# Requerimientos crudos del cliente

Origen: `CLIENTE`. Apuntes obtenidos directamente de reuniones/conversaciones con el cliente,
proporcionados el 2026-09-02 para abrir la fase de ingeniería de requisitos. Se transcriben
**sin perder el significado original**. No son requisitos definitivos: son la entrada para el
análisis y normalización en
[`requerimientos_funcionales.md`](requerimientos_funcionales.md).

---

### RC-001 — Agenda de consultas

Se necesita una agenda para consultas comunes que funcione como agenda diaria.

---

### RC-002 — Agenda de cirugías

Debe existir una agenda específica para cirugías. Cuando exista una cirugía programada, el
sistema deberá poder avisar automáticamente y con anticipación al paciente para recordársela.

Debe definirse posteriormente: cuánto tiempo antes; mediante qué medio; cuántos recordatorios;
qué sucede si el paciente no confirma; qué sucede si se reprograma; qué sucede si se cancela.

---

### RC-003 — Solicitud de turnos desde la página institucional

Desde la página institucional, el paciente deberá poder consultar disponibilidad de turnos y
solicitar uno de los horarios libres.

Existe una decisión pendiente:

**Alternativa A:** el paciente reserva automáticamente el turno.

**Alternativa B:** el paciente solicita el horario y un secretario debe confirmar/asignar
definitivamente el turno.

En caso de utilizar la alternativa B, se analiza permitir que el paciente genere
automáticamente un mensaje solicitando ese horario.

Este requerimiento debe analizarse cuidadosamente antes de tomar una decisión.

---

### RC-004 — Obras sociales

El sistema debe contemplar obras sociales. Todavía debe determinarse el alcance exacto:
asociación paciente ↔ obra social; planes; número de afiliado; autorizaciones; cobertura;
copagos; prácticas; liquidaciones; convenios; vigencia; otras necesidades administrativas.

No asumir funcionalidades sin validarlas.

---

### RC-005 — Fórmulas oftalmológicas

Existe documentación/PDF de fórmulas utilizado como referencia. Debe revisarse antes de
definir este módulo.

También existe como referencia el sistema Treelan, que aparentemente permite ingresar
determinados valores y obtener automáticamente algún resultado o diagnóstico, a diferencia de
Ampina.

NO inventar la lógica clínica. Crear este punto como requerimiento pendiente de investigación
y solicitar la documentación correspondiente. Cualquier cálculo médico deberá estar
documentado, validado por profesionales y ser trazable.

---

### RC-006 — Requerimientos de otros médicos

Es necesario consultar a los demás médicos de la clínica para conocer sus necesidades. Esto
significa que los requisitos actuales NO representan todavía las necesidades completas de
todos los profesionales.

Registrar este punto dentro de stakeholders y descubrimiento pendiente.

---

### RC-007 — Llegada anticipada del paciente / prioridad de atención

Cuando un paciente se presenta en la clínica, debe registrarse su llegada. Si tenía turno para
determinada hora pero llegó antes, el sistema debería mostrar: hora programada del turno; hora
real de llegada; estado actual; información necesaria para decidir si puede adelantarse la
atención.

Debe analizarse una posible **lista/cola de pacientes en espera con prioridades**. No asumir
que será simplemente por orden de llegada.

Definir mediante preguntas: prioridad por horario; prioridad médica; urgencias; pacientes
quirúrgicos; adultos mayores; niños; pacientes con discapacidad; retrasos; pacientes que
llegaron tarde; adelantos; sobreturnos; decisión manual del secretario/médico.

---

### RC-008 — Caja

Implementar una sección de caja. Se mencionó: apertura; cierre; cobros de consultas; cobros
relacionados con cirugías; otros gastos.

Este módulo necesita un refinamiento importante. Debe determinarse: cajas por usuario; cajas
por sede; cajas por turno; métodos de pago; ingresos; egresos; categorías; arqueos;
movimientos; comprobantes; anulaciones; devoluciones; diferencias; permisos; auditoría;
reportes.

---

### RC-009 — Roles y acceso a caja

Debe existir un sistema de usuarios y roles. Se indicó que determinados administradores deben
tener acceso a los movimientos de caja.

Personas mencionadas por el cliente como administradores: Hernán; Eduardo; Melisa; Noelia.

No diseñar permisos directamente alrededor de nombres personales. Crear roles/permisos
configurables. Ejemplo conceptual: `Usuario → Rol → Permisos`.

Los nombres anteriores son únicamente usuarios iniciales que podrían recibir determinado rol.

---

### RC-010 — Datos de contacto de médicos

Consultar a Hernán los números/datos de contacto de los médicos. Registrar como información
pendiente.

---

### RC-011 — Backups

Debe definirse: qué información se respaldará; frecuencia; retención; almacenamiento;
cifrado; restauración; responsables; formato; copias externas; automatización.

No limitar el análisis solamente al "formato del backup".

---

### RC-012 — Formulario completo para solicitud de turnos

El formulario público de solicitud de turnos deberá permitir recopilar toda la información
necesaria para gestionar correctamente la consulta del paciente. Debe determinarse qué
significa exactamente "abarcar toda la consulta".

Generar preguntas para definir: datos personales; paciente nuevo/existente; médico;
especialidad; motivo; obra social; tipo de consulta; urgencia; observaciones; archivos;
estudios previos; disponibilidad; consentimiento; datos de contacto.

---

### RC-013 — Implementación web versus local

Debe analizarse formalmente el modelo de despliegue. Comparar como mínimo: aplicación web
centralizada; instalación local; arquitectura híbrida; funcionamiento ante caída de Internet;
seguridad; backups; mantenimiento; actualizaciones; acceso remoto; costos; infraestructura;
disponibilidad; escalabilidad.

NO tomar todavía una decisión solamente por este apunte. Crear un ADR o documento de decisión
arquitectónica pendiente.

---

## Trazabilidad de esta página

Ver el desglose normalizado en [`requerimientos_funcionales.md`](requerimientos_funcionales.md)
y la matriz completa en [`matriz_trazabilidad.md`](matriz_trazabilidad.md).
