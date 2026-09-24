# Estados de requerimientos, preguntas y módulos

## Estados de módulo (`03_Modulos/MOD-###.../README.md`)

```text
IDENTIFICADO           → listado en el inventario, sin análisis todavía.
EN_DESCUBRIMIENTO      → se están relevando necesidades y generando preguntas.
EN_REFINAMIENTO        → hay respuestas parciales, documentación en construcción.
PENDIENTE_RESPUESTAS   → el refinamiento está bloqueado por preguntas de criticidad ALTA sin responder.
LISTO_PARA_VALIDACION  → cumple la Definition of Ready documental (ver definition_of_ready.md).
APROBADO               → validado explícitamente por el cliente/responsable. Solo lo puede fijar una persona humana.
EN_CONSTRUCCION        → se está implementando en código.
IMPLEMENTADO           → el código existe y pasa sus pruebas.
VALIDADO                → implementación verificada contra los criterios de aceptación por el cliente/responsable.
DEPRECADO              → descartado o reemplazado; se conserva por trazabilidad.
```

**Regla dura:** Claude/el agente de IA nunca asigna `APROBADO` por sí mismo. Ese estado
requiere una instrucción explícita del usuario indicando que el módulo fue validado con el
cliente o responsable correspondiente. Ver [`control_cambios.md`](control_cambios.md).

## Estados de clasificación del código ya existente

Al contrastar el repositorio actual contra los requerimientos, cada funcionalidad hallada se
clasifica como:

```text
IMPLEMENTADO_Y_DOCUMENTADO
IMPLEMENTADO_SIN_VALIDACION
IMPLEMENTADO_PARCIALMENTE
PLANIFICADO
NO_IMPLEMENTADO
REQUIERE_REDEFINICION
```

Una funcionalidad `IMPLEMENTADO_*` **no** se considera aprobada automáticamente: puede
requerir revisión de comportamiento antes de aceptarse como parte del alcance definitivo.

## Estados de pregunta (`preguntas.md`)

```text
ABIERTA      → sin respuesta.
RESPONDIDA   → el cliente/responsable respondió, falta propagar a los documentos afectados.
VALIDADA     → respondida y ya propagada a todos los documentos afectados.
DESCARTADA   → dejó de ser relevante (justificar el motivo).
```

## Estados de requerimiento funcional / regla de negocio

```text
PROPUESTO     → origen ANÁLISIS, no confirmado.
CONFIRMADO    → validado con el cliente/responsable.
EN_DUDA       → hay información contradictoria, requiere aclaración.
DESCARTADO    → se decidió no implementarlo (registrar motivo y fecha).
```

## Criticidad de preguntas

```text
ALTA   → bloquea el pase a LISTO_PARA_VALIDACION del módulo.
MEDIA  → afecta el diseño pero tiene una interpretación razonable temporal.
BAJA   → detalle menor, no bloquea el avance documental.
```
