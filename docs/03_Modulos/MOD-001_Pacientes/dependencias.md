# MOD-001 — Dependencias

Revisado el 2026-09-24.

| Módulo | Tipo de dependencia | Detalle |
|---|---|---|
| MOD-019 — Obras sociales | Funcional (fuerte) | Un paciente se asocia a una o más obras sociales, con una principal (`RN-PAC-003`). Este módulo necesita el **catálogo** de obras sociales (listado de 25 ya relevado, `Q-OSO-001`). No necesita convenios ni liquidaciones (`DECP-005`, abierto). |
| MOD-020 — Planes / coberturas / afiliaciones | Funcional (media) | Plan/categoría y número de afiliado se guardan en la afiliación del paciente. Si `MOD-020` define un catálogo de planes, el campo pasa de texto a listado. |
| MOD-002 — Historia Clínica | Funcional (fuerte) | Cada paciente tiene una historia clínica. Límite acordado: la ficha contiene los antecedentes siempre visibles (alergias, quirúrgicos, crónicos); el contenido de cada atención vive en `MOD-002`/`MOD-003`. |
| MOD-026 — Usuarios / MOD-027 — Roles y permisos | Funcional (fuerte) | Roles conocidos (`Q-USR-001`): recepción/administrativo, médico, Dirección/administración. `MOD-027` debe permitir asignar los permisos de la [matriz de permisos](reglas_negocio.md#permisos-por-rol-y-acción), incluidos "perfil directivo designado" y "dar de baja pacientes". |
| MOD-028 — Auditoría | Funcional (fuerte) | Todos los cambios de la ficha, las exportaciones y las descargas de adjuntos se auditan (`RN-PAC-008`, `Q-AUD-001`). |
| MOD-036 — Configuración general | Funcional (baja) | Parámetro de la ventana de corrección de antecedentes (hipótesis: 24 h, `Q-PAC-058`). |
| MOD-010 — Turnos | Funcional (media) | Un turno referencia a un paciente. Un paciente inactivo no recibe turnos nuevos (hipótesis `Q-PAC-062`). |
| MOD-011 — Recepción / MOD-012 — Sala de espera | Funcional (baja) | Usan la necesidad especial de atención (`RF-PAC-021`) para priorizar (`Q-ESP-002`). |
| MOD-014 / MOD-029 / MOD-030 — Recordatorios, notificaciones, WhatsApp | Funcional (media) | Usan teléfono, WhatsApp, canal preferido y opt-out de la ficha (`RF-PAC-009`). |
| MOD-033 — Solicitud pública de turnos | Funcional (media) | Hipótesis `RN-PAC-011`: la solicitud se vincula a una ficha existente por DNI, pero no crea ni modifica fichas (`Q-PAC-068`). |
| MOD-007 — Estudios / documentación | Funcional (baja) | Almacenamiento de los archivos adjuntos a la ficha. |
| MOD-018 — Sedes | Funcional (media) | El paciente es una ficha única compartida entre sedes (`Q-PAC-052`, `Q-SED-001`). |
| MOD-037 — Backups | No funcional | Los datos de pacientes son parte central de qué se debe respaldar (`RC-011`). |
| MOD-040 — Importación/exportación | Funcional (media) | Hay pacientes del sistema anterior a migrar (`Q-PAC-050`). Los datos migrados pueden no cumplir los obligatorios del alta: el proceso de migración define cómo marcarlos. |

## Módulos que dependen de este

Prácticamente todo el núcleo clínico y buena parte de la agenda dependen de que exista un
paciente: `MOD-002` a `MOD-008`, `MOD-010` a `MOD-014`, `MOD-019` a `MOD-021`, `MOD-033` a
`MOD-035`. Por eso es el primer módulo a refinar (ver [`README.md`](README.md)).

## Bloqueos actuales

Ninguna dependencia bloquea el pase a `LISTO_PARA_VALIDACION`. Para **construir** este módulo
hace falta, como mínimo:

- el catálogo de obras sociales de `MOD-019` (el listado ya existe, `Q-OSO-001`);
- los roles y permisos básicos de `MOD-027`, al menos los de la matriz de este módulo;
- la auditoría de `MOD-028`, que puede construirse junto con este módulo.
