```text
ID:                          MOD-002
Nombre:                      Historia Clínica
Descripción:                 Registro longitudinal de la atención de un paciente: consultas, diagnósticos, recetas, estudios y evoluciones asociadas.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-15
Dependencias:                MOD-001 (Pacientes), MOD-003 (Consultas), MOD-015 (Profesionales)
Requerimientos relacionados: RF-HCL-000
```

Módulo identificado en el inventario inicial, sin refinamiento profundo todavía. Se refina
después de `MOD-001 — Pacientes`, siguiendo el flujo de
[`../../00_Gobernanza/README.md`](../../00_Gobernanza/README.md). Ver también
[`RNF-INC-001`](../../02_Requerimientos/requerimientos_no_funcionales.md) (integridad de
información clínica, probablemente aplica directamente aquí).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-002`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-002).
**Importante:** esa ronda cubre solo el costado administrativo/legal, respondible por el
cliente. El contenido clínico de este módulo se releva aparte, directamente con los médicos
(`RC-006`, `INV-004`), no en este cuestionario. El cuestionario concreto para esa
consulta ya está armado en [`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md).
Preguntas adicionales (más profundas, incluyendo las clínicas) se agregarán cuando a este
módulo le toque su refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuestas de los médicos (Ronda 1)

`INV-004` se respondió el 2026-09-15, con aclaraciones cerradas el mismo día. Las decisiones ya
confirmadas están en [`decisiones.md`](decisiones.md): qué ver de entrada en la ficha, resumen
con detalle expandible del historial, aviso destacado para alertas críticas, visibilidad entre
especialidades resuelta caso por caso, y lista de antecedentes/alergias siempre visibles.
