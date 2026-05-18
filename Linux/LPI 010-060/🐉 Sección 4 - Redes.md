
# 📶 1. Introducción a redes

<div style="border: 2px solid #2980b9; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>🌐 Red Informática: </b></span> <span style="font-size:18px">Es un conjunto de <b>ordenadores y dispositivos</b> conectados entre sí mediante cables, señales u ondas, con el fin de compartir información, recursos (como impresoras o discos duros) y servicios (como el acceso a Internet).</span> </div> </div>

**Conceptos clave:**

- **Nodos:** Son los dispositivos que se conectan.
- **Medio de transmisión:** El "camino" por donde viajan los datos (cable de fibra óptica, Ethernet o Wifi).
- **Protocolos:** El lenguaje común que usan los equipos para entenderse, como el **TCP/IP** que es la base de Internet.

<table style="width: 100%; border-collapse: collapse; text-align: center; border: none; font-family: sans-serif;"> <thead> <tr style="background-color: rgba(26, 26, 26, 0.7); color: #8e44ad; border-bottom: 4px solid rgba(128, 128, 128, 0.3);"> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Tipo de Red</th> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Siglas</th> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Alcance y Uso</th> </tr> </thead> <tbody style="color: inherit;"> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>Red de Área Local</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">LAN</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Limitada a una casa, oficina o un edificio.</td> </tr> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>Red de Área Metropolitana</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">MAN</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Cubre una ciudad o un campus universitario.</td> </tr> <tr style="border: none;"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>Red de Área Amplia</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">WAN</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Conecta países o continentes (ej. Internet).</td> </tr> </tbody> </table>

### HOST (ANFITRIÓN)

Es cualquier dispositivo conectado a una red (ordenador, móvil, tablet, servidor) que tiene asignada una **dirección IP única**. Se le llama así porque es el "anfitrión" que aloja, envía o recibe datos y servicios.

**Relación con la dirección IP:**

<div style="border: 2px solid #8e44ad; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>🆔 Dirección IP: </b></span> <span style="font-size:18px">Es una etiqueta numérica lógica que actúa como el <b>identificador único de un dispositivo</b> (ordenador, móvil, impresora) en una red, permitiendo que los datos se envíen y reciban correctamente entre el emisor y el receptor sin errores de destino.</span> </div> </div>

- **Identificación:** La IP es el número que identifica al host dentro de la red. Sin IP, el dispositivo no puede comunicarse con otros porque nadie sabría "dónde está", permite la comunicación TCP/IP entre ordenadores.
	- IP: 192.168.0.10

- **Comunicación:** Cuando envías un mensaje, el host de origen usa su IP para firmar el envío y la IP del host de destino para que el mensaje llegue al lugar correcto.

<div style="border: 2px solid #E44919; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>📜 Protocolo: </b></span> <span style="font-size:18px">Es un <b>conjunto de reglas y normas</b> establecidas que permiten que dos o más dispositivos se comuniquen entre sí. Actúa como un "idioma común" que define el formato, el orden y la corrección de errores para que la información enviada sea interpretada correctamente por el receptor.</span> </div> </div>

<div style="border: 2px solid #3498db; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> 
    <div style="margin-bottom: 15px;"> 
        <span style="font-size:20px"><b>🌍 Modelo OSI: </b></span> 
        <span style="font-size:18px">Es un marco de referencia teórico que <b>divide el proceso de comunicación en red en 7 capas</b> distintas. Su función es estandarizar cómo los datos viajan desde una aplicación en un dispositivo hasta otra aplicación en un dispositivo remoto, asegurando que diferentes tecnologías puedan interoperar.</span> 
    </div>

    <div style="margin-bottom: 15px;">
        <span style="font-size:18px">La información viaja desde tu dispositivo a un servidor, mediante <b>cable o wifi</b>, y del servidor al destino. Para saber por donde ir están las capas que van de más a menos:</span>
    </div>

    <div style="font-size:18px; line-height: 1.6;">
        <b>💻 7.</b> Aplicación: Consume los datos, podríamos enviar correos, transferir archivos, ir a sitios web, conectarnos a otras máquinas... Aquí se encuentran HTTP, FTTP, etc<br>
        <b>🧮 6.</b> Presentación: Traduce todos los datos, convierte los códigos a caracteres para la siguiente capa, también se encarga del cifrado<br>
        <b>🛡️ 5.</b> Sesión: Responsable de establecer y terminar conexión entre hosts, brinda soporte y realiza tareas de seguridad <br>
        <b>🛻 4.</b> Transporte: Garantiza el envió y la recepción de los paquetes de la capa 3 gestionando el transporte para garantizar el éxito, aquí están <b>TCP y UDP</b><br>
        <b>🏢 3.</b> Red: Actúa como una oficina de correos, es la más activa y es donde se encuentra el IP origen y destino, puede priorizar que mensajes enviar primero, es la <b>capa de enrutamiento</b> donde se decide que camino llevará el paquete para llegar de una red a otra. <br>
        <b>🕵 2.</b> Datos: Actúa como inspector, comprueba errores en formato de paquetes y controla el flujo con el que se envían los paquetes, en esta capa se encuentran los dispositivos <b>Switches</b>. Estos dispositivos operan usando direcciones MAC para mover tramas dentro de una misma red local.<br>
        <b>🖊️ 1.</b> Física: Dispositivos y cables de red físicos por donde sale la info
    </div>
</div>

<div style="border: 2px solid #e74c3c; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> 
    <div style="margin-bottom: 15px;"> 
        <span style="font-size:20px"><b>🚀 Modelo TCP/IP: </b></span> 
        <span style="font-size:18px">Es el modelo práctico y real que <b>hace funcionar Internet</b>. A diferencia del OSI, este se divide en <b>4 capas</b> fundamentales. Es el conjunto de protocolos que permite que cualquier ordenador del mundo se conecte con otro, priorizando la eficiencia y la entrega de datos.</span> 
    </div>

    <div style="margin-bottom: 15px;">
        <span style="font-size:18px">En este modelo, las funciones se agrupan para facilitar la comunicación. La información se empaqueta y se dirige siguiendo estos niveles de arriba hacia abajo:</span>
    </div>

    <div style="font-size:18px; line-height: 1.6;">
        <b>🌐 4. Aplicación:</b> Es la capa superior donde residen los protocolos que usamos directamente. Engloba las capas 5, 6 y 7 del modelo OSI. Aquí es donde los programas interactúan con la red mediante <b>HTTP, FTP, DNS o SSH</b>.<br>
        
        <b>🛻 3. Transporte:</b> Se encarga de la comunicación extremo a extremo. Define cómo se deben enviar los datos, controlando el flujo y la corrección de errores. Sus dos pilares son <b>TCP</b> (conexión segura y garantizada) y <b>UDP</b> (conexión rápida pero sin confirmación).<br>
        
        <b>🏢 2. Internet:</b> Es el corazón del modelo. Se encarga de poner las etiquetas de dirección a los paquetes y decidir la mejor ruta para que viajen a través de distintas redes. Aquí es donde vive el protocolo <b>IP</b> y se realiza el <b>enrutamiento</b>.<br>
        
        <b>🔌 1. Acceso a la Red:</b> Define cómo los datos deben enviarse físicamente a través del medio (cable, fibra, Wi-Fi). Combina las capas 1 y 2 de OSI, gestionando el direccionamiento <b>MAC</b> y los componentes de hardware como los <b>Switches y tarjetas de red</b>.
    </div>
</div>

