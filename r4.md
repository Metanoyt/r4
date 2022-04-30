## Bluetooth

El objetivo  inicial de bluetooth fue conectar inalámbricamente dispositivos móviles con una red de radio con bajo consumo eléctrico, bajo alcance y  bajo costo, esta  idea se expandió a redes LAN inalámbricas y conexión de periféricos de computadora.

En 1999 bluetooth lanzó su documentación y la IEEE empezó desarrollar una estandarización para el sistema, este estándar cubrirá detalles sobre su capa de enlace de datos y  su capa física.


### La arquitectura bluetooth

La unidad básica de un sistema bluetooth es llamado piconet que consiste en un dispositivo maestro con un alcance de 10 metros que puede llegar a tener hasta 7 nodos esclavos, además de estos 7 nodos esclavos pueden existir hasta 255 nodos parqueados, que básicamente son dispositivos que solo pueden esperar ser activados por el dispositivo maestro y por esto se configuran en un estado de bajo consumo donde solo esperan recibir paquetes de activación y responder a estos.

### Aplicaciones de bluetooth

Los protocolos de bluetooth se diferencian de los demás en cuanto a que tan específico se definen de las utilidades de los protocolos, en general un protocolo va a definir  de que es capaz y dejar que el usuario decida qué hacer con estas capacidades, pero bluetooth define 13  ‘perfiles’ de aplicaciones de la tecnología que definen estas utilidades específicamente, de estos 13 perfiles 2 son indispensables en cualquier dispositivo que use bluetooth y 11 son opcionales, estos perfiles son el de ‘acceso genérico’ y ‘descubrimiento de servicios’.

nota: esta lista ha crecido mucho desde la escritura de este libro.

### La pila de protocolo de bluetooth

Los estándares de bluetooth se pueden representar como una pila de modelo único, en esta pila podemos encontrar protocolos que actúan sobre la capa física, de enlace de datos, de red y de aplicación.


#### Capa de radio física

Su función principal es mover bits del nodo maestro a los nodos esclavos, para esto utiliza ondas inalámbricas de bajo consumo mediante la banda ISM de 2.4 Ghz que se divide en 79 canales de 1 MHz cada uno.





#### Capa de banda base

Esta capa toma conjuntos de bits y los transforma en paquetes definiendo formatos muy importantes, el protocolo define una multiplexión por tiempo con espacios de 625 microsegundos donde las transmisiones del nodo maestro inician en los espacios pares y las transmisiones de los esclavos inician en los espacios impares, los paquetes pueden tomar 1, 3 o 5 espacios cada uno. 

El protocolo acepta transmisiones de tipo asíncronas sin conexión donde no se asegura la entrega de los paquetes por lo que puede que sea necesario re-enviarlas, y de tipo sincrónicas donde se utiliza corrección de errores hacia delante para proveer alta seguridad de llegada de paquetes.
 

#### Capa grupal o Capa L2CAP

La funcionalidades de esta capa son: aceptar paquetes de hasta 64kb de capas más altas y dividirlas en marcos para su transmisión, manejar multiplexación y demultiplexación para múltiples orígenes de paquetes y finalmente negociar y manera los requerimientos de calidad de servicio.

#### Capa de perfiles

Capa donde se encuentran las funcionalidades de bluetooth previamente definidas que hacen uso de las capas de niveles más bajos para completar sus tareas únicas.


### La estructura del marco de bluetooth

Esta se divide en 3 partes:
1. Un espacio para datos que va de 0 a 2744 bits
2. Un espacio de 72 bits para el código de acceso que define cuál es el nodo maestro en la red
3. Un header de 54 bits que se divide en 6 partes
  - 3 bits para la dirección
  - 4 bits para definir el tipo de marco 
  - 8 bits para la verificación de sumas
  - Un bit de flujo que ayuda a comunicar cuando es que el buffer de un esclavo está lleno y no puede recibir más información
  - Un bit de reconocimiento 
  - Un bit de secuencia que ayuda a determinar retransmisiones. 

