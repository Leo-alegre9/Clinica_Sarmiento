```text
ID:                          MOD-027
Nombre:                      Roles y permisos
Descripción:                 Modelo Usuario → Rol → Permisos, configurable, para controlar el acceso a funcionalidades (incluida caja e historia clínica).
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-026 (Usuarios)
Requerimientos relacionados: RF-SEG-001, RF-SEG-002, RN-SEG-001
```

Regla dura ya fijada por el cliente: los permisos **no** se codifican alrededor de nombres
personales (Hernán, Eduardo, Melisa, Noelia son usuarios iniciales, no el diseño de permisos).
Ver `RC-009` y [`../../01_Proyecto/stakeholders.md`](../../01_Proyecto/stakeholders.md).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-027`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-027).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Datos confirmados en la Ronda 3 (2026-09-26)

- Una misma persona puede ser médico y administrador: Eduardo Peña es oftalmólogo y tiene acceso a
  caja (`Q-MED-005`). Un usuario tiene que poder tener **varios roles**.
- "Dar de baja pacientes" para médicos y "perfil directivo designado" son permisos que Dirección
  asigna (`Q-PAC-059`, `Q-PAC-061`, `MOD-001`).
