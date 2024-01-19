Calcular el total de ventas para cada producto.
select p.id, p.nombre, v.cantidad as ventas from productos as p, ventas as v where p.id = v.id_producto;

sqlite> select p.id, p.nombre, v.cantidad as ventas from productos as p, ventas as v where p.id = v.id_producto;
+----+---------------+--------+
| id |    nombre     | ventas |
+----+---------------+--------+
| 1  | Arroz         | 5      |
| 2  | Leche         | 3      |
| 4  | Manzanas      | 2      |
| 5  | Pollo         | 1      |
| 6  | Huevos        | 10     |
| 8  | Tomates       | 4      |
| 10 | Cereal        | 2      |
| 14 | Galletas      | 7      |
| 16 | Café          | 3      |
| 18 | Jabón de Baño | 6      |
+----+---------------+--------+

Encontrar los productos con un precio entre 3 y 4.
select * from productos where precio between 3 and 4;
sqlite> select * from productos where precio between 3 and 4;
+----+----------+-----------+--------+
| id |  nombre  | categoria | precio |
+----+----------+-----------+--------+
| 4  | Manzanas | Frutas    | 3.0    |
| 9  | Queso    | Lácteos   | 4.0    |
| 10 | Cereal   | Desayuno  | 3.5    |
| 20 | Cerveza  | Bebidas   | 3.8    |
+----+----------+-----------+--------+


Listar los productos y sus categorías ordenados alfabéticamente por categoría.
select * from productos order by categoria;

+----+--------------------+-----------+--------+
| id |       nombre       | categoria | precio |
+----+--------------------+-----------+--------+
| 1  | Arroz              | Alimentos | 2.5    |
| 16 | Café               | Bebidas   | 5.0    |
| 19 | Botellas de Agua   | Bebidas   | 1.0    |
| 20 | Cerveza            | Bebidas   | 3.8    |
| 5  | Pollo              | Carnes    | 5.5    |
| 15 | Aceite de Oliva    | Cocina    | 4.5    |
| 17 | Sopa enlatada      | Conservas | 2.3    |
| 10 | Cereal             | Desayuno  | 3.5    |
| 4  | Manzanas           | Frutas    | 3.0    |
| 12 | Cepillo de Dientes | Higiene   | 2.0    |
| 18 | Jabón de Baño      | Higiene   | 1.2    |
| 11 | Papel Higiénico    | Hogar     | 1.5    |
| 13 | Detergente         | Limpieza  | 2.8    |
| 2  | Leche              | Lácteos   | 1.8    |
| 6  | Huevos             | Lácteos   | 1.0    |
| 7  | Yogurt             | Lácteos   | 2.0    |
| 9  | Queso              | Lácteos   | 4.0    |
| 3  | Pan                | Panadería | 1.2    |
| 14 | Galletas           | Snacks    | 1.7    |
| 8  | Tomates            | Verduras  | 2.2    |
+----+--------------------+-----------+--------+



Calcular el precio total de los productos vendidos en la fecha '2024-01-19'.
select p.id, p.nombre, p.precio*v.cantidad as precio_total, v.fecha from productos as p, ventas as v where p.id = v.id_producto and v.fecha like "2024-01-19";
+----+----------+--------------+------------+
| id |  nombre  | precio_total |   fecha    |
+----+----------+--------------+------------+
| 14 | Galletas | 11.9         | 2024-01-19 |
| 16 | Café     | 15.0         | 2024-01-19 |
+----+----------+--------------+------------+


select * from productos where categoria not like "Higiene";
sqlite> select * from productos where categoria not like "Higiene";
+----+------------------+-----------+--------+
| id |      nombre      | categoria | precio |
+----+------------------+-----------+--------+
| 1  | Arroz            | Alimentos | 2.5    |
| 2  | Leche            | Lácteos   | 1.8    |
| 3  | Pan              | Panadería | 1.2    |
| 4  | Manzanas         | Frutas    | 3.0    |
| 5  | Pollo            | Carnes    | 5.5    |
| 6  | Huevos           | Lácteos   | 1.0    |
| 7  | Yogurt           | Lácteos   | 2.0    |
| 8  | Tomates          | Verduras  | 2.2    |
| 9  | Queso            | Lácteos   | 4.0    |
| 10 | Cereal           | Desayuno  | 3.5    |
| 11 | Papel Higiénico  | Hogar     | 1.5    |
| 13 | Detergente       | Limpieza  | 2.8    |
| 14 | Galletas         | Snacks    | 1.7    |
| 15 | Aceite de Oliva  | Cocina    | 4.5    |
| 16 | Café             | Bebidas   | 5.0    |
| 17 | Sopa enlatada    | Conservas | 2.3    |
| 19 | Botellas de Agua | Bebidas   | 1.0    |
| 20 | Cerveza          | Bebidas   | 3.8    |
+----+------------------+-----------+--------+

