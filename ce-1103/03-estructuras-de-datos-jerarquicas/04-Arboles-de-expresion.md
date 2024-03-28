# Árboles de expresión

Aunque no son técnicamente un TDA distinto, es relevante mencionarlos dado que su uso es muy común en la resolución de problemas de programación.

Son árboles binarios en los que las hojas son operandos y los nodos internos son operadores. Se utilizan para representar (y resolver) expresiones aritméticas o expresiones sintacticas de un lenguaje de programación en la etapa de compilación.

Por ejemplo, la expresión matemática `3 + (4 * 5)` se puede representar con el siguiente árbol de expresión:

```
    +
   / \
  3   *
     / \
    4   5
```

# Conversión de arboles de expresión a notación infija

La notación infija es la forma tradicional de escribir expresiones matemáticas, en la que los operadores se escriben entre los operandos. Para generar la expresión, únicamente se requiere recorrer el árbol en inorden (izquierda, raíz, derecha).

```java
private void inOrderRecursive(TreeNode root) {
    if (root != null) {
        inOrderRecursive(root.left);
        System.out.print(root.key + " ");
        inOrderRecursive(root.right);
    }
}
```

| Árbol                                      | Expresión           |
| ------------------------------------------ | ------------------- |
| ![](../images/expression-tree-1.png =100x) | `(x + y) * (a - b)` |

# Conversión de expresión a árbol de expresión

Para convertir una expresión infija a un árbol de expresión, primero se debe convertir la expresión a notación postfija (postfix) y luego se debe recorrer la expresión postfija para construir el árbol.

## Convertir expresión infija a postfija

Para convertir una expresión infija a postfija, se puede utilizar el algoritmo de Shunting Yard. Este algoritmo fue desarrollado por Edsger Dijkstra en 1961 y permite convertir una expresión infija a postfija en tiempo lineal.

El algoritmo utiliza dos estructuras de datos: una pila para almacenar los operadores y una cola para almacenar los operandos. El algoritmo recorre la expresión infija de izquierda a derecha y, dependiendo del tipo de token que se encuentre, realiza una de las siguientes acciones:

- Si el token es un operando, se añade a la cola.
- Si el token es un operador, se añade a la pila. Antes de añadirlo, se verifica si hay operadores en la pila con mayor precedencia. Si es así, se desapilan y se añaden a la cola.

Por ejemplo,

```
( a + ( b * c ) )
^

cola:
pila: (
```

```
( a + ( b * c ) )
  ^

cola: a
pila: (
```

```
( a + ( b * c ) )
    ^

cola: a
pila: ( +
```

```
( a + ( b * c ) )
            ^

cola: a b c
pila: ( + ( *
```
