# Árboles B
Los árboles B son una variante de los árboles N-arios que se utilizan para almacenar grandes cantidades de datos en disco. Los árboles B son muy utilizados en bases de datos y sistemas de archivos.

Descritos por Rudolf Bayer y Edward M. McCreight en 1972, los árboles B son árboles balanceados que se caracterizan por tener un número variable de hijos por nodo. Los árboles B son muy similares a los árboles binarios de búsqueda, pero con la diferencia de que cada nodo puede tener más de dos hijos.

Visualmente se pueden representar de la siguiente forma:

![Árbol B](../images/b-tree-1.png)


## Características
Un árbol B de orden _m_, tiene las siguientes características:
- Cada nodo se compone de llaves y ramas. Las llaves están ordenadas y dividen las ramas en el órden esperado. Por ejemplo, entre las llaves 15 y 20, hay un nodo hijo, cuyas llaves serán mayores a 15 pero menores a 20.
- Todas las hojas están al mismo nivel.
- Se define con un orden _m_, que depende del tamaño del bloque del disco
- Cada nodo excepto la raíz **debe** contener al menos _m-1_ llaves. La raíz contiene un mínimo de una una llave.
- Todos los nodos (incluída la raíz) tienen a lo sumo _2*m-1_ llaves.
- La inserción siempre ocurre en las hojas.
- Crecen o decrecen desde la raíz.

> Pueden implementarse en memoria principal o en secundaria (propósito original). En este curso, nos enfocaremos en la implementación en memoria principal.

