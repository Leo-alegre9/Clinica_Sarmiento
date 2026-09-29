# Integraciones

Ninguna integración externa está confirmada todavía. Este documento lista candidatas
mencionadas directa o indirectamente por el cliente, todas `PENDIENTE_DEFINICION`.

| Integración candidata | Origen | Módulo | Estado |
|---|---|---|---|
| WhatsApp (recordatorios/confirmaciones) | ANÁLISIS (a partir de `RC-002`, `SUP-008`) | MOD-030 | PENDIENTE_DEFINICION |
| Email transaccional | ANÁLISIS | MOD-031 | PENDIENTE_DEFINICION — base técnica ya existe (`config/mail.php`) |
| Sistemas de obras sociales (verificación de cobertura/autorización) | ANÁLISIS (a partir de `RC-004`) | MOD-019, MOD-021 | PENDIENTE_DEFINICION |
| Treelan (fórmulas oftalmológicas) | CLIENTE (`RC-005`) | MOD-006 | Investigación en curso — ver `INV-002` |
| Ampina (referencia de comparación) | CLIENTE (`RC-005`) | MOD-006 | Investigación en curso — ver `INV-003` |
| Facturación electrónica / AFIP | ANÁLISIS (no pedido, riesgo potencial de `MOD-022`) | MOD-022 | No solicitado — registrar como pregunta si surge al refinar Caja |

Ninguna integración se diseña ni implementa antes de que el módulo correspondiente esté
refinado y aprobado.
