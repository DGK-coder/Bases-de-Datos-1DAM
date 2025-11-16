# AC305
## Enunciado
 (RABD.6 // CE6a, CE6b, CE6c // 3p)Crea las tablas necesarias con datos ficticios (con al menos 5 registros cada tabla) que respete las restricciones semánticas del modelo relacional a partir del siguiente esquema relacional:

## Respuesta
- Tabla `EMPLEADO`

|Columna    |Tipo de datos  |Restricción  |Descripción                                         |
|-----------|---------------|-------------|----------------------------------------------------|
|`nif`      |`VARCHAR(9)`   |`PK`         |Clave primaria. documento de identifiación nacional.|
|`nombre`   |`VARCHAR(100)` |`VNN`        |Dato obligatorio. Nombre de trabajador              |
|`direccion`|`VARCHAR(100)` |             |Dirección del trabajador                            |
|`cargo`    |`VARCHAR(30)`  |             |Cargo del trabajador                                |

- Tabla `VEHICULO`

|Columna    |Tipo de datos |Restricción    |Descripción                                                                |
|-----------|--------------|---------------|---------------------------------------------------------------------------|
|`matricula`|`VARCHAR(7)`  |`PK`           |Identificador que habilita la circulación de los vehículos.                |
|`codigo`   |`INT`         |`UK`           |Dato obligatorio. código de registro                                       |
|`modelo`   |`VARCHAR(30)` |               |Modelo de vehículo                                                         |
|`empleado` |`VARCHAR(100)`|`FK` `VNN`     |Empleado, dato extraido de la tabla `EMPLEADO`                             |

-Clave primaria en EMPLEADO: nif
-Clave primaria en VEHICULO: matricula
-Clave ajena en LIBRO: `nombre` referencia a `empleado` en la tabla `VEHICULO`, indicando la relación entre un empleado a cargo de un vehículo