# Datos sensibles

Origen: `ANÁLISIS`, sujeto a confirmación legal (ver
[`../01_Proyecto/restricciones.md`](../01_Proyecto/restricciones.md)).

## Categorías de datos sensibles identificadas

- **Datos de salud** (antecedentes, diagnósticos, alergias, alertas clínicas, fórmulas
  oftalmológicas, estudios): la categoría más sensible; en Argentina se asocian a la
  normativa de historia clínica e infosalud. Ver `RNF-PRI-001`.
- **Datos financieros** (movimientos de caja, pagos): sensibles por motivos de control interno
  y potencial fraude, no por normativa de salud.
- **Datos de identificación** (DNI, domicilio, contacto): datos personales estándar, sujetos a
  la Ley 25.326 de Protección de Datos Personales (a confirmar aplicabilidad exacta).
- **Datos de menores**: requieren un tratamiento diferenciado (consentimiento del
  responsable) — ver preguntas de `MOD-001` sobre responsables/tutores.

## Controles pendientes de diseño (no implementados, todos PENDIENTE_DEFINICION)

- Permisos diferenciados por categoría de dato (ver `Q-PAC-036` a `Q-PAC-038`).
- Auditoría de acceso/modificación (`MOD-028`).
- Cifrado en reposo, si corresponde (depende de `ADR-001`).
- Política de retención y eventual anonimización de datos históricos (ver
  [`retencion.md`](retencion.md)).

No se implementa ningún control hasta que el módulo correspondiente esté refinado y aprobado.