<div style="border: 2px solid #2ecc71; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> 
    <div style="margin-bottom: 15px;"> 
        <span style="font-size:20px"><b>🏗️ Arquitectura de Aplicación Web: </b></span> 
        <span style="font-size:18px">Es un modelo que divide el funcionamiento de una web en capas lógicas para separar la interfaz de usuario, el procesamiento de datos y el almacenamiento final.</span> 
    </div>

    <div style="margin-bottom: 15px;">
        <span style="font-size:18px">El flujo de información comienza en el navegador y atraviesa distintos servidores hasta llegar a los datos:</span>
    </div>

    <div style="font-size:18px; line-height: 1.6;">
        <b>🖥️ Capa de Presentación:</b> Es la interfaz que ve el usuario (Navegadores como Chrome o Firefox). Su función es <b>Renderizar HTML</b> y gestionar el envío de peticiones GET/POST.<br>
        
        <b>⚙️ Capa Lógica:</b> Aquí reside el motor de ejecución (Scripting engine). Se encarga de <b>cargar, compilar y ejecutar</b> el código escrito en lenguajes como <b>PHP, ASP.net o C++</b>.<br>
        
        <b>🔗 Capa de Aplicación:</b> Actúa como puente. Interactúa con el almacenamiento de datos y <b>define la lógica del negocio</b> utilizando servicios como SOAP, EJB o RMI.<br>
        
        <b>🗄️ Almacenamiento:</b> Es la base de datos final (Oracle, MySQL, SQL Server). Su tarea es la <b>ejecución de SQL</b> y el retorno de los datos solicitados hacia las capas superiores.
    </div>
</div>


- **Roles:** Un host puede ser un **cliente** (tu PC pidiendo una web) o un **servidor** (el equipo que guarda esa web y te la envía).

- **Máscara de red:** Es un número que acompaña a la dirección IP para **delimitar qué parte de esa dirección identifica a la red** y qué parte identifica al host (dispositivo). Su función es permitir que el equipo sepa si otro dispositivo está en su misma red local o si debe enviar los datos fuera de ella a través del router.
	- Máscara red: 255.255.255.0
	- Con la IP de ejemplo anterior, sacamos que:
		- 192.168.0: Nombre de tu red
		- .10: Identificador personal dentro de la red
	-  Cuando nos encontramos con **/24** es una **notación CIDR** que indica de forma abreviada cuántos "unos" tiene la máscara en binario
		- **/24:** 255.255.255.0 (Tres bloques de 8 bits: 8+8+8)
		- **/16:** 255.255.0.0 (Dos bloques de 8 bits: 8+8)
		- **/8:** 255.0.0.0 (Un bloque de 8 bits)

- **Router o Switch:** Principalmente solo "dirigen el tráfico" pero constan de un IP propio que servirá como puerta para comunicarnos con el resto de Internet, también se le llama **puerta de enlace.**
	- IP: 192.168.0.1

La cuestión es que los humanos no trabajamos con IPs públicas, si no que nos conectamos a páginas web que usan DNS que traducen las IPs a información sencilla que nosotros podemos tratar y recordar, por ejemplo, el DNS de los servidores de Google es DNS: 8.8.8.8.

Para configurar una red de demasiados ordenadores usamos un **servidor DHCP** el cual ofrece esa información a todos los ordenadores que lo están pidiendo, como cual es mi IP, DNS, Máscara de red...

<div style="border: 2px solid #FF0000; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>📍 Dirección MAC: </b></span> <span style="font-size:18px">Es un <b>identificador de 48 bits (6 bytes)</b> que corresponde de forma única a una tarjeta o dispositivo de red. Sus primeros 24 bits (3 bytes) son de <b>la dirección OUI</b> y sus otros 24 bits (3 bytes) <b>del NIC</b> Se trata de un código físico asignado por el fabricante, por lo que es <b>única a cada dispositivo</b> y actúa como su "huella dactilar" permanente a nivel de hardware. Se le conoce como <b>NIC</b> a la identidad del hardware específico, el chip que permite la comunicación, o lo que es lo mismo, <b>el controlador de interfaz de red</b>:</span> </div> </div>

Para configurarla, debemos entrar en **red** y en **configuración de red,** ponerlo en modo **manual** y no **DHCP** y configurar a mano cada uno de los valores mencionados anteriormente.

<table style="width: 100%; border-collapse: collapse; text-align: center; border: none; font-family: sans-serif;">
  <thead>
    <tr style="background-color: rgba(26, 26, 26, 0.7); color: #8e44ad; border-bottom: 4px solid rgba(128, 128, 128, 0.3);">
      <th style="padding: 12px; border: none; text-align: center; vertical-align: middle;">Parámetro</th>
      <th style="padding: 12px; border: none; text-align: center; vertical-align: middle;">Ejemplo Común</th>
      <th style="padding: 12px; border: none; text-align: center; vertical-align: middle;">Función</th>
    </tr>
  </thead>
  <tbody style="color: inherit;">
    <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);">
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;"><b>Dirección IP</b></td>
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;">192.168.1.50</td>
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;">Identidad única del dispositivo en la red.</td>
    </tr>
    <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);">
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;"><b>Máscara de Red</b></td>
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;">255.255.255.0</td>
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;">Define el límite entre la red y el host.</td>
    </tr>
    <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);">
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;"><b>Puerta de Enlace</b></td>
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;">192.168.1.1</td>
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;">IP del router para salir de la red local.</td>
    </tr>
    <tr style="border: none;">
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;"><b>DNS</b></td>
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;">8.8.8.8</td>
      <td style="padding: 10px; border: none; text-align: center; vertical-align: middle;">Traduce nombres de dominio en direcciones IP.</td>
    </tr>
  </tbody>
</table>



<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>


# 📐 2. Herramientas para configuración de red en Linux

## Comandos obsoletos

**Paquetes de comandos de red net-tools:** Durante muchos años se utilizaron estos comandos para auditar y configurar la red en Linux, Actualmente se consideran <u>obsoletos</u> y se recomienda el cambio a comandos más modernos, ya no suelen venir por defecto pero se pueden instalar con **net-tools**

Aquí tienes la tabla con la información actualizada, manteniendo el estilo y las etiquetas de negrita solicitadas:

<table style="width: 100%; border-collapse: collapse; text-align: center; border: none; font-family: sans-serif;"> <thead> <tr style="background-color: rgba(26, 26, 26, 0.7); color: #8e44ad; border-bottom: 4px solid rgba(128, 128, 128, 0.3);"> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Herramienta</th> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Función Principal</th> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Descripción Detallada</th> </tr> </thead> <tbody style="color: inherit;"> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>ifconfig</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Administrar las interfaces de red</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Gestiona IP, Máscara, etc., pero si los modificamos no son permanentes, ya que tienen más importancia los ficheros de configuración.</td> </tr> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>netstat</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Estado de conexiones y estadísticas</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Muestra conexiones, tablas de encaminamiento (mapa de rutas para enviar datos) y estadísticas. Herramienta para saber <b>qué esta ocurriendo y como se está comunicando mi dispositivo con el exterior.</b></td> </tr> <tr style="border: none;"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>route</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Administrar tablas de enrutamiento IP</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Si el destino es esta direccion de red o esta dentro de este rango, el route lo redijirá hacia el getaway o lo mandará para otro lado.</td> </tr> </tbody> </table>

Una **tabla de enrutamiento** es, en esencia, el **mapa de rutas** que utiliza un dispositivo de red (como un router o tu PC) para saber por dónde enviar los paquetes de datos para que lleguen a su destino.

