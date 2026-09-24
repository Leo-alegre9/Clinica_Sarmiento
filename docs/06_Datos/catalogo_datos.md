# Catálogo de datos

Vista consolidada de los datos identificados hasta ahora. Se completa módulo por módulo; hoy
solo tiene contenido sustantivo el bloque de Pacientes.

## MOD-001 — Pacientes

Ver detalle completo en
[`../03_Modulos/MOD-001_Pacientes/datos.md`](../03_Modulos/MOD-001_Pacientes/datos.md).
Categorías: identificación, datos personales, domicilio, contacto, emergencia,
responsables/tutores, cobertura, estado administrativo, información clínica básica,
documentación adjunta, metadatos de auditoría.

## Resto de los módulos

No se ha relevado el catálogo de datos de ningún otro módulo todavía (todos `IDENTIFICADO`,
sin refinamiento profundo). Se completa aquí a medida que cada uno avance.

## Clasificación transversal de sensibilidad (hipótesis, a confirmar por módulo)

| Nivel | Descripción | Ejemplos |
|---|---|---|
| Público | Sin restricción de acceso dentro del sistema | Nombre de especialidades, horarios de atención generales |
| Administrativo | Visible a personal de recepción/administración | Contacto, obra social, turnos |
| Clínico | Visible solo a personal médico (y quien se defina) | Antecedentes, diagnósticos, recetas, fórmulas |
| Financiero | Visible solo a roles con acceso a caja | Movimientos de caja, pagos |

Ver [`datos_sensibles.md`](datos_sensibles.md) para el detalle de por qué cada categoría es
sensible y qué la protege.
