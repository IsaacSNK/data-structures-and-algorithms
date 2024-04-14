# Introducción

_Pathfinding_ se refiere a búsqueda de caminos entre dos puntos en un plano, especialmente útil para video juegos y simulaciones. Incluye una amplia variedad de algoritmos y no hay una solución única para todos los casos. Por ejemplo, la elección del algoritmo depende de:

- ¿És el destino estacionario o móvil?
- ¿Hay obstáculos en el mapa?
- ¿Hay diferente tipos de terreno en el mapa?

# Pathfinding básico

# Pathfinding basado en grafos

## Dijkstra

Cuando hay costos de movimiento según la dirección. Se lleva el costo acumulado de llegar a cada nodo y se elige el camino con menor costo.

```java
frontier = PriorityQueue()
frontier.put(start, 0)
came_from = {}
cost_so_far = {}
came_from[start] = None
cost_so_far[start] = 0
while not frontier.empty() {
    current = frontier.get()
    if current == goal {
        break
    }
    for next in graph.neighbors(current) {
        new_cost = cost_so_far[current] + graph.cost(current, next)
        if next not in cost_so_far or new_cost < cost_so_far[next] {
            cost_so_far[next] = new_cost
            priority = new_cost
            frontier.put(next, priority)
            came_from[next] = current
        }
    }
}
```

> Visualmente, se puede entender la diferencia entre BFS y Dijkstra en el siguiente gráfico: https://www.redblobgames.com/pathfinding/a-star/introduction.html#breadth-first-search

## A\*

Considera el costo real (similar a Dijkstra) y una heurística que estima el costo restante. La heurística es una función que estima el costo de llegar al destino desde un nodo dado. La heurística debe ser admisible, es decir, nunca sobreestimar el costo real.

Se utiliza con ciertas mejoras, en game engines modernos, como Unity.

```java
frontier = PriorityQueue()
frontier.put(start, 0)
came_from = {}
cost_so_far = {}
came_from[start] = None
cost_so_far[start] = 0
while not frontier.empty() {
    current = frontier.get()
    if current == goal {
        break
    }
    for next in graph.neighbors(current) {
        new_cost = cost_so_far[current] + graph.cost(current, next)
        if next not in cost_so_far or new_cost < cost_so_far[next] {
            cost_so_far[next] = new_cost
            priority = new_cost + heuristic(goal, next)
            frontier.put(next, priority)
            came_from[next] = current
        }
    }
}
```

Para calcular la heurística, se puede utilizar la distancia Manhattan o la distancia Euclidiana. La distancia Manhattan es la suma de las diferencias en las coordenadas x y y, mientras que la distancia Euclidiana es la distancia en línea recta.

```java
// Manhattan distance
function heuristic(a, b) {
    return abs(a.x - b.x) + abs(a.y - b.y)
}
```

Dependiendo del escenario, la heurística puede ser precalculada y almacenada en una tabla de búsqueda.

A* y Dijkstra son similares, pero A* es más rápido porque la heurística guía la búsqueda hacia el destino. La visualización [aquí](https://www.redblobgames.com/pathfinding/a-star/introduction.html#astar) permite compararlas.

Aunque A* y Dijkstra encuentran el camino, la cantidad de comparaciones realizadas por A* es mucho menor. En el peor caso, A* es igual a Dijkstra, pero en el mejor caso, A* es mucho más rápido.

# Referencias

- [Pathfinding](https://en.wikipedia.org/wiki/Pathfinding)
- [Pathfinding on Grids](https://www.redblobgames.com/pathfinding/a-star/introduction.html)
