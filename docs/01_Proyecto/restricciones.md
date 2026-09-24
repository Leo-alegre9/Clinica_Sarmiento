# Restricciones

## Restricciones técnicas confirmadas (Fase 1, ya implementada)

Origen: `REQUISITO TÉCNICO` / `CLIENTE` (decisiones ya tomadas y ejecutadas). Ver
[`../../docs/architecture.md`](../../docs/architecture.md).

- Stack fijado: Laravel 13 (PHP 8.4) + Inertia.js v3 + React 19 + TypeScript + Tailwind CSS 4 +
  shadcn/ui + Vite. No cambiar durante esta fase de requisitos.
- Autenticación provista por Laravel Fortify (Starter Kit oficial), sin roles/permisos de
  dominio todavía.
- Base de datos actual: SQLite, marcada explícitamente como temporal. PostgreSQL está previsto
  pero no decidido en cuanto a cronograma dentro de esta fase de requisitos.
- Entorno local servido por Laravel Herd (`http://clinica-sarmiento.test`), Windows.
- No se han incorporado Docker, Redis ni Nginx todavía (estaban en el roadmap previo del
  `README.md`, pero no forman parte de la Fase 1 completada).

## Restricciones organizativas

- No se puede construir ningún módulo de dominio hasta que esté `APROBADO` según
  [`../00_Gobernanza/definition_of_ready.md`](../00_Gobernanza/definition_of_ready.md).
- El estado `APROBADO` requiere validación humana explícita; un agente de IA no puede
  otorgarlo.
- Las necesidades de los médicos aparte del interlocutor actual todavía no fueron relevadas
  (`RC-006`), lo que restringe el refinamiento completo de todo módulo clínico hasta tener esa
  información.

## Restricciones legales / regulatorias (a investigar — no asumir)

Origen: `ANÁLISIS`, pendiente de confirmación legal. El sistema maneja información clínica y
financiera de personas, lo que en Argentina típicamente involucra:

- Ley 25.326 de Protección de Datos Personales.
- Normativa de historia clínica (Ley 26.529 y modificatorias) en cuanto a conservación,
  acceso y confidencialidad.
- Posibles requisitos de facturación/AFIP si el módulo de Caja emite comprobantes fiscales.

Ninguno de estos puntos fue confirmado por el cliente todavía. Se listan como
`PENDIENTE_DEFINICION` y como investigación en
[`../08_Pendientes/investigaciones.md`](../08_Pendientes/investigaciones.md).

## Restricciones de tiempo/presupuesto

No se recibió información sobre plazos ni presupuesto del proyecto. `PENDIENTE_DEFINICION`.
