# MOD-001 — Criterios de aceptación

**Estado:** actualizado el 2026-09-24 para el pase a `LISTO_PARA_VALIDACION`. Todas las historias
de [`historias_usuario.md`](historias_usuario.md) tienen criterios. Los criterios que dependían de la Ronda 3 quedaron confirmados el 2026-09-26; `CR-001` agregó el
criterio de derivación en `HU-PAC-001`.

---

## HU-PAC-001 — Alta de paciente

```gherkin
Dado que no existe ningún paciente con DNI 30111222,

Cuando un usuario autenticado completa la ficha de alta con nombre, apellido, fecha de
nacimiento, DNI 30111222, teléfono, WhatsApp, domicilio con localidad, contacto de emergencia y
obra social, y confirma el consentimiento de tratamiento de datos,

Entonces el sistema debe crear el paciente como `Activo` y mostrar su ficha recién creada.
```

```gherkin
Dado que falta alguno de los datos obligatorios (documento o estado "sin documento", nombre,
apellido, fecha de nacimiento, teléfono, domicilio con localidad, obra social o "particular",
contacto de emergencia, consentimiento),

Cuando el usuario intenta guardar el alta,

Entonces el sistema debe impedirlo e indicar qué datos faltan.
```

```gherkin
Dado que ya existe un paciente con DNI 30111222,

Cuando un usuario intenta dar de alta a otro paciente con DNI 30111222,

Entonces el sistema debe impedir el alta, mostrar la ficha existente y ofrecer abrirla.
```

```gherkin
Dado que ya existe un paciente "Juan Pérez" nacido el 01/02/1980 con DNI 30111222,

Cuando un usuario da de alta a "Juan Pérez" nacido el 01/02/1980 con DNI 30999888,

Entonces el sistema debe advertir sobre un posible duplicado mostrando la ficha existente, y
permitir continuar el alta solo si el usuario confirma explícitamente que se trata de una
persona distinta.
```

```gherkin
Dado que un recién nacido todavía no tiene DNI tramitado,

Cuando recepción da de alta al paciente,

Entonces el sistema debe permitir guardar la ficha con un código provisorio interno en lugar
de DNI, marcando el estado de identificación como "sin documento", sin bloquear el resto del
alta.
```

```gherkin
Dado que un paciente extranjero presenta un pasaporte,

Cuando recepción carga el tipo de documento "pasaporte" y su número,

Entonces el sistema debe aceptarlo sin exigir formato de DNI argentino.
```

```gherkin
(CR-001)
Dado que recepción da de alta a un paciente derivado por "Hospital Regional",

Cuando un médico abre su ficha,

Entonces el encabezado debe mostrar la localidad del domicilio y "Derivado por: Hospital
Regional".
```

```gherkin
(CR-001)
Dado que recepción da de alta a un paciente sin indicar quién lo derivó,

Cuando guarda el alta,

Entonces el sistema debe aceptarla, porque la derivación es opcional.
```

---

## HU-PAC-002 — Búsqueda de paciente

```gherkin
Dado que existe un paciente con DNI 30111222,

Cuando un usuario autenticado busca "30111222" en el buscador de pacientes,

Entonces el sistema debe mostrar exactamente ese paciente en los resultados.
```

```gherkin
Dado que existe un paciente con número de afiliado 123456 en su obra social,

Cuando un usuario busca "123456",

Entonces el sistema debe mostrar a ese paciente en los resultados.
```

```gherkin
Dado que existe un paciente inactivo (dado de baja) con DNI 30111222,

Cuando un usuario autenticado busca "30111222",

Entonces el sistema debe mostrar ese paciente en los resultados, identificado como inactivo,
sin requerir ningún filtro adicional de "incluir inactivos".
```

```gherkin
Dado que un paciente fue dado de alta en la sede A,

Cuando un usuario de la sede B lo busca,

Entonces el sistema debe mostrar la misma ficha (no existe una ficha por sede).
```

```gherkin
Dado que no existe ningún paciente con DNI 99999999,

Cuando un usuario autenticado busca "99999999" en el buscador de pacientes,

Entonces el sistema debe mostrar un resultado vacío con la opción de crear un paciente nuevo.
```

---

## HU-PAC-003 — Modificación de datos del paciente

```gherkin
Dado que un paciente tiene teléfono 11-1111-1111,

Cuando recepción lo cambia a 11-2222-2222,

Entonces el sistema debe guardar el nuevo valor y registrar en el historial de cambios el
usuario, la fecha, el valor anterior y el nuevo.
```

