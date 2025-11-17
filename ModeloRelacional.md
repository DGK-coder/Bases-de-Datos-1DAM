# MR DEL MODELO EER DE LA TIENDA DE VIDEOJUEGOS
Realizado por: David García, Sergio Motoya, Pascual Calvo.

- **PROVINCIA** (`codProvincia`, `nombre`)  
	PK: (`codProvincia`)

- **PRODUCTO** (`id`, `stock`, `fechaVenta`)  
	PK: (`id`)

- **PROVENIR** (`idProducto*`, `codProvincia*`)  
	PK: (`idProducto`, `codProvincia`)  
	FK: (`idProducto`) --> *PRODUCTO*  
  		(`codProvincia`) --> *PROVINCIA*

- **CATEGORIA** (`id`, `nombre`)  
	PK: (`id`)

- **PERTENECER** (`idCategoria*`, `idProducto*`)  
	PK: (`idCategoria`, `idProducto`)  
	FK: (`idCategoria`) --> *CATEGORIA*  
		(`idProducto`) -->  *PRODUCTO*  

- **TIENDA** (`codTienda`, `direccion`, `codProvincia*`, `cantidad`)  
	PK: (`codTienda`)  
	FK: (`codProvincia`) --> *PROVINCIA*  
	UK: (`codProvincia`)  

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

- **PERSONAL** (`dni`, `nombre`, `apellido1`, `apellido2`, `codTienda*`)  
	PK: (`dni`)	  
	FK: (`codTienda`) --> *TIENDA*  

- **DEPENDIENTE** (`dniDependiente*`, `corrIdent`, `dniEns*`, `tiempo`)  
	PK: (`dniDependiente`)	  
	FK: (`dniDependiente`) --> *PERSONAL*	  
			(`dniEns`) --> *DEPENDIENTE*  
			
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

  P.E: En las relaciones `PROVINCIA:PRODUCTO`, `CATEGORIA:PRODUCTO`, `PRODUCTO:DEPENDIENTE`, `SALA:LIMPIEZA` y `TIENDA:PERSONAL`, hay una perdida expresiva, ya que 1:N no es posible expresarlo en el modelo relacional.
			

			






     