Encontrar la cantidad total de productos en cada categoría.

select categoria, count(categoria) as cantidad_productos from productos group by categoria;
+-----------+--------------------+
| categoria | cantidad_productos |
+-----------+--------------------+
| Alimentos | 1                  |
| Bebidas   | 3                  |
| Carnes    | 1                  |
| Cocina    | 1                  |
| Conservas | 1                  |
| Desayuno  | 1                  |
| Frutas    | 1                  |
| Higiene   | 2                  |
| Hogar     | 1                  |
| Limpieza  | 1                  |
| Lácteos   | 4                  |
| Panadería | 1                  |
| Snacks    | 1                  |
| Verduras  | 1                  |
+-----------+--------------------+


Listar los productos que tienen un precio igual a la media de precios.

select * from productos where precio = (select avg(precio) from productos);

2.625, es la media, no hay tabla

Calcular el precio total de los productos vendidos en cada fecha.
select sum(p.precio*v.cantidad) as precio_total, v.fecha from productos as p, ventas as v where p.id = v.id_producto group by v.fecha;

+--------------+------------+
| precio_total |   fecha    |
+--------------+------------+
| 29.4         | 2024-01-17 |
| 25.8         | 2024-01-18 |
| 26.9         | 2024-01-19 |
| 7.2          | 2024-01-20 |
+--------------+------------+

Mostrar los productos con un nombre que termina con la letra 'o'.
select * from productos where nombre like "%o";

+----+-----------------+-----------+--------+
| id |     nombre      | categoria | precio |
+----+-----------------+-----------+--------+
| 5  | Pollo           | Carnes    | 5.5    |
| 9  | Queso           | Lácteos   | 4.0    |
| 11 | Papel Higiénico | Hogar     | 1.5    |
| 18 | Jabón de Baño   | Higiene   | 1.2    |
+----+-----------------+-----------+--------+

Encontrar los productos que han sido vendidos en más de una fecha.
select p.id, p.nombre, v.fecha from productos as p, ventas as v where p.id = v.id_producto group by p.id having count(distinct fecha) > 1;



Listar los productos cuya categoría comienza con la letra 'L'.
select * from productos where categoria like "L%";

+----+------------+-----------+--------+
| id |   nombre   | categoria | precio |
+----+------------+-----------+--------+
| 2  | Leche      | Lácteos   | 1.8    |
| 6  | Huevos     | Lácteos   | 1.0    |
| 7  | Yogurt     | Lácteos   | 2.0    |
| 9  | Queso      | Lácteos   | 4.0    |
| 13 | Detergente | Limpieza  | 2.8    |
+----+------------+-----------+--------+
Calcular el total de ventas para cada producto en la fecha '2024-01-17'.
select p.id, p.nombre, p.precio*v.cantidad as total_ventas, v.fecha from productos as p, ventas as v where p.id = v.id_producto and fecha like "2024-01-17";
+----+----------+--------------+------------+
| id |  nombre  | total_ventas |   fecha    |
+----+----------+--------------+------------+
| 1  | Arroz    | 12.5         | 2024-01-17 |
| 2  | Leche    | 5.4          | 2024-01-17 |
| 4  | Manzanas | 6.0          | 2024-01-17 |
| 5  | Pollo    | 5.5          | 2024-01-17 |
+----+----------+--------------+------------+

    Mostrar los productos cuyo nombre tiene al menos 5 caracteres.