- **Función:** Cuando un paquete llega al dispositivo, este consulta la tabla para decidir si debe enviarlo a la red local o mandarlo a través de la **Puerta de Enlace** (Gateway) hacia el exterior.

- **Prioridad:** Si no sabe qué hacer con un paquete, lo envía por la **ruta por defecto** (0.0.0.0), que normalmente apunta a tu router.

### Ifconfig

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="ifconfig.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

##### *Explicación de la imagen*

- **flags=4163 <UP, BROADCAST, RUNNING, MULTICAST>**: Son las "etiquetas" de estado. **UP** significa que la tarjeta está encendida y **RUNNING** que tiene el cable (o conexión virtual) conectado y funcionando.
    
- **mtu 1500**: Es el "tamaño máximo de paquete". Indica que el trozo más grande de datos que puede enviar de una vez es de 1500 bytes.
    
- **inet 192.168.0.34**: Esta es tu **dirección IP privada** actual. Es tu DNI dentro de tu red local.
    
- **netmask 255.255.255.0**: Es la máscara de red que ya vimos; dice que tu red es la `192.168.0.x`.
    
- **broadcast 192.168.0.255**: Es la dirección especial para enviar mensajes a **todos** los equipos de tu red a la vez.
    
- **inet6 fe80::...**: Es tu dirección IP en el nuevo protocolo **IPv6**. El `scope link` indica que solo sirve para hablar con equipos de tu misma red local.
    
- **ether 08:00:27:e3:4c:b2**: Es tu **dirección MAC**. Es un número físico único grabado en el hardware de tu tarjeta de red.
    
- **RX packets / TX packets**: Estadísticas de tráfico. **RX** es lo que has recibido (descargado) y **TX** es lo que has transmitido (subido). Los "errors" y "dropped" deberían estar en 0; si suben, tienes problemas de conexión.
### Netstat -l

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="netstat.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

##### *Explicación de la imagen*

- **Proto (unix):** Indica que es un protocolo de comunicación interna. Al ser de tipo "unix", los datos no viajan por la red, sino que se quedan dentro de la memoria del ordenador.
    
- **RefCnt (2):** Es el número de procesos que están conectados a este canal en este momento. En este caso, hay 2 programas usando este bus simultáneamente.
    
- **Flags ([ ACC ]):** Significa "Accept". Indica que el servicio está configurado para aceptar y recibir nuevas conexiones de otros programas que quieran comunicarse.
    
- **Type (STREAM):** Define un flujo de datos continuo y ordenado. Es similar a una tubería donde la información llega exactamente en el mismo orden en que se envió.
    
- **State (LISTENING):** El estado "Escuchando" confirma que el servicio está activo y esperando a que alguna aplicación le envíe una petición o mensaje.
    
- **I-Node (10708):** Es el número de identificación único que el sistema operativo le asigna a este socket dentro de su registro interno para gestionarlo rápido.
    
- **Path (/run/user/1000/bus):** Es la ubicación del "buzón" en el sistema. El número `1000` es tu ID de usuario y `bus` es el canal que permite que tus aplicaciones (como el panel de Parrot o el sonido) hablen entre sí.
### Route

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="royte.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

##### *Explicación a la imagen*

La **ruta por defecto (default)** es la instrucción que sigue tu ordenador cuando quiere conectar con cualquier sitio que no está en tu casa (como Google o YouTube). Como tu PC no conoce el mapa de todo Internet, esta línea le dice que le entregue todos esos paquetes a la **Puerta de Enlace (192.168.0.1)**, que es tu router, para que él se encargue de enviarlos fuera.

La **ruta de red local (192.168.0.0)** identifica a los dispositivos que están conectados a tu mismo router. Al tener un Gateway de `0.0.0.0`, tu PC entiende que no necesita intermediarios; sabe que el destino está "al lado" y puede enviar los datos directamente a través del cable o Wi-Fi sin preguntar al router.

La **máscara (Genmask)** actúa como el filtro que separa ambos mundos. La máscara `255.255.255.0` bloquea los primeros tres números de tu IP para marcar el territorio de tu red privada, mientras que la máscara `0.0.0.0` de la ruta por defecto sirve como un "comodín" para aceptar cualquier dirección del resto del mundo.

Finalmente, las **Flags y la Interfaz** indican el estado de salud de estas rutas. La letra **U** confirma que la ruta funciona y la **G** marca quién es el jefe (el router). Todo este tráfico, ya sea para hablar con el vecino o con el otro lado del mundo, sale físicamente por tu tarjeta de red **enp0s3**.





## Ping / tracepath / traceroute

En el trayecto de comunicación en red entre mi dispositivo y un destino, recorremos ciertos nodos, en ocasiones, es interesante **saber que nodos estamos recorriendo**

Aquí tienes la tabla actualizada con la información solicitada, eliminando la mención al paquete ICMP dentro de la descripción de `ping`:

<table style="width: 100%; border-collapse: collapse; text-align: center; border: none; font-family: sans-serif;"> <thead> <tr style="background-color: rgba(26, 26, 26, 0.7); color: #8e44ad; border-bottom: 4px solid rgba(128, 128, 128, 0.3);"> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Herramienta</th> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Función Principal</th> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Descripción Detallada</th> </tr> </thead> <tbody style="color: inherit;"> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>tracepath / tracepath6</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Trazar ruta al destino</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Muestra el camino recorrido hasta llegar al destino indicado.</td> </tr> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>traceroute / traceroute6</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Trazar ruta con opciones avanzadas</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Parecido a <b>tracepath</b> pero con más opciones, aunque en ocasiones puede requerir permisos de root.</td> </tr> <tr style="border: none;"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;"><b>ping / ping6</b></td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Comprobar conectividad</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Comprueba que el destino responde; en Linux no termina hasta que pulsemos CTRL+C, aunque se puede evitar usando la opción -c que indica el número de paquetes a enviar.</td> </tr> </tbody> </table>

El **ICMP** (Protocolo de Mensajes de Control de Internet) es como el "servicio de mensajería de emergencia" de Internet. Su trabajo no es enviar datos (como fotos o mensajes de chat), sino enviar **avisos y diagnósticos** entre dispositivos.

Cuando haces un **ping**, usas ICMP para preguntar: "¿Estás ahí?". El otro equipo responde con otro paquete ICMP diciendo: "Sí, aquí estoy". También sirve para avisar si una ruta está cortada o si un destino es inalcanzable. Es, básicamente, la herramienta que usan los ordenadores para saber si la red tiene buena salud.

### Ping

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="ping.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

##### *Explicación de la imágen*

- **`ping -c 3 yahoo.com`**: Es el comando que lanzaste. La opción `-c 3` le indica a Parrot que solo envíe **3 paquetes** y se detenga automáticamente, en lugar de seguir infinitamente.
    
- **`PING yahoo.com (74.6.143.25) 56(84) bytes of data.`**: El sistema traduce el nombre "yahoo.com" a su dirección IP real (`74.6.143.25`) y avisa que va a enviar paquetes de prueba de 56 bytes.
    
- **Líneas de `64 bytes from...`**: Estas son las respuestas de Yahoo (el "eco"). Cada línea es un paquete que fue y volvió con éxito.
    
    - **icmp_seq**: Es el número de orden del paquete (1, 2 y 3). Sirve para saber si alguno se ha perdido por el camino.
        
    - **ttl (Time to Live)**: Es el "tiempo de vida". Indica cuántos nodos o routers puede saltar el paquete antes de ser descartado. Aquí sale 49 o 50.
        
    - **time**: Es lo más importante, el **latencia o lag**. Indica que el paquete tardó unos **99 milisegundos** en ir hasta el servidor de Yahoo y volver a tu PC.
        
