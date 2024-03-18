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
- Todos los nodos (incluída la raíz) tienen a lo sumo _2\*m-1_ llaves.
- La inserción siempre ocurre en las hojas.
- Crecen o decrecen desde la raíz.

> Pueden implementarse en memoria principal o en secundaria (propósito original). En este curso, nos enfocaremos en la implementación en memoria principal.

## Estructura básica en Java

```java
class BTreeNode {
    int[] keys;
    int order;
    BTreeNode[] branches;
}
```

# Inserción

El árbol B crece hacia arriba desde la raíz. La inserción siempre ocurre en las hojas.

El proceso de inserción para una llave _k_ sería:

- Se busca la llave en la raíz, entre las llaves del nodo.
- Dado que las llaves del nodo están ordenadas, se detiene si hay una llave mayor. Si tiene un hijo, se desciende a él y se repite el proceso.
- Si el nodo no tiene hijos:
  - Si el nodo no está lleno, se inserta en la posición correspondiente del arreglo de llaves
  - Si el nodo está lleno, se divide el nodo.

El proceso de división de un nodo _n_ con _2\*m-1_ llaves es el siguiente:

1. Se selecciona la llave mediana _m_ y se sube al nodo padre.
2. Se crean dos nuevos nodos, _n1_ y _n2_.
3. Se distribuyen las llaves de _n_ entre _n1_ y _n2_.
4. Se actualizan las ramas de _n1_ y _n2_.

El proceso de división se repite hasta llegar a la raíz.

Graficamente se puede ver de la siguiente manera (orden 5):

![Árbol B](../images/b-tree-insertion-1.png)

> La raíz está llena. Al insertar la llave 8:

![Árbol B](../images/b-tree-insertion-2.png)

> Varios elementos después:

![Árbol B](../images/b-tree-insertion-3.png)

> Varios elementos después...:

![Árbol B](../images/b-tree-insertion-4.png)
