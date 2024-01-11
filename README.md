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
(SELECT marca,modelo FROM vehiculos);


   Seleccionar solo los propietarios con apellido "Perez".
   Listar todos los vehículos con año 2019.
(SELECT * FROM vehiculos WHERE anio="2019");


   Seleccionar propietarios que tienen vehículos de la marca "Toyota".
(SELECT * FROM propietarios WHERE marca="Toyota");


   Listar vehículos con marca "Ford" y modelo "Fiesta".
(SELECT * FROM vehiculos WHERE marca="Ford" and modelo="Fiesta");


   Seleccionar propietarios con DNI "12345678A".
(SELECT * FROM propietarios WHERE DNI="12345678A");




   Listar vehículos que pertenecen al propietario con ID 5.
(SELECT * FROM vehiculos WHERE id="5");






   Actualizar el nombre de un propietario con DNI "12345678A".
(UPDATE propietarios set nombre="Pepita" WHERE dni="12345678A" );



   Modificar el año de un vehículo con ID 3 a 2022.
UPDATE vehiculo set anio="2022" WHERE id="3"


   Cambiar el modelo de todos los vehículos Nissan a "Micra".
UPDATE vehiculo set modelo="Micra" WHERE modelo="Nissan"


   Actualizar el apellido de un propietario con ID 7 a "Gomez".
UPDATE propietario set apellido="Gomez" WHERE id="id"


   Modificar la marca de un vehículo con modelo "Fiesta" a "Renault".
UPDATE vehiculo set modelo="Renault" WHERE modelo="Fiesta"







```



```code

sqlite> SELECT * from propietarios
   ...> ;
┌────┬──────────┬───────────┬───────────┐
│ id │  nombre  │ apellido  │    dni    │
├────┼──────────┼───────────┼───────────┤
│ 1  │ Juan     │ Perez     │ 12345678A │
│ 2  │ Maria    │ Lopez     │ 87654321B │
│ 3  │ Carlos   │ Ruiz      │ 11111111C │
│ 4  │ Laura    │ Gomez     │ 22222222D │
│ 5  │ Pedro    │ Martinez  │ 33333333E │
│ 6  │ Ana      │ Fernandez │ 44444444F │
│ 7  │ Diego    │ Sanchez   │ 55555555G │
│ 8  │ Sofia    │ Torres    │ 66666666H │
│ 9  │ Javier   │ Leon      │ 77777777I │
│ 10 │ Lucia    │ Castillo  │ 88888888J │
│ 11 │ Luis     │ Gonzalez  │ 99999999K │
│ 12 │ Marta    │ Diaz      │ 10101010L │
│ 13 │ Victor   │ Vargas    │ 11111112M │
│ 14 │ Elena    │ Castro    │ 12121212N │
│ 15 │ Roberto  │ Blanco    │ 13131313O │
│ 16 │ Natalia  │ Paredes   │ 14141414P │
│ 17 │ Fernando │ Herrera   │ 15151515Q │
│ 18 │ Clara    │ Soto      │ 16161616R │
│ 19 │ Sergio   │ Mendoza   │ 17171717S │
│ 20 │ Patricia │ Navarro   │ 18181818T │
└────┴──────────┴───────────┴───────────┘



sqlite> select * from vehiculos
   ...> ;
┌────┬────────────┬────────────┬──────┬────────────────┐
│ id │   marca    │   modelo   │ anio │ id_propietario │
├────┼────────────┼────────────┼──────┼────────────────┤
│ 1  │ Ford       │ Fiesta     │ 2019 │ 1              │
│ 2  │ Toyota     │ Corolla    │ 2018 │ 2              │
│ 3  │ Nissan     │ Sentra     │ 2020 │ 3              │
│ 4  │ Chevrolet  │ Spark      │ 2017 │ 4              │
│ 5  │ Honda      │ Civic      │ 2016 │ 5              │
│ 6  │ Ford       │ Mustang    │ 2021 │ 6              │
│ 7  │ Toyota     │ Golf       │ 2020 │ 7              │
│ 8  │ Volkswagen │ RAV4       │ 2019 │ 8              │
│ 9  │ Honda      │ CR-V       │ 2018 │ 9              │
│ 10 │ Nissan     │ Altima     │ 2017 │ 10             │
│ 11 │ Chevrolet  │ Malibu     │ 2019 │ 11             │
│ 12 │ Toyota     │ Camry      │ 2020 │ 12             │
│ 13 │ Honda      │ Accord     │ 2018 │ 13             │
│ 14 │ Ford       │ Explorer   │ 2021 │ 14             │
│ 15 │ Nissan     │ Rogue      │ 2017 │ 15             │
│ 16 │ Volkswagen │ Jetta      │ 2019 │ 16             │
│ 17 │ Chevrolet  │ Equinox    │ 2018 │ 17             │
│ 18 │ Toyota     │ Highlander │ 2020 │ 18             │
│ 19 │ Honda      │ Odyssey    │ 2016 │ 19             │
│ 20 │ Nissan     │ Murano     │ 2019 │ 20             │
└────┴────────────┴────────────┴──────┴────────────────┘


sqlite> SELECT nombre, apellido FROM propietarios
   ...> ;
