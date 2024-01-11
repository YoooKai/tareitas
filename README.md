```sql

CREATE TABLE propietarios
(id INTEGER PRIMARY KEY AUTOINCREMENT,
nombre TEXT NOT NULL,
apellido TEXT NOT NULL,
dni TEXT UNIQUE
);
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Juan', 'Perez', '12345678A' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Maria', 'Lopez', '87654321B' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Carlos', 'Ruiz', '11111111C' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Laura', 'Gomez', '22222222D' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Pedro', 'Martinez', '33333333E' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Ana', 'Fernandez', '44444444F' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Diego', 'Sanchez', '55555555G' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Sofia', 'Torres', '66666666H' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Javier', 'Leon', '77777777I' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Lucia', 'Castillo', '88888888J' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Luis', 'Gonzalez', '99999999K' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Marta', 'Diaz', '10101010L' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Victor', 'Vargas', '11111112M' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Elena', 'Castro', '12121212N' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Roberto', 'Blanco', '13131313O' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Natalia', 'Paredes', '14141414P' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Fernando', 'Herrera', '15151515Q' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Clara', 'Soto', '16161616R' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Sergio', 'Mendoza', '17171717S' );
INSERT INTO propietarios (nombre, apellido, dni) VALUES ('Patricia', 'Navarro', '18181818T' );

CREATE TABLE vehiculos
(id INTEGER PRIMARY KEY AUTOINCREMENT,
marca TEXT NOT NULL,
modelo TEXT NOT NULL,
anio INTEGER NOT NULL,
id_propietario INTEGER references propietario(id)
);

INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Ford', 'Fiesta', '2019', '1');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Toyota', 'Corolla', '2018', '2');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Nissan', 'Sentra', '2020', '3');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Chevrolet', 'Spark', '2017', '4');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Honda', 'Civic', '2016', '5');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Ford', 'Mustang', '2021', '6');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Toyota', 'Golf', '2020', '7');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Volkswagen', 'RAV4', '2019', '8');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Honda', 'CR-V', '2018', '9');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Nissan', 'Altima', '2017', '10');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Chevrolet', 'Malibu', '2019', '11');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Toyota', 'Camry', '2020', '12');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Honda', 'Accord', '2018', '13');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Ford', 'Explorer', '2021', '14');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Nissan', 'Rogue', '2017', '15');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Volkswagen', 'Jetta', '2019', '16');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Chevrolet', 'Equinox', '2018', '17');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Toyota', 'Highlander', '2020', '18');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Honda', 'Odyssey', '2016', '19');
INSERT INTO vehiculos (marca, modelo, anio, id_propietario) VALUES ('Nissan', 'Murano', '2019', '20');
```




EJERCICIOS

```SQL
Paso 3: Realizar las siguientes 10 consultas de datos


   Seleccionar todos los propietarios (SELECT * FROM propietarios);


   Listar todos los vehículos. (SELECT * FROM vehiculos);


   Seleccionar solo los nombres y apellidos de los propietarios. (SELECT nombre,apellido FROM propietarios);


   Listar todas las marcas y modelos de los vehículos.
(SELECT marcas,modelos FROM vehiculos);


   Seleccionar solo los propietarios con apellido "Perez".
   Listar todos los vehículos con año 2019.
(SELECT * FROM vehiculos WHERE anio=”2019”);


   Seleccionar propietarios que tienen vehículos de la marca "Toyota".
(SELECT * FROM propietarios WHERE marca=”Toyota”);


   Listar vehículos con marca "Ford" y modelo "Fiesta".
(SELECT * FROM vehiculos WHERE marca=”Ford” & modelo=”Fiesta”);


   Seleccionar propietarios con DNI "12345678A".
(SELECT * FROM propietarios WHERE DNI=”12345678A”);




   Listar vehículos que pertenecen al propietario con ID 5.
(SELECT * FROM vehiculos WHERE id=”5”);






   Actualizar el nombre de un propietario con DNI "12345678A".
(UPDATE propietario set nombre=”Pepita” WHERE dni=”12345678A” );
```
