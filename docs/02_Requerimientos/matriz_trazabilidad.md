# Matriz de trazabilidad

Trazabilidad de extremo a extremo: `Requerimiento cliente → RF → Módulo → HU → CU → RN →
Criterio de aceptación → Implementación → Prueba → Estado`.

Durante esta fase, `Implementación` y `Prueba` permanecen en `PENDIENTE` para todo lo que no
esté construido — hoy, todo el dominio clínico/administrativo. Se completan según
[`../00_Gobernanza/definition_of_done_documental.md`](../00_Gobernanza/definition_of_done_documental.md).

| Req. Cliente | RF | Módulo | HU | CU | RN | Criterio de aceptación | Implementación | Prueba | Estado |
|---|---|---|---|---|---|---|---|---|---|
| RC-001 | RF-AGE-001 | MOD-009 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-002 | RF-CIR-001 | MOD-013 | — | — | RN-CIR-001 | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-002 | RF-CIR-002 | MOD-014 | — | — | RN-CIR-001 | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-003 | RF-PUB-001 | MOD-034 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-003 | RF-PUB-002 | MOD-033 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-004 | RF-OSO-001 | MOD-019 / MOD-020 / MOD-021 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-005 | RF-FOR-001 | MOD-006 | — | — | RN-CLI-001 | — | PENDIENTE | PENDIENTE | IDENTIFICADO — bloqueado por INV-001/002/003 |
| RC-006 | (proceso) | — (todos los clínicos) | — | — | — | — | — | — | ABIERTO — ver INV-004 |
| RC-007 | RF-REC-001 | MOD-011 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-007 | RF-ESP-001 | MOD-012 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-008 | RF-CAJ-001 | MOD-022 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-008 | RF-CAJ-002 | MOD-022 / MOD-023 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-008 | RF-CAJ-003 | MOD-024 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-009 | RF-SEG-001 | MOD-026 / MOD-027 | — | — | RN-SEG-001 | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-009 | RF-SEG-002 | MOD-027 / MOD-022 | — | — | RN-SEG-001 | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-010 | (info pendiente) | MOD-015 | — | — | — | — | — | — | ABIERTO — ver documentos_pendientes.md |
| RC-011 | RNF-BCK-001 | MOD-037 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO — bloqueado por INV-006 |
| RC-012 | RF-PUB-003 | MOD-033 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| RC-013 | (ADR) | — | — | — | — | — | — | — | ADR-001 PROPUESTO/PENDIENTE |
| (análisis) | RF-PAC-001 a RF-PAC-022 (RF-PAC-022 por CR-001) | MOD-001 | HU-PAC-001 a HU-PAC-016 | CU-PAC-001 a CU-PAC-005 | RN-PAC-001 a RN-PAC-011 | Ver `03_Modulos/MOD-001_Pacientes/criterios_aceptacion.md` | PENDIENTE | PENDIENTE | CONFIRMADO — módulo `APROBADO` (2026-09-24). Detalle completo en `03_Modulos/MOD-001_Pacientes/trazabilidad.md`. `RF-PAC-012`/`RN-PAC-006` (unificación) y `RN-PAC-011` siguen `PROPUESTO` |
| (análisis) | RF-HCL-000 | MOD-002 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| (análisis) | RF-CON-000 | MOD-003 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| (análisis) | RF-REC-000 | MOD-005 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |
| (análisis) | RF-MED-000 | MOD-015 / MOD-016 | — | — | — | — | PENDIENTE | PENDIENTE | IDENTIFICADO |

Esta tabla crece con cada iteración de refinamiento. Cuando `MOD-001` produzca sus HU/CU/RN,
esta fila se desagrega en varias filas (una por HU relevante) en lugar de mantenerse resumida.