- **`--- yahoo.com ping statistics ---`**: Es el resumen final de la prueba.
    
- **`3 packets transmitted, 3 received, 0% packet loss`**: Confirma que enviaste 3 paquetes, Yahoo respondió a los 3 y **no se perdió nada**. Tu conexión es estable.
    
- **`rtt min/avg/max/mdev`**: Son las estadísticas de tiempo en milisegundos:
    
    - **min**: El viaje más rápido (98.1 ms).
        
    - **avg**: El tiempo promedio (98.9 ms).
        
    - **max**: El viaje más lento (99.4 ms).
        
    - **mdev**: La desviación estándar (qué tanto varió el tiempo entre un paquete y otro). Como es un número bajo (0.5), significa que tu conexión es muy constante.

### Tracepath

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="tracepath.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

##### *Explicación de la imágen*

- **`1?: [LOCALHOST] pmtu 1500`**: Es el inicio de la ruta en tu propio equipo. Te indica que el **MTU** (tamaño máximo de paquete) es de **1500 bytes**, que es el estándar para redes Ethernet.
    
- **Saltos 1, 2, 3 y 5 (`???`)**: Son los routers intermedios por los que pasa tu información. Los signos de interrogación significan que esos dispositivos están configurados para ser "invisibles": dejan pasar tus datos pero **no responden con su nombre o IP** por seguridad.
    
- **Tiempos (ms)**: Los números como `12.526ms` o `32.772ms` son el **tiempo de respuesta**. Aunque el router sea anónimo, sabemos que está ahí porque nos devuelve el paquete en ese tiempo.
    
- **`4: no reply`**: Aquí el paquete se perdió o el router de ese paso ignoró completamente la petición. Es un "salto ciego" donde no hubo ninguna respuesta de vuelta.
    
- **`6: 212-166-198-176.red-acceso.airtel.net`**: Es el destino final o el último punto alcanzable. Aquí el router **sí es público** y nos dice su nombre y que la conexión ha llegado con éxito (`reached`).
    
- **`Resume`**: Es el resumen final. Te confirma que para llegar al objetivo se han dado **6 saltos** en total y que el camino de vuelta se hizo por una ruta ligeramente distinta.
### Traceroute

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="traceroute.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>
##### *Explicación de la imágen*

- **Cabecera (`traceroute to google.com...`)**: Indica el destino final, la IP que ha resuelto el sistema para Google (`212.166.198.243`) y establece un límite de **30 saltos** máximos para no quedarse buscando eternamente si hay un error.
    
- **Salto 1 (`192.168.0.1`)**: Este es el primer paso de tus datos: **tu router**. Fíjate que el tiempo es bajísimo (unos 3 milisegundos), lo que indica que la conexión por cable o virtual entre tu Parrot y el router es perfecta.
    
- **Saltos 2, 3 y 5**: Estos son los nodos internos de tu proveedor de internet (ISP). Aquí ya empezamos a ver IPs públicas o de gestión interna de la operadora. Los tiempos suben un poco (de 12ms a 17ms) porque el paquete ya está viajando por la infraestructura de la calle.
    
- **Los asteriscos (`* * *`)**: Significan **"Request Timed Out"** (Tiempo de espera agotado).
    
    - En el **salto 4**, el router simplemente no respondió a la petición.
        
    - Del **salto 6 al 30**, vemos una pared de asteriscos. Esto ocurre porque el siguiente servidor en la ruta (o el firewall de Google) detecta que estás haciendo un rastreo y **bloquea los paquetes ICMP** por seguridad para evitar que sigas "mapeando" su red interna.
        
- **Los tres tiempos por línea**: Si te fijas, en cada salto aparecen tres mediciones de tiempo (ej. `3.227 ms 3.120 ms 2.975 ms`). Esto es porque `traceroute` envía **tres paquetes por cada salto** para sacar una media y asegurar que el tiempo de respuesta sea estable y no un golpe de suerte.


 ---


---

## El problema del Ping y la saturación 

No siempre podemos estar seguros de que un equipo nos vaya a responder al ping, ya que muchos servidores tienen esta opción desactivada por seguridad. Esto se debe a que, en el pasado, se usaron ataques masivos para colapsar sitios web: si miles de ordenadores mandan pings al mismo tiempo a un servidor, su tarjeta de red se "atonta" intentando responder a todos antes de atender a los usuarios reales que quieren entrar a la web.

Al centrar todos sus recursos en contestar esos pings, el servidor se satura y deja de funcionar para el resto del mundo. Sin embargo, las redes modernas tienen infraestructuras mucho más potentes y preparadas, capaces de gestionar miles de pings sin colapsarse ni dejar de dar servicio a la página web.

---

## Comandos nuevos


<div style="border-radius: 15px; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;"> 
  <table style="width: 100%; border-collapse: separate; border-spacing: 0; border-radius: 12px; overflow: hidden; border: 1px solid #444;"> 
    <thead> 
      <tr style="text-align: center; color: white; font-weight: bold; font-size: 1.1em;"> 
        <th style="padding: 18px; background: linear-gradient(135deg, #8a6d3b 0%, #5e4a26 100%); border-right: 1px solid #444; width: 40%; text-transform: uppercase; letter-spacing: 1px;"> 🪠 Comandos Obsoletos </th> 
        <th style="padding: 18px; background: linear-gradient(135deg, #2e7d32 0%, #1b5e20 100%); width: 60%; text-transform: uppercase; letter-spacing: 1px;"> 🧼 Comandos Nuevos </th> 
      </tr> 
    </thead> 
    <tbody style="color: #e0e0e0; font-size: 1em;"> 
      <tr style="background-color: #2a2a3c;"> 
        <td style="padding: 15px; border-bottom: 1px solid #444; border-right: 1px solid #444; text-align: center;"> 
          <code style="background: #3e3e5a; padding: 4px 8px; border-radius: 5px; color: #ffca28;">arp</code> 
        </td> 
        <td style="padding: 15px; border-bottom: 1px solid #444;"> 
          <b style="color: #81c784;">ip n</b> <span style="color: #999; font-style: italic;">(ip neighbor)</span> 
        </td> 
      </tr> 
      <tr style="background-color: #242435;"> 
        <td style="padding: 15px; border-bottom: 1px solid #444; border-right: 1px solid #444; text-align: center;"> 
          <code style="background: #3e3e5a; padding: 4px 8px; border-radius: 5px; color: #ffca28;">ifconfig</code> 
        </td> 
        <td style="padding: 15px; border-bottom: 1px solid #444;"> 
          <b style="color: #81c784;">ip a</b> <span style="color: #999; font-style: italic;">(ip addr)</span>, <b style="color: #81c784;">ip link</b>, <b style="color: #81c784;">ip -s</b> <span style="color: #999; font-style: italic;">(ip stats)</span> 
        </td> 
      </tr> 
      <tr style="background-color: #2a2a3c;"> 
        <td style="padding: 15px; border-bottom: 1px solid #444; border-right: 1px solid #444; text-align: center;"> 
          <code style="background: #3e3e5a; padding: 4px 8px; border-radius: 5px; color: #ffca28;">netstat</code> 
        </td> 
        <td style="padding: 15px; border-bottom: 1px solid #444;"> 
          <b style="color: #81c784;">ss</b>, <b style="color: #81c784;">ip route</b> <span style="color: #999;">(netstat -r)</span>, <b style="color: #81c784;">ip -s link</b> <span style="color: #999;">(netstat -i)</span>, <b style="color: #81c784;">ip maddr</b> <span style="color: #999;">(netstat -g)</span> 
        </td> 
      </tr> 
      <tr style="background-color: #242435;"> 
        <td style="padding: 15px; border-right: 1px solid #444; text-align: center;"> 
          <code style="background: #3e3e5a; padding: 4px 8px; border-radius: 5px; color: #ffca28;">route</code> 
        </td> 
        <td style="padding: 15px;"> 
          <b style="color: #81c784;">ip r</b> <span style="color: #999; font-style: italic;">(ip route)</span> 
        </td> 
      </tr> 
    </tbody> 
  </table> 
