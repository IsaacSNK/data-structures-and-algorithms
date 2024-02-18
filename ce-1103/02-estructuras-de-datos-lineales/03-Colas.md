# Colas

Es una estructura de datos que sigue el principio de FIFO (del inglés First In, First Out), es decir, el primer elemento en entrar es el primero en salir. Respeta el orden de llegada de los elementos.

## Tipo de dato abstracto Cola

```java
public interface IQueue {
    void enqueue(int element);
    int dequeue();
    int front();
}
```

## Implementación de colas con arreglos

```java
public class ArrayQueue implements IQueue {
    private int[] queue;
    private int front;
    private int rear;
    private int size;

    public ArrayQueue(int size) {
        this.size = size;
        queue = new int[size];
        front = -1;
        rear = -1;
    }

    public void enqueue(int element) {
        if (rear == size - 1) {
            System.out.println("Queue Overflow");
        } else {
            if (front == -1) {
                front = 0;
            }
            queue[++rear] = element;
        }
    }

    public int dequeue() {
        if (front == -1) {
            System.out.println("Queue Underflow");
            return -1;
        } else {
            int element = queue[front];
            if (front == rear) {
                front = -1;
                rear = -1;
            } else {
                front++;
            }
            return element;
        }
    }

    public int front() {
        if (front == -1) {
            System.out.println("Queue Underflow");
            return -1;
        } else {
            return queue[front];
        }
    }
}
```

Esta implementación tiene un problema conocido como "drifting" que ocurre cuando se hacen muchas operaciones de inserción y eliminación. La cola se desplaza hacia la izquierda y se desperdicia espacio. Para solucionar este problema se puede implementar una cola circular.

```java
public class CircularArrayQueue implements IQueue {
    private int[] queue;
    private int front;
    private int rear;
    private int size;

    public CircularArrayQueue(int size) {
        this.size = size;
        queue = new int[size];
        front = -1;
        rear = -1;
    }

    public void enqueue(int element) {
        if ((rear + 1) % size == front) {
            System.out.println("Queue Overflow");
        } else {
            if (front == -1) {
                front = 0;
            }
            rear = (rear + 1) % size;
            queue[rear] = element;
        }
    }

    public int dequeue() {
        if (front == -1) {
            System.out.println("Queue Underflow");
            return -1;
        } else {
            int element = queue[front];
            if (front == rear) {
                front = -1;
                rear = -1;
            } else {
                front = (front + 1) % size;
            }
            return element;
        }
    }

    public int front() {
        if (front == -1) {
            System.out.println("Queue Underflow");
            return -1;
        } else {
            return queue[front];
        }
    }
}
```

Con una cola circular, el frente y el final no necesariamente estan al principio y al final del arreglo, respectivamente. En lugar de eso, el frente y el final se mueven a lo largo del arreglo. Cuando el final llega al final del arreglo, se mueve al principio del arreglo.

## Implementación de colas con listas enlazadas

```java
public class LinkedListQueue {
    private Node front;
    private Node rear;

    public LinkedListQueue() {
        front = null;
        rear = null;
    }

    public void enqueue(int element) {
        Node newNode = new Node(element);
        if (rear == null) {
            front = newNode;
            rear = newNode;
        } else {
            rear.next = newNode;
            rear = newNode;
        }
    }

    public int dequeue() {
        if (front == null) {
            System.out.println("Queue Underflow");
            return -1;
        } else {
            int element = front.data;
            front = front.next;
            if (front == null) {
                rear = null;
            }
            return element;
        }
    }

    public int front() {
        if (front == null) {
            System.out.println("Queue Underflow");
            return -1;
        } else {
            return front.data;
        }
    }

    private class Node {
        private int data;
        private Node next;

        public Node(int data) {
            this.data = data;
            this.next = null;
        }
    }
}
```
