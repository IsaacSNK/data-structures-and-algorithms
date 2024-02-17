# Pilas
## Tipo de dato abstracto Pila
- Una pila es una estructura de datos lineal que sigue el principio de LIFO (del inglés Last In, First Out), es decir, el último elemento en entrar es el primero en salir. 
- La pila tiene dos operaciones básicas: 
    - **Apilar (push)**: añade un elemento a la pila, 
    - **Desapilar (pop)**: elimina el último elemento apilado. 
    - **Tope (top)**: permite ver el elemento que está en la cima de la pila sin desapilarlo.

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