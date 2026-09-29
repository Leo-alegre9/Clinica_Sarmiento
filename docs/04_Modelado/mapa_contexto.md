# Mapa de contexto

Vista de alto nivel de cómo el sistema se relaciona con actores externos y con la posible
página institucional. **Hipótesis de trabajo**, no un diseño validado.

```mermaid
flowchart LR
    Paciente((Paciente))
    Secretaria([Secretario/a])
    Medico([Médico / Profesional])
    Admin([Administrador])
    Sistema[["Sistema de Gestión\nClínica Sarmiento"]]
    Web[Página institucional]
    WhatsApp[[WhatsApp / SMS / Email]]
    ObraSocial[(Obra social - externa)]

    Paciente -- solicita turno --> Web
    Web -- disponibilidad / solicitud --> Sistema
    Paciente -- llega, se atiende --> Sistema
    Secretaria -- agenda, turnos, caja, pacientes --> Sistema
    Medico -- historia clínica, consultas, cirugías --> Sistema
    Admin -- caja, roles, configuración --> Sistema
    Sistema -- recordatorios --> WhatsApp
    WhatsApp -- notifica --> Paciente
    Sistema -. verificación de cobertura .-> ObraSocial
```

La integración con obras sociales está marcada como punteada porque su alcance es
`PENDIENTE_DEFINICION` (`RC-004`) — puede ser tan simple como un dato de referencia o tan
compleja como una verificación en tiempo real, según se resuelva en `MOD-019`.

Ver también [`../05_Arquitectura/integraciones.md`](../05_Arquitectura/integraciones.md).
