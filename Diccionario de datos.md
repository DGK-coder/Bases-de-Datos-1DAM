## Diccionario de datos
  - Tabla `PROVINCIA`

  |Columna       |Tipo de datos  |Restricción  |Descripción                                          |
  |--------------|---------------|-------------|-----------------------------------------------------|
  |`codProvincia`|`CHAR(36)`     |`PK`         |Clave primaria. código identificativo de la provincia|
  |`nombre`      |`VARCHAR(100)` |`VNN`   `UK` |Nombre que ayuda a identificar la provincia          |

  - Tabla `PRODUCTO`

  |Columna     |Tipo de datos |Restricción    |Descripción                                       |
  |------------|--------------|---------------|--------------------------------------------------|
  |`id`        |`INT`         |`PK`           |Clave primaria. código identificativo del producto|
  |`producto`  |`VARCHAR`     |`VNN` `UK`     |Nombre del producto                               |
  |`stock`     |`INT`         |               |Cantidad de producto en stock                     |
  |`fechaVenta`|`DATE`        |               |Fecha en la que se puso en venta el producto      |
  |`compra`    |`DECIMAL`     |               |Precio de compra del producto                     |
  |`venta`     |`DECIMAL`     |               |Precio de venta del producto                      |
  |`beneficio` |`DECIMAL`     |               |Beneficio calculado de `compra` y `venta`         |

  - Tabla `PROVENIR`
  
  |Columna       |Tipo de datos |Restricción  |Descripción                                                                   |
  |--------------|--------------|-------------|------------------------------------------------------------------------------|
  |`idProducto`  |`INT`         |`PK`, `FK`   |Clave primaria del producto que proviene de una provincia, apunta a `PRODUCTO`|
  |`codProvincia`|`CHAR(36)`    |`PK`, `FK`   |Clave primaria proveniente de la provincia del producto, apunta a `PROVINCIA` |
  
  - Tabla `CATEGORIA`

  |Columna    |Tipo de datos  |Restricción  |Descripción                                          |
  |-----------|---------------|-------------|-----------------------------------------------------|
  |`id`       |`INT`          |`PK`         |Clave primaria. código identificativo de la categoría|
  |`nombre`   |`VARCHAR(100)` |`VNN`  `UK`  |Nombre que "describe" el tipo de categoría a tratar  |

  - Tabla `PERTENECER`
  
  |Columna       |Tipo de datos |Restricción  |Descripción                                                                    |
  |--------------|--------------|-------------|-------------------------------------------------------------------------------|
  |`idCategoria` |`INT`         |`PK`, `FK`   |Clave primaria del producto que pertenece a una categoria, apunta a `CATEGORIA`|
  |`idProducto`  |`INT`         |`PK`, `FK`   |Clave primaria proveniente de la categoria del producto, apunta a `PRODUCTO`   |

  - Tabla `TIENDA`

  |Columna        |Tipo de datos |Restricción|Descripción                                                                                           |
  |---------------|--------------|-----------|------------------------------------------------------------------------------------------------------|
  |`codTienda`    |`INT`         |`PK`       |Clave primaria. número que identifica a la tienda                                                     |
  |`dirección`    |`VARCHAR(200)`|`VNN` `UK`     |Dirección de la tienda                                                                                |
  |`codProvincia` |`CHAR(36)`    |`FK`       |Codigo de la provincia en la que se encuentra la tienda proveniente de `PROVINCIA`                    |
  |`cantidad`     |`VARCHAR(100)`|           |Cantidad de tiendas que hay en una provincia, extraído de la tabla no expresada de la relación `HABER`|

  - Tabla `TELEFONO`
  
  |Columna       |Tipo de datos |Restricción  |Descripción                                                          |
  |--------------|--------------|-------------|---------------------------------------------------------------------|
  |`numero `     |`CHAR(9)`     |`PK`         |Clave primaria que identifica al telefono                            |
  |`codTienda`   |`CHAR(36)`    |`FK`         |Codigo de la tienda a la que pertenece el teléfono, apunta a `TIENDA`|

  - Tabla `DISPONER`
  
  |Columna       |Tipo de datos |Restricción  |Descripción                                                                  |
  |--------------|--------------|-------------|-----------------------------------------------------------------------------|
  |`idProducto`  |`INT`         |`PK`, `FK`   |Clave primaria del producto que está en una tienda, apunta a `PRODUCTO`      |
  |`codTienda`   |`CHAR(36)`    |`PK`, `FK`   |Clave primaria de la tienda la cual dispone de un producto, apunta a `TIENDA`|

  - Tabla `SALA`

  |Columna    |Tipo de datos |Restricción    |Descripción                                                                     |
  |-----------|--------------|---------------|--------------------------------------------------------------------------------|
  |`num`      |`VARCHAR(2)`  |`PK`           |Clave primaria. número que identifica la sala de la tienda                      |
  |`codTienda`|`CHAR(36)`    |`PK` `FK`      |Código de tienda de la que pertenece la sala, que proviene de la tabla `TIENDA` |
  |`metrosCua`|`INT`         |               |Metros cuadrados de la sala                                                     |
  |`nombre`   |`VARCHAR(100)`|`UK`           |Nombre de sala que ayuda a identificarla                                        |

  - Tabla `PERSONAL`

  |Columna     |Tipo de datos |Restricción    |Descripción                                                                        |
  |------------|--------------|---------------|-----------------------------------------------------------------------------------|
  |`dni`       |`CHAR(9)`     |`PK`           |Clave primaria. Documento nacional de identidad del personal                       |
  |`nombre`    |`VARCHAR(100)`|`VNN`          |Nombre del personal                                                                |
  |`apellido1` |`VARCHAR(100)`|               |Primer apellido del personal                                                       |
  |`apellido2` |`VARCHAR(100)`|               |Segundo apellido del personal                                                      |
  |`codTienda` |`CHAR(36)`    |`FK`           |Código de la tienda en la que trabaja el personal, que proviene de `TIENDA`        |
  |`fecha_nac` |`DATE`        |               |Fecha de nacimiento del personal                                                   |
  |`edad`      |`INT`         |               |Valor calculado de `fecha_nac` y la fecha actual para calcular la edad del personal|

  - Tabla `DEPENDIENTE`

  |Columna          |Tipo de datos  |Restricción  |Descripción                                                 |
  |-----------------|---------------|-------------|------------------------------------------------------------|
  |`dniDependiente` |`CHAR(9)`      |`PK`, `FK`   |DNI del dependiendote, proveniente de `PERSONAL`            |
  |`corrIdent`      |`VARCHAR(100)` |             |Correo con el que puede identificarse en la empresa         |

  - Tabla `ENSENYAR`
 
  |Columna      |Tipo de datos  |Restricción  |Descripción                                                    |
  |-------------|---------------|-------------|---------------------------------------------------------------|
  |`dniEns`     |`CHAR(9)`      |`PK`, `FK`   |DNI del dependiendote que enseña, proveniente de `DEPENDIENTE` |
  |`dniApr`     |`CHAR(9)`      |`PK`, `FK`   |DNI del dependiendote que aprende, proveniente de `DEPENDIENTE`|
  |`tiempo`     |`DATE`         |             |Fecha en la que empezó la enseñanza                            |
  
  - Tabla `VENDER`

  |Columna          |Tipo de datos  |Restricción  |Descripción                                                        |
  |-----------------|---------------|-------------|-------------------------------------------------------------------|
  |`dniDependiente` |`CHAR(9)`      |`PK`, `FK`   |DNI del dependiente, proveniente de `PERSONAL`                     |
  |`idProducto`     |`INT`          |`PK`, `FK`   |id del producto que el dependiente vende, proveniente de `PERSONAL`|
  |`cantidad`       |`INT`          |             |Cantidad del producto que el dependiente vende                     |

  - Tabla `LIMPIEZA`
 
  |Columna      |Tipo de datos  |Restricción  |Descripción                                 |
  |-------------|---------------|-------------|--------------------------------------------|
  |`dniLimpieza`|`CHAR(9)`      |`PK`, `FK`   |DNI del limpiador, proveniente de `PERSONAL`|

  - Tabla `LIMPIAR`
 
  |Columna      |Tipo de datos  |Restricción  |Descripción                                             |
  |-------------|---------------|-------------|--------------------------------------------------------|
  |`dniLimpieza`|`CHAR(9)`      |`PK`, `FK`   |DNI del limpiador, proveniente de `PERSONAL`            |
  |`numSala`    |`INT`          |`PK`, `FK`   |Numero de la sala que es limpiada, proveniente de `SALA`|
  |`codTienda`  |`CHAR(36)`     |`PK`, `FK`   |Codigo de la tienda, proveniente de `SALA`              |

