# Sistemas de archivos

- Forma en que los archivos son nombrados, organizados y almacenados en el disco.
- Es la interfaz lógica entre usuario y la capa física de almacenamiento.
- Almacena metadata/atributos de los archivos. Por ejemplo el nombre, tamaño, fecha de creación, etc.
- Fuertemente relacionado con el sistema operativo seleccionado. Por ejemplo, Windows utiliza NTFS, Linux utiliza ext4, etc.

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
