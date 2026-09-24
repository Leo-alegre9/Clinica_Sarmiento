# MOD-001 — Datos principales

Confirmado por el cliente el 2026-09-08 (ver [`preguntas.md`](preguntas.md),
[`decisiones.md`](decisiones.md)) salvo donde se indique `PENDIENTE_DEFINICION` (detalle todavía
no preguntado o diferido).

## Identificación

- Tipo de documento: catálogo (DNI, cédula de identidad extranjera, pasaporte, DNI extranjero,
  CUIL/CUIT). **Sin validación estricta de formato de DNI argentino** — el campo acepta
  cualquiera de los tipos anteriores o quedar vacío (`Q-PAC-005`, `Q-PAC-007`).
- Número/valor de documento — opcional (`Q-PAC-006`: debe poder atenderse a un paciente sin
  ningún documento).
- Estado de identificación: `sin_documento` / `documento_en_tramite` / `documento_cargado`,
  como campo explícito, no solo DNI nulo (`Q-PAC-010`).
- Código provisorio interno — para pacientes sin documento (recién nacidos u otros); se
  completa editando el mismo registro cuando llega el documento real, nunca se crea ficha
  nueva (`Q-PAC-004`, `Q-PAC-008`, `Q-PAC-009`).
- País de origen del documento (para extranjeros).
- Identificador interno del sistema (siempre existe, independiente del documento).

## Datos personales

- Nombre, apellido — obligatorios.
- Fecha de nacimiento — obligatoria.
- Sexo/género — **un solo campo**, no dos separados (`Q-PAC-035`).
- Nacionalidad.
- Necesidad especial de atención (discapacidad visual/auditiva, movilidad reducida, necesidad
  de intérprete) — campo nuevo confirmado (`Q-PAC-053`, `RF-PAC-021`).

## Domicilio

- Obligatorio (`Q-PAC-011`, `Q-PAC-043`).
- Estructurado como mínimo con un subcampo de **localidad/zona** (no un único texto libre),
  porque debe poder filtrarse por zona (`Q-PAC-044`).
- Resto del domicilio — hipótesis de trabajo hasta `Q-PAC-066`: calle y número obligatorios;
  piso/departamento y código postal opcionales; localidad y provincia elegidas de un listado.

## Contacto

- Teléfono — obligatorio.
- WhatsApp — obligatorio, puede ser un número distinto al teléfono (`Q-PAC-026`).
- Canal de contacto preferido — campo nuevo (`Q-PAC-047`). Hipótesis hasta `Q-PAC-067`:
  WhatsApp, llamada o SMS, alineado con los canales de aviso de la Ronda 2 (`Q-NOT-001`, sin
  email).
- Preferencia de opt-out de comunicaciones no esenciales (salvo aviso de turno) — campo nuevo
  (`Q-PAC-048`).
- Email — no obligatorio (no fue marcado como obligatorio en `Q-PAC-011`/`Q-PAC-026`).

## Contacto de emergencia

- Obligatorio siempre, sin excepciones por tipo de paciente (`Q-PAC-027`).
- Nombre, parentesco, teléfono.

## Responsables / tutores (para menores de 18 años)

- Se modela como **referencia a un registro de `Paciente` existente** (rol adicional), no como
  entidad propia — frecuentemente el responsable es también paciente de la clínica
  (`Q-PAC-023`, `DEC-PAC-011`).
- Puede haber más de un responsable por paciente menor (`Q-PAC-024`).
- El vínculo se conserva como dato histórico al llegar el paciente a la mayoría de edad, no se
  desvincula automáticamente (`Q-PAC-025`).

## Cobertura

- Obra social — una o más, con exactamente una marcada como **principal** (`Q-PAC-018`).
- Se conserva historial de coberturas anteriores al cambiar de obra social (`Q-PAC-020`).
- Por afiliación: número de afiliado, plan/categoría, titular o familiar a cargo (`Q-PAC-019`).
- Vencimiento de la credencial y parentesco con el titular — `Q-PAC-019` no los marcó.
  Hipótesis hasta `Q-PAC-065`: ambos existen como campos **opcionales**.
- Flag de "atención particular puntual" pese a tener obra social vigente (`Q-PAC-021`).

## Estado administrativo

- Activo / inactivo (baja lógica) / fallecido / fusionado (ver `diagramas.md`).
- La baja es siempre lógica, nunca elimina el registro (`RN-PAC-005`).
- Fecha de alta, fecha de última modificación.
- Motivo de baja (si aplica).
- Fecha de fallecimiento (si aplica) y, si se revirtió por error, motivo de la reversión
  (hipótesis `Q-PAC-063`).
