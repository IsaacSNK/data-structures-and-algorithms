# Cache

- El cache se basa en el principio de localidad, que establece que los programas tienden a acceder a un conjunto reducido de direcciones de memoria en un corto periodo de tiempo.
- El concepto de caching puede ser aplicado e cualquier capa de computación, como CPU, disco, red, etc
- Se puede aplicar en distintas capas de la arquitectura de un sistema de información.
- Busca mantener datos usados frecuentemente en una ubicación óptima: cercano al usuario, cercano a la aplicación, en memoria más rápida, etc.

## Funcionamiento general

1. Se solicita un dato
2. Se busca en el cache
3. Si se encuentra, se devuelve al usuario (cache hit)
4. Si no se encuentra, se busca en la fuente original (cache miss) y se almacena en el cache para futuras solicitudes.

## Operaciones en el cache

Dado que la capacidad de un caché es limitada, usarlo de forma eficiente es crucial. Las operaciones más comunes son:

- **Hit**: Cuando la información solicitada se encuentra en el caché.
- **Miss**: Cuando la información solicitada no se encuentra en el caché.

Cada vez que se produce un _miss_, se debe decidir qué información se debe eliminar del caché para hacer espacio para la nueva información. Existen diferentes políticas de reemplazo, como _Least Recently Used_ (LRU), _First In First Out_ (FIFO), _Least Frequently Used_ (LFU), _Most Recently Used_ (MRU), etc. Veamos algunas de estas

### Least Recently Used (LRU)

La política LRU reemplaza la entrada que no ha sido utilizada por más tiempo. Es la política más común y se basa en la idea de que si un elemento no ha sido utilizado recientemente, es menos probable que se utilice en el futuro.

### First In First Out (FIFO)

La política FIFO reemplaza la entrada que ha estado en el caché por más tiempo. Es la política más simple y se basa en la idea de que los elementos que han estado en el caché por más tiempo son menos probables de ser utilizados en el futuro.

### Least Frequently Used (LFU)

La política LFU reemplaza la entrada que ha sido utilizada menos veces. Se basa en la idea de que los elementos que han sido utilizados menos veces son menos probables de ser utilizados en el futuro.

### Most Recently Used (MRU)

La política MRU reemplaza la entrada que ha sido utilizada más recientemente. Se basa en la idea de que los elementos que han sido utilizados más recientemente son más probables de ser utilizados en el futuro.

## Tipos de cache a nivel general

### En memoria

Se almacena en la memoria RAM. Se utiliza para almacenar datos que se acceden con frecuencia a nivel del proceso.

### Caché de disco

Se almacena en el disco duro. Se utiliza para almacenar datos que se acceden con frecuencia a nivel del disco. Por ejemplo, los datos de un archivo que se accede con frecuencia.

### Caché distribuido

Se almacena en varios servidores. Se utiliza para almacenar datos que se acceden con frecuencia a nivel de la red. Por ejemplo, los datos de un sitio web que se accede con frecuencia.

## Tipos de cache a nivel específicos

### Application server cache

Es una especialización del cache en memorira. Se almacena en la memoria RAM del servidor de aplicaciones. Se utiliza para almacenar datos que se acceden con frecuencia a nivel de la aplicación.

### Caché global

Se almacena en varios servidores. Se utiliza para almacenar datos que se acceden con frecuencia a nivel global. Por ejemplo, los datos de un sitio web que se accede con frecuencia en todo el mundo.

### CDN (Content-delivery network)

## Problemas que afectan a todos los caches
