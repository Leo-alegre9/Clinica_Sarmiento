# Escalabilidad

## Principio rector

Ver [`../01_Proyecto/vision.md`](../01_Proyecto/vision.md) y `RNF-ESC-001`: el sistema debe
poder incorporar nuevas especialidades, profesionales, sedes y tipos de práctica sin
reescritura estructural.

## Aplicación concreta (a validar en cada módulo)

- `Profesional` + `Especialidad` en lugar de "médico oftalmólogo" — ver `MOD-015`, `MOD-016`.
- `Sede` como concepto presente en el modelo desde el inicio, aunque hoy solo exista una
  (`SUP-001`) — ver `MOD-018`.
- Catálogos configurables (obras sociales, tipos de práctica) en lugar de listas fijas en
  código, cuando el volumen lo justifique — a decidir por módulo, evitando
  sobregeneralización innecesaria (ver sección 23 del pedido del cliente: "priorizar
  simplicidad + extensibilidad razonable").

## Advertencia expresa del cliente

No convertir innecesariamente todo en estructuras genéricas complejas. La extensibilidad se
aplica donde hay evidencia de que se necesitará (multiespecialidad, multisede), no como regla
universal para cualquier campo.

## Escalabilidad técnica (no funcional)

Volumen esperado de pacientes, turnos y usuarios concurrentes: `PENDIENTE_DEFINICION` — no se
recibió información del cliente sobre el tamaño actual o proyectado de la operación de la
clínica.
