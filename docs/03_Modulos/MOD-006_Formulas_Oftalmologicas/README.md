```text
ID:                          MOD-006
Nombre:                      Fórmulas Oftalmológicas
Descripción:                 Registro (y eventual cálculo asistido) de fórmulas/graduaciones oftalmológicas del paciente.
Estado:                      IDENTIFICADO — BLOQUEADO por investigación documental
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-15
Dependencias:                MOD-001 (Pacientes), MOD-003 (Consultas)
Requerimientos relacionados: RF-FOR-001, RN-CLI-001
```

**Este es el único módulo explícitamente oftalmológico del inventario** (ver
[`../../01_Proyecto/vision.md`](../../01_Proyecto/vision.md) sobre extensibilidad de dominio):
no se generaliza porque la fórmula oftalmológica es, por naturaleza, propia de esa
especialidad.

No puede avanzar a `EN_DESCUBRIMIENTO` hasta resolver:

- [`INV-001`](../../08_Pendientes/investigaciones.md) — análisis del PDF/documentación de
  fórmulas provisto por el cliente.
- [`INV-002`](../../08_Pendientes/investigaciones.md) — comportamiento del sistema Treelan.
- [`INV-003`](../../08_Pendientes/investigaciones.md) — comparación con Ampina.

Regla dura ya fijada (`RN-CLI-001`): ningún cálculo clínico se implementa sin documentación
validada por un profesional. Ver `RC-005`.

## Preguntas para el cliente — solo para destrabar la investigación

El módulo sigue bloqueado, pero se incluyeron 3 preguntas cortas en el envío conjunto de la
Ronda 2 (`Q-FOR-001` a `Q-FOR-003`) que le piden al cliente exactamente lo que falta para poder
avanzar `INV-001`, `INV-002` e `INV-003` (el documento de referencia y acceso/ejemplos de
Ampina y Treelan). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-006`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-006).
El módulo recién pasa a `EN_DESCUBRIMIENTO` cuando esas investigaciones se resuelvan.

## Preguntas para los médicos

La parte que solo pueden responder los médicos (frecuencia de uso real, qué cálculo de
Ampina/Treelan les resulta útil, qué le cambiarían) está en
[`../../08_Pendientes/cuestionario_medicos_ronda_1.md`](../../08_Pendientes/cuestionario_medicos_ronda_1.md)
(`Q-FOR-004` a `Q-FOR-006`), como insumo directo de `INV-002`/`INV-003`.

## Respuestas de los médicos (Ronda 1) — el módulo sigue bloqueado

`INV-004` se respondió el 2026-09-15. Quedó confirmado el uso diario de fórmulas oftalmológicas
(`Q-FOR-004`) y, tras resolver la contradicción con la Ronda 2 del cliente, que **la clínica sí
usa Treelan** para calcular la adición de lentes de cerca (`Q-FOR-005`) — ver
[`decisiones.md`](decisiones.md). El módulo **sigue bloqueado**: ahora que se sabe que sí lo usan,
falta conseguir acceso o documentación/ejemplo de Treelan para poder diseñar el cálculo
(`RN-CLI-001`), no alcanza con saber que existe. `INV-002` sigue como investigación pendiente en
[`../../08_Pendientes/investigaciones.md`](../../08_Pendientes/investigaciones.md).
