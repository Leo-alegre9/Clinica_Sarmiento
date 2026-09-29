```text
ID:                          MOD-009
Nombre:                      Agenda Médica
Descripción:                 Gestión de la disponibilidad horaria de cada profesional (agenda diaria de consultas), base para el módulo de Turnos.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-15
Dependencias:                MOD-015 (Profesionales), MOD-017 (Consultorios)
Requerimientos relacionados: RF-AGE-001 (de RC-001)
```

Módulo identificado en el inventario inicial, sin refinamiento profundo todavía. Distinto de
`MOD-013 — Cirugías`, que requiere una agenda separada según `RC-002`.

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-009`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-009).
Además, cómo necesita ver su propia agenda el profesional (qué datos, si necesita ver la de
otros) se releva con los médicos, no con el cliente — ver
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuestas de los médicos (Ronda 1)

`INV-004` se respondió el 2026-09-15. Las decisiones ya confirmadas están en
[`decisiones.md`](decisiones.md): qué datos necesita ver el profesional en su agenda (motivo de
consulta, obra social) y que solo necesita ver la propia, no la de otros. El pedido de "agenda
quirúrgica" separada (`INV-008`) se resolvió como una extensión de `MOD-013`, no afecta el
alcance de este módulo.