</div>

<div style="font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; color: #e0e0e0; padding: 25px; border-radius: 12px; background-color: #1e1e1e; line-height: 1.6; max-width: 900px; margin: auto;">

    <div style="padding-bottom: 20px; margin-bottom: 20px; border-bottom: 1px solid #444;">
        <b style="color: #ff8a65; font-size: 1.6em; letter-spacing: 0.5px;">Iproute2 (ip)</b><br>
        <span style="color: #a0a0a0;">Reemplaza los comandos ifconfig, route, y arp. Además aporta otras muchas funciones.</span>
    </div>

    <div style="text-align: center; margin: 25px 0; font-family: 'Consolas', monospace; font-size: 1.1em; padding: 15px; background: #252525; border-radius: 8px; border: 1px solid #3d3d3d;"> 
        <span style="color: #ffab91;">ip</span> 
        <span style="color: #ce93d8;">[OPCIONES]</span> 
        <span style="color: #f48fb1;">OBJETO</span> 
        <span style="color: #81d4fa;">[COMANDO [ARGUMENTOS]]</span> 
    </div>

    <table style="width:100%; border-collapse:collapse; margin-bottom:30px; border-radius:8px; overflow:hidden; border: 1px solid #555;"> 
        <tr style="background:#d84315; color:#fff;"> 
            <td colspan="2" style="height:40px; text-align:center; font-weight: bold; text-transform: uppercase; font-size: 0.9em; letter-spacing: 2px;">Objetos</td> 
        </tr> 
        <tr style="background: #2c2c2c; color: #ff8a65; font-size: 0.85em; text-transform: uppercase;"> 
            <td style="border:1px solid #444; padding:10px; text-align:center; width:30%;">Objeto</td> 
            <td style="border:1px solid #444; padding:10px;">Función</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #ffccbc;"><b>link</b></td> 
            <td style="border:1px solid #444; padding:10px;">Para configurar los objetos físicos o lógicos de la red.</td> 
        </tr> 
        <tr style="background: #2a2a2a;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #f48fb1;"><b>address</b></td> 
            <td style="border:1px solid #444; padding:10px;">Manejo de direcciones asociadas a los diferentes dispositivos.</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #ce93d8;"><b>neighbour</b></td> 
            <td style="border:1px solid #444; padding:10px;">Administrar los enlaces de vecindad (ARP).</td> 
        </tr> 
        <tr style="background: #2a2a2a;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #ffab91;"><b>rule</b></td> 
            <td style="border:1px solid #444; padding:10px;">Ver las políticas de enrutado y cambiarlas.</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #81d4fa;"><b>route</b></td> 
            <td style="border:1px solid #444; padding:10px;">Ver las tablas de enrutado y cambiar las reglas de las tablas.</td> 
        </tr> 
        <tr style="background: #2a2a2a;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #a5d6a7;"><b>tunnel</b></td> 
            <td style="border:1px solid #444; padding:10px;">Administrar los túneles IP.</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #fff59d;"><b>maddr</b></td> 
            <td style="border:1px solid #444; padding:10px;">Ver las direcciones multienlace, sus propiedades y cambiarlas.</td> 
        </tr> 
        <tr style="background: #2a2a2a;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #bcaaa4;"><b>mroute</b></td> 
            <td style="border:1px solid #444; padding:10px;">Establecer, cambiar o borrar el enrutado multienlace.</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; text-align:center; padding:10px; color: #90caf9;"><b>monitor</b></td> 
            <td style="border:1px solid #444; padding:10px;">Monitorizar continuamente el estado de los dispositivos, direcciones y rutas.</td> 
        </tr> 
    </table>

    <table style="width:100%; border-collapse:collapse; border-radius:8px; overflow:hidden; border: 1px solid #555;"> 
        <tr style="background:#ad1457; color:#fff;"> 
            <td colspan="2" style="height:40px; text-align:center; font-weight: bold; text-transform: uppercase; font-size: 0.9em; letter-spacing: 2px;">Ejemplos de Comandos</td> 
        </tr> 
        <tr style="background: #2c2c2c; color: #f06292; font-size: 0.85em; text-transform: uppercase;"> 
            <td style="border:1px solid #444; padding:10px; width:40%;">Acción</td> 
            <td style="border:1px solid #444; padding:10px; width:60%;">Sintaxis del Comando</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Des/activar interfaz</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #ef9a9a;">ip link set enp0s3 up/down</td> 
        </tr> 
        <tr style="background: #2a2a2a;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Des/activar arp</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #f48fb1;">ip link set dev enp0s3 arp on/off</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Ver Direcciones IP</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #ffccbc;">ip addr show / ip -c a</td> 
        </tr> 
        <tr style="background: #2a2a2a;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Añadir dirección IP</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #ce93d8;">ip addr add 192.168.1.4/24 dev enp0s3</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Borrar dirección IP</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #81d4fa;">ip addr del 192.168.1.4/24 dev enp0s3</td> 
        </tr> 
        <tr style="background: #2a2a2a;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Ver tabla enrutamiento</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #a5d6a7;">ip route show</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Añadir ruta</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #fff59d;">ip route add 10.10.50.0/24 via 192.168.1.1 dev enp0s3</td> 
        </tr> 
        <tr style="background: #2a2a2a;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Borrar ruta</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #bcaaa4;">ip route del 10.10.50.0/24</td> 
        </tr> 
        <tr style="background: #252525;"> 
            <td style="border:1px solid #444; padding:12px;"><b>Puerta de enlace</b></td> 
            <td style="border:1px solid #444; padding:12px; font-family: monospace; color: #90caf9;">ip route add default via 192.168.1.1</td> 
        </tr> 
    </table>

</div>