select * from productos where length(nombre) >= 5;
+----+--------------------+-----------+--------+
| id |       nombre       | categoria | precio |
+----+--------------------+-----------+--------+
| 1  | Arroz              | Alimentos | 2.5    |
| 2  | Leche              | Lácteos   | 1.8    |
| 4  | Manzanas           | Frutas    | 3.0    |
| 5  | Pollo              | Carnes    | 5.5    |
| 6  | Huevos             | Lácteos   | 1.0    |
| 7  | Yogurt             | Lácteos   | 2.0    |
| 8  | Tomates            | Verduras  | 2.2    |
| 9  | Queso              | Lácteos   | 4.0    |
| 10 | Cereal             | Desayuno  | 3.5    |
| 11 | Papel Higiénico    | Hogar     | 1.5    |
| 12 | Cepillo de Dientes | Higiene   | 2.0    |
| 13 | Detergente         | Limpieza  | 2.8    |
| 14 | Galletas           | Snacks    | 1.7    |
| 15 | Aceite de Oliva    | Cocina    | 4.5    |
| 17 | Sopa enlatada      | Conservas | 2.3    |
| 18 | Jabón de Baño      | Higiene   | 1.2    |
| 19 | Botellas de Agua   | Bebidas   | 1.0    |
| 20 | Cerveza            | Bebidas   | 3.8    |
+----+--------------------+-----------+--------+

Encontrar los productos que tienen un precio superior al precio medio en la tabla "productos".
select * from productos where precio > (select avg(precio) from productos);

+----+-----------------+-----------+--------+
| id |     nombre      | categoria | precio |
+----+-----------------+-----------+--------+
| 4  | Manzanas        | Frutas    | 3.0    |
| 5  | Pollo           | Carnes    | 5.5    |
| 9  | Queso           | Lácteos   | 4.0    |
| 10 | Cereal          | Desayuno  | 3.5    |
| 13 | Detergente      | Limpieza  | 2.8    |
| 15 | Aceite de Oliva | Cocina    | 4.5    |
| 16 | Café            | Bebidas   | 5.0    |
| 20 | Cerveza         | Bebidas   | 3.8    |
+----+-----------------+-----------+--------+


1. Mostrar todos los productos de la categoría "Bebidas".

```sql
sqlite> select * from productos where categoria like 'Bebidas';
   ...> ;
+----+------------------+-----------+--------+
| id |      nombre      | categoria | precio |
+----+------------------+-----------+--------+
| 16 | Café             | Bebidas   | 5.0    |
| 19 | Botellas de Agua | Bebidas   | 1.0    |
| 20 | Cerveza          | Bebidas   | 3.8    |
+----+------------------+-----------+--------+

```

2. Listar los productos ordenados por precio de forma descendente.
```sql
SELECT * FROM productos ORDER BY precio desc;
```
+----+--------------------+-----------+--------+
| id |       nombre       | categoria | precio |
+----+--------------------+-----------+--------+
| 5  | Pollo              | Carnes    | 5.5    |
| 16 | Café               | Bebidas   | 5.0    |
| 15 | Aceite de Oliva    | Cocina    | 4.5    |
| 9  | Queso              | Lácteos   | 4.0    |
| 20 | Cerveza            | Bebidas   | 3.8    |
| 10 | Cereal             | Desayuno  | 3.5    |
| 4  | Manzanas           | Frutas    | 3.0    |
| 13 | Detergente         | Limpieza  | 2.8    |
| 1  | Arroz              | Alimentos | 2.5    |
| 17 | Sopa enlatada      | Conservas | 2.3    |
| 8  | Tomates            | Verduras  | 2.2    |
| 7  | Yogurt             | Lácteos   | 2.0    |
| 12 | Cepillo de Dientes | Higiene   | 2.0    |
| 2  | Leche              | Lácteos   | 1.8    |
| 14 | Galletas           | Snacks    | 1.7    |
| 11 | Papel Higiénico    | Hogar     | 1.5    |
| 3  | Pan                | Panadería | 1.2    |
| 18 | Jabón de Baño      | Higiene   | 1.2    |
| 6  | Huevos             | Lácteos   | 1.0    |
| 19 | Botellas de Agua   | Bebidas   | 1.0    |
+----+--------------------+-----------+--------+

3. Calcular el precio total de todos los productos en la tabla "productos".
SELECT SUM(precio) AS suma_precio FROM productos;

sqlite> SELECT SUM(precio) AS suma_precio FROM productos;
+-------------+
| suma_precio |
+-------------+
| 52.5        |
+-------------+

4. Encontrar los productos con un nombre que contenga la letra 'a'.

SELECT * FROM productos WHERE nombre LIKE '%a%';

