# Alcance

## Alcance de esta fase (Ingeniería de Requisitos)

- Crear y mantener `/Docs` como fuente de verdad.
- Inspeccionar el repositorio actual y clasificar lo existente.
- Registrar literalmente y luego normalizar los requerimientos crudos del cliente.
- Construir el inventario de módulos y la matriz de trazabilidad inicial (con columnas de
  implementación/prueba en `PENDIENTE`).
- Refinar exhaustivamente **MOD-001 — Pacientes** mediante preguntas, sin definir su diseño
  final todavía.
- Dejar preparada (carpeta y plantillas) la estructura del resto de los módulos, sin
  refinarlos en profundidad todavía — eso ocurre módulo por módulo, en iteraciones
  posteriores, según el flujo de [`../00_Gobernanza`](../00_Gobernanza/README.md).

## Alcance funcional macro del sistema (hipótesis de trabajo, a confirmar módulo por módulo)

El sistema, sujeto a refinamiento módulo por módulo, cubre:

- **Núcleo clínico**: pacientes, historia clínica, consultas, diagnósticos, recetas/prescripciones,
  fórmulas oftalmológicas, estudios/documentación clínica, evoluciones.
- **Agenda y atención**: agenda médica, turnos, cirugías, recepción/check-in, sala de
  espera/prioridades, recordatorios y confirmaciones.
- **Organización**: médicos/profesionales, especialidades, consultorios, sedes (si
  corresponde).
- **Cobertura médica**: obras sociales, planes/coberturas/afiliaciones, autorizaciones (si
  corresponde).
- **Administración**: caja, pagos, gastos/egresos, reportes administrativos.
- **Seguridad**: usuarios, roles y permisos, auditoría.
- **Comunicación**: notificaciones, WhatsApp/mensajería, email, plantillas.
- **Portal público**: solicitud pública de turnos, disponibilidad pública, confirmación y
  seguimiento de solicitudes.
- **Plataforma**: configuración general, backups, logs y monitoreo, integraciones externas,
  importación/exportación, reportes y estadísticas.

Ver el detalle módulo por módulo en [`../03_Modulos/README.md`](../03_Modulos/README.md).

## Multiespecialidad y multisede (principio de diseño)

El sistema se piensa desde el inicio para una **clínica**, no para un consultorio
unipersonal, y su modelo debe soportar en el futuro otras especialidades, profesionales, sedes,
consultorios, tipos de práctica y estudios sin rediseño estructural. Ver
[`vision.md`](vision.md).

## Fuera de alcance

Ver [`fuera_de_alcance.md`](fuera_de_alcance.md).

## Relación con el stack técnico

Esta fase no cambia el stack técnico definido en la Fase 1
([`../../docs/architecture.md`](../../docs/architecture.md)): Laravel 13 + Inertia + React +
TypeScript + Tailwind + shadcn/ui, con PostgreSQL previsto para una fase posterior (hoy SQLite
temporal). Ninguna decisión de esta fase de requisitos debe asumirse como cambio de stack.
