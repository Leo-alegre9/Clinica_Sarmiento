# Requerimientos funcionales — versión normalizada

Cada requerimiento crudo (`RC-###`) se descompone aquí en uno o más requerimientos
funcionales (`RF-XXX-###`) con estado y módulo asociado. Estado según
[`../00_Gobernanza/estados_requerimientos.md`](../00_Gobernanza/estados_requerimientos.md).
Todos parten en `PROPUESTO` salvo que el cliente ya los haya confirmado literalmente (en cuyo
caso igual quedan `PROPUESTO` hasta el refinamiento formal del módulo, para no adelantar
diseño sin las preguntas resueltas).

## De RC-001 — Agenda de consultas

- **RF-AGE-001** — El sistema debe permitir gestionar una agenda diaria de consultas por
  profesional. *Módulo:* `MOD-009`. *Estado:* PROPUESTO.

## De RC-002 — Agenda de cirugías

- **RF-CIR-001** — El sistema debe permitir gestionar una agenda específica para cirugías,
  diferenciada de la agenda de consultas. *Módulo:* `MOD-013`. *Estado:* PROPUESTO.
- **RF-CIR-002** — El sistema debe enviar recordatorios automáticos y anticipados al paciente
  ante una cirugía programada. Parámetros (anticipación, medio, cantidad de recordatorios,
  manejo de no confirmación/reprogramación/cancelación) `PENDIENTE_DEFINICION`. *Módulo:*
  `MOD-014`. *Estado:* PROPUESTO.

## De RC-003 — Solicitud pública de turnos

- **RF-PUB-001** — El sistema debe permitir a un paciente consultar disponibilidad de turnos
  desde la página institucional. *Módulo:* `MOD-034`. *Estado:* PROPUESTO.
- **RF-PUB-002** — El sistema debe permitir a un paciente solicitar un turno desde la página
  institucional. Modelo de confirmación (reserva automática vs. confirmación manual por
  secretario/a) `PENDIENTE_DEFINICION` — ver `Q-TUR-*`. *Módulo:* `MOD-033`. *Estado:*
  PROPUESTO.

## De RC-004 — Obras sociales

- **RF-OSO-001** — El sistema debe permitir asociar uno o más pacientes a una o más obras
  sociales. Alcance exacto (planes, autorizaciones, copagos, liquidaciones, convenios)
  `PENDIENTE_DEFINICION`. *Módulo:* `MOD-019`, `MOD-020`, `MOD-021`. *Estado:* PROPUESTO.

## De RC-005 — Fórmulas oftalmológicas

- **RF-FOR-001** — El sistema debe permitir registrar fórmulas oftalmológicas de un paciente.
  Estructura y eventual cálculo asistido `PENDIENTE_DEFINICION`, sujeto a `INV-001`, `INV-002`,
  `INV-003`. *Módulo:* `MOD-006`. *Estado:* PROPUESTO — bloqueado por investigación.

## De RC-006 — Requerimientos de otros médicos

No genera un `RF` propio: es un requisito de **proceso** (descubrimiento pendiente). Ver
[`INV-004`](../08_Pendientes/investigaciones.md) y
[`../08_Pendientes/preguntas_medicos.md`](../08_Pendientes/preguntas_medicos.md).

## De RC-007 — Llegada anticipada / prioridad de atención

- **RF-REC-001** — El sistema debe permitir registrar la llegada (check-in) de un paciente,
  mostrando horario programado, horario real de llegada y estado. *Módulo:* `MOD-011`.
  *Estado:* PROPUESTO.
- **RF-ESP-001** — El sistema debe gestionar una cola/lista de pacientes en espera. Criterio de
  ordenamiento/prioridad `PENDIENTE_DEFINICION` (no asumir orden de llegada). *Módulo:*
  `MOD-012`. *Estado:* PROPUESTO.

## De RC-008 — Caja

