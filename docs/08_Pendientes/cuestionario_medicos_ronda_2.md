# Cuestionario para los médicos — Ronda 2

**Estado: ARMADO el 2026-09-26, pendiente de envío.** 12 preguntas en 2 bloques.

Esta ronda cierra lo que falta para destrabar `MOD-006` (Fórmulas oftalmológicas) y para
diseñar la plantilla de consulta oftalmológica de `MOD-003`. Parte del ejemplo que la clínica
incluyó en [`anexos/sistema_nuevo.pdf`](anexos/sistema_nuevo.pdf) (sección 4, "Plantillas
preguardadas para las atenciones"), que el propio documento cierra así: *"para combinar lejos y
cerca tiene una fórmula específica para calcular, deberían consultar con los médicos"*.

## Criterio de armado

- Solo preguntas clínicas que el cliente no puede responder por los médicos. Lo administrativo
  ya se respondió en las rondas del cliente.
- **No se propone ninguna fórmula ni valor clínico.** Por `RN-CLI-001`, el sistema no implementa
  ningún cálculo que no esté documentado y validado por un profesional. Las preguntas piden el
  procedimiento que usan hoy, no lo confirman.
- Cada pregunta conserva su ID (`Q-XXX-###`) para volcar la respuesta al módulo de origen.
- **Responden los dos médicos por separado** (Cecilia Portillo Rivero y Eduardo Peña). Si las
  respuestas difieren, se registra la diferencia y se resuelve como en la Ronda 3 del cliente.
- Conviene pedir **un caso real** (con los datos del paciente tapados) para cada pregunta del
  bloque 1: un ejemplo resuelto vale más que una descripción.

## Antes de empezar

- Nombre de quien responde: ____________
- Especialidad: ____________

---

## Bloque 1 — Anteojos: de lejos a cerca (`MOD-006`, `MOD-005`)

Ejemplo del documento de la clínica:

| | Esférico | Cilindro | Eje |
|---|---|---|---|
| Lejos OD | +1.50 | +0.50 | 60° |
| Lejos OI | −3.50 | +2.50 | 80° |
| Cerca OD | +2.50 | +1.50 | 60° |
| Cerca OI | −1.50 | +3.50 | 80° |

**Q-FOR-009** (Alta) — ¿Cómo calculan hoy la graduación de **cerca** a partir de la de
**lejos**? Por favor, describan los pasos con un caso real resuelto de principio a fin.
Respuesta abierta.
**Respuesta:** —
**Estado:** ABIERTA

**Q-FOR-010** (Alta) — En el ejemplo de arriba, de lejos a cerca cambian el esférico **y
también el cilindro**, y el esférico sube distinto en cada ojo (+1.00 en OD, +2.00 en OI). ¿El
ejemplo es un caso real o solo ilustrativo? Si es real, ¿por qué cambian el cilindro y cada ojo
por separado?
Opciones: Es un caso real (explicar) / Es solo ilustrativo, los números no son de un caso real /
Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-FOR-011** (Alta) — La **adición** de cerca, ¿la elige el médico en cada caso (por edad,
distancia de trabajo, etc.) o sale de un cálculo? ¿Puede ser distinta en cada ojo?
Opciones: La elige el médico, igual para los dos ojos / La elige el médico, puede ser distinta
en cada ojo / Sale de un cálculo (explicar cuál) / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-FOR-012** (Alta) — ¿Qué datos cargan en **Treelan** y qué resultado les devuelve? ¿Y en
**Ampina**? Si pueden, adjunten una captura de pantalla de cada uno con un caso.
Respuesta abierta.
Resuelve `INV-002` e `INV-003`.
**Respuesta:** —
**Estado:** ABIERTA

**Q-FOR-013** (Alta) — En el sistema nuevo, ¿qué debería hacer el sistema con la graduación de
cerca?
Opciones: Calcularla y proponerla; el médico la revisa y puede cambiarla antes de guardar /
Solo mostrar los datos de lejos; el médico carga la de cerca a mano / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-FOR-014** (Media) — ¿Recetan también anteojos de **distancia intermedia**, bifocales o
multifocales? Si es así, ¿cómo se calcula o se indica cada uno en la receta?
Opciones: No, solo lejos y cerca / Sí (explicar cuáles y cómo se indican) / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-FOR-015** (Media) — Para cargar la graduación: ¿el cilindro se escribe siempre con signo
**+**, o también con signo **−**? ¿Los valores van en pasos de 0,25? ¿El eje va de 0° a 180°?
¿Hay otros datos que siempre acompañan la receta (por ejemplo, distancia pupilar)?
Respuesta abierta.
**Respuesta:** —
**Estado:** ABIERTA

---

## Bloque 2 — Plantilla de consulta oftalmológica (`MOD-003`)

La clínica pidió plantillas preguardadas con motivo de consulta, BMC, AV, PIO y anteojos. En la
Ronda 3 se decidió que la consulta tiene un formato común, con estas mediciones como campos
opcionales (`DEC-CON-005`).

**Q-CON-006** (Media) — **Agudeza visual (AV).** El documento dice que "siempre es del 1 al 10".
¿Usan solo esa escala (1/10 a 10/10)? ¿Usan también otras formas de anotarla, como "cuenta
dedos", "movimiento de manos", "percibe luz", o la escala 20/20? ¿Se registra con y sin
corrección, y con agujero estenopeico?
Respuesta abierta.
**Respuesta:** —
**Estado:** ABIERTA

**Q-CON-007** (Media) — **Presión intraocular (PIO).** El documento indica que lo normal es de 10
a 21 mmHg. ¿Quieren que el sistema **resalte** un valor fuera de ese rango (como el OI 45 del
ejemplo)? ¿El rango es siempre el mismo o depende del paciente?
Opciones: Sí, que resalte fuera de 10–21 / Sí, pero el rango lo ajusta el médico por paciente /
No hace falta resaltar nada / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-CON-008** (Media) — ¿Con qué aparatos miden la PIO? (En la Ronda 1 pidieron indicar con qué
aparato se mide.) Nombrar los que usan, para ofrecerlos en una lista.
Respuesta abierta.
**Respuesta:** —
**Estado:** ABIERTA

**Q-CON-009** (Baja) — **BMC (lámpara de hendidura).** ¿Lo escriben como un texto libre, o
prefieren un espacio por ojo y por parte del ojo (párpados, conjuntiva, córnea, cámara anterior,
iris, cristalino)?
Opciones: Texto libre, sin límite / Un texto libre por ojo / Un espacio por ojo y por parte del
ojo / Otro.
**Respuesta:** —
**Estado:** ABIERTA

**Q-CON-010** (Baja) — Además de motivo de consulta, BMC, AV, PIO y anteojos, ¿qué otras
secciones usan en la consulta (por ejemplo fondo de ojo, motilidad ocular, refracción con
autorrefractómetro)? ¿En qué orden las completan?
Respuesta abierta.
**Respuesta:** —
**Estado:** ABIERTA

---

## Resumen por criticidad

| Criticidad | Preguntas |
|---|---|
| Alta (destraban `MOD-006`) | Q-FOR-009, Q-FOR-010, Q-FOR-011, Q-FOR-012, Q-FOR-013 |
| Media | Q-FOR-014, Q-FOR-015, Q-CON-006, Q-CON-007, Q-CON-008 |
| Baja | Q-CON-009, Q-CON-010 |

**Cómo se usan las respuestas:** las del bloque 1 se vuelcan a
[`investigaciones.md`](investigaciones.md) (`INV-001`, `INV-002`, `INV-003`) y a `decisiones.md` de
`MOD-006`/`MOD-005`. Si describen el cálculo completo, con al menos un caso real resuelto, `MOD-006`
puede pasar a `EN_DESCUBRIMIENTO`. Las del bloque 2 van a `decisiones.md` de `MOD-003`.
