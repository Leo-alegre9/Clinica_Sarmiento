```text
ID:                          MOD-012
Nombre:                      Sala de espera / Cola de atención / Prioridades
Descripción:                 Orden de atención de pacientes presentes, considerando posibles criterios de prioridad más allá del orden de llegada.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-011 (Recepción / Check-in)
Requerimientos relacionados: RF-ESP-001 (de RC-007)
```

**Explícitamente no se asume orden de llegada como único criterio** (instrucción directa del
cliente en `RC-007`). El criterio real de prioridad (horario, urgencia, tipo de paciente,
decisión manual, etc.) es `PENDIENTE_DEFINICION` y debe salir de preguntas específicas al
refinar este módulo.

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-012`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-012).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).
