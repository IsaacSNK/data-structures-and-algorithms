# Pilas

Una pila es una estructura de datos lineal que sigue el principio de LIFO (del inglés Last In, First Out), es decir, el último elemento en entrar es el primero en salir.

## Tipo de dato abstracto Pila

La pila tiene dos operaciones básicas:

- **Apilar (push)**: añade un elemento a la pila.
- **Desapilar (pop)**: elimina el último elemento apilado.
- **Tope (top)**: permite ver el elemento que está en la cima de la pila sin desapilarlo.

<pre>
| Before Push | After Push 3 | After Push 5 | After Pop | After Pop |
|-------------|--------------|--------------|-----------|-----------|
|             |              |   +---+      |           |           |
|             |              |   | 5 |      |           |           |
|             |   +---+      |   +---+      |   +---+   |           |
|   +---+     |   | 3 |      |   | 3 |      |   | 3 |   |   +---+   |
|   +---+     |   +---+      |   +---+      |   +---+   |   +---+   |
</pre>


```java
public interface IStack {
    void push(int element);
    int pop();
    int top();
}
```

Al igual que en el caso de las listas, se pueden implementar pilas con arreglos o con listas enlazadas.

## Implementación de pilas con arreglos

En la implementación de pilas con arreglos, se utiliza un arreglo unidimensional para almacenar los elementos de la pila.

```java
public class ArrayStack implements IStack {
    private int[] stack;
    private int top;
    private int size;

    public ArrayStack(int size) {
        this.size = size;
        stack = new int[size];
        top = -1;
    }

    public void push(int element) {
        if (top == size - 1) {
            System.out.println("Stack Overflow");
        } else {
            stack[++top] = element;
        }
    }

    public int pop() {
        if (top == -1) {
            System.out.println("Stack Underflow");
            return -1;
        } else {
            return stack[top--];
        }
    }

    public int top() {
        if (top == -1) {
            System.out.println("Stack Underflow");
            return -1;
        } else {
            return stack[top];
        }
    }
}
```

## Implementación de pilas con listas enlazadas

```java
public class LinkedListStack implements IStack {
    private Node top;

    public void push(int element) {
        Node newNode = new Node(element);
        newNode.next = top;
        top = newNode;
    }

    public int pop() {
        if (top == null) {
            System.out.println("Stack Underflow");
            return -1;
        } else {
            int element = top.data;
            top = top.next;
            return element;
        }
    }

    public int top() {
        if (top == null) {
            // Preguntar a los estudiantes, que es mejor, este enfoque o
            // lanzar excepciones como se vio en ejemplos pasados
            System.out.println("Stack Underflow");
            return -1;
        } else {
            return top.data;
        }
    }

    // Otro enfoque para que la clase nodo solo pueda usarse dentro de
    // la clase Stack
    private class Node {
        int data;
        Node next;

        public Node(int data) {
            this.data = data;
        }
    }
}
```
