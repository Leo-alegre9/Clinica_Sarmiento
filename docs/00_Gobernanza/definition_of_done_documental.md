# Definition of Done documental

Aplica **después** de que un módulo fue `APROBADO` y construido. Define cuándo la
documentación de un módulo puede considerarse `IMPLEMENTADO` / `VALIDADO` en lugar de
simplemente "el código funciona".

Un módulo pasa de `EN_CONSTRUCCION` a `IMPLEMENTADO` cuando:

- [ ] El código que lo implementa existe en el repositorio y pasa `php artisan test` /
      `vendor/bin/phpunit` para los casos relacionados.
- [ ] Cada `RF-XXX-###` del módulo referencia, en
      [`../02_Requerimientos/matriz_trazabilidad.md`](../../02_Requerimientos/matriz_trazabilidad.md),
      el archivo/clase que lo implementa (columna `Implementación`), reemplazando `PENDIENTE`.
- [ ] Cada criterio de aceptación relevante tiene al menos una prueba automatizada asociada
      (columna `Prueba` de la matriz), reemplazando `PENDIENTE`.
- [ ] Las reglas de negocio (`RN-XXX-###`) con impacto en el modelo de datos están reflejadas
      en migraciones/constraints reales, no solo en el documento.
- [ ] Se registran en `decisiones.md` del módulo las desviaciones entre lo documentado y lo
      finalmente implementado (si las hubo), con motivo.

Un módulo pasa de `IMPLEMENTADO` a `VALIDADO` cuando:

- [ ] El cliente/responsable de validación confirmó que el comportamiento implementado
      cumple los criterios de aceptación (registrar en
      [`../09_Aprobaciones/historial_aprobaciones.md`](../../09_Aprobaciones/historial_aprobaciones.md)).

## Cambios posteriores a `VALIDADO`

Cualquier requerimiento nuevo sobre un módulo `VALIDADO` (o `APROBADO`) se gestiona como
**Change Request** (`CR-###`), nunca como una edición silenciosa de la documentación
aprobada. Ver [`control_cambios.md`](control_cambios.md).
