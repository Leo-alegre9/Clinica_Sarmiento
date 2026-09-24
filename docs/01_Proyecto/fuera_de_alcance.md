# Fuera de alcance

## De esta fase (Ingeniería de Requisitos)

- Implementación de código funcional de cualquier módulo de dominio (pacientes, turnos,
  cirugías, caja, etc.). Ver regla en
  [`../00_Gobernanza/README.md`](../00_Gobernanza/README.md).
- Decisión definitiva de arquitectura de despliegue (web/local/híbrida) — ver
  [`ADR-001`](../05_Arquitectura/ADR/ADR-001-web-vs-local-vs-hibrido.md).
- Definición de lógica clínica u oftalmológica no documentada por el cliente (fórmulas,
  cálculos, criterios de prioridad clínica). Ver [`INV-001`](../08_Pendientes/investigaciones.md)
  a [`INV-003`](../08_Pendientes/investigaciones.md).
- Cambios al stack tecnológico definido en la Fase 1.
- Refinamiento profundo de módulos distintos de MOD-001 — Pacientes (quedan `IDENTIFICADO` /
  preparados para una próxima iteración).

## Del sistema (hipótesis a confirmar, no asumir como definitivo)

Estos puntos están fuera de alcance **según la información disponible hoy**, pero deben
confirmarse con el cliente en cada módulo antes de descartarse formalmente:

- Aplicaciones móviles nativas (el roadmap previo del repositorio menciona APIs "cuando sean
  necesarias para aplicaciones móviles", sin compromiso actual).
- Telemedicina / consulta remota.
- Facturación electrónica / integración con AFIP — no mencionado por el cliente todavía;
  registrar como pregunta si el módulo de Caja lo requiere.
- Portal de paciente con historia clínica propia (el cliente solo mencionó, por ahora,
  solicitud pública de turnos — `RC-003`).
- Multi-tenant para otras clínicas (el sistema se diseña extensible, pero no se pidió operar
  múltiples clínicas como clientes independientes de una misma instalación).

Cualquier punto de esta lista puede pasar a estar dentro de alcance si el cliente lo indica
explícitamente; en ese caso se registra como `CR` una vez que exista una base aprobada, o se
incorpora directamente si el módulo aún no fue aprobado.
