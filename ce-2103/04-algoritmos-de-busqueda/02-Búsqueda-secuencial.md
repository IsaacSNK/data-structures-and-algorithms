# Introducción
Búsqueda secuencial es la solución trivial para buscar en una colección de elementos. Cuando la colección está desordenada, es la única opción. Revisa/procesa cada elemento hasta encontrar el elemento deseado.
- En el peor caso, cada elemento de la colección es comparado contra la llave de búsqueda
- Si hay un _match_, la búsqueda termina y se retorna el índice del elemento
- Si no hay _match_, se retorna -1 (u otro índice negativo)

Por ejemplo, dado el siguiente array:

