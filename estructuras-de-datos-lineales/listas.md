# Listas

## Implementación mediante arreglos

```
public class ArrayList implements List {
    private int maxSize;
    private int currentSize;
    private int[] storage;

    public ArrayList(int size) {
        this.maxSize = size;
        this.currentSize = 0;
        this.storage = new int[size];
    }

    public void clear() {
        this.currentSize = 0;
    }

    public boolean isEmpty() {
        return this.currentSize == 0;
    }

    public int size() {
        return this.currentSize;
    }

    public boolean contains(int element) {
        for (int i = 0; i < this.maxSize; i++) {
            if (this.storage[i] == element) {
                return true;
            }
        }
        return false;
    }

    public boolean add(int element) {
        if (this.currentSize > this.maxSize) {
            return false;
        }
        this.storage[currentSize++] = element;
        return true;
    }

    public int remove(int element) {
        int i;
        for (i = 0; i < this.maxSize; i++) {
            if (this.storage[i] == element) {
                indexToRemove = i;
            }
        }
        if (i == this.maxSize) {
            throw new NoSuchElementException();
        }
        for (int j = i; j < this.currentSize - 1; j++) {
            this.storage[j] = this.storage[j + 1];
        }
        this.currentSize--;
    }
}
```

- Algunos lenguajes explicitamente proveen soporte para ArrayList
- **La principal ventaja** que proveen en vez de usar directamente es la abstracción de más alto nivel. El programador no tiene que lidiar con _shifts_, re-sizes u otros problemas de usar arreglos directamente
- Una estrategia que se puede utilizar para evitar lanzar una excepción al llegar al tamaño máximo, es crear un nuevo array de mayor tamaño y copiar los elementos del array actual. Pero si tendrá un _hit_ de performance.

## Implementación mediante listas enlazadas

- Utiliza memoria dinámica en vez de un arreglo, es decir, asigna memoria en el _heap_ cada vez que un elemento se agrega
- Dado que crea la memoria _justo en el momento_, cada elemento de la lista está separado en la memoria (a diferencia de un array donde todos los elementos están en memoria contigua)
- Cada elemento de la lista es un _nodo_. Cada nodo tiene dos partes:
  - El **valor**: es el elemento relevante para el programador. El valor que solicitó registrar en la lista. Por ejemplo, `add(3)`, el 3 es el valor de interés para el programador
  - Una **referencia** al nodo siguiente que actua como el elemento que encadena la lista.
- Visualmente, una lista enlazada se puede representar como:
  ![](../images/linked-list-1.png)
  - Como se puede notar, el último elemento apunta a _null_ indicando el fin de la lista
  - Es esencial llevar y mantener una referencia a la cabeza de la lista. Si la cabeza de la lista se pierde ser
