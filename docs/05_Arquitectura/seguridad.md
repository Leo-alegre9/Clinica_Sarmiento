# Seguridad (arquitectura)

Ver también los requisitos no funcionales de seguridad en
[`../02_Requerimientos/requerimientos_no_funcionales.md`](../02_Requerimientos/requerimientos_no_funcionales.md)
(`RNF-SEG-*`, `RNF-PRI-*`, `RNF-AUD-*`).

## Ya implementado (Fase 1)

- Autenticación con Laravel Fortify: registro, verificación de email, 2FA (TOTP), passkeys
  (WebAuthn), confirmación de contraseña, throttling de login.
- Variables sensibles fuera del repositorio (`.env` no versionado).

## Pendiente de diseño

- Modelo de roles y permisos de dominio (`MOD-026`, `MOD-027`) — hoy no existe ningún rol más
  allá del usuario autenticado genérico del Starter Kit.
- Autorización a nivel de Laravel Policies para cada entidad de dominio, a definir cuando cada
  módulo esté aprobado (siguiendo `laravel-best-practices`).
- Auditoría de cambios sobre datos sensibles (`MOD-028`).
- Cifrado de datos sensibles en reposo (si corresponde) — `PENDIENTE_DEFINICION`, depende de
  `ADR-001` y de la política de backups (`INV-006`).
- Protección específica del formulario público de solicitud de turnos (rate limiting, CAPTCHA
  u otro mecanismo anti-abuso) — a definir al refinar `MOD-033`.

No se toma ninguna decisión de seguridad de dominio hasta que el módulo correspondiente esté
refinado.
