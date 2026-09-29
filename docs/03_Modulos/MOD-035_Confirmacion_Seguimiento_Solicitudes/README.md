```text
ID:                          MOD-035
Nombre:                      Confirmación / seguimiento de solicitudes
Descripción:                 Seguimiento del estado de una solicitud pública de turno (pendiente, confirmada, rechazada) por parte del paciente.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-033 (Solicitud pública de turnos)
Requerimientos relacionados: (a definir en refinamiento; depende de la Alternativa A/B de RC-003)
```

Su existencia depende directamente de qué alternativa se elija en `RC-003`: si el turno se
reserva automáticamente (Alternativa A), este módulo probablemente se reduce a una simple
confirmación; si requiere aprobación de secretaría (Alternativa B), este módulo cobra más
peso.

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-035`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-035).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).
