```text
ID:                          MOD-013
Nombre:                      Cirugías
Descripción:                 Agenda y gestión de cirugías programadas, diferenciada de la agenda de consultas comunes.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-15
Dependencias:                MOD-001 (Pacientes), MOD-015 (Profesionales), MOD-014 (Recordatorios)
Requerimientos relacionados: RF-CIR-001 (de RC-002)
```

Módulo identificado en el inventario inicial, sin refinamiento profundo todavía. Requiere
definir junto con `MOD-014`: anticipación de recordatorio, medio, cantidad de recordatorios,
comportamiento ante no confirmación/reprogramación/cancelación (todos `PENDIENTE_DEFINICION`
según `RC-002`).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-013`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-013).
Además, el costado clínico (checklist prequirúrgico, qué información necesita el profesional el
día de la cirugía) se releva con los médicos, no con el cliente — ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuestas de los médicos (Ronda 1)

`INV-004` se respondió el 2026-09-15. Las decisiones ya confirmadas están en
[`decisiones.md`](decisiones.md): checklist prequirúrgico e información crítica a mano el día de
la cirugía. La pregunta de cierre exploratoria también dejó un pedido de "agenda quirúrgica"
dentro del sistema (`INV-008`), resuelto el mismo día como una extensión de este módulo.
