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
INSERT INTO PRODUCTO (nombre, stock, fechaVenta, compra, venta) VALUES
  ('The Legend of Zelda: Tears of the Kingdom', 50, '2024-01-10', 10.00, 15.00),
  ('God of War Ragnarök', NULL, '2024-01-11', 8.50, 12.00),
  ('Elden Ring', 35, '2024-01-12', 5.00, 9.50),
  ('Call of Duty: Modern Warfare III: Modern Warfare III', 60, '2024-01-13', 10.00, 15.00),
  ('FIFA 24', NULL, '2024-01-14', 12.00, 18.00),
  ('Minecraft', 35, '2024-01-13', 10.00, 11.00),
  ('Hollow Knight', 10, '2024-01-16', 9.00, 14.00),
  ('Cyberpunk 2077', 50, '2024-01-14', 25.00, 15.00),
  ('Stardew Valley', 40, NULL, 6.00, 10.00),
  ('Resident Evil 4 Remake', 55, '2024-01-19', 11.50, 16.50);
```
### TABLA `PROVENIR`
```sql
INSERT INTO PROVENIR (idProducto, codProvincia) VALUES
  ((SELECT id FROM PRODUCTO WHERE nombre='The Legend of Zelda: Tears of the Kingdom'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Alicante')),
  ((SELECT id FROM PRODUCTO WHERE nombre='God of War Ragnarök'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Valencia')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Call of Duty: Modern Warfare III'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Madrid')),
  ((SELECT id FROM PRODUCTO WHERE nombre='FIFA 24'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Barcelona')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Minecraft'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Sevilla')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Hollow Knight'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Murcia')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Cyberpunk 2077'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Sevilla')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Stardew Valley'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Granada')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Elden Ring'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Zaragoza')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Resident Evil 4 Remake'),(SELECT codProvincia FROM PROVINCIA WHERE nombre='Tarragona'));
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
  ((SELECT id FROM CATEGORIA WHERE nombre='Acción'),(SELECT id FROM PRODUCTO WHERE nombre='The Legend of Zelda: Tears of the Kingdom')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Aventura'),(SELECT id FROM PRODUCTO WHERE nombre='God of War Ragnarök')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Deportes'),(SELECT id FROM PRODUCTO WHERE nombre='Call of Duty: Modern Warfare III')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Terror'),(SELECT id FROM PRODUCTO WHERE nombre='FIFA 24')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Estrategia'),(SELECT id FROM PRODUCTO WHERE nombre='Minecraft')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Simulación'),(SELECT id FROM PRODUCTO WHERE nombre='Hollow Knight')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Carreras'),(SELECT id FROM PRODUCTO WHERE nombre='Cyberpunk 2077')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Shooter'),(SELECT id FROM PRODUCTO WHERE nombre='Stardew Valley')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Cooperativo'),(SELECT id FROM PRODUCTO WHERE nombre='Elden Ring')),
  ((SELECT id FROM CATEGORIA WHERE nombre='Familiar'),(SELECT id FROM PRODUCTO WHERE nombre='Resident Evil 4 Remake'));