+----+------------------+-----------+--------+
| id |      nombre      | categoria | precio |
+----+------------------+-----------+--------+
| 1  | Arroz            | Alimentos | 2.5    |
| 3  | Pan              | Panadería | 1.2    |
| 4  | Manzanas         | Frutas    | 3.0    |
| 8  | Tomates          | Verduras  | 2.2    |
| 10 | Cereal           | Desayuno  | 3.5    |
| 11 | Papel Higiénico  | Hogar     | 1.5    |
| 14 | Galletas         | Snacks    | 1.7    |
| 15 | Aceite de Oliva  | Cocina    | 4.5    |
| 16 | Café             | Bebidas   | 5.0    |
| 17 | Sopa enlatada    | Conservas | 2.3    |
| 18 | Jabón de Baño    | Higiene   | 1.2    |
| 19 | Botellas de Agua | Bebidas   | 1.0    |
| 20 | Cerveza          | Bebidas   | 3.8    |
+----+------------------+-----------+--------+

5. Obtener la cantidad total de productos vendidos en todas las fechas.

SELECT SUM(cantidad) suma_producto FROM ventas;
sqlite> SELECT SUM(cantidad) suma_producto FROM ventas;
+---------------+
| suma_producto |
+---------------+
| 43            |
+---------------+

6. Encontrar el producto más caro en cada categoría.

sqlite> SELECT categoria, MAX(precio) from productos group by categoria;
+-----------+-------------+
| categoria | MAX(precio) |
+-----------+-------------+
| Alimentos | 2.5         |
| Bebidas   | 5.0         |
| Carnes    | 5.5         |
| Cocina    | 4.5         |
| Conservas | 2.3         |
| Desayuno  | 3.5         |
| Frutas    | 3.0         |
| Higiene   | 2.0         |
| Hogar     | 1.5         |
| Limpieza  | 2.8         |
| Lácteos   | 4.0         |
| Panadería | 1.2         |
| Snacks    | 1.7         |
| Verduras  | 2.2         |
+-----------+-------------+

7. Listar los productos que no han sido vendidos.

sqlite> SELECT * FROM productos where id not in (SELECT p.id from productos as p, ventas as v where p.id = v.id_producto);
+----+--------------------+-----------+--------+
| id |       nombre       | categoria | precio |
+----+--------------------+-----------+--------+
| 3  | Pan                | Panadería | 1.2    |
| 7  | Yogurt             | Lácteos   | 2.0    |
| 9  | Queso              | Lácteos   | 4.0    |
| 11 | Papel Higiénico    | Hogar     | 1.5    |
| 12 | Cepillo de Dientes | Higiene   | 2.0    |
| 13 | Detergente         | Limpieza  | 2.8    |
| 15 | Aceite de Oliva    | Cocina    | 4.5    |
| 17 | Sopa enlatada      | Conservas | 2.3    |
| 19 | Botellas de Agua   | Bebidas   | 1.0    |
| 20 | Cerveza            | Bebidas   | 3.8    |
+----+--------------------+-----------+--------+

8. Calcular el precio promedio de los productos en la categoría "Snacks".
sqlite> SELECT categoria, AVG(precio) from productos where categoria like 'Snacks';
+-----------+-------------+
| categoria | AVG(precio) |
+-----------+-------------+
| Snacks    | 1.7         |
+-----------+-------------+

9. Encontrar los productos que han sido vendidos más de 5 veces.

sqlite> SELECT v.cantidad, p.nombre FROM productos as p, ventas as v where p.id = v.id_producto and v.cantidad > 5;
+----------+---------------+
| cantidad |    nombre     |
+----------+---------------+
| 10       | Huevos        |
| 7        | Galletas      |
| 6        | Jabón de Baño |
+----------+---------------+


10. Mostrar la fecha y la cantidad de ventas para cada producto.

SELECT fecha, cantidad from productos 

11. Encontrar los productos que tienen un precio menor o igual a 2.

sqlite> SELECT * from productos where precio <= 2;
+----+--------------------+-----------+--------+
| id |       nombre       | categoria | precio |
+----+--------------------+-----------+--------+
| 2  | Leche              | Lácteos   | 1.8    |
| 3  | Pan                | Panadería | 1.2    |
| 6  | Huevos             | Lácteos   | 1.0    |
| 7  | Yogurt             | Lácteos   | 2.0    |
| 11 | Papel Higiénico    | Hogar     | 1.5    |
| 12 | Cepillo de Dientes | Higiene   | 2.0    |
| 14 | Galletas           | Snacks    | 1.7    |
| 18 | Jabón de Baño      | Higiene   | 1.2    |
| 19 | Botellas de Agua   | Bebidas   | 1.0    |
+----+--------------------+-----------+--------+

12. Calcular la cantidad total de ventas para cada fecha.

