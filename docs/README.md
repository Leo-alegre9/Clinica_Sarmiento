# Documentación funcional y técnica — Clínica Sarmiento

Esta carpeta es la **fuente oficial de verdad funcional y técnica** del sistema. Ninguna
funcionalidad se construye hasta que su alcance esté suficientemente refinado, documentado y
aprobado aquí. Ver la filosofía completa en
[`01_Proyecto/vision.md`](01_Proyecto/vision.md) y las reglas de proceso en
[`00_Gobernanza/README.md`](00_Gobernanza/README.md).

**Última actualización:** 2026-09-24 — `MOD-001` aprobado y Ronda 3 armada.

## Cómo navegar esta documentación

| Carpeta | Contenido |
|---|---|
| [`00_Gobernanza/`](00_Gobernanza/README.md) | Reglas de esta documentación: convenciones, estados, Definition of Ready, control de cambios |
| [`01_Proyecto/`](01_Proyecto/vision.md) | Visión, objetivos, alcance, stakeholders, glosario, supuestos, restricciones, riesgos |
| [`02_Requerimientos/`](02_Requerimientos/requerimientos_cliente_raw.md) | Requerimientos crudos del cliente, normalizados, no funcionales, reglas de negocio, matriz de trazabilidad |
| [`03_Modulos/`](03_Modulos/README.md) | Inventario de 41 módulos; refinamiento profundo módulo por módulo (`MOD-001 — Pacientes`, aprobado) |
| [`04_Modelado/`](04_Modelado/README.md) | Actores, contexto, procesos de negocio, modelo de dominio, diagramas |
| [`05_Arquitectura/`](05_Arquitectura/README.md) | Requisitos arquitectónicos, integraciones, seguridad, escalabilidad, ADRs |
| [`06_Datos/`](06_Datos/README.md) | Catálogo de datos, datos sensibles, retención, modelo conceptual |
| [`07_QA/`](07_QA/README.md) | Estrategia de pruebas, criterios de aceptación globales, trazabilidad de pruebas |
| [`08_Pendientes/`](08_Pendientes/README.md) | Preguntas al cliente y a los médicos, investigaciones, decisiones y documentos pendientes |
| [`09_Aprobaciones/`](09_Aprobaciones/README.md) | Estado de aprobación de cada módulo (`MOD-001` aprobado) |

## Estado actual del proyecto

- **Fase de código:** Fase 1 completada (base tecnológica Laravel + Inertia + React). Ningún
  módulo de dominio implementado. Ver
  [`../docs/architecture.md`](../docs/architecture.md) y
  [`03_Modulos/README.md`](03_Modulos/README.md) (sección "Hallazgos del sistema actual").
- **Fase de requisitos:** **`MOD-001 — Pacientes`** está **`APROBADO`** desde el
  2026-09-24 (ver [`03_Modulos/MOD-001_Pacientes/README.md`](03_Modulos/MOD-001_Pacientes/README.md)).
  Respondieron la Ronda 1 y la Ronda 2 del cliente y la Ronda 1 de médicos (Cecilia Portillo
  Rivero y Eduardo Peña). La **Ronda 3** para el cliente está armada y pendiente de envío:
  [`08_Pendientes/cuestionario_cliente_ronda_3.md`](08_Pendientes/cuestionario_cliente_ronda_3.md).
- **Módulos aprobados:** `MOD-001` (2026-09-24). Ver
  [`09_Aprobaciones/modulos_aprobados.md`](09_Aprobaciones/modulos_aprobados.md).
- **Investigaciones abiertas:** `INV-002`, `INV-003` (reabierta), `INV-005`, `INV-006` e
  `INV-007`. Ver [`08_Pendientes/investigaciones.md`](08_Pendientes/investigaciones.md).

## Regla de oro

> Preguntar antes que asumir. Documentar antes que implementar. Validar antes que construir.

Ningún estado `APROBADO` se asigna sin instrucción explícita del usuario confirmando validación
con el cliente. Ver
[`00_Gobernanza/estados_requerimientos.md`](00_Gobernanza/estados_requerimientos.md).
