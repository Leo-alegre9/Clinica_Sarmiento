```text
ID:                          MOD-030
Nombre:                      WhatsApp / mensajería
Descripción:                 Canal de comunicación por WhatsApp u otra mensajería para recordatorios y confirmaciones.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-029 (Notificaciones)
Requerimientos relacionados: RF-CIR-002
```

**Integración confirmada (2026-09-08):** el cliente decide migrar el número general de WhatsApp
de la clínica a la **WhatsApp Business Platform (Cloud API)** — necesaria tanto para automatizar
recordatorios (`Q-NOT-001`) como para el agendamiento de turnos por WhatsApp pedido
explícitamente por el cliente (ver [`../../08_Pendientes/anexos/sistema_nuevo.pdf`](../../08_Pendientes/anexos/sistema_nuevo.pdf),
punto 1). Uso manual de números individuales por administrador queda como canal aparte, no
sustituye la API. Ver [`../../08_Pendientes/decisiones_pendientes.md`](../../08_Pendientes/decisiones_pendientes.md)
(`DECP-007`). Proveedor/BSP concreto todavía `PENDIENTE_DEFINICION` (decisión técnica del
equipo, no requiere pregunta al cliente).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-030`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-030).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).
