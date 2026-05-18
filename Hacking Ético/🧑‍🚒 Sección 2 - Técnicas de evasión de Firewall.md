
<div style="border: 2px solid #D81B60; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>🚒 Firewall</b></span> <span style="font-size:18px">Es un sistema de seguridad de red que su función es controlar y supervisar el tráfico de red entrante y saliente según unas reglas de seguridad predeterminadas.</span> </div> </div>

Los firewall son los responsables que al usar herramientas como ss o nmap, **obtengamos puertos diferentes** o que nos salga en uno puertos abiertos y en otro los mismos puertos cerrados.

En nmap, cuando nos sale un puerto **FILTERED** significa que no puede determinar si se encuentra abierto o cerrado, y esto se debe al firewall.

Mencionar que para capturar este tráfico, usamos **tcpdump -i enp0s3 -w Captura.cap -v** y esto es lo que abrimos con wireshark para analizar el tráfico, **wireshark Captura.cap &>/dev/null & disown.**

# Fragmentar paquetes

Al fragmentar un mensaje, logramos que igual un firewall esté esperando "x" mensaje específico para bloquearlo, al estar fragmentado **(-f con nmap)** no lo detecta, y podemos lograr ver puertos que antes no nos salían porque el propio firewall nos lo bloqueaba. Con --mtu establecemos el maximum  transmition unit, esta unidad en los firewall puede estar establecida, normalmente son multiplos de 8, si establecemos con **nmap -p- ip --mtu 16 (múltiplo de 8)** un valor inferior a ese numero, podemos burlarlo. Hay más técnicas que se explican en el comando **nmap --help** en la sección FIREWALL/IDS EVASION AND SPOOFING

# Spoofear IP

con -D podemos ponernos -D IP nueva, y **spoofeamos con una IP diferente a la nuestra de nuestro ordenador/máquina.** Podemos liarla parda y hacer -D y poner separados por espacios 20 IPs, entonces recibirá llamadas de muchisimas IP, esto se usa porque a vecesel firewall bloquea determinadas IPs, y podriamos lograr ver mas IPs (podemos automatizar esto con un python, calculando la mascara, sacando todas las IPs posibles del host y realizar un bucle por todas las IPs), aunque con todas estas IPs podemos liar al firewall y hacerle la picha un lio

# Puerto temporal de entrada/salida aleatorio

**Otra cosa importante,** cuando hacemos llamadas a un equipo en escucha, la propia seguridad habilita un puerto aleatorio para recibir ese paquete, enviarlo al puerto, y en caso de recibir respuesta, sacar la respuesta por dicho puerto aleatorio que se abre temporalmente **(si usamos wireshark y filtramos por x puerto, veremos que en el three way shake, en SYNC y ACK o RST, se nos abrirá un puerto random de los 65635 puertos disponibles.** Esto se puede manipular con nmap usando **--source-port 57898 abriendo el puerto 53 de forma temporal, dependiendo de este puerto a veces recibimos mas informacion.

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="wireshark--source-port.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

# Manipulación de longitud del paquete

¿Y que es el número 58 de la izquierda? **la longitud del paquete,** esto tambien se puede filtrar, debido a que existen medidas de que, oye, si la longitud es de 58 en el puerto X, puede ser que nos estén **haciendo un reconocimiento, bloquealo.** podemos manipularlo, pero la base siempre será lo mínimo (en este caso 58) y ya podemos sumarle valores, se hace con **--data-length 21** (58 + 21 = 79)

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="wire2.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

# Spoofear MAC

Podemos **falsificar direcciones MAC** con **--spoof-mac Dell** que esto significa, que usará una dirección de un Dell EMC (puede ser una VMWare o otras cosas, el OUI de lo que hablábamos anteriormente, la parte que identifica de que dispositivo se trata vaya), pero lo mas probable es que nos diga que no está activo el host, y aqui ahora es donde entra el famoso **-Pn** obligando a que se use como si estuviese activo (falsificación total vamos), pero no siempre funciona, tambien podemos escribir tal cual **--spoof-mac 00:11:22:33:44:55** para poner la propia dirección.

# Stealth Scan

Se usa con **sS,** cuando tramitas un SYN, recibes un RST en caso de estar cerrado, y en caso de abierto, se envia un SYN/ACK y posteriormente se envia un ACK y se establece conexión, con este escaneo es **silencioso.**

Se usa para, en caso de estar abierto, después del SYN/ACK enviamos un RST en vez de un ACK, esto hace que el firewall no detecte evidencias de que hemos estado ahí, ya que muchos solo registran conexiones que se **haya establecido completamente.**

# Minimo y maximo de paquetes

com **--min-rate** y **--max-rate** podemo establecer un **mínimo/máximo número de paquetes que se tienen que tramitar por segundo.** Es sugerible usar --min-rate 5000, 5000 es un numero minimo que garantiza si esta abierto o cerrado, no da problemas y aumenta la velocidad

# Uso de scripts

Si abrimos un servidor temportal http con python3 -m http.server 80, podemos usar con --script, scripts como **http-enum,** quien por fuerza bruta, tiene un diccionario de 1000 y pico posibilidades de distintos directorios, y lo usará para intentar sacarnos directorios coincidentes dentro del servidor en el puerto 80.

# Otros comandos

- v: verbose
- n: no aplicar dns
- --open: solo abiertos
- -p-: todos los puertos
- -p22: especificar puerto 22 en este caso
- -sC: Muestra los scripts de nmap útiles para este caso, todos los scripts se muestran en **locate .nse**
- --script="categorie", ejecutas el script con la categoria dada, para saber las categorias disponibes es **locate .nse | xargs grep "categories" | grep -oP ".\*?" | sort -u**
	- sscript="vuln and safe" -sV, decimos que sea de categoria vuln y la safe
- -sV: Muestra version y sistema e información extra