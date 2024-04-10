# Introducción

- Es una mejora sobre `búsqueda binaria`, especificamente si los valores en el array están distribuídos uniformemente. La búsqueda por interpolación calcula la posición de la mitad del array basado en el valor del elemento buscado y los valores en los extremos del array.

- Búsqueda binaria siempre compara contra el elemento central del array, mientras que búsqueda por interpolación considera la llave de búsqueda antes de decidir contra cual elemento del array comparar.

- El código es igual al de búsqueda binaria, con la diferencia de que la posición del elemento medio se calcula de manera diferente:

```
mid = low + ((high - low) / (arr[high] - arr[low])) * (x - arr[low])
```

> Low y high se refieren a los índices del array, y arr[low] y arr[high] a los valores en esos índices.

La mejora en rendimiento con respecto a búsqueda binaria se da en el caso promedio (que depende de la distribución uniforme de los elementos en el array), con una complejidad de tiempo de `O(log log n)`.

# Referencias

- https://iq.opengenus.org/time-complexity-of-interpolation-search/
