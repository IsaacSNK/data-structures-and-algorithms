Introducción a SQL
SQL (Structured Query Language) es un lenguaje estándar utilizado para interactuar con bases de datos relacionales. Permite realizar diversas operaciones para gestionar datos de manera eficiente y precisa.

Operaciones Básicas en SQL
1. Consultas SELECT
La operación más común en SQL es la consulta SELECT, que se utiliza para recuperar datos de una o más tablas.

Ejemplo:

sql
Copy code
SELECT columna1, columna2
FROM tabla
WHERE condición;
2. Inserción de Datos
Para insertar nuevos registros en una tabla, se utiliza la instrucción INSERT.

Ejemplo:

sql
Copy code
INSERT INTO tabla (columna1, columna2)
VALUES (valor1, valor2);
3. Actualización de Datos
Para actualizar registros existentes en una tabla, se utiliza la instrucción UPDATE.

Ejemplo:

sql
Copy code
UPDATE tabla
SET columna1 = nuevo_valor
WHERE condición;
4. Eliminación de Datos
Para eliminar registros de una tabla, se utiliza la instrucción DELETE.

Ejemplo:

sql
Copy code
DELETE FROM tabla
WHERE condición;
Cláusulas y Expresiones SQL
1. Cláusula WHERE
La cláusula WHERE se utiliza para filtrar registros basados en una condición específica.

Ejemplo:

sql
Copy code
SELECT columna1, columna2
FROM tabla
WHERE columna1 = 'valor';
2. Cláusula ORDER BY
La cláusula ORDER BY se utiliza para ordenar los resultados de una consulta en orden ascendente o descendente.

Ejemplo:

sql
Copy code
SELECT columna1, columna2
FROM tabla
ORDER BY columna1 DESC;
3. Funciones Agregadas
SQL proporciona funciones agregadas como COUNT, SUM, AVG, MIN y MAX para realizar cálculos en conjuntos de datos.

Ejemplo:

sql
Copy code
SELECT COUNT(*)
FROM tabla;