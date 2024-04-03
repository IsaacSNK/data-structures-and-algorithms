# Tema #1 - Administración De Memoria

---

## Punteros

- La memoria se puede representar como celdas o filas

| Direccion | Valor |
| --------- | ----- |

---

- Una variable es un alias de una dirección

| Direccion         | Valor | Alias                                             |
| ----------------- | ----- | ------------------------------------------------- |
| 0x01<—(int x = 0) | 0     | X—>(Esto solo existe en el contexto del programa) |

---

- Para simplificar, podemos representar:

| Alias | Direccion | Valor | Tipo (Determina el tamaño del bloque de memoria) |
| ----- | --------- | ----- | ------------------------------------------------ |

---

- Una variable puede ser mas de una dirección de memoria.
  Int->32 bits->48->4 Dir.

- Un puntero es un tipo de datos

  - Los valores que pueden almacenar son direcciones de memoria.
  - Soporta ciertos operadores especiales
  - Tamaño de memoria ocupada por una variable tipo pointer depende de la arquitectura(32bits o 64bits)

- Declaración

        Int* ptr = null;
        char* char ptr = nul;
        void* ptr = null;

- Cual es el proposito de declarar pointers con tipo si todos ocupen el mismo espacio?

* Type check
* Read/Write size
* Aritmetica de pointers

- Todo puntero debe asignarse con un valor inicial. Un puntero sin inicializar en un bad pointer

        Int* ptr; 	:(

        int* ptr=null; 	:)

        char* ptr=0; 	:)

        char* ptr=nullptr;—>c++ 14 	:)

        int* ptr;

        if(ptr==null) {

        //————>nunca entrara

        } else {

        //

        }

* Un bad pointer tiene un valor random

## Operador &

- Unario
- Retorna la dirección de memoria de una variable
  Int n = 10;
  Int \* ptr = &n;

| Direccion | Alias | Valor                 |
| --------- | ----- | --------------------- |
| 0x01      | n     | 20                    |
| 0x05      | ptr   | 0x01 (—> apunta a 20) |
| 0x06      | b     | 20                    |

## Operador\*

- Unario
- Accede a la dirección de memoria contenida en la variable pointer
- Lectura—> rvalue

  Escritura—> lvalue

        *ptr = 20; //Lvalue
        Int b = * ptr; //Rvalue

* Los punteros pueden ser fuerte de bugs. Tener cuidado al usarlos.

        int* foo() {
          int temp = 50;
          return&temp;
      }
      void bar() {
          int temp = 66;
          return;
      }
      int main() {
          int* r = foo();
          cout <<*r; —>50
          bar();
          cout <<*r; —>60
      }				WTF!!!

* Usando el API del heap

        Int ptr= (int*)malloc(size of(int)); ——>Cantidad de Bytes por reservar

* Para liberar memoria se usa free(ptr);
* La casilla de memoria se marca como libre pero la mem no se libera
* En c++ se puede usar new/delete

        int* ptr= new int;
      free(ptr);
      if(ptr==null) {
       ———>no entra :((
      }

- El operador -> se utiliza en c++

      Person* p = new Person();
      p->name = “Hola”;

## Sharing

- Dos o mas pointers hacia la misma memoria

| Direccion | Alias | Value                 |
| --------- | ----- | --------------------- |
| 0x01      | num   | 20                    |
| 0x05      | Ptr 1 | 0x01 (—> apunta a 20) |
| 0x06      | Ptr 2 | 0x05 (—> apunta a 20) |

- Dos formas de acceder a la misma memoria.