```

### TABLA `TIENDA`
```sql
INSERT INTO TIENDA (direccion, codProvincia, cantidad) VALUES
  ('Calle A', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Alicante'),10),
  ('Calle B', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Valencia'),12),
  ('Calle C', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Madrid'),8),
  ('Calle D', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Barcelona'),20),
  ('Calle E', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Sevilla'),5),
  ('Calle F', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Murcia'),3),
  ('Calle G', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Sevilla'),9),
  ('Calle H', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Granada'),5),
  ('Calle I', (SELECT codProvincia FROM PROVINCIA WHERE nombre='Zaragoza'),14),
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
  ('600000006',(SELECT codTienda FROM TIENDA WHERE direccion='Calle F')),
  ('600000007',(SELECT codTienda FROM TIENDA WHERE direccion='Calle G')),
  ('600000008',(SELECT codTienda FROM TIENDA WHERE direccion='Calle H')),
  ('600000009',(SELECT codTienda FROM TIENDA WHERE direccion='Calle I')),
  ('600000010',(SELECT codTienda FROM TIENDA WHERE direccion='Calle J'));
```

### TABLA `DISPONER`
```sql
INSERT INTO DISPONER (idProducto, codTienda) VALUES
  ((SELECT id FROM PRODUCTO WHERE nombre='The Legend of Zelda: Tears of the Kingdom'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle A')),
  ((SELECT id FROM PRODUCTO WHERE nombre='God of War Ragnarök'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle B')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Call of Duty: Modern Warfare III'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle C')),
  ((SELECT id FROM PRODUCTO WHERE nombre='FIFA 24'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle D')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Minecraft'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle E')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Hollow Knight'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle F')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Cyberpunk 2077'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle G')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Stardew Valley'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle H')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Elden Ring'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle I')),
  ((SELECT id FROM PRODUCTO WHERE nombre='Resident Evil 4 Remake'),(SELECT codTienda FROM TIENDA WHERE direccion='Calle J'));
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
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle F'),55,'Sala G'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle G'),48, NULL),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle H'),65,'Sala I'),
  ((SELECT codTienda FROM TIENDA WHERE direccion='Calle I'),NULL,'Sala J');
```

### TABLA `PERSONAL`
```sql
INSERT INTO PERSONAL (dni, nombre, apellido1, apellido2, codTienda, fecha_nac) VALUES
  ('11111111A','Juan','Pérez',NULL,(SELECT codTienda FROM TIENDA WHERE direccion='Calle A'), '1990-05-12'),
  ('22222222B','Ana','García','Ruiz',(SELECT codTienda FROM TIENDA WHERE direccion='Calle B'), '1988-09-20'),
  ('33333333C','Luis','Martín','Soto',(SELECT codTienda FROM TIENDA WHERE direccion='Calle C'), '1995-03-08'),
  ('44444444D','Marta','Díaz','Gil',(SELECT codTienda FROM TIENDA WHERE direccion='Calle D'), '1992-11-15'),
  ('55555555E','Carlos','Vega','Mora',(SELECT codTienda FROM TIENDA WHERE direccion='Calle E'), '1985-01-30'),
  ('66666666F','Laura','Navarro','Cruz',(SELECT codTienda FROM TIENDA WHERE direccion='Calle F'), '1998-07-04'),
  ('77777777G','Pablo','Pérez','León',(SELECT codTienda FROM TIENDA WHERE direccion='Calle G'), '1991-12-22'),
  ('88888888H','Sara','Romero',NULL,(SELECT codTienda FROM TIENDA WHERE direccion='Calle H'), '1996-04-18'),
  ('99999999I','Luis','Torres','Soto',(SELECT codTienda FROM TIENDA WHERE direccion='Calle I'), '1988-09-20'),
  ('00000000J','Elena','Ramos','Serrano',(SELECT codTienda FROM TIENDA WHERE direccion='Calle J'), '1988-09-20');
```

### TABLA `DEPENDIENTE`
```sql
INSERT INTO DEPENDIENTE (dniDependiente, corrIdent) VALUES
  ((SELECT dni FROM PERSONAL WHERE nombre='Laura' AND apellido1='Navarro'),'emp6@tienda.com'),
  ((SELECT dni FROM PERSONAL WHERE nombre='Pablo' AND apellido1='Pérez'),'emp7@tienda.com'),
  ((SELECT dni FROM PERSONAL WHERE nombre='Sara' AND apellido1='Romero'),'emp8@tienda.com'),
  ((SELECT dni FROM PERSONAL WHERE nombre='Luis' AND apellido1='Torres'),'emp9@tienda.com'),
  ((SELECT dni FROM PERSONAL WHERE nombre='Elena' AND apellido1='Ramos'),'emp10@tienda.com');
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
  ('11111111A',((SELECT id FROM PRODUCTO WHERE nombre='The Legend of Zelda: Tears of the Kingdom'),2),
  ('22222222B',((SELECT id FROM PRODUCTO WHERE nombre='God of War Ragnarök'),1),
  ('33333333C',((SELECT id FROM PRODUCTO WHERE nombre='Call of Duty: Modern Warfare III'),NULL),
  ('44444444D',((SELECT id FROM PRODUCTO WHERE nombre='FIFA 24'),2),
  ('55555555E',((SELECT id FROM PRODUCTO WHERE nombre='Hollow Knight'),1),
  ('66666666F',((SELECT id FROM PRODUCTO WHERE nombre='Minecraft'),4),
  ('77777777G',((SELECT id FROM PRODUCTO WHERE nombre='Cyberpunk 2077'),2),
  ('88888888H',((SELECT id FROM PRODUCTO WHERE nombre='Stardew Valley'),NULL),
  ('99999999I',((SELECT id FROM PRODUCTO WHERE nombre='Elden Ring'),1),
  ('00000000J',((SELECT id FROM PRODUCTO WHERE nombre='Resident Evil 4 Remake'),2);
```

### TABLA `LIMPIEZA`
```sql
INSERT INTO LIMPIEZA (dniLimpieza) VALUES
  (SELECT dni FROM PERSONAL WHERE nombre='Juan' AND apellido1='Pérez'),
  (SELECT dni FROM PERSONAL WHERE nombre='Ana' AND apellido1='García'),
  (SELECT dni FROM PERSONAL WHERE nombre='Luis' AND apellido1='Martín'),
  (SELECT dni FROM PERSONAL WHERE nombre='Marta' AND apellido1='Díaz'),
  (SELECT dni FROM PERSONAL WHERE nombre='Carlos' AND apellido1='Vega');
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
