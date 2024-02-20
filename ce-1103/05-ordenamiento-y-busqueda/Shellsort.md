# Introducción a Shellsort

Fue propuesto por Donald Shell en 1959.

La idea básica de Shellsort es que los elementos de un arreglo se ordenan en incrementos cada vez más pequeños. El último incremento es 1, que es el tamaño del arreglo. El algoritmo de Shellsort es una generalización del algoritmo **InsertionSort** y busca aprovechar al máximo el mejor caso de este, es decir, cuando los elementos ya están _casi_ ordenados.

Shellsort trabaja realizando sus Insertion Sorts en sublistas cuidadosamente seleccionadas, primero en sublistas pequeñas y luego en sublistas cada vez más grandes.

Shellsort rompe la lista en subconjuntos disjuntos, donde un subconjunto está definido por un "incremento", I. Cada registro en un subconjunto dado está separado por I posiciones. Por ejemplo, si el incremento fuera 4, entonces cada registro en el subconjunto estaría separado por 4 posiciones.

# Ejecución de Shellsort

Usando un enfoque sencillo, podemos definir los gaps (o incrementos) de la siguiente manera:

```
size / 2, size / 4, size / 8, ..., 1
```

Rendondeando hacia el entero más cercano hacia arriba. Entonces, dado un array de 9 elementos, los gaps serían:

```
5, 3, 1
```

Dado el siguiente arreglo:

<pre>
| Indices   | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |  
| Elementos | 5 | 3 | 8 | 6 | 2 | 7 | 1 | 4 | 9 |
=================================================
| gap=5     | 5 | 3 | 8 | 6 | 2 | 7 | 1 | 4 | 9 |
|           | ^-------------------^             |
|           | 5 | 3 | 8 | 6 | 2 | 7 | 1 | 4 | 9 |
|           |     ^-------------------^         |
|           | 5 | 1 | 8 | 6 | 2 | 7 | 3 | 4 | 9 |
|                     ^-------------------^     |
|           | 5 | 1 | 4 | 6 | 2 | 7 | 3 | 8 | 9 |
|                         ^-------------------^ |
|           | 5 | 1 | 4 | 6 | 2 | 7 | 3 | 8 | 9 |
=================================================
| gap de 3  | ^-----------^                     |
|           | 5 | 1 | 4 | 6 | 2 | 7 | 3 | 8 | 9 |
|           |     ^-----------^                 |
|           | 5 | 1 | 4 | 6 | 2 | 7 | 3 | 8 | 9 |
|           |         ^-----------^             |
|           | 5 | 1 | 4 | 6 | 2 | 7 | 3 | 8 | 9 |
|           |             ^-----------^         |
|           | 5 | 1 | 4 | 3 | 2 | 7 | 6 | 8 | 9 |
|           | ^-----------^                     |
|           | 3 | 1 | 4 | 5 | 2 | 7 | 6 | 8 | 9 |
|           |                 ^-----------^     |
|           | 3 | 1 | 4 | 5 | 2 | 7 | 6 | 8 | 9 |
|           |                     ^-----------^ |
|           | 3 | 1 | 4 | 5 | 2 | 7 | 6 | 8 | 9 |
=================================================
| gap de 1  | 1 | 3 | 8 | 7 | 2 | 5 | 6 | 4 | 9 |
|           | ^---^                             |
|           | 1 | 3 | 8 | 7 | 2 | 5 | 4 | 6 | 9 |
|           |     ^---^                         |
|           | 1 | 3 | 8 | 7 | 2 | 5 | 4 | 6 | 9 |
|           |         ^---^                     |
|           | 1 | 3 | 7 | 8 | 2 | 5 | 4 | 6 | 9 |
|           |             ^---^                 |
|           | 1 | 3 | 7 | 2 | 8 | 5 | 4 | 6 | 9 |
|           |         ^---^                     |
|           | 1 | 3 | 2 | 7 | 8 | 5 | 4 | 6 | 9 |
|           |     ^---^                         |
|           | 1 | 2 | 3 | 7 | 8 | 5 | 4 | 6 | 9 |
|           |                 ^---^             |
|           | 1 | 2 | 3 | 7 | 5 | 8 | 4 | 6 | 9 |
|           |             ^---^                 |
|           | 1 | 2 | 3 | 5 | 7 | 8 | 4 | 6 | 9 |
|           |                     ^---^         |
|           | 1 | 2 | 3 | 5 | 7 | 4 | 8 | 6 | 9 |
|           |                 ^---^             |
|           | 1 | 2 | 3 | 5 | 4 | 7 | 8 | 6 | 9 |
|           |             ^---^                 |
|           | 1 | 2 | 3 | 4 | 5 | 7 | 8 | 6 | 9 |
|           |                         ^---^     |
|           | 1 | 2 | 3 | 4 | 5 | 7 | 6 | 8 | 9 |
|           |                     ^---^         |
|           | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|           |                             ^---^ |
=================================================
</pre>