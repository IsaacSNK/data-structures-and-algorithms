# Thread vs Process

## Programa

Un programa es un archivo ejecutable que contiene el código o el conjunto de instrucciones del procesador, que se almacena como un archivo en el disco.

## Process

Cuando un programa se ejecuta, se carga en memoria y se convierte en un **proceso**.

Un proceso activo incluye los recursos administrados por el sistema operativo que el programa necesita para ejecutarse

Ejemplos de procesos pueden ser:

1. Registros de procesador.
2. Contadores de programas.
3. Punteros de pila.
4. Páginas de memoria.

Cabe mencionar que cada proceso tiene su propio espacio de direcciones de memoria, por lo cual no pueden corromper el espacio de memoria de otro proceso.

## Thread

Un **hilo**, traducido al español, es la unidad de ejecución dentro de un proceso.

Todo proceso tiene al menos un hilo, llamado hilo principal.

Un programa suele tener varios hilos, también llamados subprocesos, y cada hilo tiene su propia pila.

Los hilos dentro de un proceso comparten un espacio de direcciones de memoria, haciendo posible comunicarse entre hilos utilizando ese espacio de memoria compartido.

Sin embargo, un hilo que se comporte mal podría arruinar todo el proceso.

## ¿Cómo el sistema operativo ejecuta un proceso o un hilo en un procesador?

Esto se maneja mediante el **cambio de contexto,** tanto para procesos como hilos**.**

Durante un cambio de contexto, un proceso se desconecta del procesador para que se pueda ejecutar otro proceso.

El sistema operativo almacena los estados del proceso en ejecución actual para que el proceso pueda restaurarse y reanudar la ejecución en un momento posterior.

Luego restaura los estados previamente guardados de un proceso diferente y reanuda la ejecución de ese proceso.

El cambio de proceso es costoso, este implica guardar y cargar registros, cambiar paginas de memoria y actualizar varias estructuras de datos del kernel.

Generalmente es más rápido cambiar de contexto entre hilos que entre procesos, ya que hay menos estados que rastrear, y la principal razón, es que dado que los hilos comparten el mismo espacio de direcciones de memoriam, no hay necesidad de cambiar páginas de memoria virtual, que es una de las operaciones más costosas durante un cambio de contexto.

Existen mecanismos para minimizar el costo de los cambios de contexto, como las fibras y corrutinas, que intercambian complejidad por costos de cambio de contexto aún más bajos. En general, se programan de forma cooperativa, es decir, deben ceder el control para que otros los ejecuten.