<div style="font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; color: #e0e0e0; padding: 25px; border-radius: 12px; line-height: 1.6; max-width: 900px; margin: auto;">

    <div style="padding-bottom: 20px; margin-bottom: 20px; border-bottom: 1px solid #3f3d71;">
        <b style="color: #b39ddb; font-size: 1.6em; letter-spacing: 0.5px;">Socket Statistics (ss)</b><br>
        <span style="color: #9fa8da;">Obtiene información sobre los sockets (internos y de red). Sin parámetros lista todas las conexiones actuales.</span>
    </div>

    <div style="text-align: center; margin: 25px 0; font-family: 'Consolas', monospace; font-size: 1.1em; padding: 15px; background: #16213e; border-radius: 8px; border: 1px solid #283593;"> 
        <span style="color: #f3e5f5;">ss</span> 
        <span style="color: #ce93d8;">[ options ]</span> 
        <span style="color: #81d4fa;">[ FILTER ]</span> 
    </div>

    <table style="width:100%; border-collapse:collapse; margin-bottom:30px; border-radius:8px; overflow:hidden; border: 1px solid #3f3d71;"> 
        <tr style="background:#4527a0; color:#fff;"> 
            <td colspan="2" style="height:40px; text-align:center; font-weight: bold; text-transform: uppercase; font-size: 0.9em; letter-spacing: 2px;">Options</td> 
        </tr> 
        <tr style="background: #1f1b2e; color: #b39ddb; font-size: 0.85em; text-transform: uppercase;"> 
            <td style="border:1px solid #3f3d71; padding:10px; text-align:center; width:30%;">Opción</td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Función</td> 
        </tr> 
        <tr style="background: #16213e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #ce93d8;"><b>-t</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Solo conexiones TCP</td> 
        </tr> 
        <tr style="background: #1a1a2e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #ce93d8;"><b>-u</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Solo conexiones UDP</td> 
        </tr> 
        <tr style="background: #16213e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #ce93d8;"><b>-4</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Solo conexiones IPV4</td> 
        </tr> 
        <tr style="background: #1a1a2e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #ce93d8;"><b>-6</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Solo conexiones IPV6</td> 
        </tr> 
        <tr style="background: #16213e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #ce93d8;"><b>-l</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Sockets a la escucha</td> 
        </tr> 
        <tr style="background: #1a1a2e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #ce93d8;"><b>-p</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Muestra el nombre y el PID del proceso asociado a cada conexion</td> 
        </tr> 
        <tr style="background: #16213e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #ce93d8;"><b>-s</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Estadísticas resumidas</td> 
        </tr> 
        <tr style="background: #1a1a2e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #ce93d8;"><b>-n</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">No resolver los nombres, mostrar las IPs</td> 
        </tr> 
    </table>

    <table style="width:100%; border-collapse:collapse; margin-bottom:30px; border-radius:8px; overflow:hidden; border: 1px solid #3f3d71;"> 
        <tr style="background:#283593; color:#fff;"> 
            <td colspan="2" style="height:40px; text-align:center; font-weight: bold; text-transform: uppercase; font-size: 0.9em; letter-spacing: 2px;">Filter</td> 
        </tr> 
        <tr style="background: #16213e; color: #81d4fa; font-family: monospace; text-align: center;">
            <td colspan="2" style="border:1px solid #3f3d71; padding:10px;">filtro := [ state ESTADO-TCP ] [ exclude ESTADO-TCP ] [ EXPRESION ]</td>
        </tr>
        <tr style="background: #1a1a2e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #90caf9; width:30%;"><b>-state</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Indica el estado del socket, como ESTABLISED, LISTENING, CLOSED, CONNECTED, TIME-WAIT, etc.</td> 
        </tr> 
        <tr style="background: #16213e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #90caf9;"><b>-exclude</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">Se excluirán los que estén en el estado indicado.</td> 
        </tr> 
        <tr style="background: #1a1a2e;"> 
            <td style="border:1px solid #3f3d71; text-align:center; padding:10px; color: #90caf9;"><b>-Expresión</b></td> 
            <td style="border:1px solid #3f3d71; padding:10px;">
                Se puede construir con:<br>
                • Operadores lógicos AND, OR, NOT<br>
                • <b>{src | dst} [IP[/prefijo]][:puerto]</b>: Origen (src) y/o destino (dst) por IP, prefijo o puerto.<br>
                • <b>{dport | sport} {eq | neq | gt | ge | lt | le} [IP]:puerto</b>: Puerto de origen o destino igual, mayor o menor que cierto rango.
            </td> 
        </tr> 
    </table>

    <table style="width:100%; border-collapse:collapse; border-radius:8px; overflow:hidden; border: 1px solid #3f3d71;"> 
        <tr style="background:#6a1b9a; color:#fff;"> 
            <td colspan="2" style="height:40px; text-align:center; font-weight: bold; text-transform: uppercase; font-size: 0.9em; letter-spacing: 2px;">Ejemplo</td> 
        </tr> 
        <tr style="background: #1f1b2e;"> 
            <td colspan="2" style="border:1px solid #3f3d71; padding:15px; font-family: monospace; color: #e1bee7; text-align: center; font-size: 1.1em;">
                ss state established '(sport = :http or sport = :https)' src 192.168.0.34/24
            </td> 
        </tr> 
        <tr style="background: #1a1a2e;"> 
            <td style="border:1px solid #3f3d71; padding:12px; width:30%; color: #ce93d8;"><b>state established</b></td> 
            <td style="border:1px solid #3f3d71; padding:12px;">Filtra solo las conexiones que están actualmente establecidas.</td> 
        </tr> 
        <tr style="background: #16213e;"> 
            <td style="border:1px solid #3f3d71; padding:12px; color: #ce93d8;"><b>sport = :http or :https</b></td> 
            <td style="border:1px solid #3f3d71; padding:12px;">Define que el puerto de origen (source port) sea el puerto 80 (http) o el 443 (https).</td> 
        </tr> 
        <tr style="background: #1a1a2e;"> 
            <td style="border:1px solid #3f3d71; padding:12px; color: #ce93d8;"><b>src 192.168.0.34/24</b></td> 
            <td style="border:1px solid #3f3d71; padding:12px;">Establece que la dirección IP de origen debe pertenecer al rango de red especificado.</td> 
        </tr> 
    </table>

</div>


<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>



# ⚓ 3. Configuración de red persistente

<div style="text-align:center;"><b>El directorio de configuración por excelencia es /etc, y aquí es donde encontraremos todos los ficheros para ello.</b></div>
<br>
<div style="text-align:center;"><h1 style="color:#a83232; margin-bottom:0;">/etc/hostname</h1></div>
<hr style="border:1.5px solid #a83232; margin-top:5px;">
**Donde se encuentra el nombre de nuestro host,** es decir, **de nuestro ordenador,** aparece siempre a la derecha de "@" de nuestra bash, es el propio nombre de la máquina y se puede configurar con el comando <b>hostname nuevo_nombre</b> o directamente reescribiendo el fichero <b>/etc/hostname</b>.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#a83232; color:#fff; font-weight:bold;">
    <td style="border:1px solid #7a2525; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #7a2525; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #7a2525; text-align:center; vertical-align:middle;">-s</td>
    <td style="border:1px solid #7a2525; text-align:left; vertical-align:middle; padding:8px;">Consulta el nombre</td>
  </tr>
  <tr>
    <td style="border:1px solid #7a2525; text-align:center; vertical-align:middle;">-f</td>
    <td style="border:1px solid #7a2525; text-align:left; vertical-align:middle; padding:8px;">Consulta el nombre y el dominio</td>
  </tr>
</table>

<br>
<div style="text-align:center;"><h1 style="color:#325ca8; margin-bottom:0;">/etc/hosts</h1></div>
<hr style="border:1.5px solid #325ca8; margin-top:5px;">
Fichero para **asociar nombres a IP's.** Cada linea contiene una IP seguido por uno o varios nombres que se asociarán a dicha IP. Para poner nuestras propias traducciones asociando a un IP el nombre que queramos, exactamente igual que hacen los DNS

<br>
<div style="text-align:center;"><h1 style="color:#2e7d32; margin-bottom:0;">hostnamectl</h1></div>
<hr style="border:1.5px solid #2e7d32; margin-top:5px;">
Comando del ecosistema Systemd para **modificar el nombre del host y otros valores**

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#2e7d32; color:#fff; font-weight:bold;">
    <td style="border:1px solid #1b5e20; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #1b5e20; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">Status</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Ver el estado</td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">Set-hostname NAME</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Modificar el nombre</td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">etc</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Otras opciones del sistema</td>
  </tr>
