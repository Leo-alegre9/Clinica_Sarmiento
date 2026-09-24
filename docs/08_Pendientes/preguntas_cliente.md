# Preguntas para el cliente — resumen ejecutivo

Este archivo resume, para consulta rápida, las preguntas de mayor criticidad dirigidas al
cliente (dueño/interlocutor del proyecto), agrupadas por tema. El detalle completo con motivo,
impacto y formato de respuesta vive en cada módulo (por ahora, solo
[`../03_Modulos/MOD-001_Pacientes/preguntas.md`](../03_Modulos/MOD-001_Pacientes/preguntas.md)).

## Rondas de envío al cliente

- **Ronda 1 — `MOD-001` Pacientes** (enviada 2026-09-03, **respondida completa el 2026-09-08**
  por otro canal, no por el artifact interactivo — el envío parcial del 2026-09-03 en el
  artifact queda superado): las 51 preguntas 🟢 quedaron `RESPONDIDA`. Detalle completo en
  [`../03_Modulos/MOD-001_Pacientes/preguntas.md`](../03_Modulos/MOD-001_Pacientes/preguntas.md)
  y decisiones derivadas en
  [`../03_Modulos/MOD-001_Pacientes/decisiones.md`](../03_Modulos/MOD-001_Pacientes/decisiones.md).
  Dos respuestas resultaron contradictorias entre sí y quedan pendientes de repregunta antes de
  propagarlas (`Q-PAC-013`/`Q-PAC-039` sobre "dar de baja", y `Q-PAC-041` sobre fallecimiento) —
  ver [`decisiones_pendientes.md`](decisiones_pendientes.md) (`DECP-008`, `DECP-009`).
- **Ronda 2 — resto de los módulos que no dependen de las respuestas de `MOD-001`**
  (enviada 2026-09-05, **respondida 2026-09-08**): cubre estructuralmente 38 de los 41 módulos
  del inventario (todos menos `MOD-001`, `MOD-006` y `MOD-038`) en un solo envío, para no
  hacerle al cliente una ronda por módulo. Las 89 preguntas quedaron `RESPONDIDA` — detalle
  completo con cada respuesta en
  [`cuestionario_cliente_ronda_2.md`](cuestionario_cliente_ronda_2.md). Estas respuestas
  resolvieron `DECP-001`, `DECP-004` y `DECP-007`, cerraron `INV-002`/`INV-003` como no
  aplicables, e informaron parcialmente `DECP-003`, `DECP-005`, `DECP-006`, `INV-005`, `INV-006`
  e `INV-007` (ver [`decisiones_pendientes.md`](decisiones_pendientes.md) e
  [`investigaciones.md`](investigaciones.md)). También corrigieron un supuesto del inventario:
  la clínica ya opera **más de una sede** hoy (`Q-SED-001`), no una sola. Quedaron algunos
  puntos ambiguos o contradictorios a repreguntar antes de diseñar los módulos afectados — ver
  la sección "Próximos pasos" de `cuestionario_cliente_ronda_2.md`.
- **Ronda 3 — armada el 2026-09-24, pendiente de envío**:
  [`cuestionario_cliente_ronda_3.md`](cuestionario_cliente_ronda_3.md). 29 preguntas en cuatro
  bloques: cierre de `MOD-001` (propuestas a confirmar, `Q-PAC-054` a `Q-PAC-069`), temas
  diferidos (turno web vs. ficha, obra social por atención, liquidaciones), diferencias entre
  los dos médicos que respondieron, y otros pendientes (quién aprueba, soporte técnico). Tiene
  además un bloque 5 con los documentos a pedir. Las repreguntas que se pensaban incluir acá
  (`DECP-008`, `DECP-009`, `Q-AGE-003`, `Q-CAJ-001`, `Q-INTG-001`) ya se habían aclarado el
  2026-09-08, así que no se repiten.

## Sobre Pacientes (MOD-001) — respondida el 2026-09-08

Las 17 preguntas de criticidad ALTA quedaron `RESPONDIDA` (detalle completo en
[`../03_Modulos/MOD-001_Pacientes/preguntas.md`](../03_Modulos/MOD-001_Pacientes/preguntas.md)).
Dos de ellas — "dar de baja" (`Q-PAC-013`) y qué pasa al fallecer un paciente (`Q-PAC-041`, esta
de criticidad MEDIA) — resultaron contradictorias con otra respuesta y están pendientes de
repregunta antes de tomarse como decisión, ver `DECP-008`/`DECP-009` más abajo.

## Sobre el resto del sistema — ver Ronda 2

Los temas que antes estaban acá como bullets sueltos (`RC-002`, `RC-003`, `RC-004`, `RC-007`,
`RC-008`, `RC-011`, `RC-012`, `RC-013`) ya se formalizaron como preguntas cerradas con ID
propio en [`cuestionario_cliente_ronda_2.md`](cuestionario_cliente_ronda_2.md). Esa ronda se
seguirá profundizando (baterías más exhaustivas, al estilo de `MOD-001`) cuando cada módulo
entre en su refinamiento formal, uno por vez, según
[`../03_Modulos/README.md`](../03_Modulos/README.md).
