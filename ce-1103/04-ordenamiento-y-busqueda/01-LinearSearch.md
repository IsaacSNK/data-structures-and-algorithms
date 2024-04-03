# Introducción a búsqueda lineal
La búsqueda lineal es el método más sencillo para buscar un elemento en un arreglo (o una lista). Consiste en recorrer el arreglo desde el primer elemento hasta el último, comparando cada elemento con el valor que se busca.

Cuando el arreglo **no está ordenado**, la búsqueda lineal es la **única opción**. Sin embargo, cuando el arreglo está ordenado, existen algoritmos más eficientes para realizar la búsqueda, como la búsqueda binaria.

# Ejecución de búsqueda lineal

Dado el siguiente arreglo:

```
| Indices   | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| Elementos | 5 | 3 | 8 | 6 | 2 | 7 | 1 | 4 | 9 |
```

Buscamos el número 7.

- Comenzamos comparando el número 7 con el primer elemento del arreglo, que es 5. 
- Como no son iguales, pasamos al siguiente elemento, que es 3. 
- Tampoco es igual, así que pasamos al siguiente elemento, que es 8. 
- Tampoco es igual, así que pasamos al siguiente elemento, que es 6. 
- Tampoco es igual, así que pasamos al siguiente elemento, que es 2. 
- Tampoco es igual, así que pasamos al siguiente elemento, que es 7. 
- Como son iguales, hemos encontrado el número que buscábamos.

Este proceso se puede representar visualmenete de la siguiente manera:
```
| Indices   | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| Elementos | 5 | 3 | 8 | 6 | 2 | 7 | 1 | 4 | 9 |
    5 != 7    ^
    3 != 7        ^
    8 != 7            ^
    6 != 7                ^
    2 != 7                    ^
    7 == 7                        ^              
```

# Implementación en Java
```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}
```