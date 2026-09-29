# Inventario de módulos

Cada módulo tiene su propia carpeta `MOD-###_Nombre/` con un `README.md` que fija su estado
(ver [`../00_Gobernanza/estados_requerimientos.md`](../00_Gobernanza/estados_requerimientos.md)).
Esta página es el índice general y el punto de entrada para decidir qué se refina a
continuación.

**Regla de proceso:** el refinamiento profundo (`EN_REFINAMIENTO`: flujos, reglas de negocio,
casos de uso, criterios de aceptación completos) ocurre **de a un módulo por vez**, y
`MOD-001 — Pacientes` es el primero por decisión del cliente. Eso no impide que otros módulos
entren en `EN_DESCUBRIMIENTO` (relevar preguntas estructurales, sin refinamiento profundo
todavía) en paralelo, para poder juntar en un solo envío todo lo que el cliente puede
responder sin esperar a que le toque el turno de cada módulo. Así avanzó la
[Ronda 2](../08_Pendientes/cuestionario_cliente_ronda_2.md) (2026-09-05): pasaron a
`EN_DESCUBRIMIENTO` todos los módulos cuyas preguntas no dependen de las respuestas —todavía
pendientes— de `MOD-001`. Quedan en `IDENTIFICADO`: `MOD-006` y `MOD-037` (bloqueados por
investigaciones, ver tabla de investigaciones en
[`../08_Pendientes/investigaciones.md`](../08_Pendientes/investigaciones.md)) y `MOD-038`
(decisión puramente técnica, sin pregunta al cliente).

## Hallazgos del sistema actual (auditoría del repositorio, 2026-09-02)

El repositorio, a la fecha, contiene **exclusivamente la Fase 1** (base tecnológica): Laravel
13 + Inertia + React + TypeScript + Tailwind + shadcn/ui, con autenticación Fortify del
Starter Kit oficial (`app/Models/User.php`, `app/Actions/Fortify`, rutas de
`settings/profile`, `settings/security`, `settings/appearance`, passkeys, 2FA). Ver
[`../../docs/architecture.md`](../../docs/architecture.md).

**No existe ningún módulo de dominio clínico o administrativo implementado**: no hay modelos,
migraciones, controladores ni páginas de Pacientes, Turnos, Agenda, Cirugías, Historia
Clínica, Obras Sociales, Caja, ni Roles/Permisos de negocio. La única tabla de usuarios es la
de autenticación estándar del Starter Kit, sin rol de dominio.

| Elemento | Clasificación |
|---|---|
| Autenticación (registro, login, 2FA, passkeys, verificación de email) | `IMPLEMENTADO_SIN_VALIDACION` — funciona (39 tests pasando en Fase 1) pero no fue validado como parte de un flujo de negocio de la clínica (p. ej. no hay roles clínicos todavía) |
| Perfil de usuario / seguridad / apariencia (`settings/*`) | `IMPLEMENTADO_SIN_VALIDACION` — genérico del starter kit |
| Todo lo demás (pacientes, agenda, turnos, cirugías, historia clínica, obras sociales, caja, roles de negocio, notificaciones, portal público) | `NO_IMPLEMENTADO` |
| Roadmap de fases del `README.md` original (Fase 2 PostgreSQL … Fase 15 Producción) | `PLANIFICADO` — es un plan previo a esta fase de requisitos; **no vincula** el orden de construcción real, que ahora depende de la aprobación módulo por módulo |

No se detectaron inconsistencias entre código y requerimientos porque no hay código de
dominio que contrastar todavía. La única observación es que el `README.md` raíz describe un
roadmap fase-por-fase construido *antes* de este proceso de descubrimiento, por lo que su
orden de fases (Pacientes → Turnos → Consulta → Historia clínica → Recetas → …) debe tratarse
como una **hipótesis de priorización**, no como un compromiso, hasta que el cliente confirme
el orden real que quiere construir.

## Notas de clasificación del inventario

La lista de 41 módulos de partida (sección 8 del pedido del cliente) se mantiene sin fusionar
ni eliminar módulos todavía, para no perder trazabilidad con el pedido original. Se marcan
aquí candidatos a revisión futura, a decidir durante el refinamiento de cada uno:

- `MOD-020` (Planes/coberturas/afiliaciones) y `MOD-021` (Autorizaciones) podrían terminar
  siendo secciones de `MOD-019` (Obras sociales) en lugar de módulos independientes — depende
  de cuánta complejidad tenga la autorización de prácticas. Más probable desde el 2026-09-26: el
  alcance de obras sociales es solo registro, sin liquidaciones (`Q-OSO-005`).
- `MOD-004` (Diagnósticos) podría integrarse a `MOD-003` (Consultas médicas) si en la práctica
  el diagnóstico siempre se registra dentro de la consulta y no tiene ciclo de vida propio.
- `MOD-018` (Sedes) **sí requiere un módulo propio**: el cliente confirmó que la clínica ya
  opera más de una sede hoy y planea abrir otra en 1-2 años (`Q-SED-001`, `Q-SED-002`, Ronda 2,
  2026-09-08). Descartada la hipótesis de sede única.
- `MOD-033`/`MOD-034`/`MOD-035` (portal público) están muy acoplados entre sí y podrían
  documentarse como un único módulo "Portal público de turnos" con tres sub-flujos.

Ninguna fusión se aplica todavía: se decide al refinar cada módulo, con el cliente.

## Inventario

| ID | Nombre | Estado | Prioridad tentativa | Dependencias principales |
|---|---|---|---|---|
| MOD-001 | Pacientes | **APROBADO** (2026-09-24, Leonel Alegre) — hipótesis confirmadas en la Ronda 3 (2026-09-26); `CR-001` agrega "derivado por"; unificación de duplicados en un incremento posterior | Alta | MOD-019 (obra social), MOD-026 (usuarios) |
| MOD-002 | Historia Clínica | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Alta | MOD-001, MOD-015, MOD-003 |
| MOD-003 | Consultas Médicas | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Alta | MOD-001, MOD-009, MOD-015 |
| MOD-004 | Diagnósticos | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Media | MOD-003, MOD-002 |
| MOD-005 | Recetas / Prescripciones | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Media | MOD-001, MOD-003, MOD-015 |
| MOD-006 | Fórmulas Oftalmológicas | IDENTIFICADO — bloqueado por INV-001/002/003; confirmado 2026-09-15 que la clínica sí usa Treelan (contradice y desactualiza `Q-FOR-002` del cliente); el 2026-09-26 se confirmó que todos usan Treelan y Ampina (`Q-FOR-007`). Falta acceso/documentación de ambas para avanzar (de Ampina llegará un PDF) | Media | MOD-001, MOD-003 |
| MOD-007 | Estudios / Resultados / Documentación clínica | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Media | MOD-001, MOD-002 |
| MOD-008 | Evoluciones / Seguimiento del paciente | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Media | MOD-002, MOD-003 |
| MOD-009 | Agenda Médica | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Alta | MOD-015, MOD-017 |
| MOD-010 | Turnos | EN_DESCUBRIMIENTO | Alta | MOD-001, MOD-009, MOD-015 |
| MOD-011 | Recepción / Check-in | EN_DESCUBRIMIENTO | Alta | MOD-010 |
| MOD-012 | Sala de espera / Cola de atención / Prioridades | EN_DESCUBRIMIENTO | Media | MOD-011 |
| MOD-013 | Cirugías | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`); agenda quirúrgica confirmada como parte de este módulo (`INV-008`, resuelta) | Alta | MOD-001, MOD-015, MOD-014 |
| MOD-014 | Recordatorios y confirmaciones | EN_DESCUBRIMIENTO | Alta | MOD-010, MOD-013, MOD-029 |
| MOD-015 | Médicos / Profesionales | EN_DESCUBRIMIENTO | Alta | MOD-016, MOD-026 |
| MOD-016 | Especialidades | EN_DESCUBRIMIENTO | Alta | — |
| MOD-017 | Consultorios | EN_DESCUBRIMIENTO | Media | MOD-018 |
| MOD-018 | Sedes | EN_DESCUBRIMIENTO | **Media** — la clínica ya opera más de una sede hoy, no una sola (`Q-SED-001`, Ronda 2, 2026-09-08); prioridad corregida desde "Baja (hoy 1 sede)" | — |
| MOD-019 | Obras sociales | EN_DESCUBRIMIENTO — alcance: solo registro, sin liquidaciones (`Q-OSO-005`, 2026-09-26) | Alta | MOD-001 |
| MOD-020 | Planes / coberturas / afiliaciones | EN_DESCUBRIMIENTO | Media | MOD-019 |
| MOD-021 | Autorizaciones | EN_DESCUBRIMIENTO | Baja/Media | MOD-019, MOD-020 |
| MOD-022 | Caja | EN_DESCUBRIMIENTO | Alta | MOD-026, MOD-027 |
| MOD-023 | Pagos | EN_DESCUBRIMIENTO | Alta | MOD-022 |
| MOD-024 | Gastos / Egresos | EN_DESCUBRIMIENTO | Media | MOD-022 |
| MOD-025 | Reportes administrativos | EN_DESCUBRIMIENTO | Baja | MOD-022, MOD-023, MOD-024 |
| MOD-026 | Usuarios | EN_DESCUBRIMIENTO | Alta | — |
| MOD-027 | Roles y permisos | EN_DESCUBRIMIENTO | Alta | MOD-026 |
| MOD-028 | Auditoría | EN_DESCUBRIMIENTO | Media | MOD-026 |
| MOD-029 | Notificaciones | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Media | MOD-030, MOD-031 |
| MOD-030 | WhatsApp / mensajería | EN_DESCUBRIMIENTO | Media | MOD-029 |
| MOD-031 | Email | EN_DESCUBRIMIENTO | Media | MOD-029 |
| MOD-032 | Plantillas de comunicación | EN_DESCUBRIMIENTO | Baja | MOD-029 |
| MOD-033 | Solicitud pública de turnos | EN_DESCUBRIMIENTO | Alta | MOD-010, MOD-034 |
| MOD-034 | Disponibilidad pública | EN_DESCUBRIMIENTO | Alta | MOD-009 |
| MOD-035 | Confirmación / seguimiento de solicitudes | EN_DESCUBRIMIENTO | Media | MOD-033 |
| MOD-036 | Configuración general | EN_DESCUBRIMIENTO | Baja | — |
| MOD-037 | Backups | IDENTIFICADO — bloqueado por INV-006 | Alta (riesgo) | ADR-001 |
| MOD-038 | Logs y monitoreo | IDENTIFICADO | Media | — |
| MOD-039 | Integraciones externas | EN_DESCUBRIMIENTO | Baja | — |
| MOD-040 | Importación / exportación | EN_DESCUBRIMIENTO | Baja | — |
| MOD-041 | Reportes y estadísticas | EN_DESCUBRIMIENTO — respuestas de médicos incorporadas 2026-09-15 (`INV-004`) | Baja | Varios |

## Códigos de dominio (para IDs `RF-XXX`, `RN-XXX`, `HU-XXX`, `CU-XXX`, `Q-XXX`)

| Código | Módulo(s) |
|---|---|
| PAC | MOD-001 |
| HCL | MOD-002 |
| CON | MOD-003 |
| DIA | MOD-004 |
| RET | MOD-005 (Recetas) |
| FOR | MOD-006 |
| EST | MOD-007 |
| EVO | MOD-008 |
| AGE | MOD-009 |
| TUR | MOD-010 |
| REC | MOD-011 (Recepción) |
| ESP | MOD-012 (Espera) |
| CIR | MOD-013 |
| RCD | MOD-014 (Recordatorios) |
| MED | MOD-015 |
| ESPC | MOD-016 (Especialidad) — evitar confundir con ESP; usar `ESC` si se necesita distinguir |
| CTO | MOD-017 (Consultorio) |
| SED | MOD-018 |
| OSO | MOD-019 |
| PLA | MOD-020 |
| AUT | MOD-021 |
| CAJ | MOD-022 |
| PAG | MOD-023 |
| GAS | MOD-024 |
| RAD | MOD-025 (Reportes administrativos) |
| USR | MOD-026 |
| ROL | MOD-027 |
| AUD | MOD-028 |
| NOT | MOD-029 |
| WHA | MOD-030 |
| MAI | MOD-031 |
| PLT | MOD-032 |
| PUB | MOD-033 |
| DIS | MOD-034 |
| SEG (seguimiento solicitud) | MOD-035 — cuidado: no confundir con `RNF-SEG` (seguridad); usar `SOL` |
| CFG | MOD-036 |
| BCK | MOD-037 |
| LOG | MOD-038 |
| INTG | MOD-039 |
| IMP | MOD-040 |
| RES | MOD-041 (Reportes/estadísticas) |

Ver también [`../00_Gobernanza/convenciones.md`](../00_Gobernanza/convenciones.md).