## Restricciones
### PK
- Clave primaria en `PROVINCIA`: `codProvincia`
- Clave primaria en `PRODUCTO`: `id`
- Clave primaria en `PROVENIR`: `idProducto`, `idProvincia`
- Clave primaria en `CATEGORIA`: `id`
- Clave primaria en `PERTENECER`: `idCategoria`, `idProducto`
- Clave primaria en `TIENDA`: `codTienda`
- Clave primaria en `TELEFONO`: `numero`
- Clave primaria en `DISPONER`: `idProducto`, `codTienda`
- Clave primaria en `SALA`: `num`, `codTienda`
- Clave primaria en `PERSONAL`: `dni`
- Clave primaria en `DEPENDIENTE`: `dniDependiente`
- Clave primaria en `VENDER`: `dniDependiente`, `idProducto`
- Clave primaria en `LIMPIEZA`: `dniLimpieza`
- Clave primaria en `LIMPIAR`: `dniLimpieza`, `numSala`, `codTienda`
- Clave primaria en `ENSENYAR`: `dniEns`. `dniApr`
### FK
- Clave ajena en `PROVENIR`: `idProducto` referencia a `id` en la tabla `PRODUCTO`, indicando el producto que proviene de una provincia.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `PROVENIR`: `codProvincia` referencia a `codProvincia` en la tabla `PROVINCIA`, indicando la provincia de la que proviene un producto.
  - Restricción de borrado: rechazar
  - Restricción de modificación: propagar