sqlite> SELECT fecha,SUM(cantidad) FROM  ventas  group by fecha;
+------------+---------------+
|   fecha    | SUM(cantidad) |
+------------+---------------+
| 2024-01-17 | 11            |
| 2024-01-18 | 16            |
| 2024-01-19 | 10            |
| 2024-01-20 | 6             |
+------------+---------------+


13. Listar los productos cuyo nombre comienza con la letra 'P'.

SELECT * FROM productos WHERE nombre LIKE 'P%';

+----+-----------------+-----------+--------+
| id |     nombre      | categoria | precio |
+----+-----------------+-----------+--------+
| 3  | Pan             | Panadería | 1.2    |
| 5  | Pollo           | Carnes    | 5.5    |
| 11 | Papel Higiénico | Hogar     | 1.5    |
+----+-----------------+-----------+--------+

14. Obtener el producto más vendido en términos de cantidad.

sqlite> select p.nombre,MAX(v.cantidad) FROM ventas as v, productos as p;
+--------+-----------------+
| nombre | MAX(v.cantidad) |
+--------+-----------------+
| Arroz  | 10              |
+--------+-----------------+


15. Mostrar los productos que fueron vendidos en la fecha '2024-01-18'.

SELECT p.id, p.nombre, v.fecha FROM ventas as v, productos as p where v.fecha like '2024-01-18' and p.id = v.id_producto;

+----+---------+------------+
| id | nombre  |   fecha    |
+----+---------+------------+
| 6  | Huevos  | 2024-01-18 |
| 8  | Tomates | 2024-01-18 |
| 10 | Cereal  | 2024-01-18 |
+----+---------+------------+

16. Calcular el total de ventas para cada producto.
SELECT 

Encontrar los productos con un precio entre 3 y 4.
Listar los productos y sus categorías ordenados alfabéticamente por categoría.
Calcular el precio total de los productos vendidos en la fecha '2024-01-19'.
Mostrar los productos que no pertenecen a la categoría "Higiene".
Encontrar la cantidad total de productos en cada categoría.
Listar los productos que tienen un precio igual a la media de precios.
Calcular el precio total de los productos vendidos en cada fecha.
Mostrar los productos con un nombre que termina con la letra 'o'.
Encontrar los productos que han sido vendidos en más de una fecha.
Listar los productos cuya categoría comienza con la letra 'L'.
Calcular el total de ventas para cada producto en la fecha '2024-01-17'.
Mostrar los productos cuyo nombre tiene al menos 5 caracteres.
Encontrar los productos que tienen un precio superior al precio máximo en la tabla "productos".





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
SELECT Propietarios WHERE apellido="Perez";
+----+--------+----------+-----------+
| id | nombre | apellido |    dni    |
+----+--------+----------+-----------+
| 1  | Juan   | Perez    | 12345678A |
+----+--------+----------+-----------+
SELECT * FROM Propietarios WHERE apellido="Perez";


   Listar todos los vehículos con año 2019.
(SELECT * FROM vehiculos WHERE anio="2019");


   Seleccionar propietarios que tienen vehículos de la marca "Toyota".
SELECT * FROM Propietarios as p,Vehiculos as v WHERE v.id_propietario = p.id and v.marca="Toyota";
+----+--------+----------+-----------+----+--------+------------+------+----------------+
| id | nombre | apellido |    dni    | id | marca  |   modelo   | anio | id_propietario |
+----+--------+----------+-----------+----+--------+------------+------+----------------+
| 2  | Maria  | Lopez    | 87654321B | 2  | Toyota | Corolla    | 2018 | 2              |
| 7  | Diego  | Sanchez  | 55555555G | 7  | Toyota | Golf       | 2020 | 7              |
| 12 | Marta  | Diaz     | 10101010L | 12 | Toyota | Camry      | 2020 | 12             |
| 18 | Clara  | Soto     | 16161616R | 18 | Toyota | Highlander | 2020 | 18             |
+----+--------+----------+-----------+----+--------+------------+------+----------------+


   Listar vehículos con marca "Ford" y modelo "Fiesta".
(SELECT * FROM vehiculos WHERE marca="Ford" and modelo="Fiesta");


   Seleccionar propietarios con DNI "12345678A".
(SELECT * FROM propietarios WHERE DNI="12345678A");




   Listar vehículos que pertenecen al propietario con ID 5.
(SELECT * FROM vehiculos WHERE id="5");






   Actualizar el nombre de un propietario con DNI "12345678A".
