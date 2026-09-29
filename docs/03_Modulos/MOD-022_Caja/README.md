```text
ID:                          MOD-022
Nombre:                      Caja
Descripción:                 Apertura, cierre y movimientos de caja de la clínica: cobros de consultas y cirugías, otros gastos.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-026 (Usuarios), MOD-027 (Roles y permisos)
Requerimientos relacionados: RF-CAJ-001, RF-CAJ-002 (de RC-008); RF-SEG-002 (de RC-009)
```

El cliente marcó explícitamente que este módulo "necesita un refinamiento importante"
(`RC-008`). Administradores mencionados con acceso a caja: Hernán, Eduardo, Melisa, Noelia
(`RC-009`) — a modelar como usuarios con un rol, nunca como permisos atados al nombre. Ver
[`../../01_Proyecto/stakeholders.md`](../../01_Proyecto/stakeholders.md).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-022`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-022).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).
