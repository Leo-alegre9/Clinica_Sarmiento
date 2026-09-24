```text
ID:                          MOD-004
Nombre:                      Diagnósticos
Descripción:                 Registro de diagnósticos asociados a una consulta o evolución del paciente.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-15
Dependencias:                MOD-003 (Consultas), MOD-002 (Historia clínica)
Requerimientos relacionados: (a definir en refinamiento)
```

Candidato a fusionarse con `MOD-003` si en la práctica el diagnóstico no tiene ciclo de vida
propio — ver nota en [`../README.md`](../README.md), sección "Notas de clasificación". Decisión
pendiente hasta el refinamiento formal.

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-004`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-004).
**Importante:** esa ronda cubre solo el costado administrativo/legal, respondible por el
cliente. El contenido clínico de este módulo se releva aparte, directamente con los médicos
(`RC-006`, `INV-004`), no en este cuestionario. El cuestionario concreto para esa
consulta ya está armado en [`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).
Preguntas adicionales (más profundas, incluyendo las clínicas) se agregarán cuando a este
módulo le toque su refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuestas de los médicos (Ronda 1)

`INV-004` se respondió el 2026-09-15. Las decisiones ya confirmadas están en
[`decisiones.md`](decisiones.md): diagnóstico como combinación de código estándar y texto libre,
múltiples diagnósticos activos permitidos, y distinción entre presuntivo y confirmado.
