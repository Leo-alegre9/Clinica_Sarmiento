# Visión del proyecto

## Origen: CLIENTE / ANÁLISIS

## Declaración de visión

Clínica Sarmiento necesita un **sistema integral de gestión** que reemplace el manejo actual
(aparentemente manual y/o basado en herramientas dispares como Ampina y planillas) por una
plataforma única que centralice la actividad clínica y administrativa de una clínica
oftalmológica: agenda, atención de pacientes, historia clínica, cirugías, obras sociales y
caja.

El sistema **no se diseña para un único médico**, sino para una clínica con múltiples
profesionales, múltiples usuarios administrativos, múltiples consultorios y, potencialmente,
múltiples sedes en el futuro. Esta decisión de diseño es de origen `ANÁLISIS`, derivada de la
lectura de los requerimientos crudos (ver
[`../02_Requerimientos/requerimientos_cliente_raw.md`](../02_Requerimientos/requerimientos_cliente_raw.md)),
y debe validarse explícitamente con el cliente como principio rector del proyecto.

## Por qué existe este sistema

- Reemplazar procesos manuales/dispersos de agenda, caja e historia clínica por un sistema
  único, auditable y trazable.
- Reducir errores operativos: turnos superpuestos, pacientes sin recordatorio de cirugía,
  diferencias de caja no explicadas, pérdida de información clínica.
- Permitir que el paciente interactúe con la clínica (al menos para solicitar turnos) sin
  depender exclusivamente de una llamada telefónica.
- Dejar una base de datos clínica y administrativa consultable, en lugar de información
  dispersa entre sistemas o papel.

## Filosofía del sistema (más allá del software)

Este documento fija también la filosofía de **proceso** adoptada a partir de esta fase: ninguna
funcionalidad se construye hasta que su alcance esté suficientemente refinado, documentado y
aprobado. Ver [`00_Gobernanza/README.md`](../00_Gobernanza/README.md).

## Escalabilidad de dominio

Aunque el uso inicial es oftalmológico, el modelo funcional y de datos debe evitar acoplar
conceptos genéricos (profesional, especialidad, consultorio, práctica) a la oftalmología de
forma rígida. Ver [`alcance.md`](alcance.md) y la nota de diseño en
[`../04_Modelado/modelo_dominio/modelo_conceptual.md`](../04_Modelado/modelo_dominio/modelo_conceptual.md).
Cuando una regla o dato es intrínsecamente oftalmológico (p. ej. una fórmula de lente), se
documenta explícitamente como tal en lugar de generalizarse artificialmente.

## Relación con el estado actual del repositorio

A la fecha de este documento (2026-09-02), el repositorio contiene únicamente la **Fase 1**:
base tecnológica Laravel 13 + Inertia + React + TypeScript + Tailwind + shadcn/ui, con
autenticación estándar del Starter Kit (Fortify: registro, verificación de email, 2FA,
passkeys). No existe todavía ningún módulo clínico ni administrativo. Ver
[`../03_Modulos/README.md`](../03_Modulos/README.md), sección "Hallazgos del sistema actual".

Esta fase de ingeniería de requisitos se abre **antes** de construir el primer módulo de
dominio (Pacientes), precisamente para no repetir el patrón sugerido por el `README.md` previo
del repositorio (roadmap de fases fijado de antemano sin descubrimiento) sin antes validar el
alcance real con el cliente y los médicos.
