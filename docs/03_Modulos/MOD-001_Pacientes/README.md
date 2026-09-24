```text
ID:                          MOD-001
Nombre:                      Gestión de Pacientes
Descripción:                 Alta, modificación, baja, búsqueda y consulta de pacientes de la clínica: identificación, datos personales, contacto, cobertura y estado.
Estado:                      APROBADO (2026-09-24)
Responsable de validación:   Leonel Alegre (responsable del proyecto)
Última actualización:        2026-09-24
Dependencias:                MOD-019 (Obras sociales — asociación paciente↔obra social), MOD-026/MOD-027 (Usuarios y roles — permisos sobre datos del paciente), MOD-002 (Historia clínica — asociada 1:1 a cada paciente)
Requerimientos relacionados: RF-PAC-001 a RF-PAC-021 (ver requerimientos.md)
```

## Por qué este módulo se refina primero

Decisión explícita del cliente (sección 30 del pedido de apertura de esta fase): aunque el
inventario completo de 41 módulos ya está preparado (ver
[`../README.md`](../README.md)), el refinamiento profundo avanza **de a un módulo por vez**, y
Pacientes es el primero porque es la entidad central de la que dependen prácticamente todos
los demás módulos clínicos y administrativos.

## Qué contiene esta carpeta

| Archivo | Contenido |
|---|---|
| [`alcance.md`](alcance.md) | Qué incluye y qué no incluye el módulo |
| [`requerimientos.md`](requerimientos.md) | Requerimientos funcionales `RF-PAC-###` derivados del análisis |
| [`historias_usuario.md`](historias_usuario.md) | Historias de usuario `HU-PAC-001` a `HU-PAC-016` |
| [`casos_uso.md`](casos_uso.md) | Casos de uso `CU-PAC-001` a `CU-PAC-005` (alta, búsqueda, unificación, antecedentes, baja) |
| [`reglas_negocio.md`](reglas_negocio.md) | Reglas `RN-PAC-###` y matriz de permisos por rol |
| [`datos.md`](datos.md) | Datos del paciente, separados por categoría |
| [`criterios_aceptacion.md`](criterios_aceptacion.md) | Criterios Given/When/Then de todas las historias |
| [`preguntas.md`](preguntas.md) | Preguntas de refinamiento `Q-PAC-001` a `Q-PAC-069` con su estado |
| [`dependencias.md`](dependencias.md) | Dependencias con otros módulos |
| [`riesgos.md`](riesgos.md) | Riesgos específicos del módulo |
| [`diagramas.md`](diagramas.md) | Diagramas Mermaid (estados del paciente, flujo de alta, relaciones) |
| [`decisiones.md`](decisiones.md) | Decisiones ya tomadas, con origen y fecha |
| [`trazabilidad.md`](trazabilidad.md) | Trazabilidad interna del módulo (RC → RF → HU → CU → RN → criterio) |

## Actores

