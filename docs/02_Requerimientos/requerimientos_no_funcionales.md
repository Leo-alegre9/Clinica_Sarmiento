# Requisitos no funcionales

Origen: `ANÁLISIS`, salvo donde se indique `CLIENTE`. Ninguno de estos requisitos tiene
parámetros concretos confirmados todavía (p. ej. tiempos de respuesta, RTO/RPO de backup):
figuran como marco a completar durante el refinamiento de cada módulo y de
[`../05_Arquitectura`](../05_Arquitectura/requisitos_arquitectonicos.md).

## Seguridad — `RNF-SEG-###`

- **RNF-SEG-001** — Toda credencial de acceso debe manejarse mediante autenticación segura
  (ya cubierto en Fase 1 por Laravel Fortify: registro, verificación de email, 2FA, passkeys).
  *Estado:* CONFIRMADO (implementado en Fase 1, sin roles de dominio todavía).
- **RNF-SEG-002** — El acceso a información clínica y financiera debe estar controlado por
  roles y permisos configurables, no por pertenencia a un grupo fijo de personas. Origen:
  `CLIENTE` (`RC-009`). *Estado:* PROPUESTO.
- **RNF-SEG-003** — Las contraseñas, credenciales, tokens y archivos `.env` nunca deben
  versionarse en el repositorio (ya respetado). *Estado:* CONFIRMADO.

## Privacidad — `RNF-PRI-###`

- **RNF-PRI-001** — Los datos personales y clínicos de pacientes deben tratarse conforme a
  normativa de protección de datos aplicable (a confirmar alcance legal exacto). *Estado:*
  PENDIENTE_DEFINICION.
- **RNF-PRI-002** — Debe poder restringirse por rol quién visualiza historia clínica completa
  frente a quién solo ve datos administrativos (turno, contacto). *Estado:* **DESCARTADO para
  `MOD-001`** (2026-09-08) — el cliente decidió explícitamente que todo el personal autenticado
  ve todos los datos del paciente por igual, sin distinción administrativo/clínico (`Q-PAC-036`,
  `Q-PAC-038`). Queda como riesgo aceptado, no como pendiente de definición — ver
  `RIE-PAC-004` en `03_Modulos/MOD-001_Pacientes/riesgos.md`. Sigue `PROPUESTO` para otros
  módulos que aún no lo preguntaron.

## Auditoría — `RNF-AUD-###`

- **RNF-AUD-001** — Los cambios sobre datos sensibles (historia clínica, caja, datos de
  paciente) deben quedar auditados: usuario, fecha/hora, valor anterior, valor nuevo. **Para
  `MOD-001` el alcance es aún más amplio**: el cliente confirmó auditar **todos** los cambios
  sobre la ficha del paciente, no solo los sensibles (`Q-PAC-040`, `RN-PAC-008`, 2026-09-08).
  *Estado:* CONFIRMADO para `MOD-001`, PROPUESTO para el resto. *Módulo:* `MOD-028`.

## Disponibilidad — `RNF-DIS-###`

- **RNF-DIS-001** — El sistema debe estar disponible durante el horario de atención de la
  clínica. Ventana horaria exacta y tolerancia a caídas `PENDIENTE_DEFINICION` (depende de
  `ADR-001`). *Estado:* PENDIENTE_DEFINICION.
- **RNF-DIS-002** — Debe definirse el comportamiento del sistema ante una caída de conexión a
  Internet (si el modelo de despliegue es web). *Estado:* PENDIENTE_DEFINICION. Ver
  `ADR-001`.

## Rendimiento — `RNF-PER-###`

- **RNF-PER-001** — Las operaciones de agenda/turnos y caja, al ser de uso diario intensivo en
  recepción, deben responder en tiempos que no interrumpan la atención presencial. Umbral
  concreto `PENDIENTE_DEFINICION`.

## Usabilidad y accesibilidad — `RNF-USA-###`

- **RNF-USA-001** — El personal de recepción/administración (no necesariamente técnico) debe
  poder operar el sistema sin capacitación extensa. Criterio de aceptación concreto
  `PENDIENTE_DEFINICION`.
- **RNF-USA-002** — El formulario público de solicitud de turnos debe ser utilizable por
  pacientes sin asistencia, incluyendo adultos mayores. `PENDIENTE_DEFINICION` en cuanto a
  estándar de accesibilidad exigido (p. ej. WCAG).

## Mantenibilidad — `RNF-MAN-###`

- **RNF-MAN-001** — El código debe seguir las convenciones ya fijadas para el proyecto
  (`laravel-best-practices`, `testing-best-practices`, resto de skills en `.claude/skills`).
  *Estado:* CONFIRMADO como práctica de desarrollo.

## Escalabilidad — `RNF-ESC-###`

- **RNF-ESC-001** — El modelo de datos y funcional debe permitir agregar especialidades,
  profesionales, sedes y tipos de práctica sin rediseño estructural. Origen: `CLIENTE` (sección
  3 del pedido) + `ANÁLISIS`. *Estado:* PROPUESTO, principio rector de diseño.

## Interoperabilidad — `RNF-INT-###`

- **RNF-INT-001** — El sistema debe poder integrarse en el futuro con canales de comunicación
  externos (WhatsApp, email) y potencialmente con sistemas de obras sociales.
  `PENDIENTE_DEFINICION` en cuanto a integraciones concretas.

## Backups y recuperación — `RNF-BCK-###`

- **RNF-BCK-001** — Ver `RF`/`RNF` derivado de `RC-011`, arriba. Alcance, frecuencia,
  retención, cifrado, restauración, responsables: todos `PENDIENTE_DEFINICION`. Ver
  `INV-006` y futuro `MOD-037`.

## Trazabilidad / logging — `RNF-LOG-###`

- **RNF-LOG-001** — Deben registrarse logs de operación suficientes para diagnosticar
  incidentes y sostener la auditoría de `RNF-AUD-001`. *Módulo:* `MOD-038`.

## Integridad de información clínica — `RNF-INC-###`

- **RNF-INC-001** — La información clínica no debe permitir eliminación física sin control;
  se prioriza baja lógica/anulación/versionado sobre borrado irreversible (ver sección 25 del
  pedido del cliente). Aplica en particular a `MOD-001`, `MOD-002`, `MOD-022`.
  *Estado:* **CONFIRMADO para `MOD-001`** (`RN-PAC-005`, 2026-09-08), PROPUESTO pendiente de
  confirmar caso por caso en el resto.
