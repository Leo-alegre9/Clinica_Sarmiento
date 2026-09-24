# Control de cambios

## Regla general

Mientras un módulo está `EN_DESCUBRIMIENTO`, `EN_REFINAMIENTO` o `PENDIENTE_RESPUESTAS`, sus
documentos se editan libremente a medida que se responden preguntas (ver
[flujo de propagación](#propagación-de-respuestas) más abajo).

Una vez que un módulo llega a `APROBADO`, la documentación pasa a ser **contractual**. Ningún
requerimiento nuevo se agrega sobreescribiendo silenciosamente el contenido aprobado.

## Change Requests (`CR-###`)

Todo requerimiento nuevo o cambio sobre un módulo ya `APROBADO` (o `VALIDADO`) se registra
como una entrada en una tabla de Change Requests (a crear en este mismo archivo o en un
archivo `change_requests.md` cuando exista el primer caso real), con:

```text
ID:                  CR-001
Fecha:
Solicitante:
Requerimiento nuevo:
Motivo:
Módulos afectados:
HU afectadas:
CU afectados:
Impacto técnico:
Impacto en datos:
Impacto en pruebas:
Estado:              PROPUESTO | ACEPTADO | RECHAZADO | IMPLEMENTADO
```

Un CR aceptado actualiza los documentos del módulo y dispara una nueva pasada por
`EN_REFINAMIENTO` para ese módulo si el impacto lo amerita, en lugar de reabrirse como si
nunca hubiera sido aprobado.

No hay CRs registrados todavía. Primer módulo `APROBADO`: `MOD-001` (2026-09-24); a partir de ahí,
todo cambio sobre él se registra como CR.

## Propagación de respuestas

Cuando el cliente responde una pregunta (`Q-XXX-###`), la respuesta **no** se agrega solo al
final de `preguntas.md`. Se propaga a todos los documentos listados en el campo
`Impacta en:` de esa pregunta (requerimientos, reglas de negocio, modelo de dominio, historias,
casos de uso, matriz de trazabilidad), y solo entonces la pregunta pasa a `VALIDADA`.

## Autoridad para marcar `APROBADO`

Reiterado de [`estados_requerimientos.md`](estados_requerimientos.md): ningún agente de IA
puede fijar el estado `APROBADO` por iniciativa propia. Requiere instrucción explícita del
usuario confirmando validación con el cliente/responsable real.
