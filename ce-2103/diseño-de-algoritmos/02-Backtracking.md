# Backtracking
- Popularizado por Henry Lehmer, matemático estadounidense.
- Es una forma metódica de probar distintas secuencias de decisiones hasta encontrar una que funcione
- Se puede conceptualizar como un árbol de decisiones
    - Cada nodo del árbol solo puede ver sus hijos directos
    - Si un nodo conduce a error, se regresa al anterior y se prueba con otro hijo

La estructura general en código se puede resumir como:

```java
backtrack(x) {
    if (x == solucion) {
        return true;
    }
    for (nodo in x.nodos) {
        if (nodo == solution) {
            return true;
        } else {
            return backtrack(nodo);
        }
        
    }
}
```    

## Ejemplo: el problema de las N-reinas
Dado un tablero de ajedrez de NxN, colocar N reinas de tal forma que no se ataquen entre sí. Una reina puede atacar a otra si están en la misma fila, columna o diagonal.

```java
bool solve(board[][] col) {
    if (col == N) {
        return true;
    }
    for (int i = 0; i < N; i++) {
        if (isSafe(board, i, col)) {
            board[i][col] = 1;
            if (solve(board, col + 1)) {
                return true;
            }
            board[i][col] = 0;
        }
    }
    return false;
}
```
}