```gherkin
Dado que el paciente A tiene DNI 30111222 y el paciente B tiene DNI 30111223,

Cuando un usuario intenta cambiar el DNI de B a 30111222,

Entonces el sistema debe impedirlo, indicando que ese documento ya pertenece a otro paciente.
```

---

## HU-PAC-004 — Baja y reactivación de paciente

```gherkin
Dado que un paciente está activo,

Cuando un usuario de Dirección/administración lo da de baja indicando un motivo,

Entonces el sistema debe marcarlo como inactivo sin eliminar ningún dato ni su historia clínica,
y debe seguir apareciendo en las búsquedas.
```

```gherkin
Dado que un secretario/a de recepción intenta dar de baja a un paciente,

Cuando ejecuta la acción,

Entonces el sistema debe rechazarla por falta de permiso.
```

```gherkin
Dado que un paciente activo tiene dos turnos futuros,

Cuando se lo da de baja,

Entonces el sistema debe avisar que tiene turnos futuros y listarlos, sin cancelarlos, y a partir
de ese momento no debe permitir asignarle turnos nuevos.
```

```gherkin
Dado que un paciente está inactivo,

Cuando un usuario con permiso lo reactiva,

Entonces el sistema debe marcarlo como activo y volver a permitir asignarle turnos.
```

---

## HU-PAC-005 — Registro de fallecimiento

```gherkin
Dado que un paciente está activo con turnos futuros agendados,

Cuando administración registra su fallecimiento,

Entonces el sistema debe marcar al paciente como fallecido sin cancelar automáticamente sus
turnos futuros, sin detener automáticamente sus recordatorios y sin dar de baja automáticamente
su obra social: cada uno de esos casos queda para revisión manual del personal.
```

```gherkin
Dado que un médico (no administración) intenta registrar el fallecimiento de un paciente,

Cuando ejecuta la acción,

Entonces el sistema debe rechazarla por falta de permiso.
```

```gherkin
Dado que un paciente fue marcado como fallecido por error,

Cuando administración revierte el fallecimiento indicando un motivo,

Entonces el sistema debe volver al estado anterior y registrar la reversión en auditoría.
```

---

## HU-PAC-006 — Asociar obra social a un paciente

```gherkin
Dado que un paciente no tiene ninguna obra social asociada,

Cuando recepción le asocia su primera obra social,

Entonces el sistema debe marcarla automáticamente como principal.
```

```gherkin
Dado que un paciente ya tiene una obra social marcada como principal,

Cuando recepción le asocia una segunda obra social,

Entonces el sistema debe permitirlo, exigiendo que el usuario indique cuál de las dos queda
como principal.
```

```gherkin
Dado que un paciente cambia de obra social,

Cuando recepción da por terminada la cobertura anterior y carga la nueva,

Entonces la cobertura anterior debe quedar visible en el historial de coberturas del paciente.
```

---

## HU-PAC-007 — Registrar responsable/tutor de un menor

```gherkin
Dado que se da de alta a un paciente de 10 años,

Cuando recepción intenta guardar la ficha sin ningún responsable asociado,

Entonces el sistema debe exigir al menos un responsable antes de permitir guardar.
```

```gherkin
Dado que un paciente menor tiene un responsable asociado que también es paciente de la
clínica,

Cuando se registra el vínculo,

Entonces el sistema debe permitir seleccionar como responsable a un registro de paciente ya
existente, en lugar de exigir cargarlo como un dato nuevo separado.
```

```gherkin
Dado que un paciente menor cumple 18 años,

Cuando se abre su ficha,

Entonces el vínculo con su(s) responsable(s) debe seguir visible como dato histórico, sin
haberse eliminado ni desvinculado automáticamente.
```

---

## HU-PAC-008 — Unificar fichas duplicadas

Confirmados por el cliente el 2026-09-26 (`Q-PAC-054` a `Q-PAC-056`). Se construye en un
incremento posterior al primero (`DEC-PAC-025`).

```gherkin
Dado que la ficha A (código provisorio) y la ficha B (DNI 30111222) son la misma persona,
y la ficha A tiene una consulta y un turno futuro,

Cuando Dirección/administración unifica ambas eligiendo que quede la ficha B,

Entonces la consulta y el turno futuro deben pasar a la ficha B, la ficha A debe quedar en estado
`Fusionado` apuntando a B, y la operación debe quedar auditada.
```

```gherkin
Dado que la ficha A registra alergia a la penicilina y la ficha B registra alergia a la
dipirona,

Cuando se unifican,

Entonces la ficha que queda debe registrar ambas alergias.
```

```gherkin
Dado que un secretario/a de recepción intenta unificar dos fichas,

Cuando ejecuta la acción,

Entonces el sistema debe rechazarla por falta de permiso.
```

