# INSERTAR REGISTROS A CADA TABLA
## USAR BASE DE DATOS
```sql
use TiendasDeVideojuegos;
```
## CREACION DE REGISTROS
### TABLA `PROVINCIA`
```sql
INSERT INTO PROVINCIA (nombre) VALUES
  ('Alicante'),
  ('Valencia'),
  ('Madrid'),
  ('Barcelona'),
  ('Murcia'),
  ('Sevilla'),
  ('Granada'),
  ('Zaragoza'),
  ('Bilbao'),
  ('Tarragona');
```

### TABLA `PRODUCTO`
```sql
INSERT INTO PRODUCTO (stock, fechaVenta, compra, venta) VALUES
  (50,'2024-01-10', 10.00, 15.00),
  (NULL,'2024-01-11', 8.50, 12.00),
  (35,'2024-01-12', 5.00, 9.50),
  (60,'2024-01-13', 20.00, 27.50),
  (NULL,'2024-01-14', 12.00, 18.00),
  (80,'2024-01-15', 7.25, 11.00),
  (10,'2024-01-16', 9.00, 14.00),
  (25,'2024-01-17', 25.00, 32.00),
  (40,NULL,6.00, 10.00),
  (55,'2024-01-19', 11.50, 16.50);
```
### TABLA `PROVENIR`
```sql
INSERT INTO PROVENIR (idProducto, codProvincia) VALUES
  (1,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Alicante')),
  (2,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Valencia')),
  (3,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Madrid')),
  (4,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Barcelona')),
  (5,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Sevilla')),
  (6,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Murcia')),
  (7,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Sevilla')),
  (8,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Granada')),
  (9,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Zaragoza')),
  (10,(SELECT codProvincia FROM PROVINCIA WHERE nombre='Tarragona'));
```

### TABLA `CATEGORIA`
```sql
INSERT INTO CATEGORIA (nombre) VALUES
  ('Acción'),
  ('Aventura'),
  ('Deportes'),
  ('Terror'),
  ('Estrategia'),
  ('Simulación'),
  ('Carreras'),
  ('Shooter'),
  ('Cooperativo'),
  ('Familiar');
```

### TABLA `PERTENECER`
```sql
INSERT INTO PERTENECER (idCategoria, idProducto) VALUES
  (1,1),(2,2),(3,3),(4,4),(5,5),
  (6,6),(7,7),(8,8),(9,9),(10,10);
```

### TABLA `TIENDA`
```sql
INSERT INTO TIENDA (direccion, codProvincia, cantidad) VALUES
  ('Calle A', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Alicante'),10),
  ('Calle B', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Valencia'),12),
  ('Calle C', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Madrid'),8),
  ('Calle D', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Barcelona'),20),
  ('Calle E', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Sevilla'),
  ('Calle F', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Murcia'),
  ('Calle G', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Sevilla'),
  ('Calle H', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Granada')),
  ('Calle I', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Zaragoza')),14),
  ('Calle J',(SELECT codProvincia FROM PROVINCIA WHERE nombre='Tarragona'),16);
```

### TABLA `TELEFONO`
```sql
INSERT INTO TELEFONO (numero, codTienda) VALUES
  ('600000001',(SELECT codTienda FROM TIENDA WHERE direccion='Calle A')),
  ('600000002',(SELECT codTienda FROM TIENDA WHERE direccion='Calle B')),
  ('600000003',(SELECT codTienda FROM TIENDA WHERE direccion='Calle C')),
  ('600000004',(SELECT codTienda FROM TIENDA WHERE direccion='Calle D')),
  ('600000005',(SELECT codTienda FROM TIENDA WHERE direccion='Calle E')),
  ('600000005',(SELECT codTienda FROM TIENDA WHERE direccion='Calle F')),
  ('600000007',(SELECT codTienda FROM TIENDA WHERE direccion='Calle G')),
  ('600000008',(SELECT codTienda FROM TIENDA WHERE direccion='Calle H')),
  ('600000008',(SELECT codTienda FROM TIENDA WHERE direccion='Calle I')),
  ('600000010',(SELECT codTienda FROM TIENDA WHERE direccion='Calle J'));
```

### TABLA `DISPONER`
```sql
INSERT INTO DISPONER (idProducto, codTienda) VALUES
  (1,(SELECT codTienda FROM TIENDA WHERE direccion='Calle A')),
  (2,(SELECT codTienda FROM TIENDA WHERE direccion='Calle B')),
  (3,(SELECT codTienda FROM TIENDA WHERE direccion='Calle C')),
  (4,(SELECT codTienda FROM TIENDA WHERE direccion='Calle D')),
  (5,(SELECT codTienda FROM TIENDA WHERE direccion='Calle E')),
  (6,(SELECT codTienda FROM TIENDA WHERE direccion='Calle F')),
  (7,(SELECT codTienda FROM TIENDA WHERE direccion='Calle G')),
  (8,(SELECT codTienda FROM TIENDA WHERE direccion='Calle H')),
  (9,(SELECT codTienda FROM TIENDA WHERE direccion='Calle I')),
  (10,(SELECT codTienda FROM TIENDA WHERE direccion='Calle J'));
```

