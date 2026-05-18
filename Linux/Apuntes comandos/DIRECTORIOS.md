- `bin:`  directorio estático donde se almacenan todos los binarios para garantizar las funciones básicas a nivel de usuario

- `sbin:` igual que bin pero para binarios de tareas propias del SO gestionadas únicamente por usuario root

- `boot:` directorio estatico que contiene todos los archivos y ejecutables necesarios en el arranque del sistema, que se deben de ejecutar antes del kernel (núcleo) del SO

- `dev:` incluye todos los dispositivos de almacenamiento en forma de archivo conectados al sistema, CDROM, USB, Disco duro...

- `etc:` almacenar archivos de configuración tanto a nivel de componente del SO como los programas y aplicaciones instaladas, debería de tener archivos configuración

- `home:` directorio de los usuarios estándar, almacenar archivos del usuario

- `lib:` incluye las bibliotecas necesarias para que se ejecuten todos los binarios que se encuentran en los directorios *bin* y *sbin*, así como los módulos propios del kernel. Y librerias compartidas

- `lib64:` igual que *lib* pero para sistemas de 64 bits

- `media:` el punto de montaje de todos los volúmenes propios que se montan temporalmente, como USB externos

- `opt:` extensión de usr onde hay archivos solo de lectura que son parte de programas autocontenidos

- `proc:` contiene información de procesos y aplicaciones que se están ejecutando en un momento determinado en el sistema, pero realmente no guarda nada como tal, son listas de eventos que se generan en el momento en el que accedemos a ello

- `root:` como home pero de root

- `srv:` almacenar archivos y directorios relativos a servidores que puedas tener instalados dentro de tu sistema

- `sys:` al igual que *proc* contiene archivos virtuales tambien que proveen información del kernel relativa a eventos del SO, es una evolución de proc

- `tmp:` guardar archivos temporales de todo tipo, ya sea de elementos del sistema o aplicaciones

- `usr:` almacenar todos los archivos de solo lectura relativo a las utilidades del usuario incluido todo el software

- `var:` contiene varios archivos con información del sistema, como bases de datos o información almacenada en la cache, actúa como registro del sistema