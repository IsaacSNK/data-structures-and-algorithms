# Árboles AVL
Los árboles AVL son árboles binarios de búsqueda **balanceados**. Fueron los primeros árboles auto-balanceados que se propusieron. Fueron introducidos por Adelson-Velsky y Landis en 1962.

Dado que se mantienen balanceados, las operaciones de búsqueda, inserción y eliminación tienen un tiempo de ejecución garantizado de O(log n) y no sufren de la degradación de rendimiento que sufren los árboles binarios de búsqueda no balanceados.

## Características
- Es un árbol binario de búsqueda.
- Está balanceado en altura.
- El factor de balance de cada nodo es -1, 0 o 1.
- Las eliminaciones e inserciones pueden requerir balanceo a través de rotaciones.

> El factor de balance de un nodo es la diferencia entre la altura del subárbol derecho y la altura del subárbol izquierdo.

<pre>
          10
        /    \
       5      15
      / \    /  \
     3   8  12   20
    / \         /   \
   2   4       17    25
</pre>


Factores de balance de cada nodo:

| Nodo | Factor de Balance |
|------|------------------|
| 10   | 3 - 2 = 1       |
| 5    | 2 - 1 = 1       |
| 15   | 3 - 2 = 1       |
| 3    | 1 - 0 = 1       |
| 8    | 1 - 0 = 1       |
| 12   | 1 - 0 = 1       |
| 20   | 2 - 0 = 2       |
| 2    | 0 - 0 = 0       |
| 4    | 0 - 0 = 0       |
| 17   | 0 - 0 = 0       |
| 25   | 0 - 0 = 0       |


## Ventajas
- Búsquedas rápidas
- Auto-balanceados

## Desventajas
- Requieren más memoria que los árboles binarios de búsqueda no balanceados.
- Las operaciones de inserción y eliminación son más lentas que en los árboles binarios de búsqueda no balanceados.
- Las rotaciones pueden ser costosas.
- Difficiles de implementar.

# Inserción
Para insertar un nodo _w_: 
- Se realiza una inserción normal de un árbol binario de búsqueda para el nodo _w_.
- Iniciando en _w_, se recorre el camino de búsqueda hacia la raíz. Sea _z_ el primero nodo no balanceado, _y_ el hijo de _z_ que está en el camino de _w_ a _z_ y _x_ el nieto de _z_ que está en el camino de _w_ a _z_.
- Se rebalancea el árbol mediante rotaciones simples o dobles en el subárbol con raíz en _z_. Hay 4 posibles casos de rotaciones.
 
    - **Rotación derecha**: y es el hijo izquierdo de z y x es el hijo izquierdo de y. 
    - **Rotación Izquierda-derecha**: y es el hijo izquierdo de z y x es el hijo derecho de y.
    - **Rotación Izquierda**: y es el hijo derecho de z y x es el hijo derecho de y.
    - **Rotación Derecha-izquierda**: y es el hijo derecho de z y x es el hijo izquierdo de y.


## Ejemplo de rotación derecha

Dado el siguiente árbol AVL:

 <pre>
                  10
                /    \
               5      15
              / \    /  \
             3   8  12   20
            / \         /   \
           2   4       17    25
</pre>

Se inserta el nodo 1:
 
 <pre>
                  10
                /    \
               5      15  -------> 5 es z
              / \    /  \
             3   8  12   20 -------> 3 es y
            / \         /   \
           2   4       17    25 -------> 2 es x
          /
         1
</pre>

El factor de balance del nodo 5 es 2, por lo que se debe rebalancear el árbol. El nodo 3 es el hijo de 5 que está en el camino de 1 a 5 y el nodo 2 es el nieto de 5 que está en el camino de 1 a 5. Estamos en el caso de rotación derecha.

Aplicando el siguiente código a _z_:

```java
void rotateRight(Node z) {
    Node y = z.left;
    z.left = y.right;
    y.right = z;
    z = y;
}
```

Se obtiene: 

 <pre>
                  10
                /    \
               3      15
              / \    /  \
             2   5  12   20
            /   / \    /   \
           1   4   8  17    25   
</pre>