### TABLA `SALA`
```sql
INSERT INTO SALA (codTienda, metrosCua, nombre) VALUES
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle A'),NULL,'Sala A'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle B'),60,'Sala B'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle C'),45,'Sala C'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle C'),70, NULL),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle D'),55,'Sala E'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle E'),65,'Sala F'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle F'),40,'Sala G'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle G'),48, NULL),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle H'),58,'Sala I'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle I'),NULL,'Sala J');
```

### TABLA `PERSONAL`
```sql
INSERT INTO PERSONAL (dni, nombre, apellido1, apellido2, codTienda, fecha_nac) VALUES
  ('11111111A','Juan','Pérez',NULL,(SELECT codTienda FROM TIENDA WHERE direccion='Calle A'), '1990-05-12'),
  ('22222222B','Ana','García','Ruiz',(SELECT codTienda FROM TIENDA WHERE direccion='Calle B') '1988-09-20'),
  ('33333333C','Luis','Martín','Soto',(SELECT codTienda FROM TIENDA WHERE direccion='Calle C'), '1995-03-08'),
  ('44444444D','Marta','Díaz','Gil',(SELECT codTienda FROM TIENDA WHERE direccion='Calle D'), '1992-11-15'),
  ('55555555E','Carlos','Vega','Mora',(SELECT codTienda FROM TIENDA WHERE direccion='Calle E'), '1985-01-30'),
  ('66666666F','Laura','Navarro','Cruz',(SELECT codTienda FROM TIENDA WHERE direccion='Calle F'), '1998-07-04'),
  ('77777777G','Pablo','Ortega','León',(SELECT codTienda FROM TIENDA WHERE direccion='Calle G'), '1991-12-22'),
  ('88888888H','Sara','Romero',NULL,(SELECT codTienda FROM TIENDA WHERE direccion='Calle H'), '1996-04-18'),
  ('99999999I','Luis','Torres','Blanco',(SELECT codTienda FROM TIENDA WHERE direccion='Calle I'), '1989-06-10'),
  ('00000000J','Elena','Ramos','Serrano',(SELECT codTienda FROM TIENDA WHERE direccion='Calle J'), '1988-09-20');
```

### TABLA `DEPENDIENTE`
```sql
INSERT INTO DEPENDIENTE (dniDependiente, corrIdent) VALUES
  ('11111111A','emp1@tienda.com'),
  ('22222222B','emp2@tienda.com'),
  ('33333333C',NULL),
  ('44444444D','emp4@tienda.com'),
  ('55555555E','emp5@tienda.com'),
  ('66666666F','emp6@tienda.com'),
  ('77777777G',NULL),
  ('88888888H','emp8@tienda.com'),
  ('99999999I','emp9@tienda.com'),
  ('00000000J','emp10@tienda.com');
```

### TABLA `ENSENYAR`
```sql
INSERT INTO ENSENYAR (dniEns, dniApr, tiempo) VALUES
  ('11111111A','22222222B','2023-01-01'),
  ('22222222B','33333333C','2023-01-02'),
  ('33333333C','44444444D','2023-01-08'),
  ('44444444D','55555555E','2023-01-04'),
  ('55555555E','66666666F',NULL),
  ('66666666F','77777777G','2023-01-06'),
  ('77777777G','88888888H','2023-01-07'),
  ('88888888H','99999999I','2023-01-08'),
  ('99999999I','00000000J','2023-01-09'),
  ('00000000J','11111111A',NULL);
```

### TABLA `VENDER`
```sql
INSERT INTO VENDER (dniDependiente, idProducto, cantidad) VALUES
  ('11111111A',1,2),
  ('22222222B',2,1),
  ('33333333C',3,NULL),
  ('44444444D',4,2),
  ('55555555E',5,1),
  ('66666666F',6,4),
  ('77777777G',7,2),
  ('88888888H',8,NULL),
  ('99999999I',9,1),
  ('00000000J',10,2);
```

### TABLA `LIMPIEZA`
```sql
INSERT INTO LIMPIEZA (dniLimpieza) VALUES
  ('11111111A'),
  ('22222222B'),
  ('33333333C'),
  ('44444444D'),
  ('55555555E'),
  ('66666666F'),
  ('77777777G'),
  ('88888888H'),
  ('99999999I'),
  ('00000000J');
```

### TABLA `LIMPIAR`
```sql
INSERT INTO LIMPIAR (dniLimpieza, numSala, codTienda) VALUES
  ('11111111A',1,(SELECT codTienda FROM TIENDA WHERE direccion='Calle A')),
  ('22222222B',2,(SELECT codTienda FROM TIENDA WHERE direccion='Calle B')),
  ('33333333C',3,(SELECT codTienda FROM TIENDA WHERE direccion='Calle C')),
  ('44444444D',4,(SELECT codTienda FROM TIENDA WHERE direccion='Calle D')),
  ('55555555E',5,(SELECT codTienda FROM TIENDA WHERE direccion='Calle E')),
  ('66666666F',6,(SELECT codTienda FROM TIENDA WHERE direccion='Calle F')),
  ('77777777G',7,(SELECT codTienda FROM TIENDA WHERE direccion='Calle G')),
  ('88888888H',8,(SELECT codTienda FROM TIENDA WHERE direccion='Calle H')),
  ('99999999I',9,(SELECT codTienda FROM TIENDA WHERE direccion='Calle I')),
  ('00000000J',10,(SELECT codTienda FROM TIENDA WHERE direccion='Calle J'));
```