- Clave ajena en `PERTENECER`: `idCategoria` referencia a `id` en la tabla `CATEGORIA`, indicando la categoria a la que pertenece un producto.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `PERTENECER`: `idProducto` referencia a `id` en la tabla `PRODUCTO`, indicando el producto que pertenece una categoria.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `TIENDA`: `codProvincia` referencia `codProvincia` en la tabla `PROVINCIA`, indicando la provincia en la que se encuentra una tienda.
  - Restricción de borrado: rechazar
  - Restricción de modificación: propagar
- Clave ajena en `TELEFONO`: `codTienda` referencia a `codTienda` en la tabla `TIENDA`, indicando la tienda a la que pertenece ese teléfono.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `DISPONER`: `idProducto` referencia a `id` en la tabla `PRODUCTO`, indicando los productos de los que dispone una tienda.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `DISPONER`: `codTienda` referencia a `codTienda` en la tabla `TIENDA`, indicando la tienda que dispone de ciertos productos.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `SALA`: `codTienda` referencia a `codTienda` en la tabla `TIENDA`, indicando a que tienda pertenece esa sala.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `PERSONAL`: `codTienda` referencia a `codTienda` en la tabla `TIENDA`, indicando la tienda en la que trabaja el personal.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `DEPENDIENTE`: `dniDependiente` referencia a `dni` en la tabla `PERSONAL`, indicando el dni del personal dependiente.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `DEPENDIENTE`: `dniEns` referencia a `dni` en la tabla `PERSONAL`, indicando el dni del dependiente que enseña a otro.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `VENDER`: `dniDependiente` referencia a `dniDependiente` en la tabla `DEPENDIENTE`, indicando el empleado que vende un producto.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `VENDER`: `idProducto` referencia a `id` en la tabla `PRODUCTO`, indicando el producto que es vendido por un empleado.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `LIMPIEZA`: `dniLimpieza` referencia a `dni` en `PERSONAL`, indicando el dni del personal de limpieza.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `LIMPIAR`: `dniLimpieza` referencia a `dniLimpieza` en `LIMPIEZA`, indicando el personal que limpia una sala.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `LIMPIAR`: `numSala` referencia a `num` en `SALA`, indicando la sala que es limpiada.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `LIMPIAR`: `codTienda` referencia a `codTienda` en la tabla `TIENDA`, indicando la tienda de la sala que es limpiada.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `ENSENYAR`: `dniEns` referencia a `dniDependiente` en la tabla `DEPENDIENTE`, indicando el dependiente que enseña.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
- Clave ajena en `ENSENYAR`: `dniApr` referencia a `dniDependiente` en la tabla `DEPENDIENTE`, indicando el dependiente que aprende.
  - Restricción de borrado: propagar
  - Restricción de modificación: propagar
