```text
ID:                          MOD-023
Nombre:                      Pagos
Descripción:                 Registro de pagos (cobros) recibidos, con método de pago, dentro del flujo de caja.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-022 (Caja)
Requerimientos relacionados: RF-CAJ-002 (de RC-008)
```

Módulo identificado en el inventario inicial, sin refinamiento profundo todavía. Podría
terminar siendo una sección de `MOD-022` según el resultado del refinamiento de Caja.

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-023`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-023).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuesta de la Ronda 3 (2026-09-26)

`Q-OSO-004`: en cada atención, recepción elige con qué obra social se registra; viene marcada la
principal del paciente. No hay liquidación a obras sociales (`Q-OSO-005`, ver `MOD-019`).
