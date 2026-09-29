# MOD-001 — Trazabilidad interna

Vista detallada del módulo, complementaria a la matriz global en
[`../../02_Requerimientos/matriz_trazabilidad.md`](../../02_Requerimientos/matriz_trazabilidad.md).
Actualizada el 2026-09-24 para el pase a `LISTO_PARA_VALIDACION`. Los requerimientos del módulo
salen del análisis del pedido general del cliente (sección 18) y de sus respuestas a las
preguntas; la columna `Preguntas` en [`requerimientos.md`](requerimientos.md) da el origen
puntual de cada uno.

| RC | RF | HU | CU | RN | Criterio de aceptación | Implementación | Prueba | Estado |
|---|---|---|---|---|---|---|---|---|
| (análisis) | RF-PAC-001 | HU-PAC-001, HU-PAC-012 | CU-PAC-001 | RN-PAC-001, RN-PAC-002 | HU-PAC-001, HU-PAC-012 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-002 | HU-PAC-002 | CU-PAC-002 | RN-PAC-007 | HU-PAC-002 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-003 | HU-PAC-001 | CU-PAC-001 | RN-PAC-001 | HU-PAC-001 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-004 | HU-PAC-003 | — | RN-PAC-001, RN-PAC-008 | HU-PAC-003 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-005 | HU-PAC-004 | CU-PAC-005 | RN-PAC-005 | HU-PAC-004 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-006 | HU-PAC-005 | — | RN-PAC-005 | HU-PAC-005 | PENDIENTE | PENDIENTE | CONFIRMADO |
| RC-004 | RF-PAC-007 | HU-PAC-006 | CU-PAC-001 | RN-PAC-003 | HU-PAC-006 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-008 | HU-PAC-007 | CU-PAC-001 | RN-PAC-004 | HU-PAC-007 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-009 | HU-PAC-011 | — | RN-PAC-008 | HU-PAC-011 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-010 | HU-PAC-012 | — | RN-PAC-010 | HU-PAC-012 | PENDIENTE | PENDIENTE | CONFIRMADO |
| RC-006 | RF-PAC-011 | HU-PAC-009 | CU-PAC-004 | RN-PAC-007 | HU-PAC-009 | PENDIENTE | PENDIENTE | CONFIRMADO (cliente + médicos) |
| (análisis) | RF-PAC-012 | HU-PAC-008 | CU-PAC-003 | RN-PAC-006 | HU-PAC-008 | PENDIENTE | PENDIENTE | CONFIRMADO — incremento posterior (`DEC-PAC-025`) |
| (análisis) | RF-PAC-013 | HU-PAC-001 | CU-PAC-001 | RN-PAC-002 | HU-PAC-001 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-014 | HU-PAC-002, HU-PAC-009, HU-PAC-010 | CU-PAC-002, CU-PAC-004 | RN-PAC-007 | HU-PAC-002, HU-PAC-004, HU-PAC-005, HU-PAC-010 (permisos) | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-015 | HU-PAC-014 | — | RN-PAC-008 | HU-PAC-003, HU-PAC-014 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-016 | HU-PAC-013 | — | RN-PAC-008 | HU-PAC-013 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-017 | HU-PAC-003, HU-PAC-006, HU-PAC-014 | — | RN-PAC-003, RN-PAC-008 | HU-PAC-006, HU-PAC-014 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-018 | HU-PAC-010 | CU-PAC-004 | RN-PAC-007 | HU-PAC-010 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-019 | HU-PAC-002 | CU-PAC-002 | RN-PAC-009 | HU-PAC-002 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-020 | HU-PAC-015 | — | — | HU-PAC-015 | PENDIENTE | PENDIENTE | CONFIRMADO |
| (análisis) | RF-PAC-021 | HU-PAC-016 | — | — | HU-PAC-016 | PENDIENTE | PENDIENTE | CONFIRMADO |
| CR-001 | RF-PAC-022 | HU-PAC-001 | CU-PAC-001 | — | HU-PAC-001 (CR-001) | PENDIENTE | PENDIENTE | CONFIRMADO |

Regla sin requerimiento propio: `RN-PAC-011` (la solicitud pública no crea fichas,
`Q-PAC-068`) condiciona `RF-PAC-001`/`RF-PAC-003` y se traza en `MOD-033`.

Ninguna fila pasa a `Implementación`/`Prueba` distinto de `PENDIENTE` hasta que el módulo sea
`APROBADO` y entre en `EN_CONSTRUCCION`.
