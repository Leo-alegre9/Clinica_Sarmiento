```text
ID:                          MOD-015
Nombre:                      Médicos / Profesionales
Descripción:                 Gestión de los profesionales de la clínica, modelados de forma extensible (no acoplados a "médico oftalmólogo").
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-016 (Especialidades), MOD-026 (Usuarios)
Requerimientos relacionados: RF-MED-000
```

Módulo identificado en el inventario inicial, sin refinamiento profundo todavía. Datos de
contacto de los médicos son información pendiente de recopilar del cliente (`RC-010`) — ver
[`../../08_Pendientes/documentos_pendientes.md`](../../08_Pendientes/documentos_pendientes.md).
Sus necesidades funcionales específicas dependen de `RC-006` (consultar a los demás médicos) —
ver [`INV-004`](../../08_Pendientes/investigaciones.md) y el cuestionario ya armado en
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).

## Datos ya conocidos

El documento del cliente [`../../08_Pendientes/anexos/sistema_nuevo.pdf`](../../08_Pendientes/anexos/sistema_nuevo.pdf)
(recibido 2026-09-08) nombra a los oftalmólogos que trabajan hoy en la clínica: **Arkwright
Ayelen**, **Coppini Emiliano** y **Rivera del Toro Luz**. Faltan matrícula, teléfono/email y
horarios de cada uno (ver [`../../08_Pendientes/documentos_pendientes.md`](../../08_Pendientes/documentos_pendientes.md)).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-015`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-015).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Datos confirmados en la Ronda 3 (2026-09-26)

- **Cecilia Portillo Rivero** y **Eduardo Peña** atienden **Oftalmología** (`Q-MED-005`).
- Eduardo Peña es también el "Eduardo" administrador con acceso a caja (`RC-009`). Un profesional
  puede tener además un rol administrativo: el modelo no puede suponer que "médico" y
  "administrador" son personas distintas (ver `MOD-027`).
- Los datos de cada médico (matrícula, contacto, horarios) se piden al final
  ([`documentos_pendientes.md`](../../08_Pendientes/documentos_pendientes.md)).