(UPDATE propietarios set nombre="Pepita" WHERE dni="12345678A" );



   Modificar el año de un vehículo con ID 3 a 2022.
UPDATE vehiculos set anio="2022" WHERE id="3"


   Cambiar el modelo de todos los vehículos Nissan a "Micra".
UPDATE vehiculos set modelo="Micra" WHERE modelo="Nissan"


   Actualizar el apellido de un propietario con ID 7 a "Gomez".
UPDATE propietarios set apellido="Gomez" WHERE id="7"


   Modificar la marca de un vehículo con modelo "Fiesta" a "Renault".
UPDATE vehiculos set modelo="Renault" WHERE modelo="Fiesta"







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


sqlite> SELECT propietarios WHERE apellido="Perez"
   ...> ;
+----+--------+----------+-----------+
| id | nombre | apellido |    dni    |
+----+--------+----------+-----------+
| 1  | Juan   | Perez    | 12345678A |
+----+--------+----------+-----------+

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

SELECT * FROM Propietarios as p,Vehiculos as v WHERE v.id_propietario = p.id and v.marca="Toyota";
+----+--------+----------+-----------+----+--------+------------+------+----------------+
| id | nombre | apellido |    dni    | id | marca  |   modelo   | anio | id_propietario |
+----+--------+----------+-----------+----+--------+------------+------+----------------+
| 2  | Maria  | Lopez    | 87654321B | 2  | Toyota | Corolla    | 2018 | 2              |
| 7  | Diego  | Sanchez  | 55555555G | 7  | Toyota | Golf       | 2020 | 7              |
| 12 | Marta  | Diaz     | 10101010L | 12 | Toyota | Camry      | 2020 | 12             |
| 18 | Clara  | Soto     | 16161616R | 18 | Toyota | Highlander | 2020 | 18             |
+----+--------+----------+-----------+----+--------+------------+------+----------------+


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
sqlite> UPDATE vehiculos set anio="2022" WHERE id="3";
sqlite> select * from vehiculos
   ...> ;
┌────┬────────────┬────────────┬──────┬────────────────┐
│ id │   marca    │   modelo   │ anio │ id_propietario │
├────┼────────────┼────────────┼──────┼────────────────┤
│ 1  │ Ford       │ Fiesta     │ 2019 │ 1              │
│ 2  │ Toyota     │ Corolla    │ 2018 │ 2              │
│ 3  │ Nissan     │ Sentra     │ 2022 │ 3              │
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


sqlite> UPDATE vehiculos set modelo="Micra" WHERE modelo="Nissan"
   ...> ;
sqlite> select * from vehiculos
   ...> ;
┌────┬────────────┬────────────┬──────┬────────────────┐
│ id │   marca    │   modelo   │ anio │ id_propietario │
├────┼────────────┼────────────┼──────┼────────────────┤
│ 1  │ Ford       │ Fiesta     │ 2019 │ 1              │
│ 2  │ Toyota     │ Corolla    │ 2018 │ 2              │
│ 3  │ Nissan     │ Sentra     │ 2022 │ 3              │
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

sqlite> UPDATE propietarios set apellido="Gomez" WHERE id="7"
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
│ 7  │ Diego    │ Gomez     │ 55555555G │
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


sqlite> UPDATE vehiculos set modelo="Renault" WHERE modelo="Fiesta"
   ...> ;
sqlite> select * from vehiculos
   ...> ;
┌────┬────────────┬────────────┬──────┬────────────────┐
│ id │   marca    │   modelo   │ anio │ id_propietario │
├────┼────────────┼────────────┼──────┼────────────────┤
│ 1  │ Ford       │ Renault    │ 2019 │ 1              │
│ 2  │ Toyota     │ Corolla    │ 2018 │ 2              │
│ 3  │ Nissan     │ Sentra     │ 2022 │ 3              │
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

















































```


1. Mostrar todos los productos de la categoría "Bebidas".

```sql
sqlite> select * from productos where categoria like 'Bebidas';
   ...> ;
+----+------------------+-----------+--------+
| id |      nombre      | categoria | precio |
+----+------------------+-----------+--------+
| 16 | Café             | Bebidas   | 5.0    |
| 19 | Botellas de Agua | Bebidas   | 1.0    |
| 20 | Cerveza          | Bebidas   | 3.8    |
+----+------------------+-----------+--------+

