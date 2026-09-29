# Riesgos del proyecto (nivel macro)

Los riesgos específicos de cada módulo se documentan en `03_Modulos/MOD-###.../riesgos.md`.
Este archivo cubre riesgos transversales al proyecto completo.

| ID | Riesgo | Probabilidad | Impacto | Mitigación propuesta | Origen |
|---|---|---|---|---|---|
| RIE-001 | Construir módulos antes de validar el alcance con el cliente, generando retrabajo | Media (mitigada por esta misma fase) | Alto | Aplicar estrictamente el flujo de `00_Gobernanza`: nada se construye sin `APROBADO` | ANÁLISIS |
| RIE-002 | Diseñar el modelo de datos/reglas asumiendo un único médico y tener que reescribirlo al incorporar la clínica completa | Media | Alto | Modelar desde el inicio con `Profesional` + `Especialidad` en vez de conceptos rígidos de oftalmología, ver [`vision.md`](vision.md) | ANÁLISIS |
| RIE-003 | Requerimientos incompletos por no haber consultado aún a los demás médicos (`RC-006`) | Alta (confirmado por el propio cliente) | Alto para módulos clínicos | No aprobar módulos clínicos sensibles a la práctica médica sin esa consulta; ver `INV-004` | CLIENTE |
| RIE-004 | Inventar lógica clínica/oftalmológica (fórmulas, prioridades) sin respaldo profesional | Media | Muy alto (riesgo clínico/legal) | Regla dura: nunca inventar cálculos médicos; toda lógica clínica requiere documentación y validación profesional — ver `RC-005`, sección 20 del prompt maestro | CLIENTE |
| RIE-005 | Ambigüedad sobre el modelo de despliegue (web/local/híbrido) retrasa decisiones de arquitectura de datos, backups y seguridad | Media | Medio-Alto | `ADR-001` explícito, `PROPUESTO/PENDIENTE` hasta reunir información suficiente | ANÁLISIS |
| RIE-006 | Diseñar permisos de caja atados a personas (Hernán, Eduardo, Melisa, Noelia) en vez de a roles configurables | Baja (ya identificado y mitigado en `RC-009`) | Medio | Modelo `Usuario → Rol → Permisos` desde el inicio | CLIENTE/ANÁLISIS |
| RIE-007 | Falta de definición sobre backups deja a la clínica sin respaldo de información crítica ante una falla | Media | Muy alto | `INV-006`, `ADR` de backups antes de ir a producción con datos reales | CLIENTE |
| RIE-008 | El formulario público de solicitud de turnos recolecta datos sensibles (motivo de consulta, obra social) sin definir aún consentimiento ni tratamiento de datos | Media | Alto (legal/reputacional) | Resolver `RC-012` con preguntas específicas de privacidad antes de aprobar `MOD-033` | ANÁLISIS |
| RIE-009 | Doble fuente de verdad: este repositorio convive con "la versión anterior" del sistema mencionada en el `README.md` original | Baja-Media | Medio | Confirmar con el cliente si hay datos a migrar y cuándo se desactiva el sistema anterior | ANÁLISIS |
| RIE-010 | Quien aprueba los módulos es la misma persona que los construye (`Q-PRY-001`, 2026-09-26). Sin una revisión independiente de la clínica, un requerimiento mal entendido puede aprobarse y construirse sin que nadie lo detecte | Media | Alto | Mantener las rondas de preguntas al cliente y a los médicos como fuente de las decisiones clínicas, registrar el origen de cada decisión y hacer revisar por la clínica los puntos clínicos sensibles antes de pasar a `VALIDADO` | CLIENTE/ANÁLISIS |
| RIE-011 | Nadie se ocupa hoy de las computadoras ni de la conexión de la clínica (`Q-DEP-003`). Una falla de red o de equipos no tiene a quién recurrir, y un despliegue local no tendría mantenimiento | Alta | Alto | Preferir servicios gestionados en la nube y backups automáticos (`ADR-001`, `INV-005`, `INV-006`) | CLIENTE |

Este listado se revisa cada vez que se cierra una investigación (`INV-###`) o se responde una
pregunta de criticidad ALTA que lo module.
