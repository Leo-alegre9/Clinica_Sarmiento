# Cuestionario para los médicos — Ronda 1

**Estado: RESPONDIDA el 2026-09-15, con aclaraciones cerradas el mismo día.** Ver `INV-004` en
[`investigaciones.md`](investigaciones.md). Las 28 preguntas fueron respondidas y volcadas a
`decisiones.md` de cada módulo afectado. Los puntos que habían quedado ambiguos o contradictorios
se resolvieron directamente con el responsable del proyecto (no se volvió a los médicos/cliente
formalmente, para no frenar el avance) — ver el detalle en cada pregunta más abajo y el resumen en
la nota al final de este documento.

**Profesionales que respondieron (identificados el 2026-09-24):**

| Profesional | Especialidad | Respuestas |
|---|---|---|
| Dra. Cecilia Portillo Rivero | `PENDIENTE_DEFINICION` (no declarada en el formulario) | Las volcadas en cada pregunta más abajo, recibidas el 2026-09-15 |
| Dr. Eduardo Peña | `PENDIENTE_DEFINICION` (no declarada en el formulario) | Recibidas por separado; transcriptas en la sección [Respuestas de Eduardo Peña](#respuestas-de-eduardo-peña) al final de este documento, con las divergencias frente a Portillo Rivero |

Hipótesis a confirmar (`Q-MED-005`, Ronda 3): Eduardo Peña es el mismo "Eduardo" que figura
como administrador con acceso a caja (`RC-009`), y en la Ronda 2 el cliente menciona "los turnos
de Eduardo" y "según Eduardo el paciente que va ahí no ve", lo que sugiere que también atiende.

Origen del requisito de proceso: `CLIENTE` (`RC-006`) — "es necesario consultar a los demás
médicos de la clínica para conocer sus necesidades". Este documento reemplaza la lista de 10
temas genéricos que tenía [`preguntas_medicos.md`](preguntas_medicos.md) por preguntas
concretas, listas para llevar a la reunión/entrevista de `INV-004`.

## A quién se le hace y por qué es distinta de la consulta al cliente

El cliente (dueño/interlocutor administrativo) ya respondió — o está respondiendo — todo lo que
es política de negocio, administrativa y legal (ver
[`cuestionario_cliente_ronda_2.md`](cuestionario_cliente_ronda_2.md)). Lo que falta y **no
puede responder el cliente** es el contenido clínico en sí: qué necesita ver o registrar un
profesional para atender bien a un paciente. Eso solo lo saben los médicos, y por eso `RC-006`
pide consultarlos directamente en vez de asumirlo.

Estas preguntas alimentan directamente: `MOD-002` (Historia Clínica), `MOD-003` (Consultas),
`MOD-004` (Diagnósticos), `MOD-005` (Recetas), `MOD-006` (Fórmulas oftalmológicas), `MOD-007`
(Estudios), `MOD-008` (Evoluciones), `MOD-009`/`MOD-013` (Agenda y Cirugías, vistas desde el
profesional) y, de forma cruzada, dos preguntas de `MOD-001` que ya están en la Ronda 1 del
cliente (`Q-PAC-030`, `Q-PAC-031`, sobre antecedentes/alertas) — acá se les pide a los médicos
el contenido real de esa respuesta.

## Cómo se hace (formato sugerido)

A diferencia del cuestionario del cliente, varias de estas preguntas piden una respuesta
abierta o un ejemplo real (una consulta ya hecha, una receta ya emitida) en vez de una opción
cerrada, porque la variedad clínica no siempre entra en un catálogo prearmado. Se recomienda
hacerlo como entrevista breve (30-40 min) por profesional o grupo de especialidad, no como
formulario para completar solo/a — varias respuestas van a generar repreguntas en el momento.

Las respuestas obtenidas se vuelcan a `decisiones.md` de cada módulo correspondiente, igual que
las respuestas del cliente (ver
[`../00_Gobernanza/control_cambios.md`](../00_Gobernanza/control_cambios.md)).

## Insumo ya recibido del cliente, a llevar como punto de partida a la entrevista

[`anexos/sistema_nuevo.pdf`](anexos/sistema_nuevo.pdf) (recibido 2026-09-08, ver `INV-001`)
trae un ejemplo concreto de plantilla de consulta oftalmológica (motivo de consulta, BMC, AV,
PIO, anteojos lejos/cerca en formato esférico/cilindro/eje) y aclara que la **fórmula para
combinar la graduación de lejos y cerca "tiene una fórmula específica... deberían consultar con
los médicos"** — es exactamente lo que deben cerrar `Q-FOR-005`/`Q-FOR-006` y `Q-RET-004` en
esta entrevista. Llevar el documento impreso o a mano como disparador, no asumir que ya
responde esas preguntas.

---

## 1. Historia clínica — qué necesitan ver de un paciente (`MOD-002`)

**Q-HCL-003** — Al abrir la ficha de un paciente, antes de atenderlo, ¿qué necesitan ver de
entrada, sin tener que buscarlo?
Respuesta abierta.
**Respuesta:** Nombre, edad, obra social, procedencia.
**Estado:** RESPONDIDA

**Q-HCL-004** — ¿Necesitan el historial completo de consultas anteriores siempre visible, o
alcanza con un resumen de lo más relevante y poder expandirlo si hace falta?
Opciones: Historial completo siempre visible / Resumen con opción de ver el detalle / Otro.
**Respuesta:** Resumen con opción de ver el detalle.
**Estado:** RESPONDIDA

**Q-HCL-005** — Cuando un paciente fue atendido por más de una especialidad, ¿cada profesional
debería ver todo lo que registraron las otras especialidades, o solo lo propio?
Opciones: Todo visible para cualquier profesional tratante / Cada especialidad ve solo lo
propio / Depende del caso (indicar cuál) / Otro.
**Respuesta:** Depende del caso — no se especificó cuál caso en el campo "Otro" que pedía la
pregunta.
**Estado:** RESPONDIDA — **aclarado 2026-09-15:** no hay una lista cerrada de casos ("en los que
sea"); la visibilidad entre especialidades se resuelve caso por caso, a criterio clínico, no con
una regla fija de "todo visible" o "solo lo propio". Implica que el sistema necesita un mecanismo
para compartir puntualmente un registro con otras especialidades cuando corresponda, en vez de un
permiso global — ver `DEC-HCL-004` en
[`../03_Modulos/MOD-002_Historia_Clinica/decisiones.md`](../03_Modulos/MOD-002_Historia_Clinica/decisiones.md).

### Antecedentes y alertas clínicas (insumo directo para `Q-PAC-030`/`Q-PAC-031` del cliente)

**Q-HCL-006** — ¿Qué antecedentes o alergias consideran indispensable que estén siempre
visibles al abrir la ficha, sin tener que revisar consultas viejas una por una?
Respuesta abierta (pedir ejemplos concretos).
**Respuesta:** Alergias medicamentosas deben aparecer como advertencia.
**Estado:** RESPONDIDA — **completado 2026-09-15:** confirmado que también deben incluirse
antecedentes quirúrgicos relevantes y enfermedades crónicas, además de alergias medicamentosas.
Coincide exactamente con lo que ya había definido el cliente en `DEC-PAC-012`, sin contradicción.

**Q-HCL-007** — ¿Cómo debería mostrarse una alerta crítica (por ejemplo, alergia grave a un
medicamento) para que nadie la pase por alto?
Opciones: Un aviso destacado siempre visible arriba de la ficha / Una ventana emergente al
abrirla / Ambas / Otro.
**Respuesta:** Un aviso destacado siempre visible arriba de la ficha.
**Estado:** RESPONDIDA — nota: el cliente ya había definido "ambas" (aviso + ventana emergente)
en `DEC-PAC-012`. Lo elegido acá es subconjunto de esa decisión, no la contradice; se mantiene
`DEC-PAC-012` sin cambios.

---

## 2. Consultas médicas (`MOD-003`)

**Q-CON-002** — ¿Qué registran (o necesitarían poder registrar) en cada consulta, más allá del
motivo de consulta?
Opciones (múltiple): Examen físico/oftalmológico / Diagnóstico / Indicaciones o tratamiento /
Próximo control sugerido / Otro.
**Respuesta:** Examen físico/oftalmológico, Diagnóstico, Indicaciones o tratamiento.
**Estado:** RESPONDIDA

**Q-CON-003** — ¿La estructura de una consulta cambia según la especialidad, o hay un formato
común a todas?
Opciones: Formato común para todas / Cambia según la especialidad (indicar en qué) / Otro.
**Respuesta:** Cambia según la especialidad. El detalle de "en qué" cambia, para Oftalmología,
queda cubierto por la respuesta a `Q-CON-004`.
**Estado:** RESPONDIDA — el detalle para el resto de las especialidades de la clínica (ver
listado en `Q-ESC-001`, Ronda 2 del cliente) se releva más adelante, cuando esas especialidades
se incorporen al sistema (decisión del responsable del proyecto, 2026-09-15). No bloquea el
refinamiento de `MOD-003` para Oftalmología.

**Q-CON-004** — ¿Necesitan registrar mediciones o signos específicos durante la consulta
(agudeza visual, presión intraocular, tensión arterial, peso, etc.)? ¿Cuáles, según su
especialidad?
Respuesta abierta.
**Respuesta:** Oftalmología — agudeza visual con y sin corrección; presión intraocular (indicando
con qué aparato se registra); y, opcional, medición de ARM (autorrefractómetro).
**Estado:** RESPONDIDA

---

## 3. Diagnósticos (`MOD-004`)

**Q-DIA-001** — ¿Usan hoy algún código estándar de diagnóstico (por ejemplo, CIE-10), o lo
registran en texto libre?
Opciones: Código estándar / Texto libre / Una combinación de ambos / Otro.
**Respuesta:** Una combinación de ambos.
**Estado:** RESPONDIDA

**Q-DIA-002** — ¿Un paciente puede tener más de un diagnóstico activo al mismo tiempo?
Opciones: Sí / No / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

**Q-DIA-003** — ¿Necesitan diferenciar un diagnóstico "presuntivo" (a confirmar) de uno ya
confirmado?
Opciones: Sí / No, se registra directamente el diagnóstico / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

---

## 4. Recetas / prescripciones (`MOD-005`)

**Q-RET-003** — ¿Qué datos no pueden faltar en una receta para que sea válida?
Opciones (múltiple): Nombre genérico y/o comercial del medicamento / Dosis y frecuencia /
Duración del tratamiento / Diagnóstico asociado / Firma y matrícula del profesional / Otro.
**Respuesta:** Las cinco opciones (Dosis y frecuencia, Duración del tratamiento, Nombre genérico
y/o comercial del medicamento, Firma y matrícula del profesional, Diagnóstico asociado) — ninguna
quedó afuera.
**Estado:** RESPONDIDA

**Q-RET-004** — Para recetas ópticas (anteojos, lentes de contacto), ¿qué datos específicos
necesitan además de lo anterior (graduación, distancia pupilar, tipo de cristal, etc.)?
Respuesta abierta.
**Respuesta:** Para la receta se coloca esférico, cilíndrico y ángulo (eje); después se puede
especificar si sugiere algún filtro, tipo de vidrio, o si son lentes de contacto — lo que puede
cambiar la receta original.
**Estado:** RESPONDIDA

**Q-RET-005** — ¿Necesitan poder repetir o renovar una receta anterior del mismo paciente
rápidamente, sin cargar todo de nuevo?
Opciones: Sí / No es necesario / Otro.
**Respuesta:** Sí.
**Estado:** RESPONDIDA

---

## 5. Fórmulas oftalmológicas (`MOD-006`) — insumo directo para `INV-002`/`INV-003`

**Q-FOR-004** — ¿Con qué frecuencia usan fórmulas oftalmológicas en la práctica diaria?
Opciones: Todos los días / Algunas veces por semana / Rara vez / Otro.
**Respuesta:** Todos los días.
**Estado:** RESPONDIDA

**Q-FOR-005** — De lo que calcula o completa automáticamente Ampina o Treelan hoy, ¿qué les
resulta realmente útil y les gustaría conservar en el sistema nuevo?
Respuesta abierta (pedir que muestren un caso real si es posible).
**Respuesta (textual):** "Del trelan que calcula los lentes de cerca que son una adicción."
**Estado:** RESPONDIDA — **contradicción con `Q-FOR-002` de la Ronda 2 resuelta el 2026-09-15**:
confirmado que sí usan Treelan. `Q-FOR-002` queda marcada como desactualizada en
`cuestionario_cliente_ronda_2.md`. `INV-002` se reabre como investigación real: falta conseguir
acceso/documentación de Treelan para entender qué calcula antes de poder diseñar algo similar
(`RN-CLI-001`). "Adicción" se mantiene sin confirmar si era error de tipeo por "adición"; no
bloquea nada mientras tanto.

**Q-FOR-006** — ¿Hay algo de esos sistemas actuales que consideren que funciona mal, que sea
incómodo, o que no usarían en el sistema nuevo?
Respuesta abierta.
**Respuesta (textual):** "El sistema actual es un hoja en blanco, será más para tico casillas
para completar lo basico."
**Estado:** RESPONDIDA — **descartada 2026-09-15**, decisión del responsable del proyecto de no
perseguir la aclaración para no frenar el avance. Queda sin usarse como insumo de diseño.

---

## 6. Estudios y documentación clínica (`MOD-007`)

**Q-EST-003** — ¿Qué estudios solicitan u ordenan con más frecuencia?
Respuesta abierta.
**Respuesta:** OCT (tomografía de coherencia óptica) de mácula o de nervio, retinografía, campo
visual, IOL (biometría para cálculo de lente intraocular).
**Estado:** RESPONDIDA

**Q-EST-004** — Cuando llega el resultado de un estudio, ¿necesitan poder agregar un comentario
o interpretación propia dentro del sistema, o alcanza con tener el archivo adjunto?
Opciones: Sí, necesitamos poder comentarlo/interpretarlo / No, alcanza con el archivo adjunto /
Otro.
**Respuesta:** Sí, necesitamos poder comentarlo/interpretarlo.
**Estado:** RESPONDIDA

---

## 7. Evoluciones / seguimiento del paciente (`MOD-008`)

**Q-EVO-002** — ¿En qué momentos registran (o deberían registrar) una nota de evolución, más
allá de cada consulta presencial?
Opciones (múltiple): Llamados telefónicos de seguimiento / Cambios de indicación entre
consultas / Resultados de un estudio que llega después / Otro.
**Respuesta:** Llamados telefónicos de seguimiento.
**Estado:** RESPONDIDA — **ampliado 2026-09-15:** confirmado que también se registra evolución
por cambios de indicación entre consultas y por resultados de un estudio que llega después. Las
tres opciones aplican.

**Q-EVO-003** — Para revisar cómo evolucionó un paciente en el tiempo, ¿prefieren una vista tipo
línea de tiempo, o alcanza con la lista de consultas en orden cronológico?
Opciones: Línea de tiempo visual / Alcanza con la lista en orden / Otro.
**Respuesta:** Alcanza con la lista en orden.
**Estado:** RESPONDIDA

---

## 8. Agenda — desde la mirada del profesional (`MOD-009`)

**Q-AGE-005** — Para organizar tu día, ¿qué necesitás ver de tu agenda además del nombre y el
horario del paciente?
Opciones (múltiple): Motivo de la consulta / Si es primera vez o control / Obra social /
Alertas clínicas del paciente / Otro.
**Respuesta:** Motivo de la consulta, Obra social.
**Estado:** RESPONDIDA

**Q-AGE-006** — ¿Necesitás ver la agenda de otros profesionales o consultorios para coordinar,
o te alcanza con ver la propia?
Opciones: Solo la propia / También la de otros, para coordinar casos / Otro.
**Respuesta:** Solo la propia.
**Estado:** RESPONDIDA

---

## 9. Cirugías (`MOD-013`)

**Q-CIR-005** — ¿Qué necesitan tener chequeado o preparado antes de una cirugía (checklist
prequirúrgico)?
Respuesta abierta.
**Respuesta:** Antes de que el paciente entre: prequirúrgicos completos, exámenes
oftalmológicos, consentimiento firmado (obligatorio, sin excepción).
**Estado:** RESPONDIDA — consistente con `Q-CIR-002` de Ronda 2 (consentimiento informado
obligatorio).

**Q-CIR-006** — El día de la cirugía, ¿qué información del paciente es crítica tener a mano de
forma inmediata?
Respuesta abierta.
**Respuesta:** Motivo de la cirugía, antecedentes.
**Estado:** RESPONDIDA

---

## 10. Reportes de la propia actividad (`MOD-041`)

**Q-RES-001** — ¿Qué te gustaría poder consultar sobre tu propia actividad (cantidad de
consultas, cirugías realizadas, pacientes atendidos por período, etc.)?
Respuesta abierta.
**Respuesta:** Consulta, Cx (cirugías).
**Estado:** RESPONDIDA — **completado 2026-09-15:** además del conteo, también quieren el
desglose por período (por ejemplo, por semana o por mes).

---

## 11. Notificaciones para el profesional (`MOD-029`)

**Q-NOT-003** — ¿Cómo preferís que te avisen sobre cambios en tu propia agenda (cancelaciones,
turnos nuevos, recordatorio de una cirugía próxima)?
Opciones (múltiple): WhatsApp / Email / Notificación dentro del sistema / No hace falta
avisarme, lo reviso yo mismo/a / Otro.
**Respuesta:** WhatsApp, Notificación dentro del sistema.
**Estado:** RESPONDIDA

---

## 12. Pregunta de cierre — descubrimiento abierto

**Pregunta de cierre** (sin ID de módulo específico, es exploratoria) — ¿Existen prácticas,
estudios o procedimientos que realicen habitualmente en la clínica y que no vean reflejados en
ninguno de los módulos de este relevamiento?
Respuesta abierta.
**Respuesta:** Crear una agenda quirúrgica dentro del sistema.
**Estado:** RESPONDIDA — hallazgo nuevo, no es una práctica/estudio sino un pedido de alcance:
una agenda quirúrgica separada de la agenda general. Registrado como `INV-008` en
[`investigaciones.md`](investigaciones.md) y **resuelto el 2026-09-15: es una extensión de
`MOD-013` (Cirugías)**, que ya preveía una agenda diferenciada de `MOD-009` según `RC-002`. No se
crea módulo nuevo.

---

## Próximos pasos

1. ~~Coordinar con el cliente la disponibilidad de los médicos para esta entrevista~~ — hecho,
   respuestas recibidas el 2026-09-15.
2. ~~Registrar cada respuesta en `decisiones.md` del módulo correspondiente~~ — hecho para
   `MOD-002, 003, 004, 005, 007, 008, 009, 013, 029, 041` (`MOD-006` queda aparte, con nota de
   contradicción resuelta, ver punto 5).
3. Si aparecen respuestas contradictorias entre profesionales de una misma especialidad,
   documentarlo como tal (no promediar ni elegir una a criterio del equipo de desarrollo) y
   escalarlo al cliente para resolución — no se pudo evaluar todavía porque el archivo de
   respuestas recibido no identifica qué profesional(es) respondieron cada pregunta. A partir de
   la próxima ronda de cuestionarios a médicos, se va a registrar el progreso identificado por
   profesional (nombre/especialidad), como estaba pensado originalmente. **Actualizado
   2026-09-24:** se identificó a quienes respondieron (Portillo Rivero y Peña) y se evaluaron las
   divergencias; ver la sección [Respuestas de Eduardo Peña](#respuestas-de-eduardo-peña). Las
   contradicciones se escalan al cliente en
   [`cuestionario_cliente_ronda_3.md`](cuestionario_cliente_ronda_3.md) (bloque 3).
4. ~~Una vez respondido, actualizar el estado de `INV-004`~~ — hecho. Estado de
   `MOD-002, 003, 004, 005, 007, 008, 009, 013, 029, 041` actualizado en sus respectivos
   `README.md` (enlazan a `decisiones.md`).
5. ~~Escalar la contradicción `Q-FOR-002`/`Q-FOR-005` (Treelan)~~ — **resuelto 2026-09-15**: el
   responsable del proyecto confirmó que sí usan Treelan, sin pasar por una ronda formal al
   cliente. `Q-FOR-002` quedó anotada como desactualizada en `cuestionario_cliente_ronda_2.md`;
   `INV-002` se reabrió como investigación real (conseguir acceso/documentación de Treelan). El
   caso sin especificar de `Q-HCL-005` también se aclaró (visibilidad caso por caso, sin lista
   fija); el texto poco claro de `Q-FOR-006` se descartó sin seguir indagando, por decisión del
   responsable del proyecto.
6. ~~Confirmar el alcance de la "agenda quirúrgica" (`CIERRE-001`, `INV-008`)~~ — **resuelto
   2026-09-15**: es una extensión de `MOD-013` (Cirugías), no un módulo nuevo.
7. **Pendiente:** conseguir acceso o documentación/ejemplo de Treelan (retomar `Q-FOR-003` del
   cliente) para poder avanzar `INV-002` y destrabar `MOD-006`.
8. **Pendiente:** resolver con el cliente las divergencias entre Portillo Rivero y Peña
   (sección siguiente) y reabrir `INV-003` (Peña menciona Ampina) — ver
   [`cuestionario_cliente_ronda_3.md`](cuestionario_cliente_ronda_3.md).

---

## Respuestas de Eduardo Peña

Recibidas por separado y registradas el 2026-09-24. Las respuestas que figuran en cada pregunta
más arriba son las de Cecilia Portillo Rivero (con las aclaraciones del 2026-09-15). Siguiendo el
punto 3 de "Próximos pasos", **no se promedian ni se elige una a criterio del equipo**: cuando las
dos respuestas son compatibles (una amplía a la otra) se registra como complemento; cuando se
contradicen, se marca `DIVERGE` y se escala al cliente.

Clasificación:

- **Coincide**: misma respuesta.
- **Complementa**: agrega información compatible con la de Portillo Rivero; se puede sumar sin
  decidir entre ambas.
- **DIVERGE**: las respuestas no pueden cumplirse las dos a la vez, o una niega lo que la otra
  pide. Se escala en [`cuestionario_cliente_ronda_3.md`](cuestionario_cliente_ronda_3.md).

| Pregunta | Respuesta de Eduardo Peña (textual) | Portillo Rivero | Clasificación |
|---|---|---|---|
| Q-HCL-003 | "Apellido y nombre. Obra social" | Nombre, edad, obra social, procedencia | Complementa (subconjunto) |
| Q-HCL-004 | Historial completo siempre visible | Resumen con opción de ver el detalle | **DIVERGE** → `Q-HCL-008` |
| Q-HCL-005 | Todo visible para cualquier profesional tratante | Depende del caso (aclarado: caso por caso) | **DIVERGE** → `Q-HCL-009`. Peña coincide con la decisión del cliente para la ficha del paciente (`Q-PAC-038`, todo el personal ve todo) |
| Q-HCL-006 | "Ninguna" | Alergias medicamentosas como advertencia (+ antecedentes quirúrgicos y enfermedades crónicas) | **DIVERGE** — no bloquea: la regla ya la fijó el cliente (`DEC-PAC-012`). Se pide confirmación en `Q-HCL-010` |
| Q-HCL-007 | Un aviso destacado siempre visible arriba de la ficha | Igual | Coincide |
| Q-CON-002 | Diagnóstico, indicaciones o tratamiento, **próximo control sugerido**, examen físico/oftalmológico | Examen, diagnóstico, indicaciones | Complementa (agrega próximo control sugerido) |
| Q-CON-003 | Formato común para todas | Cambia según la especialidad | **DIVERGE** → `Q-CON-005` |
| Q-CON-004 | "No" | AV con/sin corrección, PIO con aparato, ARM opcional | **DIVERGE** → `Q-CON-005` (puede explicarse por especialidad distinta, ver `Q-MED-005`) |
| Q-DIA-001 | Texto libre | Combinación código + texto libre | **DIVERGE** → `Q-DIA-004` |
| Q-DIA-002 | Sí | Sí | Coincide |
| Q-DIA-003 | No, se registra directamente el diagnóstico | Sí | **DIVERGE** → `Q-DIA-004` |
| Q-RET-003 | Nombre del medicamento, diagnóstico asociado, firma y matrícula | Las cinco opciones (agrega dosis/frecuencia y duración) | **DIVERGE** en qué es obligatorio → `Q-RET-006` |
| Q-RET-004 | "Ninguna mas" | Esférico, cilíndrico, eje; filtro, tipo de vidrio, lentes de contacto | Complementa (Peña no pide datos extra; Portillo Rivero sí) |
| Q-RET-005 | No es necesario | Sí | DIVERGE leve — funcionalidad opcional que no obliga a nadie a usarla; se mantiene `DEC-RET-003` salvo que el cliente diga lo contrario (`Q-RET-006`) |
| Q-FOR-004 | Todos los días | Todos los días | Coincide |
| Q-FOR-005 | "Ampina" | Treelan (adición de cerca) | **DIVERGE** → reabre `INV-003`; `Q-FOR-007` |
| Q-FOR-006 | "La base de datos. Lente respuesta del proveedor" | (descartada, texto poco claro) | Sin interpretar — repregunta `Q-FOR-008` |
| Q-EST-003 | OCT, CVC (campo visual computarizado), retinografía, **ecografía ocular** | OCT, retinografía, campo visual, IOL | Complementa (agrega ecografía ocular) |
| Q-EST-004 | Sí, necesitamos poder comentarlo/interpretarlo | Igual | Coincide |
| Q-EVO-002 | Cambios de indicación entre consultas, resultados de un estudio que llega después | Llamados (ampliado a las tres el 2026-09-15) | Coincide con la versión ampliada |
| Q-EVO-003 | Alcanza con la lista en orden | Igual | Coincide |
| Q-AGE-005 | Motivo de la consulta, **si es primera vez o control**, obra social | Motivo, obra social | Complementa (agrega primera vez / control) |
| Q-AGE-006 | Solo la propia | Igual | Coincide |
| Q-CIR-005 | "Varios. Exámenes de laboratorio y ECG. Estudios oftalmológicos (ecografía + ecometría y/o IOL Master)" | Prequirúrgicos completos, exámenes oftalmológicos, consentimiento firmado | Complementa (detalla qué son los prequirúrgicos) |
| Q-CIR-006 | Ecometría, OCT, IOL | Motivo de la cirugía, antecedentes | Complementa |
| Q-RES-001 | "Todas las anteriores" (consultas, cirugías, pacientes atendidos por período) | Consultas, cirugías, por período | Complementa (agrega pacientes atendidos) |
| Q-NOT-003 | WhatsApp | WhatsApp, notificación dentro del sistema | Complementa (subconjunto) — sugiere que el canal sea configurable por profesional |
| CIERRE-001 | "No" | Agenda quirúrgica | Complementa (sin hallazgos nuevos) |

Los complementos se incorporaron el 2026-09-24 a `decisiones.md` de cada módulo afectado. Las
divergencias quedan anotadas en esos mismos archivos, sin modificar la decisión vigente hasta
que responda el cliente.
