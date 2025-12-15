# MR DEL MODELO EER DE LA TIENDA DE VIDEOJUEGOS
Realizado por: David García, Sergio Motoya, Pascual Calvo.

- **PROVINCIA** (`codProvincia`, `nombre`)  
	PK: (`codProvincia`)  
	VNN: (`nombre`)  
	UK: (`nombre`)

- **PRODUCTO** (`id`, `nombre`, `stock`, `fechaVenta`,`compra`,`venta`,`beneficio`)  
	PK: (`id`)  
	VNN: (`nombre`)  
	UK: (`nombre`)

- **PROVENIR** (`idProducto*`, `codProvincia*`)  
	PK: (`idProducto`, `codProvincia`)  
	FK: (`idProducto`) --> *PRODUCTO*  
  		(`codProvincia`) --> *PROVINCIA*

- **CATEGORIA** (`id`, `nombre`)  
	PK: (`id`)  
	VNN: (`nombre`)

- **PERTENECER** (`idCategoria*`, `idProducto*`)  
	PK: (`idCategoria`, `idProducto`)  
	FK: (`idCategoria`) --> *CATEGORIA*  
		(`idProducto`) -->  *PRODUCTO*  

- **TIENDA** (`codTienda`, `direccion`, `codProvincia*`, `cantidad`)  
	PK: (`codTienda`)  
	FK: (`codProvincia`) --> *PROVINCIA*  
  	VNN: (`codProvincia`)  
  	VNN: (`direccion`)  
  	UK: (`direccion`)

- **TELEFONO** (`numero`, `codigo*`)  
	PK: (`numero`)	  
	FK: (`codigo`) --> *TIENDA*	  
 
- **DISPONER** (`idProducto*`, `codTienda*`)	  
	PK: (`idProducto`, `codTienda`)	  
	FK: (`idProducto`) --> *PRODUCTO*	  
        (`codTienda`) --> *TIENDA*	  

- **SALA** (`num`, `codTienda*`, `nombre`, `metrosCua`)  
	PK: (`num`, `codTienda`)	  
	FK: (`codTienda`) --> *TIENDA*  
	VNN: (`nombre`)  
	UK: (`nombre`)

- **PERSONAL** (`dni`, `nombre`, `apellido1`, `apellido2`, `codTienda`*,`fecha_nac`,`edad`)  
	PK: (`dni`)  
	FK: (`codTienda`) --> *TIENDA*  
	VNN: (`nombre`)  
	VNN: (`apellido1`)

- **DEPENDIENTE** (`dniDependiente*`, `corrIdent`)  
	PK: (`dniDependiente`)	  
	FK: (`dniDependiente`) --> *PERSONAL*

- **ENSENYAR** (`dniEns*`, `dniApr*`,`tiempo`)  
  	PK: (`dniEns`, `dniApr`)  
  	FK: (`dniEns`,`dniApr`) --> *DEPENDIENTE*  
			
- **VENDER** (`dniDependiente*`, `idProducto*`, `cantidad`)  
	PK: (`dniDependiente`, `idProducto`)  
	FK: (`dniDependiente`) --> *DEPENDIENTE*  
			(`idProducto`) --> *PRODUCTO*  

- **LIMPIEZA** (`dniLimpieza*`)  
	PK: (`dniLimpieza`)  
	FK: (`dniLimpieza`) --> *PERSONAL*  

- **LIMPIAR** (`dniLimpieza*`, `numSala*`, `codTienda*`)  
	PK: (`dniLimpieza`, `numSala`, `codTienda`)  
	FK: (`dniLimpieza`) --> *LIMPIEZA*  
			(`numSala`, `codTienda`) --> *SALA*

  P.E: En las relaciones `PROVINCIA:PRODUCTO`, `CATEGORIA:PRODUCTO`, `PRODUCTO:DEPENDIENTE`, `DEPENDIENTE:ENSENYAR`, `SALA:LIMPIEZA`, `TIENDA:SALA` y `TIENDA:PERSONAL`, hay una perdida expresiva, ya que 1:N no es posible expresarlo en el modelo relacional.

  P.E: El atributo Nombre de SALA es opcional y no puede expresarse en el modelo relacional.	

			






     
