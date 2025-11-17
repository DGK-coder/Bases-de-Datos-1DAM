## Tablas
  - Tabla `PROVINCIA`

  |Columna       |Tipo de datos  |Restricción  |Descripción                                          |
  |--------------|---------------|-------------|-----------------------------------------------------|
  |`CodProvincia`|`INT`          |`PK`         |Clave primaria. código identificativo de la provincia|
  |`Nombre`      |`VARCHAR(100)` |             |Nombre que ayuda a identificar la provincia          |

  - Tabla `PRODUCTO`

  |Columna     |Tipo de datos |Restricción    |Descripción                                       |
  |------------|--------------|---------------|--------------------------------------------------|
  |`ID`        |`INT`         |`PK`           |Clave primaria. código identificativo del producto|
  |`Stock`     |`INT`         |               |Cantidad de producto en stock                     |
  |`FechaVenta`|`DATE`        |               |Fecha en la que se puso en venta el producto      |

  - Tabla `PROVENIR`
  
  |Columna       |Tipo de datos |Restricción  |Descripción                                                                   |
  |--------------|--------------|-------------|------------------------------------------------------------------------------|
  |`idProducto`  |`INT`         |`PK`, `FK`   |Clave primaria del producto que proviene de una provincia, apunta a `PRODUCTO`|
  |`codProvincia`|`INT`         |`PK`, `FK`   |Clave primaria proveniente de la provincia del producto, apunta a `PROVINCIA` |
  
  - Tabla `CATEGORIA`

  |Columna    |Tipo de datos  |Restricción  |Descripción                                          |
  |-----------|---------------|-------------|-----------------------------------------------------|
  |`ID`       |`INT`          |`PK`         |Clave primaria. código identificativo de la categoría|
  |`Nombre`   |`VARCHAR(100)` |             |Nombre que "describe" el tipo de categoría a tratar  |

  - Tabla `PERTENECER`
  
  |Columna       |Tipo de datos |Restricción  |Descripción                                                                    |
  |--------------|--------------|-------------|-------------------------------------------------------------------------------|
  |`idCategoria` |`INT`         |`PK`, `FK`   |Clave primaria del producto que pertenece a una categoria, apunta a `CATEGORIA`|
  |`idProducto`  |`INT`         |`PK`, `FK`   |Clave primaria proveniente de la categoria del producto, apunta a `PRODUCTO`   |

  - Tabla `TIENDA`

  |Columna    |Tipo de datos |Restricción    |Descripción                                                                                           |
  |-----------|--------------|---------------|------------------------------------------------------------------------------------------------------|
  |`CodTienda`    |`INT`         |`PK`       |Clave primaria. número que identifica a la tienda                                                     |
  |`Dirección`    |`VARCHAR(200)`|           |Dirección de la tienda                                                                                |
  |`codProvincia` |`INT`         |`FK`       |Codigo de la provincia en la que se encuentra la tienda proveniente de `PROVINCIA`                    |
  |`Cantidad`     |`VARCHAR(100)`|           |Cantidad de tiendas que hay en una provincia, extraído de la tabla no expresada de la relación `HABER`|

  - Tabla `TELEFONO`
  
  |Columna       |Tipo de datos |Restricción  |Descripción                                                          |
  |--------------|--------------|-------------|---------------------------------------------------------------------|
  |`numero `     |`INT`         |`PK`         |Clave primaria que identifica al telefono                            |
  |`idProducto`  |`INT`         |`FK`         |Codigo de la tienda a la que pertenece el teléfono, apunta a `TIENDA`|

  - Tabla `DISPONER`
  
  |Columna       |Tipo de datos |Restricción  |Descripción                                                                  |
  |--------------|--------------|-------------|-----------------------------------------------------------------------------|
  |`idProducto`  |`INT`         |`PK`, `FK`   |Clave primaria del producto que está en una tienda, apunta a `PRODUCTO`      |
  |`codTienda`   |`INT`         |`PK`, `FK`   |Clave primaria de la tienda la cual dispone de un producto, apunta a `TIENDA`|

- Tabla `SALA`

  |Columna    |Tipo de datos |Restricción    |Descripción                                                                     |
  |-----------|--------------|---------------|--------------------------------------------------------------------------------|
  |`num`      |`INT`         |`PK`           |Clave primaria. número que identifica la sala de la tienda                      |
  |`CodTienda`|`INT`         |`PK` `FK`      |Código de tienda de la que pertenece la sala, que proviene de la tabla `TIENDA`|
  |`metrosCua`|`INT`         |               |Metros cuadrados de la sala                                                     |
  |`nombre`   |`VARCHAR(100)`|               |Nombre de sala que ayuda a identificarla                                        |

- Tabla `PERSONAL`

  |Columna     |Tipo de datos |Restricción    |Descripción                                                                     |
  |------------|--------------|---------------|--------------------------------------------------------------------------------|
  |`dni`       |`VARCHAR(9)`  |`PK`           |Clave primaria. Documento nacional de identidad del personal                    |
  |`nombre`    |`VARCHAR(100)`|               |Nombre del personal                                                             |
  |`apellido1` |`VARCHAR(100)`|               |Primer apellido del personal                                                    |
  |`apellido2` |`VARCHAR(100)`|               |Segundo apellido del personal                                                   |
  |`codTienda` |`INT`         |`FK`           |Código de la tienda en la que trabaja el personal, que proviene de `TIENDA`     |

- Tabla `DEPENDIENTE`

  |Columna          |Tipo de datos  |Restricción  |Descripción                                                 |
  |-----------------|---------------|-------------|------------------------------------------------------------|
  |`dniDependiente` |`VARCHAR(9)`   |`PK`, `FK`   |DNI del dependiendote, proveniente de `PERSONAL`            |
  |`CorrIdent`      |`VARCHAR(100)` |             |Correo con el que puede identificarse en la empresa         |
  |`dniEns`         |`VARCHAR(9)`   |`FK`         |DNI del dependiente que le enseña, proveniente de `PERSONAL`|
  |`tiempo`         |`VARCHAR(100)` |             |Cuanto tiempo lleva siendo enseñado por el otro dependiente |

  - Tabla `VENDER`

  |Columna          |Tipo de datos  |Restricción  |Descripción                                                        |
  |-----------------|---------------|-------------|-------------------------------------------------------------------|
  |`dniDependiente` |`VARCHAR(9)`   |`PK`, `FK`   |DNI del dependiente, proveniente de `PERSONAL`                     |
  |`idProducto`     |`INT`          |`PK`, `FK`   |id del producto que el dependiente vende, proveniente de `PERSONAL`|
  |`cantidad`       |`INT`          |             |Cantidad del producto que el dependiente vende                     |

  - Tabla `LIMPIEZA`
 
  |Columna      |Tipo de datos  |Restricción  |Descripción                                 |
  |-------------|---------------|-------------|--------------------------------------------|
  |`dniLimpieza`|`VARCHAR(9)`   |`PK`, `FK`   |DNI del limpiador, proveniente de `PERSONAL`|

  - Tabla `LIMPIAR`
 
  |Columna      |Tipo de datos  |Restricción  |Descripción                                             |
  |-------------|---------------|-------------|--------------------------------------------------------|
  |`dniLimpieza`|`VARCHAR(9)`   |`PK`, `FK`   |DNI del limpiador, proveniente de `PERSONAL`            |
  |`numSala`    |`INT`          |`PK`, `FK`   |Numero de la sala que es limpiada, proveniente de `SALA`|
  |`codTienda`  |`INT`          |`PK`, `FK`   |Codigo de la tienda, proveniente de `SALA`              |

## Restricciones
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
