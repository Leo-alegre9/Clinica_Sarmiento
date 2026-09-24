```text
ID:                          MOD-037
Nombre:                      Backups
Descripción:                 Respaldo y recuperación de la información del sistema (qué se respalda, frecuencia, retención, cifrado, restauración, responsables).
Estado:                      IDENTIFICADO — BLOQUEADO por investigación/decisión
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                ADR-001 (modelo de despliegue)
Requerimientos relacionados: RNF-BCK-001 (de RC-011)
```

Riesgo alto marcado en [`../../01_Proyecto/riesgos.md`](../../01_Proyecto/riesgos.md)
(`RIE-007`): sin backup definido, la clínica queda expuesta a pérdida de información crítica.
No puede definirse completamente hasta resolver [`ADR-001`](../../05_Arquitectura/ADR/ADR-001-web-vs-local-vs-hibrido.md)
y [`INV-006`](../../08_Pendientes/investigaciones.md).

## Preguntas para el cliente — insumo de negocio para destrabar `ADR-001`/`INV-006`

El módulo sigue bloqueado (la decisión en sí es técnica), pero se incluyeron en el envío
conjunto de la Ronda 2 las preguntas de negocio que hacen falta para poder tomar esa decisión:
qué tan grave sería una caída o pérdida de información (`Q-BCK-001`), presupuesto disponible
para hosting recurrente vs. equipo propio (`Q-BCK-002`), y dos preguntas transversales de
infraestructura para `ADR-001` (`Q-DEP-001`, `Q-DEP-002`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-037`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-037).
