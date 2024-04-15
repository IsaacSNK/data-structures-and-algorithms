# Particionamiento de discos

Un solo disco físico puede ser dividido en varias particiones, cada una de las cuales se comporta como un disco independiente (lógico). Las particiones se pueden formatear con diferentes sistemas de archivos y se pueden montar en diferentes puntos de montaje.

En enlace entre lo físico y lo lógico se hace a través de la _metadada_ almacenada en la tabla de particiones. La tabla de particiones es un registro que contiene información sobre las particiones del disco, como su tamaño, ubicación y tipo de sistema de archivos. Esta tabla se encuentra en el primer sector del disco (MBR) y es leída por el sistema operativo al arrancar.

Una partición puede existir sin inicializarse.

## Volumen

Es una partición inicializada con un _sistema de archivos_. Es la interfaz lógica que utiliza el sistema operativo para acceder a los datos almacenados en el disco.
