# MOD-001 — Diagramas

Actualizados el 2026-09-24 con las respuestas del cliente y de los médicos. Las transiciones que
dependían de la Ronda 3 quedaron confirmadas el 2026-09-26.

## Estados del paciente

```mermaid
stateDiagram-v2
    [*] --> Activo: Alta (ficha completa)
    Activo --> Inactivo: Baja lógica (Dirección/administración o médico con permiso)
    Inactivo --> Activo: Reactivación
    Activo --> Fallecido: Registro de fallecimiento (solo administración)
    Inactivo --> Fallecido: Registro de fallecimiento (solo administración)
    Fallecido --> Activo: Reversión por error, con motivo (Q-PAC-063)
    Activo --> Fusionado: Unificación (Q-PAC-054)
    Inactivo --> Fusionado: Unificación (Q-PAC-054)
    Fusionado --> [*]
```

- Ningún estado elimina datos (`RN-PAC-005`). No existe un estado "Bloqueado" aparte: la baja
  lógica cubre ese caso (`Q-PAC-013`).
- Ni la baja ni el fallecimiento disparan acciones automáticas sobre turnos, recordatorios u
  obra social (`Q-PAC-041`, `Q-PAC-062`).
- En estado `Inactivo` no se asignan turnos nuevos (`Q-PAC-062`).

## Flujo de alta de paciente en recepción

```mermaid
flowchart TD
    A[Recepción busca por DNI, nombre o N.º de afiliado] --> B{¿Existe?}
    B -- Sí --> C[Abrir ficha existente]
    B -- No --> D[Completar ficha completa: documento o 'sin documento', datos personales, contacto, emergencia, domicilio con localidad, derivado por - opcional, obra social o particular]
    D --> M{¿Menor de 18?}
    M -- Sí --> R[Asociar al menos un responsable]
    M -- No --> K
    R --> K[Registrar consentimiento de datos]
    K --> E{¿Mismo tipo y número de documento que otro paciente?}
    E -- Sí --> X[Impedir alta y ofrecer abrir la ficha existente - Q-PAC-057]
    X --> C
    E -- No --> F{¿Coincide nombre + fecha de nacimiento o N.º de afiliado?}
    F -- Sí --> G{¿Recepción confirma que es otra persona?}
    G -- No --> C
    G -- Sí --> H[Crear paciente Activo]
    F -- No --> H
    H --> I[Paciente disponible para turno / historia clínica]
    C --> I
```

## Relación conceptual con otros módulos (vista parcial)

```mermaid
erDiagram
    PACIENTE ||--o{ AFILIACION_OBRA_SOCIAL : "tiene (una principal)"
    OBRA_SOCIAL ||--o{ AFILIACION_OBRA_SOCIAL : "cubre"
    PACIENTE ||--|| HISTORIA_CLINICA : "tiene"
    PACIENTE ||--o{ ANTECEDENTE_CLINICO : "registra"
    PACIENTE ||--o{ TURNO : "reserva"
    PACIENTE ||--o{ VINCULO_RESPONSABLE : "es menor en"
    PACIENTE ||--o{ VINCULO_RESPONSABLE : "es responsable en"
    PACIENTE ||--o{ DOCUMENTO_ADJUNTO : "tiene"
    PACIENTE |o--o| PACIENTE : "fusionado en"
```

El responsable de un menor es otro registro de `PACIENTE` (`DEC-PAC-011`); por eso el vínculo
relaciona dos pacientes. Este modelo es conceptual; el modelo de dominio del proyecto está en
[`../../04_Modelado/modelo_dominio/modelo_conceptual.md`](../../04_Modelado/modelo_dominio/modelo_conceptual.md).
