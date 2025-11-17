# ¿Por qué lo hemos hecho así?

 
Hemos hecho el modelo así porque queríamos aplicar todo lo que hemos aprendido en clase, pero dentro de un caso real, como una cadena de tiendas de videojuegos. 
Decidimos usar entidades como tienda, sala, producto, categoría, provincia y personal, y este último lo hicimos con especialización en dependiente y limpieza, 
las subclases serán parciales ya que podríamos tener otro tipo de empleado, además es exclusiva porque un dependiente no puede ser parte de la limpieza y viceversa.

**Tienda:** Tiene como atributos el código, dirección y teléfono que será un atributo multivaluado. Cada tienda puede tener varias salas, 
vender diferentes productos y estar ubicada en una provincia concreta. Además, en cada tienda trabajan entre una y cinco personas.

**Sala:** Sus atributos son el número de sala (Num), los metros cuadrados (MetrosCua), el nombre (que es opcional) y el código de tienda como identificador parcial. 
Cada tienda puede tener varias salas, y las salas pueden ser limpiadas por uno o varios empleados del personal de limpieza. 

**Producto:**  Tiene como atributos el ID, el stock y la fecha de venta. Un producto puede pertenecer a una o varias categorías, venderse en distintas tiendas y proceder de una o más provincias. 
Además, los dependientes son los encargados de venderlos y se registra la cantidad vendida.

**Categoría:**  Sus atributos son el ID y el nombre. Un producto puede pertenecer a una o varias categorías, y también pueden existir categorías sin productos.

**Personal:**  Se conoce el DNI, el nombre completo (nombre y dos apellidos) y la provincia de origen. Cada persona puede estar asignada a una tienda o no, pero siempre debe existir al menos un trabajador por tienda.

**Dependiente:** El subtipo Dependiente hereda los datos del personal y añade el atributo correo identificativo (CorIdent), que utilizan para acceder a la información de la tienda. 
Además, se relacionan entre sí mediante una relación reflexiva llamada Enseñar, donde se guarda el tiempo de formación. 
También participan en la relación Vender con los productos, donde se indica la cantidad vendida.

**Limpieza:** El subtipo Limpieza representa al personal encargado de mantener las salas en buen estado. No añade nuevos atributos, ya que hereda los del personal, 
pero se relaciona con la entidad Sala mediante la relación Limpiar, que refleja qué salas limpia cada trabajador, un limpiador puede limpiar varias salas y una sala puede ser limpiada por varios empleados.
