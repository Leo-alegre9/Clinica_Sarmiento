```text
ID:                          MOD-033
Nombre:                      Solicitud pública de turnos
Descripción:                 Formulario público (página institucional) para que un paciente solicite un turno, con modelo de confirmación a definir.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-010 (Turnos), MOD-034 (Disponibilidad pública)
Requerimientos relacionados: RF-PUB-002, RF-PUB-003 (de RC-003, RC-012)
```

Decisión pendiente crítica (`RC-003`): reserva automática (Alternativa A) vs. solicitud con
confirmación manual de secretaría (Alternativa B). Recolecta datos potencialmente sensibles
(motivo de consulta, obra social) — ver `RIE-008` en
[`../../01_Proyecto/riesgos.md`](../../01_Proyecto/riesgos.md).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-033`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-033).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuesta de la Ronda 3 (2026-09-26)

`Q-PAC-068` confirmó `RN-PAC-011` de `MOD-001`: la solicitud web o por WhatsApp **no crea ni
modifica fichas**. Si el DNI existe, el turno se vincula a esa ficha y recepción revisa las
diferencias; si no existe, el turno queda con datos provisorios y la ficha completa se hace en
recepción.