---

## HU-PAC-009 — Registrar y ver alertas clínicas

```gherkin
Dado que un paciente tiene registrada una alergia a un medicamento,

Cuando cualquier usuario autenticado (médico o administración/recepción) abre su ficha,

Entonces el sistema debe mostrar un aviso destacado y permanente en la parte superior de la
ficha, y además una ventana emergente al momento de abrirla.
```

```gherkin
Dado que recepción carga una alergia a un medicamento en la ficha de un paciente,

Cuando un médico abre esa ficha,

Entonces la alergia debe mostrarse como alerta, marcada "pendiente de revisión médica", y el
médico debe poder confirmarla.
```

---

## HU-PAC-010 — Corrección de antecedentes clínicos

Valores confirmados en `Q-PAC-058` (ventana de 24 h, configurable) y `Q-PAC-059` (perfil
directivo sin límite).

```gherkin
Dado que un médico cargó un antecedente hace 3 horas,

Cuando lo corrige,

Entonces el sistema debe permitir la edición y registrarla en auditoría.
```

```gherkin
Dado que pasaron más de 24 horas desde que se cargó un antecedente clínico,

Cuando un médico sin perfil directivo designado intenta modificarlo,

Entonces el sistema debe rechazar la edición.
```

```gherkin
Dado que pasaron 30 días desde que se cargó un antecedente clínico,

Cuando una persona con perfil directivo designado lo corrige,

Entonces el sistema debe permitir la edición y registrarla en auditoría.
```

```gherkin
Dado que un secretario/a de recepción abre un antecedente clínico existente,

Cuando intenta modificarlo o eliminarlo,

Entonces el sistema debe rechazar la acción.
```

---

## HU-PAC-011 — Datos de contacto y contacto de emergencia

```gherkin
Dado que un paciente tiene el mismo número para teléfono y WhatsApp,

Cuando recepción lo carga,

Entonces el sistema debe permitir indicar que el WhatsApp es el mismo número, sin cargarlo dos
veces.
```

```gherkin
Dado que un paciente pidió no recibir comunicaciones salvo el aviso de turno,

Cuando se registra esa preferencia,

Entonces la ficha debe mostrarla y quedar disponible para los módulos de avisos (`MOD-014`,
`MOD-029`).
```

---

## HU-PAC-012 — Adjuntos y consentimientos

```gherkin
Dado que un paciente entrega su carnet de obra social,

Cuando recepción adjunta la imagen a la ficha,

Entonces el archivo debe quedar asociado al paciente, con el tipo de documento "carnet de obra
social", y visible desde la ficha.
```

```gherkin
Dado que un paciente no firmó el consentimiento de uso de imagen,

Cuando alguien intenta cargar su fotografía,

Entonces el sistema debe impedirlo hasta que se registre ese consentimiento.
```

---

## HU-PAC-013 — Exportar o imprimir la ficha

```gherkin
Dado que un usuario autenticado abre la ficha de un paciente,

Cuando la exporta o imprime,

Entonces el sistema debe generar la ficha y registrar en auditoría quién lo hizo y cuándo.
```

---

## HU-PAC-014 — Consultar el historial de cambios de la ficha

```gherkin
Dado que el DNI de un paciente fue corregido dos veces,

Cuando cualquier usuario autenticado consulta el historial de la ficha,

Entonces debe ver ambos cambios con usuario, fecha, valor anterior y valor nuevo.
```

---

## HU-PAC-015 — Filtrar pacientes por localidad

```gherkin
Dado que hay 3 pacientes con localidad "Localidad A" y 2 con "Localidad B",

Cuando un usuario filtra por "Localidad A",

Entonces el sistema debe listar exactamente esos 3 pacientes.
```

---

## HU-PAC-016 — Necesidad especial de atención

```gherkin
Dado que un paciente tiene registrada "movilidad reducida" como necesidad especial,

Cuando cualquier usuario abre su ficha,

Entonces esa necesidad debe verse en el encabezado de la ficha.
```

---

## Referencia — ejemplo provisto por el cliente (pertenece a MOD-011/MOD-012)

```gherkin
Dado que un paciente tiene un turno a las 10:00
y llega a las 09:30,

Cuando recepción registra su llegada,

Entonces el sistema deberá mostrar:
- horario programado;
- horario de llegada;
- estado del paciente;
- posición/prioridad correspondiente.
```

Se conserva aquí como referencia de formato porque fue el ejemplo dado por el cliente al abrir
esta fase; su desarrollo funcional completo corresponde a `MOD-011` y `MOD-012`, no a
Pacientes.
