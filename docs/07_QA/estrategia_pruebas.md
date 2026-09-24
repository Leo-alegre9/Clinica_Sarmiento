# Estrategia de pruebas

## Marco ya vigente (Fase 1)

El proyecto usa PHPUnit (compatible con Pest, ver `phpunit.xml` y `composer.json`) para tests
de backend, con la convención `php artisan test` / `vendor/bin/phpunit`. Ver la skill
`testing-best-practices` (`.claude/skills/testing-best-practices/`) para lineamientos de
cobertura, nombrado, estructura y aislamiento de dependencias — se aplica a todo módulo cuando
entre en construcción.

## Principio para esta fase

No se escriben pruebas de módulos de dominio todavía: no hay código que probar. La estrategia
de pruebas de cada módulo se documenta cuando el módulo entra en `EN_CONSTRUCCION`, derivada de
sus criterios de aceptación (`criterios_aceptacion.md` del módulo).

## Cómo se conecta con la documentación funcional

Cada historia de usuario con criterios de aceptación Given/When/Then (ver
[`criterios_aceptacion_globales.md`](criterios_aceptacion_globales.md)) debe poder traducirse a
uno o más tests de feature. La columna `Prueba` de
[`../02_Requerimientos/matriz_trazabilidad.md`](../02_Requerimientos/matriz_trazabilidad.md) y
de `trazabilidad.md` de cada módulo registra qué test cubre qué criterio, una vez que exista.

## Áreas que ya se anticipan como críticas (a confirmar por módulo)

- Autenticación y autorización (roles y permisos) — origen `MOD-026`/`MOD-027`.
- Unicidad e integridad de pacientes (duplicados, fusión) — origen `MOD-001`.
- Reglas de caja (apertura/cierre, diferencias) — origen `MOD-022`.
- Reglas de negocio clínicas u oftalmológicas, una vez validadas — origen `MOD-006`.
