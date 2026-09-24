```text
ID:                          MOD-007
Nombre:                      Estudios / Resultados / Documentación clínica
Descripción:                 Registro de estudios solicitados/realizados, resultados, imágenes y documentación adjunta del paciente.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-15
Dependencias:                MOD-001 (Pacientes), MOD-002 (Historia clínica)
Requerimientos relacionados: (a definir en refinamiento)
```

Módulo identificado en el inventario inicial, sin refinamiento profundo todavía. Probablemente
comparte reglas de almacenamiento seguro de archivos con `MOD-001` (fotografías/documentación
del paciente).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-007`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-007).
**Importante:** esa ronda cubre solo el costado administrativo/legal, respondible por el
cliente. El contenido clínico de este módulo se releva aparte, directamente con los médicos
(`RC-006`, `INV-004`), no en este cuestionario. El cuestionario concreto para esa
consulta ya está armado en [`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).
Preguntas adicionales (más profundas, incluyendo las clínicas) se agregarán cuando a este
módulo le toque su refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuestas de los médicos (Ronda 1)

`INV-004` se respondió el 2026-09-15. Las decisiones ya confirmadas están en
[`decisiones.md`](decisiones.md): estudios más frecuentes (OCT, retinografía, campo visual, IOL)
y necesidad de poder comentar/interpretar un resultado dentro del sistema, no solo adjuntarlo.
