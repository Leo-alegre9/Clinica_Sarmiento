```text
ID:                          MOD-031
Nombre:                      Email
Descripción:                 Canal de comunicación por correo electrónico (recordatorios, confirmaciones, notificaciones administrativas).
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-029 (Notificaciones)
Requerimientos relacionados: RF-CIR-002
```

Laravel ya trae soporte de mail configurado (`config/mail.php`) desde la Fase 1, sin uso de
dominio todavía (solo lo usa Fortify para verificación de email).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-031`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-031).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).
