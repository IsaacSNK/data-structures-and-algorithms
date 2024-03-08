# Análisis teórico de algoritmos

Parte de la teoría de complejidad computacional que provee estimación teórica de los recursos (tiempo, espacio) que un algoritmo requiere para ejecutarse.

- No depende de la máquina
- No es sencillo de calcular
- No requiere ejecutar el programa.
- Se enfoca en algoritmos y no en programas completos.

El output del análisis teórico es una función que describe el comportamiento del algoritmo. Por ejemplo, si se tiene un algoritmo de ordenamiento, se puede obtener una función que describe el tiempo que el algoritmo requiere para ordenar una lista de tamaño _n_.

- Si la función crece lento para valores grandes de _n_, el algoritmo es eficiente.

# Enfoques de análisis teórico

- _Complejidad como función del input_: calcular una función contando las operaciones elementales que el algoritmo realiza.

> Operaciones fundamentales son aquellas que se realizan en tiempo constante. Por ejemplo, una suma, una multiplicación, una comparación, etc.

- _Comportamiento asintótico_: sin calcular una función exacta, se busca una función que describa el comportamiento del algoritmo para valores grandes de _n_.

## Complejidad como función del input

Se consideran operaciones fundamentales, es decir, operaciones que se realizan en tiempo constante. Por ejemplo, una suma, una multiplicación, una comparación, etc.

El tiempo que toma cada operación fundamental se designa con una constante T.

Por ejemplo, para el siguiente algoritmo:

```java
int max(int[] array) {
    int max = array[0];
    for (int i = 1; i < array.length; i++) {
        if (array[i] > max) {
            max = array[i];
        }
    }
    return max;
}
```

La función que describe el tiempo que el algoritmo requiere para encontrar el máximo de un arreglo de tamaño _n_ es:

```java
int max = array[0]; ------------------------> 3T
for (int i = 1; i < array.length; i++) { ---> T + 2nT
    if (array[i] > max) { ------------------> 2T(n-1)
        max = array[i]; --------------------> 2T(n-1)
    }
```

Por lo tanto, `f(n) = 4T + 6nT`

## Análisis asintótico

Suponga que usted necesita enviar un archivo a un amigo en Guanacaste. ¿Qué es más rápidp, enviarlo por correo/FTP o llevarlo personalmente? Asumiento que ir a Guanacaste sin presas, tarda siempre 3 horas, podríamos tener el siguiente grafico:

![](../images/03-analisis-teorico-1.png)

No importa que tan grande sea el archivo, llevarlo físicamente siempre tarda lo mismo. Por medio electrónico, el tiempo de transferencia depende del tamaño del archivo y en algún momento será mayor que las 3 horas que tarda llevarlo físicamente.

Análisis asistóntico busca encontrar la función que represente el crecimiento con respecto a _n_.

### Big O, Big Θ, Big Ω

Son notaciones para describir la ejecución de un algoritmo en términos de su comportamiento asintótico.

- _Big O_: describe el límite suuperior. Por ejemplo O(n^2), O(n), O(2ˆn). El algoritmo es al menos tan rápido como este límite. No sobrepasa el límite dictado por Big O
