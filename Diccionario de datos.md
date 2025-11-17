- Tabla `CATEGORIA`

  |Columna    |Tipo de datos  |Restricción  |Descripción                                          |
  |-----------|---------------|-------------|-----------------------------------------------------|
  |`ID`       |`INT`          |`PK`         |Clave primaria. código identificativo de la categoría|
  |`Nombre`   |`VARCHAR(100)` |`VNN`        |Nombre que "describe" el tipo de categoría a tratar  |

- Tabla `PROVINCIA`

  |Columna       |Tipo de datos  |Restricción  |Descripción                                          |
  |--------------|---------------|-------------|-----------------------------------------------------|
  |`CodProvincia`|`INT`          |`PK`         |Clave primaria. código identificativo de la provincia|
  |`Nombre`      |`VARCHAR(100)` |`VNN`        |Nombre que ayuda a identificar la provincia          |

- Tabla `PRODUCTO`

  |Columna     |Tipo de datos |Restricción    |Descripción                                       |
  |------------|--------------|---------------|--------------------------------------------------|
  |`ID`        |`INT`         |`PK`           |Clave primaria. código identificativo del producto|
  |`Stock`     |`INT`         |               |Cantidad de producto en stock                     |
  |`FechaVenta`|`DATE`        |               |Fecha en la que se puso en venta el producto      |

- Tabla `VENDER`

  |Columna    |Tipo de datos  |Restricción  |Descripción                      |
  |-----------|---------------|-------------|---------------------------------|
  |`cantidad` |`INT`          |             |cantidad de productos al venderse|

- Tabla `TIENDA`

  |Columna    |Tipo de datos |Restricción    |Descripción                                                                                           |
  |-----------|--------------|---------------|------------------------------------------------------------------------------------------------------|
  |`CodTienda`|`INT`         |`PK`           |Clave primaria. número que identifica a la tienda                                                     |
  |`Dirección`|`VARCHAR(200)`|               |Dirección de la tienda                                                                                |
  |`Teléfono` |`VARCHAR(9)`  |               |Teléfono de la tienda                                                                                 |
  |`Cantidad` |`VARCHAR(100)`|`FK`           |Cantidad de tiendas que hay en una provincia, extraído de la tabla no expresada de la relación `HABER`|

- Tabla `SALA`

  |Columna    |Tipo de datos |Restricción    |Descripción                                                                     |
  |-----------|--------------|---------------|--------------------------------------------------------------------------------|
  |`Num`      |`INT`         |`PK`           |Clave primaria. número que identifica la sala de la tienda                      |
  |`MetrosCua`|`INT`         |               |Metros cuadrados de la sala                                                     |
  |`Nombre`   |`VARCHAR(100)`|               |Nombre de sala que ayuda a identificarla                                        |
  |`CodTienda`|`INT`         |`PK` `FK`       |Código de tienda de la que pertenece la sala, que proviene de la tabla `TIENDA`|

- Tabla `PERSONAL`

  |Columna     |Tipo de datos |Restricción    |Descripción                                                                     |
  |------------|--------------|---------------|--------------------------------------------------------------------------------|
  |`DNI`       |`VARCHAR(9)`  |`PK`           |Clave primaria. Documento nacional de identidad del personal                    |
  |`Nombre`    |`VARCHAR(100)`|               |Nombre del personal                                                             |
  |`Apellido1` |`VARCHAR(100)`|               |Primer apellido del personal                                                    |
  |`Apellido2` |`VARCHAR(100)`|               |Segundo apellido del personal                                                   |
  |`ProvOrigen`|`INT`         |`FK`           |Código de provincia de la que pertenece el personal, que proviene de `PROVINCIA`|

- Tabla `DEPENDIENTE`

  |Columna     |Tipo de datos  |Restricción  |Descripción                                        |
  |------------|---------------|-------------|---------------------------------------------------|
  |`CorrIdent` |`VARCHAR(100)` |             |Correo con el que puede identificarse en la empresa|

- Tabla `ENSEÑAR`

  |Columna    |Tipo de datos  |Restricción  |Descripción                               |
  |-----------|---------------|-------------|------------------------------------------|
  |`Tiempo`   |`INT`          |             |Número de días siendo enseñado o enseñando|

- Clave primaria en CATEGORIA: ID
- Clave primaria en PROVINCIA: CodProvincia
- Clave primaria en PRODUCTO: ID
- Clave primaria en TIENDA: CodTienda
- Clave primaria en SALA: Num
- Clave primaria en PERSONAL: DNI
- Clave ajena en TIENDA: `Cantidad` referencia a una relación de una tabla no expresada
  - Restricción de borrado: rechazar
  - Restricción de modificación: propagar
- Clave ajena en SALA: `CodTienda` referencia a `CodTienda` en la tabla `TIENDA`, indicando a que tienda pertenece esa sala
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en PERSONAL: `ProvOrigen` referencia a `CodProvincia` en la tabla `PROVINCIA`, indicando la provincia de la que se originan los empleados
  - Restricción de borrado: rechazar
  - Restricción de modificación: propagar
