# Introducción a búsqueda binaria
Búsqueda binaria es un algoritmo de búsqueda que encuentra la posición de un valor en un arreglo ordenado. A diferencia de la búsqueda lineal, que recorre el arreglo desde el primer elemento hasta el último, la búsqueda binaria divide el arreglo en dos mitades y compara el valor buscado con el elemento en el medio. 
- Si el valor buscado es menor que el elemento en el medio, la búsqueda continúa en la mitad izquierda del arreglo. 
- Si el valor buscado es mayor que el elemento en el medio, la búsqueda continúa en la mitad derecha del arreglo. 

Este proceso se repite hasta que el valor buscado sea encontrado o hasta que el subarreglo de búsqueda sea vacío.

# Ejecución de búsqueda binaria
Dado el siguiente arreglo:

```
| Indices   | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| Elementos | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
```
Para buscar el número 9:
- Comenzamos comparando el número 9 con el elemento en el medio del arreglo, que es 5.
- Como 9 es mayor que 5, la búsqueda continúa en la mitad derecha del arreglo.
- Ahora comparamos el número 9 con el elemento en el medio de la mitad derecha del arreglo, que es 8.
- Como 9 es mayor que 8, la búsqueda continúa en la mitad derecha de la mitad derecha del arreglo.
- Ahora comparamos el número 9 con el elemento en el medio de la mitad derecha de la mitad derecha del arreglo, que es 9.
- Como 9 es igual a 9, hemos encontrado el número que buscábamos.

Visualmente, se puede representar de la siguiente manera:
```
| Indices   | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| Elementos | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
            |-----------------------------------|
    5 < 9                     ^
                                |---------------|
    7 < 9                             ^  
                                        |-------|  
    8 < 9                                 ^
                                             |--|
    9 == 9                                    ^
```

# Implementación en Java
```java	
public static int binarySearch(int[] arr, int target) {
    int left = 0;
    int right = arr.length - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid;
        }

        if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return -1;
}
```