- **RF-CAJ-001** — El sistema debe permitir abrir y cerrar una caja. *Módulo:* `MOD-022`.
  *Estado:* PROPUESTO.
- **RF-CAJ-002** — El sistema debe permitir registrar cobros asociados a consultas y a
  cirugías. *Módulo:* `MOD-022`, `MOD-023`. *Estado:* PROPUESTO.
- **RF-CAJ-003** — El sistema debe permitir registrar egresos/gastos. *Módulo:* `MOD-024`.
  *Estado:* PROPUESTO.
  Alcance detallado (cajas por usuario/sede/turno, métodos de pago, categorías, arqueos,
  comprobantes, anulaciones, devoluciones, diferencias) `PENDIENTE_DEFINICION`.

## De RC-009 — Roles y acceso

- **RF-SEG-001** — El sistema debe implementar un modelo de usuarios, roles y permisos
  configurable (`Usuario → Rol → Permisos`), no atado a personas específicas. *Módulo:*
  `MOD-026`, `MOD-027`. *Estado:* PROPUESTO.
- **RF-SEG-002** — El rol de administrador debe poder incluir acceso a los movimientos de
  caja. *Módulo:* `MOD-027`, `MOD-022`. *Estado:* PROPUESTO.

## De RC-010 — Datos de contacto de médicos

No genera un `RF`: es información pendiente de recopilar del cliente. Ver
[`../08_Pendientes/documentos_pendientes.md`](../08_Pendientes/documentos_pendientes.md).

## De RC-011 — Backups

- **RNF-BCK-001** — El sistema debe respaldar la información según una política a definir
  (alcance, frecuencia, retención, cifrado, restauración, responsables).
  `PENDIENTE_DEFINICION`. Ver [`requerimientos_no_funcionales.md`](requerimientos_no_funcionales.md)
  y `INV-006`. *Módulo:* `MOD-037`.

## De RC-012 — Formulario público de solicitud de turnos

- **RF-PUB-003** — El formulario público debe recopilar la información necesaria para
  gestionar la consulta del paciente. Campos exactos `PENDIENTE_DEFINICION` — ver
  `Q-PUB-*` (a generar en el refinamiento de `MOD-033`). *Módulo:* `MOD-033`. *Estado:*
  PROPUESTO.

## De RC-013 — Implementación web vs. local

No genera un `RF`: es una decisión de arquitectura. Ver
[`ADR-001`](../05_Arquitectura/ADR/ADR-001-web-vs-local-vs-hibrido.md).

## Requerimientos funcionales adicionales detectados por análisis (no explícitos en RC-###)

Origen: `ANÁLISIS`, derivados de la sección 6 del pedido del cliente ("información ya conocida
del proyecto") y del `README.md`/roadmap previo del repositorio. Requieren validación como
cualquier otro punto de origen `ANÁLISIS`.

- **RF-PAC-000** — El sistema debe permitir gestionar pacientes (alta, modificación, baja,
  búsqueda). *Módulo:* `MOD-001`. *Estado:* PROPUESTO — en refinamiento activo, ver
  [`../03_Modulos/MOD-001_Pacientes/requerimientos.md`](../03_Modulos/MOD-001_Pacientes/requerimientos.md).
- **RF-HCL-000** — El sistema debe sostener una historia clínica por paciente. *Módulo:*
  `MOD-002`. *Estado:* PROPUESTO.
- **RF-CON-000** — El sistema debe registrar consultas médicas. *Módulo:* `MOD-003`. *Estado:*
  PROPUESTO.
- **RF-REC-000** — El sistema debe permitir generar recetas/prescripciones. *Módulo:*
  `MOD-005`. *Estado:* PROPUESTO.
- **RF-MED-000** — El sistema debe permitir gestionar profesionales/médicos y sus
  especialidades. *Módulo:* `MOD-015`, `MOD-016`. *Estado:* PROPUESTO.

Este listado se amplía cuando cada módulo entra en refinamiento formal.
