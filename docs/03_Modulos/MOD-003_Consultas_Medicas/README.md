```text
ID:                          MOD-003
Nombre:                      Consultas Médicas
Descripción:                 Registro de la atención médica no quirúrgica de un paciente: motivo, evaluación, indicaciones.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-15
Dependencias:                MOD-001 (Pacientes), MOD-009 (Agenda), MOD-015 (Profesionales)
Requerimientos relacionados: RF-CON-000
```

Módulo identificado en el inventario inicial, sin refinamiento profundo todavía. Ver
[`../README.md`](../README.md) para el inventario completo y el orden de refinamiento.

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-003`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-003).
**Importante:** esa ronda cubre solo el costado administrativo/legal, respondible por el
cliente. El contenido clínico de este módulo se releva aparte, directamente con los médicos
(`RC-006`, `INV-004`), no en este cuestionario. El cuestionario concreto para esa
consulta ya está armado en [`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).
Preguntas adicionales (más profundas, incluyendo las clínicas) se agregarán cuando a este
módulo le toque su refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuestas de los médicos (Ronda 1)

`INV-004` se respondió el 2026-09-15. Las decisiones ya confirmadas están en
[`decisiones.md`](decisiones.md): qué se registra en cada consulta y que la estructura cambia
por especialidad (con el detalle completo solo para Oftalmología por ahora —
`PENDIENTE_DEFINICION` para el resto de las especialidades).
