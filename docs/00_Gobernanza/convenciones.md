# Convenciones documentales

## Idioma

Toda la documentación funcional se redacta en **español (es-AR)**. Los identificadores de
código (nombres de tablas, campos, clases) se documentan tal como existen o existirán en el
código, que sigue convenciones en inglés según `laravel-best-practices`.

## Identificadores estables

Ningún identificador se reutiliza ni se renombra una vez publicado. Si un elemento se
descarta, se marca `DESCARTADA` / `DEPRECADO` pero el ID permanece reservado y visible en el
historial.

| Prefijo | Significa | Ejemplo |
|---|---|---|
| `MOD-###` | Módulo funcional | `MOD-001` |
| `RF-XXX-###` | Requerimiento funcional | `RF-PAC-001` |
| `RNF-XXX-###` | Requisito no funcional | `RNF-SEG-001` |
| `RN-XXX-###` | Regla de negocio | `RN-TUR-001` |
| `HU-XXX-###` | Historia de usuario | `HU-PAC-001` |
| `CU-XXX-###` | Caso de uso | `CU-PAC-001` |
| `Q-XXX-###` | Pregunta de refinamiento | `Q-PAC-001` |
| `RC-###` | Requerimiento crudo del cliente | `RC-001` |
| `INV-###` | Investigación pendiente | `INV-001` |
| `ADR-###` | Decisión arquitectónica | `ADR-001` |
| `CR-###` | Solicitud de cambio (Change Request) | `CR-001` |

`XXX` es un código corto de 3 letras del módulo/dominio (ver tabla en
[`../03_Modulos/README.md`](../03_Modulos/README.md)), por ejemplo `PAC` (Pacientes), `TUR`
(Turnos), `CIR` (Cirugías), `CAJ` (Caja), `HCL` (Historia Clínica), `OSO` (Obras Sociales).

## Origen de la información

Todo requerimiento, regla o decisión debe declarar su **origen**:

```text
CLIENTE
MÉDICO
ADMINISTRACIÓN
USUARIO
ANÁLISIS
REQUISITO TÉCNICO
REQUISITO LEGAL
```

Una propuesta con origen `ANÁLISIS` es una hipótesis de trabajo, no un requerimiento
confirmado, y debe marcarse `Requiere validación: SÍ`.

## Hechos vs. hipótesis vs. preguntas vs. decisiones pendientes

Cada documento de módulo separa explícitamente:

- **Información confirmada** — validada por el cliente/responsable.
- **Hipótesis** — supuesto razonable de análisis, no confirmado.
- **Preguntas abiertas** — remiten a `preguntas.md` por ID.
- **Decisiones pendientes** — remiten a `08_Pendientes/decisiones_pendientes.md`.

## Enlaces

Usar siempre rutas relativas entre documentos Markdown, para que el repositorio siga siendo
navegable fuera de cualquier herramienta específica.

## No inventar respuestas

Ante la ausencia de una decisión del cliente, el valor correcto a registrar es
`PENDIENTE_DEFINICION`, nunca un supuesto no marcado como tal. Ver
[`estados_requerimientos.md`](estados_requerimientos.md).