- Ficha que queda (solo si el estado es `Fusionado`, hipótesis `Q-PAC-054`).

## Encabezado de la ficha (lo que se ve al abrirla)

Pedido por los médicos (`Q-HCL-003`, `DEC-HCL-001`): nombre y apellido, **edad** (calculada a
partir de la fecha de nacimiento, no se carga aparte), obra social principal y **procedencia**.
Hipótesis hasta `Q-PAC-064`: "procedencia" es la localidad del domicilio, sin campo nuevo. Si el
cliente responde que se refiere a quién lo derivó, se agrega un campo "derivado por". Debajo del
encabezado van las alertas clínicas (sección siguiente).

## Información clínica básica (límite con MOD-002)

- Antecedentes visibles siempre en la ficha (no solo en la consulta): alergias a medicamentos,
  antecedentes quirúrgicos relevantes, enfermedades crónicas (`Q-PAC-030`).
- Alertas clínicas críticas — requieren aviso destacado permanente **y** ventana emergente al
  abrir la ficha (`Q-PAC-031`).
- Confirmado por los médicos (`Q-HCL-006`, `Q-HCL-007`, `INV-004`, 2026-09-24): son estas tres
  categorías, y la alergia medicamentosa se muestra como advertencia en un aviso destacado arriba
  de la ficha. Eduardo Peña respondió "Ninguna" a `Q-HCL-006`; no cambia la regla, que fijó el
  cliente (`Q-HCL-010` pide confirmarlo).
- Por cada antecedente: categoría, descripción, si es alerta crítica, quién lo cargó y cuándo, y
  estado de revisión (`pendiente de revisión médica` / `confirmado`, hipótesis `Q-PAC-060`).

## Documentación adjunta

- DNI escaneado, carnet de obra social, consentimientos firmados (`Q-PAC-029`).
- Fotografía del paciente — deseable pero no prioritaria (`Q-PAC-028`); requiere consentimiento
  específico de uso de imagen, distinto del consentimiento general (`Q-PAC-046`).

## Consentimientos

- Consentimiento de tratamiento de datos personales y clínicos — obligatorio en el alta
  presencial; no confirmado (no marcado) para el formulario de turnos online (`Q-PAC-045`).
  Es consistente con la hipótesis `RN-PAC-011`: la solicitud web no crea la ficha, así que el
  consentimiento se registra en recepción, al completar el alta.
- Consentimiento de uso de fotografía — separado del anterior (`Q-PAC-046`).

## Metadatos de auditoría

- Usuario que creó/modificó el registro.
- Fecha/hora de creación/modificación.
- Historial de **todos** los cambios sobre la ficha, no solo los sensibles (`Q-PAC-040`),
  incluyendo el historial de correcciones de DNI, consultable sin restricción de rol
  (`Q-PAC-017`).
- Ventana de corrección de antecedentes clínicos para el médico (`Q-PAC-037`, `RF-PAC-018`).
  Hipótesis: 24 h desde la carga, configurable (`Q-PAC-058`); los perfiles directivos designados
  corrigen sin límite (`Q-PAC-059`).
- Registro de exportaciones/impresiones de la ficha: quién y cuándo (`Q-PAC-034`).

## Multisede

- El paciente es una ficha única compartida entre sedes, no una ficha por sede (`Q-PAC-052`;
  confirmado además que la clínica ya opera más de una sede, ver Ronda 2 `Q-SED-001`).

## Privacidad (clasificación confirmada)

| Categoría | Visibilidad | Edición |
|---|---|---|
| Identificación, datos personales, contacto, cobertura | Todo el personal autenticado (`Q-PAC-036`, `Q-PAC-038`) | Todo el personal con acceso a la ficha |
| Antecedentes, alergias, alertas clínicas | Todo el personal autenticado (`Q-PAC-038`: no hay separación de visibilidad) | Agregar: todos (si no es médico, queda pendiente de revisión). Modificar/eliminar: médico dentro de la ventana, o perfil directivo designado (`Q-PAC-032`, `Q-PAC-037`, hipótesis `Q-PAC-058` a `Q-PAC-060`) |
| Documentación adjunta | Todo el personal autenticado, con auditoría de cada descarga (hipótesis `Q-PAC-069`) | Todo el personal con acceso a la ficha |

Detalle de permisos por rol y acción: ver [`reglas_negocio.md`](reglas_negocio.md#permisos-por-rol-y-acción).

**Nota de riesgo:** que todo el personal vea todos los datos clínicos sin restricción es una
simplificación deliberada del cliente, no una omisión del análisis — ver nota de riesgo de
privacidad en [`decisiones.md`](decisiones.md) y `RIE-PAC-004` en [`riesgos.md`](riesgos.md).
