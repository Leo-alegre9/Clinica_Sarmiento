# Criterios de aceptación globales

Criterios que aplican transversalmente a cualquier módulo, más allá de los criterios
específicos de cada historia de usuario (que viven en
`03_Modulos/MOD-###.../criterios_aceptacion.md`).

## Auditoría (aplica a todo dato clasificado como sensible, ver `06_Datos/datos_sensibles.md`)

```gherkin
Dado que un usuario autorizado modifica un campo sensible de un registro,

Cuando la modificación se guarda,

Entonces el sistema debe registrar: usuario, fecha/hora, campo modificado,
valor anterior y valor nuevo.
```

## Permisos (aplica a toda pantalla/acción con control de rol)

```gherkin
Dado que un usuario no tiene el permiso requerido para una acción,

Cuando intenta ejecutar esa acción (por UI o por ruta directa),

Entonces el sistema debe rechazarla y no debe exponer datos ni realizar cambios.
```

## Baja lógica (aplica a entidades con RN-DAT-001 confirmada)

```gherkin
Dado que un registro tiene información clínica, financiera o de auditoría asociada,

Cuando un usuario intenta eliminarlo,

Entonces el sistema no debe permitir la eliminación física,
y debe ofrecer en su lugar una baja lógica/anulación/archivado.
```

Estos criterios son plantillas: se concretan por módulo una vez que sus reglas de negocio
específicas estén `CONFIRMADO`.
