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

Primer módulo `APROBADO`: `MOD-001` (2026-09-24); a partir de ahí, todo cambio sobre él se
registra como CR.

### Registro

| ID | Fecha | Módulo | Resumen | Estado |
|---|---|---|---|---|
| [CR-001](#cr-001) | 2026-09-26 | MOD-001 | "Procedencia" incluye quién derivó al paciente: nuevo dato opcional "derivado por" | ACEPTADO |

### CR-001

```text
ID:                  CR-001
Fecha:               2026-09-26
Solicitante:         Leonel Alegre, responsable del proyecto (Ronda 3, Q-PAC-064)
Requerimiento nuevo: Registrar, como dato opcional, quién derivó al paciente (médico o
                     institución, texto libre) y mostrarlo en el encabezado de la ficha junto
                     con la localidad del domicilio (RF-PAC-022).
Motivo:              Los médicos pidieron ver la "procedencia" (Q-HCL-003). La hipótesis
                     aprobada era "solo la localidad"; la respuesta fue "ambas".
Módulos afectados:   MOD-001 (y MOD-002: DEC-HCL-001 queda cubierta)
HU afectadas:        HU-PAC-001 (alta), encabezado de la ficha
CU afectados:        CU-PAC-001 (un campo opcional más en el alta)
Impacto técnico:     Bajo: un campo de texto opcional en el alta, la edición y el encabezado.
Impacto en datos:    Una columna nullable en la tabla de pacientes. Sin catálogo de derivantes.
Impacto en pruebas:  Dos criterios nuevos en HU-PAC-001 (se muestra en el encabezado; no es
                     obligatorio).
Estado:              ACEPTADO (2026-09-26). No requiere nueva pasada por EN_REFINAMIENTO.
```

## Propagación de respuestas

Cuando el cliente responde una pregunta (`Q-XXX-###`), la respuesta **no** se agrega solo al
final de `preguntas.md`. Se propaga a todos los documentos listados en el campo
`Impacta en:` de esa pregunta (requerimientos, reglas de negocio, modelo de dominio, historias,
casos de uso, matriz de trazabilidad), y solo entonces la pregunta pasa a `VALIDADA`.

## Autoridad para marcar `APROBADO`

Reiterado de [`estados_requerimientos.md`](estados_requerimientos.md): ningún agente de IA
puede fijar el estado `APROBADO` por iniciativa propia. Requiere instrucción explícita del
usuario confirmando validación con el cliente/responsable real.