</table>

<br>
<div style="text-align:center;"><h1 style="color:#b0468c; margin-bottom:0;">/etc/resolv.conf</h1></div>
<hr style="border:1.5px solid #b0468c; margin-top:5px;">
Fichero donde se **guarda la configuración del servicio de resolución de nombres o DNS,** el cual es fundamental para acceder a internet al establecer la dirección IP que se tiene que consultar.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#b0468c; color:#fff; font-weight:bold;">
    <td style="border:1px solid #8a376d; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #8a376d; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #8a376d; text-align:center; vertical-align:middle;">nameserver</td>
    <td style="border:1px solid #8a376d; text-align:left; vertical-align:middle; padding:8px;">"direccion DNS que queremos usar"</td>
  </tr>
</table>

<br>
<div style="text-align:center;"><h1 style="color:#d17a15; margin-bottom:0;">/etc/nsswitch.conf</h1></div>
<hr style="border:1.5px solid #d17a15; margin-top:5px;">
**Fichero donde se específica el orden en el que se buscará la información,** por ejemplo, para establecer que a la hora de buscar DNS, busque primero en hosts antes que en los propios DNS del sistema y asi poder coger el DNS que hemos configurado nosotros.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#d17a15; color:#fff; font-weight:bold;">
    <td style="border:1px solid #a66110; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #a66110; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #a66110; text-align:center; vertical-align:middle;">hosts: files dns</td>
    <td style="border:1px solid #a66110; text-align:left; vertical-align:middle; padding:8px;">Primero mira los files, y luego los DNS</td>
  </tr>
</table>

<div style="text-align:center;"><b>El directorio de configuración por excelencia es /etc, y aquí es donde encontraremos todos los ficheros para ello.</b></div>

<br>

<div style="text-align:center;"><h1 style="color:#a83232; margin-bottom:0;">/etc/hostname</h1></div>
<hr style="border:1.5px solid #a83232; margin-top:5px;">
Donde se encuentra el nombre de nuestro host, es decir, de nuestro ordenador, aparece siempre a la derecha de "@" de nuestra bash, es el propio nombre de la máquina y se puede configurar con el comando <b>hostname nuevo_nombre</b> o directamente reescribiendo el fichero <b>/etc/hostname</b>.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#a83232; color:#fff; font-weight:bold;">
    <td style="border:1px solid #7a2525; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #7a2525; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #7a2525; text-align:center; vertical-align:middle;">-s</td>
    <td style="border:1px solid #7a2525; text-align:left; vertical-align:middle; padding:8px;">Consulta el nombre</td>
  </tr>
  <tr>
    <td style="border:1px solid #7a2525; text-align:center; vertical-align:middle;">-f</td>
    <td style="border:1px solid #7a2525; text-align:left; vertical-align:middle; padding:8px;">Consulta el nombre y el dominio</td>
  </tr>
</table>

<br>

<div style="text-align:center;"><h1 style="color:#325ca8; margin-bottom:0;">/etc/hosts</h1></div>
<hr style="border:1.5px solid #325ca8; margin-top:5px;">
Fichero para asociar nombres a IP's. Cada linea contiene una IP seguido por uno o varios nombres que se asociarán a dicha IP. Para poner nuestras propias traducciones asociando a un IP el nombre que queramos, exactamente igual que hacen los DNS

<br>

<div style="text-align:center;"><h1 style="color:#2e7d32; margin-bottom:0;">hostnamectl</h1></div>
<hr style="border:1.5px solid #2e7d32; margin-top:5px;">
Comando del ecosistema Systemd para modificar el bombre del host y otros valores

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#2e7d32; color:#fff; font-weight:bold;">
    <td style="border:1px solid #1b5e20; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #1b5e20; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">Status</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Ver el estado</td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">Set-hostname NAME</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Modificar el nombre</td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">etc</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Otras opciones del sistema</td>
  </tr>
</table>

<br>

<div style="text-align:center;"><h1 style="color:#b0468c; margin-bottom:0;">/etc/resolv.conf</h1></div>
<hr style="border:1.5px solid #b0468c; margin-top:5px;">
Fichero donde se guarda la configuración del servicio de resolución de nombres o DNS, el cual es fundamental para acceder a internet al establecer la dirección IP que se tiene que consultar.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#b0468c; color:#fff; font-weight:bold;">
    <td style="border:1px solid #8a376d; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #8a376d; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #8a376d; text-align:center; vertical-align:middle;">nameserver</td>
    <td style="border:1px solid #8a376d; text-align:left; vertical-align:middle; padding:8px;">"direccion DNS que queremos usar"</td>
  </tr>
</table>

<br>

<div style="text-align:center;"><h1 style="color:#d17a15; margin-bottom:0;">/etc/nsswitch.conf</h1></div>
<hr style="border:1.5px solid #d17a15; margin-top:5px;">
Fichero donde se específica el orden en el que se buscará la información, por ejemplo, para establecer que a la hora de buscar DNS, busque primero en hosts antes que en los propios DNS del sistema y asi poder coger el DNS que hemos configurado nosotros.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#d17a15; color:#fff; font-weight:bold;">
    <td style="border:1px solid #a66110; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #a66110; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #a66110; text-align:center; vertical-align:middle;">hosts: files dns</td>
    <td style="border:1px solid #a66110; text-align:left; vertical-align:middle; padding:8px;">Primero mira los files, y luego los DNS</td>
  </tr>
</table>

<br>
<div style="text-align:center;"><b>El directorio de configuración por excelencia es /etc, y aquí es donde encontraremos todos los ficheros para ello.</b></div>

<br>

<div style="text-align:center;"><h1 style="color:#a83232; margin-bottom:0;">/etc/hostname</h1></div>
<hr style="border:1.5px solid #a83232; margin-top:5px;">
Donde se encuentra el nombre de nuestro host, es decir, de nuestro ordenador, aparece siempre a la derecha de "@" de nuestra bash, es el propio nombre de la máquina y se puede configurar con el comando <b>hostname nuevo_nombre</b> o directamente reescribiendo el fichero <b>/etc/hostname</b>.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#a83232; color:#fff; font-weight:bold;">
    <td style="border:1px solid #7a2525; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #7a2525; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #7a2525; text-align:center; vertical-align:middle;">-s</td>
    <td style="border:1px solid #7a2525; text-align:left; vertical-align:middle; padding:8px;">Consulta el nombre</td>
  </tr>
  <tr>
    <td style="border:1px solid #7a2525; text-align:center; vertical-align:middle;">-f</td>
    <td style="border:1px solid #7a2525; text-align:left; vertical-align:middle; padding:8px;">Consulta el nombre y el dominio</td>
  </tr>
</table>

<br>

<div style="text-align:center;"><h1 style="color:#325ca8; margin-bottom:0;">/etc/hosts</h1></div>
<hr style="border:1.5px solid #325ca8; margin-top:5px;">
Fichero para asociar nombres a IP's. Cada linea contiene una IP seguido por uno o varios nombres que se asociarán a dicha IP. Para poner nuestras propias traducciones asociando a un IP el nombre que queramos, exactamente igual que hacen los DNS

<br>

