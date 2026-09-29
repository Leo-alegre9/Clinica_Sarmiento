# Definition of Ready documental

Un módulo solo puede pasar a `LISTO_PARA_VALIDACION` (ver
[`estados_requerimientos.md`](estados_requerimientos.md)) cuando su carpeta en
`03_Modulos/MOD-###_Nombre/` contiene, como mínimo:

- [ ] Objetivo del módulo claramente definido (`README.md`).
- [ ] Alcance (`alcance.md`).
- [ ] Fuera de alcance (`alcance.md`).
- [ ] Actores identificados (`README.md` / `casos_uso.md`).
- [ ] Requerimientos funcionales (`requerimientos.md`), cada uno con ID `RF-XXX-###`.
- [ ] Requisitos no funcionales aplicables (referenciados desde
      [`../02_Requerimientos/requerimientos_no_funcionales.md`](../../02_Requerimientos/requerimientos_no_funcionales.md)).
- [ ] Datos principales manejados (`datos.md`).
- [ ] Reglas de negocio (`reglas_negocio.md`), cada una con ID `RN-XXX-###`.
- [ ] Flujo principal descripto (`casos_uso.md` o `README.md`).
- [ ] Flujos alternativos identificados.
- [ ] Excepciones identificadas.
- [ ] Permisos por rol/acción (`reglas_negocio.md` o `datos.md`, sección de seguridad).
- [ ] Historias de usuario (`historias_usuario.md`), cada una con criterios de aceptación.
- [ ] Casos de uso relevantes (`casos_uso.md`) para los flujos no triviales.
- [ ] Criterios de aceptación (`criterios_aceptacion.md`), formato Given/When/Then donde aporte claridad.
- [ ] Dependencias con otros módulos (`dependencias.md`).
- [ ] Riesgos identificados (`riesgos.md`).
- [ ] **Todas las preguntas de criticidad ALTA en `preguntas.md` están en estado `RESPONDIDA` o `VALIDADA`.**
      Las de criticidad MEDIA/BAJA pueden quedar `ABIERTA` con una hipótesis de trabajo documentada.
- [ ] Decisiones tomadas registradas (`decisiones.md`), con origen y fecha.
- [ ] Fila(s) correspondientes completas en
      [`../02_Requerimientos/matriz_trazabilidad.md`](../../02_Requerimientos/matriz_trazabilidad.md)
      (las columnas `Implementación` y `Prueba` pueden seguir en `PENDIENTE`).

## De `LISTO_PARA_VALIDACION` a `APROBADO`

Cumplir la checklist anterior habilita a **presentar** el módulo para validación humana. El
pase a `APROBADO` exige además:

- Validación explícita del cliente o responsable del módulo (nombrado en el `README.md` del
  módulo como "Responsable de validación").
- Registro de esa aprobación en
  [`../09_Aprobaciones/historial_aprobaciones.md`](../../09_Aprobaciones/historial_aprobaciones.md)
  y actualización de
  [`../09_Aprobaciones/modulos_aprobados.md`](../../09_Aprobaciones/modulos_aprobados.md).

Solo después de `APROBADO` se habilita la construcción del módulo (`EN_CONSTRUCCION`).

Ver también [`definition_of_done_documental.md`](definition_of_done_documental.md) para el
cierre documental posterior a la implementación.