Recepción/administrativo, médico, Dirección/administración (`Q-USR-001`), más el permiso
asignable de perfil directivo designado. Ver la matriz de permisos en
[`reglas_negocio.md`](reglas_negocio.md#permisos-por-rol-y-acción).

## Estado frente a la Definition of Ready

Revisado el 2026-09-24 contra
[`../../00_Gobernanza/definition_of_ready.md`](../../00_Gobernanza/definition_of_ready.md):

- [x] Objetivo del módulo (este archivo).
- [x] Alcance y fuera de alcance ([`alcance.md`](alcance.md)).
- [x] Actores (sección anterior).
- [x] Requerimientos funcionales `RF-PAC-001` a `RF-PAC-021` ([`requerimientos.md`](requerimientos.md)).
- [x] Requisitos no funcionales aplicables (sección en [`requerimientos.md`](requerimientos.md)).
- [x] Datos principales ([`datos.md`](datos.md)).
- [x] Reglas de negocio `RN-PAC-001` a `RN-PAC-011` ([`reglas_negocio.md`](reglas_negocio.md)).
- [x] Flujo principal, flujos alternativos y excepciones (`CU-PAC-001` a `CU-PAC-005` en
      [`casos_uso.md`](casos_uso.md); flujos simples en las historias).
- [x] Permisos por rol y acción ([`reglas_negocio.md`](reglas_negocio.md#permisos-por-rol-y-acción)).
- [x] Historias de usuario `HU-PAC-001` a `HU-PAC-016`, todas con criterios
      ([`historias_usuario.md`](historias_usuario.md), [`criterios_aceptacion.md`](criterios_aceptacion.md)).
- [x] Dependencias ([`dependencias.md`](dependencias.md)).
- [x] Riesgos ([`riesgos.md`](riesgos.md)).
- [x] Las 17 preguntas de criticidad ALTA están `VALIDADA`. Las 16 preguntas nuevas de la
      Ronda 3 (`Q-PAC-054` a `Q-PAC-069`) son MEDIA o BAJA, cada una con hipótesis de trabajo
      documentada ([`preguntas.md`](preguntas.md), sección 24).
- [x] Decisiones con origen y fecha ([`decisiones.md`](decisiones.md), hasta `DEC-PAC-024`).
- [x] Trazabilidad completa ([`trazabilidad.md`](trazabilidad.md) y la fila de `MOD-001` en
      [`../../02_Requerimientos/matriz_trazabilidad.md`](../../02_Requerimientos/matriz_trazabilidad.md)).

### Qué hay que tener en cuenta al validar

1. **Hipótesis de trabajo.** Varios detalles (valor de la ventana de corrección, qué pasa con
   los turnos al dar de baja, qué significa "procedencia", etc.) están escritos como
   hipótesis y se preguntan en el bloque 1 de
   [`../../08_Pendientes/cuestionario_cliente_ronda_3.md`](../../08_Pendientes/cuestionario_cliente_ronda_3.md).
   Conviene validar el módulo **junto con** esas respuestas: si una hipótesis se rechaza, se
   ajusta el documento antes de aprobar.
2. **Unificación de duplicados** (`RF-PAC-012`): hipótesis completa, fuera del primer incremento
   de construcción hasta que se confirme (`DEC-PAC-022`).
3. **Riesgo de privacidad aceptado** (`RIE-PAC-004`): todo el personal ve toda la ficha, por
   decisión explícita del cliente. Tiene que quedar registrado en la aprobación que el riesgo
   fue comunicado.
4. **Responsable de validación**: Leonel Alegre, responsable del proyecto. `Q-PRY-001` (Ronda 3)
   sigue abierta para definir quién aprueba los módulos siguientes.

## Aprobación

**Aprobado el 2026-09-24** por Leonel Alegre, responsable del proyecto, por instrucción
explícita ("Validamos el módulo 001"). Registrado en
[`../../09_Aprobaciones/historial_aprobaciones.md`](../../09_Aprobaciones/historial_aprobaciones.md).

Condiciones de la aprobación:

1. **Las hipótesis de trabajo se aprueban tal como están escritas.** Si una respuesta del
   bloque 1 de la Ronda 3 (`Q-PAC-054` a `Q-PAC-069`) confirma la propuesta, el punto pasa a
   `CONFIRMADO` sin más trámite. Si la contradice, el cambio se gestiona como **Change Request**
   (`CR-###`), según
   [`../../00_Gobernanza/control_cambios.md`](../../00_Gobernanza/control_cambios.md).
2. **La unificación de fichas duplicadas** (`RF-PAC-012`) sigue fuera del primer incremento de
   construcción hasta que se confirmen `Q-PAC-054` a `Q-PAC-056` (`DEC-PAC-022`).
3. **Riesgo de privacidad aceptado** (`RIE-PAC-004`): la aprobación incluye, con conocimiento de
   causa, que todo el personal ve toda la ficha.

## Siguiente paso

1. Pasar a `EN_CONSTRUCCION`, empezando por lo mínimo de `MOD-027`/`MOD-028` que este módulo
   necesita (ver [`dependencias.md`](dependencias.md)).
2. Volcar las respuestas del bloque 1 de la Ronda 3 cuando lleguen (confirmación o CR).