```

2. Listar los productos ordenados por precio de forma descendente.
```sql
SELECT * FROM productos ORDER BY precio desc;
```
+----+--------------------+-----------+--------+
| id |       nombre       | categoria | precio |
+----+--------------------+-----------+--------+
| 5  | Pollo              | Carnes    | 5.5    |
| 16 | Café               | Bebidas   | 5.0    |
| 15 | Aceite de Oliva    | Cocina    | 4.5    |
| 9  | Queso              | Lácteos   | 4.0    |
| 20 | Cerveza            | Bebidas   | 3.8    |
| 10 | Cereal             | Desayuno  | 3.5    |
| 4  | Manzanas           | Frutas    | 3.0    |
| 13 | Detergente         | Limpieza  | 2.8    |
| 1  | Arroz              | Alimentos | 2.5    |
| 17 | Sopa enlatada      | Conservas | 2.3    |
| 8  | Tomates            | Verduras  | 2.2    |
| 7  | Yogurt             | Lácteos   | 2.0    |
| 12 | Cepillo de Dientes | Higiene   | 2.0    |
| 2  | Leche              | Lácteos   | 1.8    |
| 14 | Galletas           | Snacks    | 1.7    |
| 11 | Papel Higiénico    | Hogar     | 1.5    |
| 3  | Pan                | Panadería | 1.2    |
| 18 | Jabón de Baño      | Higiene   | 1.2    |
| 6  | Huevos             | Lácteos   | 1.0    |
| 19 | Botellas de Agua   | Bebidas   | 1.0    |
+----+--------------------+-----------+--------+

3. Calcular el precio total de todos los productos en la tabla "productos".
SELECT SUM(precio) AS suma_precio FROM productos;

sqlite> SELECT SUM(precio) AS suma_precio FROM productos;
+-------------+
| suma_precio |
+-------------+
| 52.5        |
+-------------+

4. Encontrar los productos con un nombre que contenga la letra 'a'.

SELECT * FROM productos WHERE nombre LIKE '%a%';

+----+------------------+-----------+--------+
| id |      nombre      | categoria | precio |
+----+------------------+-----------+--------+
| 1  | Arroz            | Alimentos | 2.5    |
| 3  | Pan              | Panadería | 1.2    |
| 4  | Manzanas         | Frutas    | 3.0    |
| 8  | Tomates          | Verduras  | 2.2    |
| 10 | Cereal           | Desayuno  | 3.5    |
| 11 | Papel Higiénico  | Hogar     | 1.5    |
| 14 | Galletas         | Snacks    | 1.7    |
| 15 | Aceite de Oliva  | Cocina    | 4.5    |
| 16 | Café             | Bebidas   | 5.0    |
| 17 | Sopa enlatada    | Conservas | 2.3    |
| 18 | Jabón de Baño    | Higiene   | 1.2    |
| 19 | Botellas de Agua | Bebidas   | 1.0    |
| 20 | Cerveza          | Bebidas   | 3.8    |
+----+------------------+-----------+--------+

5. Obtener la cantidad total de productos vendidos en todas las fechas.

SELECT SUM(cantidad) suma_producto FROM ventas;
sqlite> SELECT SUM(cantidad) suma_producto FROM ventas;
+---------------+
| suma_producto |
+---------------+
| 43            |
+---------------+

6. Encontrar el producto más caro en cada categoría.

sqlite> SELECT categoria, MAX(precio) from productos group by categoria;
+-----------+-------------+
| categoria | MAX(precio) |
+-----------+-------------+
| Alimentos | 2.5         |
| Bebidas   | 5.0         |
| Carnes    | 5.5         |
| Cocina    | 4.5         |
| Conservas | 2.3         |
| Desayuno  | 3.5         |
| Frutas    | 3.0         |
| Higiene   | 2.0         |
| Hogar     | 1.5         |
| Limpieza  | 2.8         |
| Lácteos   | 4.0         |
| Panadería | 1.2         |
| Snacks    | 1.7         |
| Verduras  | 2.2         |
+-----------+-------------+

7. Listar los productos que no han sido vendidos.

sqlite> SELECT * FROM productos where id not in (SELECT p.id from productos as p, ventas as v where p.id = v.id_producto);
+----+--------------------+-----------+--------+
| id |       nombre       | categoria | precio |
+----+--------------------+-----------+--------+
| 3  | Pan                | Panadería | 1.2    |
| 7  | Yogurt             | Lácteos   | 2.0    |
| 9  | Queso              | Lácteos   | 4.0    |
| 11 | Papel Higiénico    | Hogar     | 1.5    |
| 12 | Cepillo de Dientes | Higiene   | 2.0    |
| 13 | Detergente         | Limpieza  | 2.8    |
| 15 | Aceite de Oliva    | Cocina    | 4.5    |
| 17 | Sopa enlatada      | Conservas | 2.3    |
| 19 | Botellas de Agua   | Bebidas   | 1.0    |
| 20 | Cerveza            | Bebidas   | 3.8    |
+----+--------------------+-----------+--------+

8. Calcular el precio promedio de los productos en la categoría "Snacks".
sqlite> SELECT categoria, AVG(precio) from productos where categoria like 'Snacks';
+-----------+-------------+
| categoria | AVG(precio) |
+-----------+-------------+
| Snacks    | 1.7         |
+-----------+-------------+

9. Encontrar los productos que han sido vendidos más de 5 veces.

sqlite> SELECT v.cantidad, p.nombre FROM productos as p, ventas as v where p.id = v.id_producto and v.cantidad > 5;
+----------+---------------+
| cantidad |    nombre     |
+----------+---------------+
| 10       | Huevos        |
| 7        | Galletas      |
| 6        | Jabón de Baño |
+----------+---------------+


10. Mostrar la fecha y la cantidad de ventas para cada producto.

SELECT fecha, cantidad from productos 

11. Encontrar los productos que tienen un precio menor o igual a 2.

sqlite> SELECT * from productos where precio <= 2;
+----+--------------------+-----------+--------+
| id |       nombre       | categoria | precio |
+----+--------------------+-----------+--------+
| 2  | Leche              | Lácteos   | 1.8    |
| 3  | Pan                | Panadería | 1.2    |
| 6  | Huevos             | Lácteos   | 1.0    |
| 7  | Yogurt             | Lácteos   | 2.0    |
| 11 | Papel Higiénico    | Hogar     | 1.5    |
| 12 | Cepillo de Dientes | Higiene   | 2.0    |
| 14 | Galletas           | Snacks    | 1.7    |
| 18 | Jabón de Baño      | Higiene   | 1.2    |
| 19 | Botellas de Agua   | Bebidas   | 1.0    |
+----+--------------------+-----------+--------+

12. Calcular la cantidad total de ventas para cada fecha.

sqlite> SELECT fecha,SUM(cantidad) FROM  ventas  group by fecha;
+------------+---------------+
|   fecha    | SUM(cantidad) |
+------------+---------------+
| 2024-01-17 | 11            |
| 2024-01-18 | 16            |
| 2024-01-19 | 10            |
| 2024-01-20 | 6             |
+------------+---------------+


13. Listar los productos cuyo nombre comienza con la letra 'P'.

SELECT * FROM productos WHERE nombre LIKE 'P%';

+----+-----------------+-----------+--------+
| id |     nombre      | categoria | precio |
+----+-----------------+-----------+--------+
| 3  | Pan             | Panadería | 1.2    |
| 5  | Pollo           | Carnes    | 5.5    |
| 11 | Papel Higiénico | Hogar     | 1.5    |
+----+-----------------+-----------+--------+

14. Obtener el producto más vendido en términos de cantidad.

sqlite> select p.nombre,MAX(v.cantidad) FROM ventas as v, productos as p;
+--------+-----------------+
| nombre | MAX(v.cantidad) |
+--------+-----------------+
| Arroz  | 10              |
+--------+-----------------+


Mostrar los productos que fueron vendidos en la fecha '2024-01-18'.
Calcular el total de ventas para cada producto.
Encontrar los productos con un precio entre 3 y 4.
Listar los productos y sus categorías ordenados alfabéticamente por categoría.
Calcular el precio total de los productos vendidos en la fecha '2024-01-19'.
Mostrar los productos que no pertenecen a la categoría "Higiene".
Encontrar la cantidad total de productos en cada categoría.
Listar los productos que tienen un precio igual a la media de precios.
Calcular el precio total de los productos vendidos en cada fecha.
Mostrar los productos con un nombre que termina con la letra 'o'.
Encontrar los productos que han sido vendidos en más de una fecha.
Listar los productos cuya categoría comienza con la letra 'L'.
Calcular el total de ventas para cada producto en la fecha '2024-01-17'.
Mostrar los productos cuyo nombre tiene al menos 5 caracteres.
Encontrar los productos que tienen un precio superior al precio máximo en la tabla "productos".
