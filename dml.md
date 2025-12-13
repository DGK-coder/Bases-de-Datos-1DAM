# INSERTAR REGISTROS A CADA TABLA
## USAR BASE DE DATOS
```sql
use TiendasDeVideojuegos;
```
## CREACION DE REGISTROS
### TABLA `PROVINCIA`
```sql
INSERT INTO PROVINCIA (codProvincia, nombre) VALUES
  ('11111111-1111-1111-1111-111111111111','Alicante'),
  ('22222222-2222-2222-2222-222222222222', NULL),
  ('33333333-3333-3333-3333-333333333333','Madrid'),
  ('44444444-4444-4444-4444-444444444444','Barcelona'),
  ('55555555-5555-5555-5555-555555555555','Murcia'),
  ('66666666-6666-6666-6666-666666666666','Sevilla'),
  ('77777777-7777-7777-7777-777777777777','Granada'),
  ('88888888-8888-8888-8888-888888888888','Zaragoza'),
  ('99999999-9999-9999-9999-999999999999','Bilbao'),
  ('aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa', NULL);
```

### TABLA `PRODUCTO`
```sql
INSERT INTO PRODUCTO (stock, fechaVenta) VALUES
  (50,'2024-01-10'),
  (NULL,'2024-01-11'),
  (35,'2024-01-12'),
  (60,'2024-01-13'),
  (NULL,'2024-01-14'),
  (80,'2024-01-15'),
  (10,'2024-01-16'),
  (25,'2024-01-17'),
  (40,NULL),
  (55,'2024-01-19');
```
### TABLA `PROVENIR`
```sql
INSERT INTO PROVENIR (idProducto, codProvincia) VALUES
  (1,'11111111-1111-1111-1111-111111111111'),
  (2,'22222222-2222-2222-2222-222222222222'),
  (3,'33333333-3333-3333-3333-333333333333'),
  (4,'44444444-4444-4444-4444-444444444444'),
  (5,'55555555-5555-5555-5555-555555555555'),
  (6,'66666666-6666-6666-6666-666666666666'),
  (7,'77777777-7777-7777-7777-777777777777'),
  (8,'88888888-8888-8888-8888-888888888888'),
  (9,'99999999-9999-9999-9999-999999999999'),
  (10,'aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa');
```

### TABLA `CATEGORIA`
```sql
INSERT INTO CATEGORIA (nombre) VALUES
  ('Acción'),
  ('Aventura'),
  ('Deportes'),
  (NULL),
  ('Estrategia'),
  ('Simulación'),
  ('Carreras'),
  ('Shooter'),
  (NULL),
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
INSERT INTO TIENDA (codTienda, direccion, codProvincia, cantidad) VALUES
  ('t1','Calle A', '11111111-1111-1111-1111-111111111111',10),
  ('t2','Calle B', '22222222-2222-2222-2222-222222222222',12),
  ('t3',NULL, '33333333-3333-3333-3333-333333333333',8),
  ('t4','Calle D', '44444444-4444-4444-4444-444444444444',20),
  ('t5','Calle E', '55555555-5555-5555-5555-555555555555',12),
  ('t6','Calle F', '11111111-1111-1111-1111-111111111111',18),
  ('t7','Calle G', '77777777-7777-7777-7777-777777777777',9),
  ('t8','Calle H', '88888888-8888-8888-8888-888888888888',NULL),
  ('t9','Calle I', '99999999-9999-9999-9999-999999999999',14),
  ('t10',NULL,'aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa',16);
```

### TABLA `TELEFONO`
```sql
INSERT INTO TELEFONO (numero, codTienda) VALUES
  ('600000001','t1'),
  ('600000002','t2'),
  ('600000003','t3'),
  ('600000004','t4'),
  ('600000005','t5'),
  ('600000006','t6'),
  ('600000007','t7'),
  ('600000008','t8'),
  ('600000009','t9'),
  ('600000010','t10');
```

### TABLA `DISPONER`
```sql
INSERT INTO DISPONER (idProducto, codTienda) VALUES
  (1,'t1'),(2,'t2'),(3,'t3'),(4,'t4'),(5,'t5'),
  (6,'t6'),(7,'t7'),(8,'t8'),(9,'t9'),(10,'t10');
```

### TABLA `SALA`
```sql
INSERT INTO SALA (codTienda, metrosCua, nombre) VALUES
  ('t1',NULL,'Sala A'),
  ('t2',60,'Sala B'),
  ('t3',45,'Sala C'),
  ('t4',70,'Sala D'),
  ('t5',55,NULL),
  ('t1',65,'Sala F'),
  ('t7',40,NULL),
  ('t8',48,'Sala H'),
  ('t9',58,'Sala I'),
  ('t10',NULL,'Sala J');
```

### TABLA `PERSONAL`
```sql
INSERT INTO PERSONAL (dni, nombre, apellido1, apellido2, codTienda) VALUES
  ('11111111A','Juan','Pérez',NULL,'t1'),
  ('22222222B','Ana','García','Ruiz','t2'),
  ('33333333C','Luis','Martín','Soto','t3'),
  ('44444444D','Marta','Díaz','Gil','t4'),
  ('55555555E','Carlos','Vega','Mora','t5'),
  ('66666666F','Laura','Navarro','Cruz','t6'),
  ('77777777G','Pablo','Ortega','León','t7'),
  ('88888888H','Sara','Romero',NULL,'t8'),
  ('99999999I','Luis','Torres','Blanco','t9'),
  ('00000000J','Elena','Ramos','Serrano','t10');
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

### TABLA `ENSEYAR`
```sql
INSET INTO ENSENYAT (dniEns, dniApr, tiempo) VALUES
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
  ('11111111A',1,'t1'),
  ('22222222B',2,'t2'),
  ('33333333C',3,'t3'),
  ('44444444D',4,'t4'),
  ('55555555E',5,'t5'),
  ('66666666F',6,'t6'),
  ('77777777G',7,'t7'),
  ('88888888H',8,'t8'),
  ('99999999I',9,'t9'),
  ('00000000J',10,'t10');
```
