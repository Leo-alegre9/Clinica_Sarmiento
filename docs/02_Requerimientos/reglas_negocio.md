# Reglas de negocio — índice global

Este archivo indexa las reglas de negocio transversales o que todavía no tienen módulo
asignado en detalle. Las reglas específicas de un módulo viven en
`03_Modulos/MOD-###.../reglas_negocio.md` y se referencian aquí solo por ID cuando cruzan
varios módulos.

## Reglas confirmadas (origen `CLIENTE`)

- **RN-SEG-001** — Los permisos se modelan como `Usuario → Rol → Permisos`; ningún permiso se
  codifica en referencia directa a una persona. *Fuente:* `RC-009`. *Módulos:* `MOD-026`,
  `MOD-027`.
- **RN-CIR-001** — Toda cirugía programada debe generar al menos un recordatorio automático al
  paciente antes de la fecha. Parámetros exactos `PENDIENTE_DEFINICION`. *Fuente:* `RC-002`.
  *Módulos:* `MOD-013`, `MOD-014`.
- **RN-CLI-001** — Ningún cálculo o criterio clínico/oftalmológico se implementa sin
  documentación de referencia validada por un profesional. *Fuente:* `RC-005`, regla general
  del proceso. *Módulos:* `MOD-006` y cualquier módulo con lógica clínica.

## Reglas propuestas (origen `ANÁLISIS`, pendientes de confirmación)

- **RN-DAT-001** — La información clínica, financiera y de auditoría no se elimina
  físicamente; se anula, archiva o versiona. **Confirmada para `MOD-001`** (`RN-PAC-005`,
  2026-09-08: baja siempre lógica; la historia clínica se conserva indefinidamente, `Q-HCL-001`,
  lo que cubre el mínimo legal de 10 años).
  *Módulos:* `MOD-001` (confirmado), `MOD-002`, `MOD-022`, `MOD-028` (propuesta, pendientes de
  confirmar). Ver preguntas correspondientes en cada módulo.
- **RN-ESC-001** (propuesta) — Ninguna regla de negocio debe codificar "oftalmología" donde el
  concepto correcto es "especialidad", salvo que la regla sea intrínsecamente oftalmológica
  (declarado explícitamente en ese caso). *Módulos:* todos los que definan `Profesional`,
  `Consulta`, `Práctica`.

## Reglas por módulo (pendientes de generarse en el refinamiento)

Cuando cada módulo entra en refinamiento formal, sus reglas de negocio (`RN-XXX-###`) se
documentan en su propio `reglas_negocio.md` y se enlazan aquí si tienen alcance transversal.
Ver el inventario en [`../03_Modulos/README.md`](../03_Modulos/README.md).

Para el módulo actualmente en refinamiento, ver
[`../03_Modulos/MOD-001_Pacientes/reglas_negocio.md`](../03_Modulos/MOD-001_Pacientes/reglas_negocio.md).
