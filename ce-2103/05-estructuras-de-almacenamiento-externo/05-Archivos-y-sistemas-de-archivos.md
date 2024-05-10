# Sistemas de archivos

- Forma en que los archivos son nombrados, organizados y almacenados en el disco.
- Es la interfaz lógica entre usuario y la capa física de almacenamiento.
- Almacena metadata/atributos de los archivos. Por ejemplo el nombre, tamaño, fecha de creación, etc.
- Fuertemente relacionado con el sistema operativo seleccionado. Por ejemplo, Windows utiliza NTFS, Linux utiliza ext4, etc.

El sistema de archivos requiere espacio en disco para almacenar la metadata. Por ejemplo, si se tiene un archivo de 1 KB, el sistema de archivos necesita espacio adicional para almacenar la metadata del archivo (nombre, tamaño, fecha de creación, etc.). Por tal motivo, posterior a formatear un disco, el espacio disponible es menor al espacio total del disco.

## Propósito

- Nombrar y organizar archivos.
- Proveer un API para el acceso a los archivos: Creación, lectura, escritura, eliminación, etc.
- Almacenar un índice de archivos y directorios.
- Gestionar permisos y restricciones de acceso para mantener la integridad y seguridad de los datos.
- Funciones avanzadas como compresión, cifrado, cuotas de disco, etc.

# Archivos

Se puede definir como el mecanismo de abstracción para hacer transparente al usuario, los detalles complejos del disco. Dicha abstracción provee un "canal de comunicación" para poder ejecutar operaciones como:

- Leer bytes
- Escribir bytes
- Desplazarse a una posición específica en el disco

Un archivo se puede procesar de varias formas:

- **Acceso secuencial**: byte por byte desde el principio hasta el final según el orden en que fueron escritos.

- **Acceso aleatorio**: acceso directo a cualquier parte del archivo (conocido como acceso directo) independientemente del orden de escritura.

> Acceso secuencial es más rápido que el acceso aleatorio, pero el acceso aleatorio es más flexible.

- **Acceso indexado**: acceso a través de un índice que contiene la ubicación de los datos. Depende de la estructura y propósito del archivo. Por ejemplo, si es un archivo que contiene registros de clientes, un índice puede mapear el identificador de cada cliente, a la posición de su registro en el archivo. Precursor de las bases de datos.

## Estructura de un archivo

Las estructuras más comunes de archivos son:

- Secuencia de bytes
- Registros de tamaño fijo
- Árboles de registros

### Secuencia de bytes

En este caso, se trata de archivos planos que contienen una secuencia de bytes. No tienen estructura interna y se pueden leer o escribir byte por byte. El sistema operativo no tiene conocimiento de la estructura interna del archivo, por lo que no puede realizar operaciones avanzadas como búsqueda o indexación.

Los archivos se reducen a ser "cubetas" de bytes, maximizando la flexibilidad. Windows/Linux/MacOS utilizan este tipo de archivos.

### Registros de tamaño fijo

En este caso, el archivo se organiza en registros de tamaño fijo. Cada registro contiene una estructura de datos con campos de tamaño fijo. Los registros se pueden leer o escribir de forma secuencial o aleatoria. Este tipo de archivos permite realizar operaciones de búsqueda y ordenamiento.

Al crear un archivo de registros de tamaño fijo, se debe especificar la estructura de cada registro. Por ejemplo, si se tiene un archivo de registros de empleados, cada registro puede contener los campos: nombre, apellido, edad, salario, etc.

Muy utilizados en mainframes y bases de datos.

### Árboles de registros

Similar al caso anterior, pero en lugar de almacenar los registros de forma secuencial, se almacenan en una estructura de árbol. Cada nodo del árbol contiene un registro y apunta a otros nodos. Este tipo de archivos permite realizar operaciones de búsqueda y ordenamiento de forma eficiente.

## Tipos de archivos

- **Archivos regulares**: Contienen datos de usuario. Pueden ser de texto o binarios.
- **Directorios**: Archivos que contienen una lista de archivos y directorios. Son partes esenciales del sistema de archivos.
- **Character special files**: Representan dispositivos de caracteres, como terminales y puertos serie.
- **Block special files**: Representan dispositivos de bloques, como discos duros y unidades flash.
- **Sockets**: Archivos que permiten la comunicación entre procesos.
- **Pipes**: Archivos que permiten la comunicación entre procesos.
- **Symbolic links**: Archivos que apuntan a otros archivos.
- **Binary files**: Archivos que contienen datos binarios, como imágenes, videos, etc.
