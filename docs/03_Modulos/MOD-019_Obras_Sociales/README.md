```text
ID:                          MOD-019
Nombre:                      Obras sociales
Descripción:                 Entidades de cobertura médica que pueden asociarse a un paciente. Alcance funcional exacto pendiente de definir.
Estado:                      EN_DESCUBRIMIENTO
Responsable de validación:   PENDIENTE_DEFINICION
Última actualización:        2026-09-05
Dependencias:                MOD-001 (Pacientes)
Requerimientos relacionados: RF-OSO-001 (de RC-004)
```

El cliente pidió explícitamente **no asumir funcionalidades sin validarlas** (`RC-004`).
Pendiente determinar si planes, autorizaciones, copagos y liquidaciones son módulos separados
(`MOD-020`, `MOD-021`) o secciones de este — ver nota en
[`../README.md`](../README.md).

## Preguntas para el cliente (Ronda 2)

Este módulo entró en `EN_DESCUBRIMIENTO` el 2026-09-05: sus preguntas estructurales para el
cliente ya están armadas y forman parte del envío conjunto de la Ronda 2 (no depende de
respuestas todavía pendientes de `MOD-001`). Ver
[`../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-019`](../../08_Pendientes/cuestionario_cliente_ronda_2.md#mod-019).
Preguntas adicionales (más profundas) se agregarán cuando a este módulo le toque su
refinamiento completo, uno por vez, según [`../README.md`](../README.md).

## Respuestas de la Ronda 3 (2026-09-26)

- **Alcance (`Q-OSO-005`):** alcanza con **registrar** qué obra social tiene cada paciente y qué
  se le hizo. El sistema **no** arma presentaciones ni liquidaciones a las obras sociales.
  Resuelve `DECP-005` e `INV-007`. Con este alcance, `MOD-020` y `MOD-021` son candidatos
  firmes a quedar como secciones de este módulo (se decide al refinarlo).
- **Obra social de cada atención (`Q-OSO-004`):** recepción la elige en cada atención; viene
  marcada la principal del paciente. Alimenta `MOD-023` (Pagos).
- Los convenios y planes de cada obra social se piden más adelante (documento pendiente).