<div style="text-align:center;"><h1 style="color:#2e7d32; margin-bottom:0;">hostnamectl</h1></div>
<hr style="border:1.5px solid #2e7d32; margin-top:5px;">
Comando del ecosistema Systemd para modificar el bombre del host y otros valores

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#2e7d32; color:#fff; font-weight:bold;">
    <td style="border:1px solid #1b5e20; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #1b5e20; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">Status</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Ver el estado</td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">Set-hostname NAME</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Modificar el nombre</td>
  </tr>
  <tr>
    <td style="border:1px solid #1b5e20; text-align:center; vertical-align:middle;">etc</td>
    <td style="border:1px solid #1b5e20; text-align:left; vertical-align:middle; padding:8px;">Otras opciones del sistema</td>
  </tr>
</table>

<br>

<div style="text-align:center;"><h1 style="color:#b0468c; margin-bottom:0;">/etc/resolv.conf</h1></div>
<hr style="border:1.5px solid #b0468c; margin-top:5px;">
Fichero donde se guarda la configuración del servicio de resolución de nombres o DNS, el cual es fundamental para acceder a internet al establecer la dirección IP que se tiene que consultar.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#b0468c; color:#fff; font-weight:bold;">
    <td style="border:1px solid #8a376d; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #8a376d; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #8a376d; text-align:center; vertical-align:middle;">nameserver</td>
    <td style="border:1px solid #8a376d; text-align:left; vertical-align:middle; padding:8px;">"direccion DNS que queremos usar"</td>
  </tr>
</table>

<br>

<div style="text-align:center;"><h1 style="color:#d17a15; margin-bottom:0;">/etc/nsswitch.conf</h1></div>
<hr style="border:1.5px solid #d17a15; margin-top:5px;">
Fichero donde se específica el orden en el que se buscará la información, por ejemplo, para establecer que a la hora de buscar DNS, busque primero en hosts antes que en los propios DNS del sistema y asi poder coger el DNS que hemos configurado nosotros.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#d17a15; color:#fff; font-weight:bold;">
    <td style="border:1px solid #a66110; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #a66110; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #a66110; text-align:center; vertical-align:middle;">hosts: files dns</td>
    <td style="border:1px solid #a66110; text-align:left; vertical-align:middle; padding:8px;">Primero mira los files, y luego los DNS</td>
  </tr>
</table>

<br>

<div style="text-align:center;"><h1 style="color:#0086b3; margin-bottom:0;">/etc/network/interfaces</h1></div>
<hr style="border:1.5px solid #0086b3; margin-top:5px;">
Fichero de configuración de las tarjetas de red en Debian.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#0086b3; color:#fff; font-weight:bold;">
    <td style="border:1px solid #005f80; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #005f80; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #005f80; text-align:center; vertical-align:middle;">allow-hotplug enp0s3<br>iface enp0s3 inet dhcp</td>
    <td style="border:1px solid #005f80; text-align:left; vertical-align:middle; padding:8px;">Configuración para obtener dirección IP de forma dinámica (DHCP).</td>
  </tr>
  <tr>
    <td style="border:1px solid #005f80; text-align:center; vertical-align:middle;">auto enp0s3<br>iface enp0s3 inet static<br>address 192.168.0.5<br>netmask 255.255.255.0<br>gateway 192.168.0.1</td>
    <td style="border:1px solid #005f80; text-align:left; vertical-align:middle; padding:8px;">Configuración para establecer una dirección IP estática con su respectiva máscara y puerta de enlace.</td>
  </tr>
</table>

<br>

<div style="text-align:center;"><h1 style="color:#6a1b9a; margin-bottom:0;">/etc/sysconfig/network-scripts/ifcfg-nombre_interfaz</h1></div>
<hr style="border:1.5px solid #6a1b9a; margin-top:5px;">
Fichero de configuración de las tarjetas de red en Red Hat.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">
  <tr style="background:#6a1b9a; color:#fff; font-weight:bold;">
    <td style="border:1px solid #4a148c; height:35px; width:40%; text-align:center; vertical-align:middle;"><b>Opción</b></td>
    <td style="border:1px solid #4a148c; height:35px; width:60%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">TYPE=Ethernet</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Tipo de interfaz</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">DEVICE=enp0s3</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Nombre de la interfaz</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">NM_CONTROLLED="no"</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Ignorado por NetworkManager</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">ONBOOT=yes</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Inicia al arrancar el Sistema</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">BOOTPROTO=none</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Usar configuración estática (dhcp)</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">HWADDR=01:0A:03:1F:67:13</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Dirección MAC</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">IPADDR=192.168.0.5</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Dirección IP</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">NETMASK=255.255.255.0</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Máscara de red</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">NETWORK=192.168.0.0</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Dirección de red</td>
  </tr>
  <tr>
    <td style="border:1px solid #4a148c; text-align:center; vertical-align:middle;">GATEWAY=192.168.0.1</td>
    <td style="border:1px solid #4a148c; text-align:left; vertical-align:middle; padding:8px;">Puerta de enlace</td>
  </tr>
</table>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>

# 🛸 4. IPv6

Existe un problema con la cantidad de direcciones públicas de IPv4, las cuales se agotaron hace ya un tiempo y ahora las organizaciones están ajustando para poder añadir mas dispositivos, supone tener que generar un cambio gigante a IPv6 ya que necesitaríamos que todo fuese compatible con IPv6, **se registra que un 30% de Internet ya lo está utilizando pero no está totalmente extendido.**

El problema principal reside en que IPv4 tiene muy pocas direcciones para la cantidad de dispositivos existentes, debido a que al inicio se pensaba que nunca haría falta más, pues para solucionarlo, **si IPv4 usa 32 bits...**

**IPv6 usa 128 bits:** Lo que supone que admite 340 sextillones de direcciones IP's distintas, es una locura.

Para manejar estos números tan grandes, vamos a tener que usar <b>notación Hexadecimal para aprovechar mejor las cifras, haciendo que en esa misma posición pasemos de representar 9 números (0-9) a 15 números (0-15 siendo A=10 y F=15) en un mismo carácter.</b>

**Se agrupan en 8 grupos separados por ":"** pero si hay muchos "0" seguidos se pueden **quitar todos los que están seguidos,** esto solo se puede hacer una vez.
<div style="text-align:center; font-weight:bold; font-size:1.8em;">
    <span style="color:#FF1493;">:0000:0000:</span> 
    <span style="color:#FFB6C1;"> = </span>
    <span style="color:#FF1493;">: :</span>
</div>
Si después de eso, hay otros 8 ceros, **ya no puedo,** sin embargo con esto:
<div style="text-align:center; font-weight:bold; font-size:1.8em;">
    <span style="color:#FF1493;">:</span><span style="color:#880E4F;">000</span><span style="color:#FF1493;">1:</span><span style="color:#880E4F;">000</span><span style="color:#FF1493;">F:</span> 
    <span style="color:#FFB6C1;"> = </span>
    <span style="color:#FF1493;">:1:F:</span>
</div>
Si puedo hacerlo las veces que quiera, **porque los 0 a la izquierda de otro número si podemos quitarlos.**

**IPv6 es autoconfigurable,** es decir, como sabemos que una tarjeta de red tiene una direccion MAC unica, la podemos usar para construir nuestra direccion IPv6, **pudiendo hacer que se autoconfigure ese dispositivo y autoasignandose un IP de red.**

Además, esta totalmente definido cual es la **parte de red, (los 4 primeros números)** y cual es la **parte de host, (el resto)** lo que supone que no necesitamos <b><u>máscaras de red.</b></u>

Y para finalizar, es **mucho más seguro,** Incorpora opciones de seguridad como <u><b>IPsec</b></u> que viene integrado y permite **autenticar y cifrar los paquetes.**