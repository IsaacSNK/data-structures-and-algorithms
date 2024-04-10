# Introducción

Se fundamentan en el trabajo de John Holland en 1962, quien luego publica en 1975 su libro "Adaptation in Natural and Artificial Systems". Los algoritmos genéticos son una técnica de optimización y búsqueda basada en la teoría de la evolución de Darwin.

En 1980 se aplican en problemas de optimización y en 1989 en problemas de aprendizaje automático.

Se pueden definir como una técnica de búsqueda para problemas de optimización y aprendizaje automático que simula el proceso de selección natural.

Se consideran como algoritmos heurísticos, ya que no garantizan la obtención de la solución óptima, pero sí una solución aceptable en un tiempo razonable.

> Heurística significa "encontrar" en griego. Se refiere a la búsqueda de soluciones a problemas de forma rápida y eficiente, pero no necesariamente óptima. Es el pasado de _eureka_.

Utilizan técnicas inspiradas en la biología evolutiva, como la selección natural, la reproducción y la mutación.

# Definiciones esenciales

- **Individuo**: Representa una solución al problema. Puede ser una cadena de bits, un vector de números, una estructura de datos, etc.
- **Población**: Conjunto de individuos/posibles soluciones.
- **Fitness**: Función que evalúa la calidad de una solución/individuos
- **Características**: Representan las propiedades de un individuo. Pueden ser los genes de un individuo.
- **Genoma**: Conjunto de características de un individuo.

> Dependiendo del problema se pueden usar multiples cromosomas para representar un individuo.

# Representación de un individuo

El objetivo es optimizar el espacio de búsqueda escogiendo uan representación adecuada para el problema. Usualmente se recomienda el uso de bit-vectors, donde cada entrada indica si cierta característica está presente o no.

# Funcionamiento general

Inician con una población de individuos aleatorios. En cada generación, se evalúa el fitness de cada individuo, se seleccionan los mejores y se reproducen para generar una nueva generación.

La nueva población reemplaza a la anterior y se repite el proceso hasta que se cumple un criterio de parada.

> ¿Cuando se detiene el algoritmo? Puede ser cuando se alcanza un número máximo de generaciones, cuando se alcanza un fitness mínimo, cuando se alcanza un fitness máximo, etc.

<img src="../images/algoritmos-geneticos-1.png" style="background-color: white">

## ¿Cómo seleccionar los padres?

Después de aplicar la función de fitness, se obtiene un grupo de posibles padres:

- Secuencia: 1 - 2, 3 - 4...
- Random

## Introducir variabilidad

Después de seleccionar los padres, se aplica recombinación y mutaciones.

### Recombinación

Se mezclan los genes de los padres para generar nuevos individuos. Suponiendo que los siguientes bit-vectors representan los padres:

```
    | 0 | 1 | 2 | 3 | 4 | 5 |
P1: | 0 | 0 | 0 | 0 | 0 | 0 |
P2: | 1 | 1 | 1 | 1 | 1 | 1 |
                ˆ
                Cross-over point
```

Se generan los siguientes hijos:

```
    | 0 | 1 | 2 | 3 | 4 | 5 |
H1: | 0 | 0 | 0 | 1 | 1 | 1 |
H2: | 1 | 1 | 1 | 0 | 0 | 0 |
```

### Mutación

Con base en alguna probabilidad determinada, se hace flig a agunos bits aleatorios de cada bit-vector de los hijos generados.
