```text
ID:                          MOD-016
Nombre:                      Especialidades
Descripción:                 Catálogo de especialidades médicas que un profesional puede ejercer, base de la extensibilidad multiespecialidad.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                —
Requerimientos relacionados: RNF-ESC-001
```

Módulo pequeño pero estructuralmente importante: es la pieza que permite que el sistema no
quede atado a oftalmología. Ver [`../../01_Proyecto/vision.md`](../../01_Proyecto/vision.md).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-016`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-016).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Datos confirmados en la Ronda 3 (2026-09-26)

Los dos médicos que respondieron el cuestionario son de **Oftalmología** (`Q-MED-005`). La
consulta usa un formato común para todas las especialidades, con campos opcionales propios de
oftalmología (`DEC-CON-005`), y cada especialidad ve lo que registra en la historia clínica
(`DEC-HCL-007`).
