# Definición de Sistema Operativo (S.O)

- Capa de software que interactúa directamente con el hardware.

Por así decirlo, el S.O interactúa como un intermediario entre el hardware que posee una computadora y las aplicaciones de software, así facilitando la gestión de recursos del sistema.

## Funciones

### API para los developers

API corresponde a las siglas de la palabra _Application Programming Interface_, la cual es una interface para los recursos del hardware. Es utilizado para varias cosas, como por ejemplo API web, API S.O, API class libraries, etc; en nuestro caso, nos interesa el API S.O.

Un estándar para las API de los S.O es el **posix**. El posix son las siglas de la palabra en inglés _portable operative interface for unix_. Como se mencionó, el posix es un **estándar del IEEE para los APIS del S.O**.

Un ejemplo de API, para archivos es el _pointer_ o _handler_ al archivo:
`fptr = fopen("archivo.txt")`

### Administrar los recursos de la máquina.

La idea de estos recursos administrados por el S.O es buscar una transpariencia con los componentes del hardware. La idea es poder interactuar con ellos de forma directa sin la necesidad de usarlos o visualizarlos físicamente, lo cual se vuelve más complejo.

Ejemplos de estos recursos son los siguientes:

- Procesos (CPU): Programas en ejecución con recursos asignados.
- Memoria Principal: RAM (_Random Acces Memory_).
- Archivos: Discos.
- I/O (_Input/Output_): Entrada y salida del sistema, como por ejemplo el teclado, mouse, red, entre otros.

Dentro de los procesos, se encuentran los _threads_ (hilos) y los procesos como tal. Los hilos son procesos que se realizan de forma "aparte", siendo tareas muy pequeñas a la cual el procesador pueda dedicarle tiempo. A diferencia de un hilo, un proceso corresponde al programa que se encuentra en "acción".

Respecto a la memoria principal, se tienen las abstracciones de _heap_ y _stack_.

## Definición de Administración de Memoria (ADM)

La administración de memoria viene de la pregunta ¿cómo distribuyo la RAM? Donde estas corresponde a tareas que realia el S.O para distinguir la memoria principal entre los procesos. Incluye la gestión de RAM y disco (memoria virtual).

## ¿Por qué se necesita?

- Asignar/Liberar memoria al inicio/fin de un proceso.
- Controlar la memoria asignada a un proceso.
- Minimizar la fragmentación.
- Mantener la integridad de los datos.

La idea de controlar la memoria asignada a un proceso, tiene como fin hacer que el mismo tenga un límite y aislamiento, para que así no afecte a otros procesos en la memoria que se estén ejecutando.

Además, al ser disminuida la fragmentación se puede brindar una memoria continua a los procesos (desfragmentación).

A continuación se comparte un par de imágenes para explicar la fragmentación.

![Desfragmentacion.png](https://github.com/devrepox/img/blob/main/Desfragmentacion.PNG?raw=true)

En la imagen anterior se puede visualizar una malla de cuadrados donde cada uno tiene o no tiene una equis dentro, donde cada cuadrado representa un espacio en memoria y cada equis (del mismo color) representa un proceso.

La idea de realizar una desfragmentación en la memoria permite evitar el siguiente tipo de situación:

![Desfragmentacion2.png](https://github.com/devrepox/img/blob/main/Desfragmentacion2.PNG?raw=true)

Si se desea realizar un proceso que requiera tres espacios en memoria, no se podría realizar la ejecución del mismo, ya que requiere los tres espacios de memoria continuos y no "separados".

Así teniendo lo siguiente al realizar la desfragmentación:

![Desfragmentacion2.png](https://github.com/devrepox/img/blob/main/Desfragmentacion3.PNG?raw=true)

Por lo tanto, ahora si se puede realizar el proceso que necesita tres espacios en memoria.