┌──────────┬───────────┐
│  nombre  │ apellido  │
├──────────┼───────────┤
│ Juan     │ Perez     │
│ Maria    │ Lopez     │
│ Carlos   │ Ruiz      │
│ Laura    │ Gomez     │
│ Pedro    │ Martinez  │
│ Ana      │ Fernandez │
│ Diego    │ Sanchez   │
│ Sofia    │ Torres    │
│ Javier   │ Leon      │
│ Lucia    │ Castillo  │
│ Luis     │ Gonzalez  │
│ Marta    │ Diaz      │
│ Victor   │ Vargas    │
│ Elena    │ Castro    │
│ Roberto  │ Blanco    │
│ Natalia  │ Paredes   │
│ Fernando │ Herrera   │
│ Clara    │ Soto      │
│ Sergio   │ Mendoza   │
│ Patricia │ Navarro   │
└──────────┴───────────┘

sqlite> SELECT marca,modelo FROM vehiculos
   ...> ;
┌────────────┬────────────┐
│   marca    │   modelo   │
├────────────┼────────────┤
│ Ford       │ Fiesta     │
│ Toyota     │ Corolla    │
│ Nissan     │ Sentra     │
│ Chevrolet  │ Spark      │
│ Honda      │ Civic      │
│ Ford       │ Mustang    │
│ Toyota     │ Golf       │
│ Volkswagen │ RAV4       │
│ Honda      │ CR-V       │
│ Nissan     │ Altima     │
│ Chevrolet  │ Malibu     │
│ Toyota     │ Camry      │
│ Honda      │ Accord     │
│ Ford       │ Explorer   │
│ Nissan     │ Rogue      │
│ Volkswagen │ Jetta      │
│ Chevrolet  │ Equinox    │
│ Toyota     │ Highlander │
│ Honda      │ Odyssey    │
│ Nissan     │ Murano     │
└────────────┴────────────┘

sqlite> SELECT * FROM vehiculos WHERE anio="2019"
   ...> ;
┌────┬────────────┬────────┬──────┬────────────────┐
│ id │   marca    │ modelo │ anio │ id_propietario │
├────┼────────────┼────────┼──────┼────────────────┤
│ 1  │ Ford       │ Fiesta │ 2019 │ 1              │
│ 8  │ Volkswagen │ RAV4   │ 2019 │ 8              │
│ 11 │ Chevrolet  │ Malibu │ 2019 │ 11             │
│ 16 │ Volkswagen │ Jetta  │ 2019 │ 16             │
│ 20 │ Nissan     │ Murano │ 2019 │ 20             │
└────┴────────────┴────────┴──────┴────────────────┘


sqlite> SELECT * FROM vehiculos WHERE marca="Ford" and modelo="Fiesta"
   ...> ;
┌────┬───────┬────────┬──────┬────────────────┐
│ id │ marca │ modelo │ anio │ id_propietario │
├────┼───────┼────────┼──────┼────────────────┤
│ 1  │ Ford  │ Fiesta │ 2019 │ 1              │
└────┴───────┴────────┴──────┴────────────────┘

sqlite> SELECT * FROM propietarios WHERE DNI="12345678A"
   ...> ;
┌────┬────────┬──────────┬───────────┐
│ id │ nombre │ apellido │    dni    │
├────┼────────┼──────────┼───────────┤
│ 1  │ Juan   │ Perez    │ 12345678A │
└────┴────────┴──────────┴───────────┘


sqlite> SELECT * FROM vehiculos WHERE id="5"
   ...> ;
┌────┬───────┬────────┬──────┬────────────────┐
│ id │ marca │ modelo │ anio │ id_propietario │
├────┼───────┼────────┼──────┼────────────────┤
│ 5  │ Honda │ Civic  │ 2016 │ 5              │
└────┴───────┴────────┴──────┴────────────────┘


sqlite> UPDATE propietario set nombre="Roberto" WHERE dni="12345678A"
   ...> ;
Error: in prepare, no such table: propietario (1)
sqlite> UPDATE propietarios set nombre="Roberto" WHERE dni="12345678A"
   ...> ;
sqlite> select * from propietarios
   ...> ;
┌────┬──────────┬───────────┬───────────┐
│ id │  nombre  │ apellido  │    dni    │
├────┼──────────┼───────────┼───────────┤
│ 1  │ Roberto  │ Perez     │ 12345678A │
│ 2  │ Maria    │ Lopez     │ 87654321B │
│ 3  │ Carlos   │ Ruiz      │ 11111111C │
│ 4  │ Laura    │ Gomez     │ 22222222D │
│ 5  │ Pedro    │ Martinez  │ 33333333E │
│ 6  │ Ana      │ Fernandez │ 44444444F │
│ 7  │ Diego    │ Sanchez   │ 55555555G │
│ 8  │ Sofia    │ Torres    │ 66666666H │
│ 9  │ Javier   │ Leon      │ 77777777I │
│ 10 │ Lucia    │ Castillo  │ 88888888J │
│ 11 │ Luis     │ Gonzalez  │ 99999999K │
│ 12 │ Marta    │ Diaz      │ 10101010L │
│ 13 │ Victor   │ Vargas    │ 11111112M │
│ 14 │ Elena    │ Castro    │ 12121212N │
│ 15 │ Roberto  │ Blanco    │ 13131313O │
│ 16 │ Natalia  │ Paredes   │ 14141414P │
│ 17 │ Fernando │ Herrera   │ 15151515Q │
│ 18 │ Clara    │ Soto      │ 16161616R │
│ 19 │ Sergio   │ Mendoza   │ 17171717S │
│ 20 │ Patricia │ Navarro   │ 18181818T │
└────┴──────────┴───────────┴───────────┘

```


