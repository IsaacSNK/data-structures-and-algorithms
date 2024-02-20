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
5, 2, 1
```

Dado el siguiente arreglo:

<pre>
[ 5, 3, 8, 6, 2, 7, 1, 4, 9 ]
</pre>

Con el gap de 5,

<pre>
[3, 4, 2, 6, 1, 5, 7, 9, 8]
</pre>
