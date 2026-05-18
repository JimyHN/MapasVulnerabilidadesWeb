
# 👾 1. Principales SO

- **🐧 1. Linux** 
	- **Distribuciones específicas para escritorio:** Ubunto, Mint, Deepin, etc
	- **Distribuciones para servidores** para ofrecer servicios: Ubuntu server, Debian, CentOS, Red Hat, etc.
- **🪟 2. Windows**
	- **Distribuciones para escritorio** donde tuvo <u><b>mayor exito:</b></u> Windows 10, Windows 7, etc
	- También tiene **para servidor** como Windows Server, el gran cambio es que las distribuciones para servidor <u><b>nunca se habia podido instalar sin entorno grafico,</u></b> **Windows lo permitió y ahora Linux esta copiándolo**.
- **🍎 3. Mac OS X**
	- Se usa sobre todo para **usuarios finales** ofreciendo una facilidad de uso, sorbe todo para editores, diseñadores, fotógrafos... se centra en que es **para escritorio y workstation.**
- 🐚 **4. UNIX**
	- Esta enfocado **100% para servidores,** no es lo mismo que Linux, tiene distribuciones muy famosas como Solaris, BSD e Irix.

--- 
### Ciclo de vida de una distribución Linux

Depende de la distribución tendrá diferentes plazos en los que esa distribución esta soportada por la organización que se encarga de ella, y cuando pase ese periodo de tiempo, se considera obsoleta
- **Ubuntu:** lanza versión cada 6 meses pero tiene una versión LTS (Long Term Support) que tiene soporte durante 5 años
- **Red Hat Enterprise Linux:** Es de pago, por eso tiene un soporte de 10 años
- **Debian:** Lanza version cada 2 años, siempre tiene **tres versiones** que van <u><b>rotando:</b></u> 
	- **Testing:** en fase de pruebas, la más inestable
	- **Unstable:** Inestable, no pueden garantizar que funcione al 100% pero apunta a ser estable
	- **Stable:** Estable, cuando se garantiza que ya todos los paquetes de esa distribución funcionan correctamente

---

### Diferencia entre una interfaz gráfica vs una línea de comandos (CLI)

La interfaz grafica son aquellos elementos como escritorio, menús, iconos, ratón, que vemos y podemos interactuar, Windows siempre funciona con esto y Linux tiene cositas, esta orientada a usuarios finales y aquellos que no tienen porque ser informáticos.

Sin embargo, en servidores se centra en interpretes de comandos, suele estar mas pensado para administradores de sistemas, programadores o informáticos con conocimientos de que tienen que hacer en el sistema.

En la interfaz grafica te dejas guiar por el entorno grafico mientras que en un interprete de comandos espera a que indiques tu que orden y que cosas tiene que hacer.


<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>

# ✂️ 2. Particiones del disco

Cuando instalamos un sistema Linux, debemos elegir en que parte del disco se va a instalar.

<div style="border: 2px solid #4E9F3D; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>🍕 Partición: </b></span> <span style="font-size:18px">Division del espacio físico disponible. Un disco hardware de 2TB se puede dividir en dos divisiones de 1TB cada una, y en cada parte <b>puedo hacer independientemente lo que quiera,</b> como instalar SO independientes, sistemas de ficheros independientes, etc.</span> </div> </div>

Para Linux como mínimo necesitamos dos particiones: una para el sistema y otra para el área de intercambio **Swap**, la cual actúa como memoria auxiliar cuando la RAM se agota.

Varios directorios se **pueden establecer en particiones distintas** para mejorar el rendimiento o la seguridad

Por ejemplo, podemos tener un disco al que dedicamos 80GB para Windows y el resto para Linux, y ahora viene la cuestión, y es que para Linux no voy a utilizar solo una particion, si no que he decidido que varios directorios importantes utilizarán particiones distintas, por ello, voy a dedicar 50GB al Sistema, 2GB a Swap, 2GB a /boot/, 20GB a /usr/ y 50GB a /home/

De aquí sacamos una tabla con las <b>particiones más importantes</b>

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">

<tr style="background:rgba(47,47,47,0.7); color:#fff; font-weight:bold;"> <td style="border:1px solid #000; height:35px; width:30%; text-align:center; vertical-align:middle;">Directorio</td> <td style="border:1px solid #000; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Descripción e Información Clave</td> </tr>

<tr style="border: 2.5px dotted #00CED1;"> <td style="border: 2.5px dotted #00CED1; text-align:center; vertical-align:middle;"><b>/</b></td> <td style="border: 2.5px dotted #00CED1; text-align:left; vertical-align:middle; padding:8px;">Directorio <b>raíz (root)</b> del que cuelga toda la jerarquía del sistema.</td> </tr>

<tr style="border: 2.5px dotted #FF8C00;"> <td style="border: 2.5px dotted #FF8C00; text-align:center; vertical-align:middle;"><b>/bin/</b></td> <td style="border: 2.5px dotted #FF8C00; text-align:left; vertical-align:middle; padding:8px;">Contiene los <b>binarios ejecutables</b> esenciales para todos los usuarios.</td> </tr>

<tr style="border: 2.5px dotted #32CD32;"> <td style="border: 2.5px dotted #32CD32; text-align:center; vertical-align:middle;"><b>/boot/</b></td> <td style="border: 2.5px dotted #32CD32; text-align:left; vertical-align:middle; padding:8px;">
  Archivos necesarios para el <b>arranque del sistema</b>.
  <ul style="margin-top: 8px; font-size: 0.9em; line-height: 1.4em;">
    <li><b>vmlinuz-(versión):</b> Es el <b>Kernel</b> comprimido; la pieza central y más importante del SO.</li>
    <li><b>initrd.img-(versión):</b> Imagen cargada en RAM al inicio para preparar el arranque de drivers y servicios base.</li>
    <li><b>grub/:</b> Carpeta con los archivos de configuración del gestor de arranque.</li>
  </ul>
</td> </tr>

<tr style="border: 2.5px dotted #FF00FF;"> <td style="border: 2.5px dotted #FF00FF; text-align:center; vertical-align:middle;"><b>/dev/</b></td> <td style="border: 2.5px dotted #FF00FF; text-align:left; vertical-align:middle; padding:8px;">
  Archivos especiales de <b>dispositivos</b> y <b>udev</b>.
  <ul style="margin-top: 8px; font-size: 0.9em; line-height: 1.4em;">
    <li><b>/zero:</b> Fuente infinita de valores nulos (ceros) para relleno o pruebas.</li>
    <li><b>/null:</b> "Pozo sin fondo"; descarta y elimina cualquier dato que se le envíe.</li>
    <li><b>/urandom:</b> Generador de números <b>pseudoaleatorios</b> (algoritmos matemáticos que simulan el azar de forma rápida y eficiente para seguridad).</li>
  </ul>
</td> </tr>

<tr style="border: 2.5px dotted #FFD700;"> <td style="border: 2.5px dotted #FFD700; text-align:center; vertical-align:middle;"><b>/etc/</b></td> <td style="border: 2.5px dotted #FFD700; text-align:left; vertical-align:middle; padding:8px;">
  <b>Configuración global</b> (passwd, group, shadow, hostname, hosts, archivos .conf y directorios .d).
</td> </tr>

<tr style="border: 2.5px dotted #4169E1;"> <td style="border: 2.5px dotted #4169E1; text-align:center; vertical-align:middle;"><b>/home/</b></td> <td style="border: 2.5px dotted #4169E1; text-align:left; vertical-align:middle; padding:8px;">
  Carpetas personales (representado por el símbolo <b>~</b>).
  <ul style="margin-top: 8px; font-size: 0.9em; line-height: 1.4em;">
    <li><b>.bash_history:</b> Registro de todos los comandos ejecutados que se guarda al cerrar la sesión.</li>
    <li><b>.bashrc:</b> Script de personalización que define el entorno (alias, colores, variables) cada vez que abres la terminal.</li>
  </ul>
</td> </tr>

<tr style="border: 2.5px dotted #FF7F50;"> <td style="border: 2.5px dotted #FF7F50; text-align:center; vertical-align:middle;"><b>/lib/</b></td> <td style="border: 2.5px dotted #FF7F50; text-align:left; vertical-align:middle; padding:8px;"><b>Bibliotecas compartidas</b> necesarias para los binarios de /bin/ y /sbin/.</td> </tr>

<tr style="border: 2.5px dotted #9370DB;"> <td style="border: 2.5px dotted #9370DB; text-align:center; vertical-align:middle;"><b>/media/</b></td> <td style="border: 2.5px dotted #9370DB; text-align:left; vertical-align:middle; padding:8px;">Puntos de montaje para <b>medios extraíbles</b>.</td> </tr>

<tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>/mnt/</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Puntos de montaje temporales.</td> </tr> 
<tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>/opt/</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Software adicional.</td> </tr> 

<tr style="border: 2.5px dotted #32CD32;"> <td style="border: 2.5px dotted #32CD32; text-align:center; vertical-align:middle;"><b>/proc/</b></td> <td style="border: 2.5px dotted #32CD32; text-align:left; vertical-align:middle; padding:8px;">Directorio <b>virtual</b> (en memoria RAM, no en disco) con información sobre procesos activos, configuración del Kernel y estado del Hardware.
</td> </tr> 

<tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>/root/</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Home de Root.</td> </tr> 
<tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>/sbin/</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Binarios de sistema.</td> </tr> 
<tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>/srv/</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Servicios.</td> </tr> 

<tr style="border: 2.5px dotted #00BFFF;"> <td style="border: 2.5px dotted #00BFFF; text-align:center; vertical-align:middle;"><b>/sys/</b></td> <td style="border: 2.5px dotted #00BFFF; text-align:left; vertical-align:middle; padding:8px;">Información del Hardware (<b>Sysfs</b>).</td></tr> 

<tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>/tmp/</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Archivos temporales.</td> </tr>

<tr style="border: 2.5px dotted #7FFFD4;"> <td style="border: 2.5px dotted #7FFFD4; text-align:center; vertical-align:middle;"><b>/usr/</b></td> <td style="border: 2.5px dotted #7FFFD4; text-align:left; vertical-align:middle; padding:8px;">Utilidades y aplicaciones multiusuario.</td> </tr>

<tr style="border: 2.5px dotted #FF69B4;"> <td style="border: 2.5px dotted #FF69B4; text-align:center; vertical-align:middle;"><b>/var/</b></td> <td style="border: 2.5px dotted #FF69B4; text-align:left; vertical-align:middle; padding:8px;">Datos variables (logs, bases de datos).</td> </tr>

<tr> 
  <td colspan="2" style="border:1px solid #000; height:40px; text-align:center; vertical-align:middle; padding:8px;">
    <b>los de <span style="color:#00CED1;">c</span><span style="color:#FF8C00;">o</span><span style="color:#32CD32;">l</span><span style="color:#FF00FF;">o</span><span style="color:#FFD700;">r</span><span style="color:#4169E1;">e</span><span style="color:#FF7F50;">s</span> entran en el examen</b>
  </td> 
</tr>

</table>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>


<div style="padding: 25px; border: 3px solid #004D40; border-radius: 15px; color: var(--text-normal); font-family: sans-serif; text-align: left;">

  <div style="text-align: center; margin-bottom: 30px;">
    <h1 style="color: white; font-size: 3em; font-weight: bold; margin: 0; text-shadow: -2px -2px 0 #004D40, 2px -2px 0 #004D40, -2px 2px 0 #004D40, 2px 2px 0 #004D40;">HARDWARE</h1>
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #00796B; font-size: 1.4em;">Caja</strong></div>
    <p style="margin-top: 10px;">Es la <b>armadura</b> del ordenador que protege los componentes y organiza el <b>flujo de aire</b> interno. Incluye las conexiones a la torre que van unidas a la placa base.</p>
    <div style="text-align: center; margin: 20px 0;">
      <img src="orcaja.png" style="max-width: 65%; border: 4px solid #004D40; border-radius: 10px;">
    </div>
    <hr style="border: 0; border-top: 2px solid #006064; width: 100%;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #DAA520; font-size: 1.4em;">Fuente de alimentación</strong></div>
    <p style="margin-top: 10px;">Transforma la <b>corriente de casa</b> para dar <b>energía</b> a la placa base y el resto de componentes.</p>
    <div style="text-align: center; margin: 20px 0;">
      <img src="oralim.png" style="max-width: 65%; border: 4px solid #004D40; border-radius: 10px;">
    </div>
    <hr style="border: 0; border-top: 2px solid #006064; width: 100%;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #CD5C5C; font-size: 1.4em;">Procesador CPU</strong></div>
    <p style="margin-top: 10px;">Es el <b>cerebro</b> del sistema y se encuentra instalado directamente en la placa base.</p>
    <ul style="font-size: 0.9em; line-height: 1.6em;">
      <li><b>Estructura:</b> Actualmente los sockets (agujeros) están arriba y los <b>pines</b> abajo en la placa base.</li>
      <li><b>Rendimiento:</b> Velocidad en <b>GHz</b>. Posee <b>núcleos</b> independientes y tecnología <b>Hyperthreading</b>.</li>
      <li><b>Linux:</b> Comandos <b>lscpu</b>, <b>arch</b> y ficheros en <b>/proc/cpuinfo</b>.</li>
    </ul>
    <div style="text-align: center; margin: 20px 0;">
      <img src="orProces.png" style="max-width: 65%; border: 4px solid #004D40; border-radius: 10px;">
    </div>
    <hr style="border: 0; border-top: 2px solid #006064; width: 100%;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #FF4500; font-size: 1.4em;">Gráfica GPU</strong></div>
    <p style="margin-top: 10px;">Encargada de procesar datos visuales y renderizar imágenes, aligerando la carga de trabajo del procesador central.</p>
    <ul style="font-size: 0.9em; line-height: 1.6em;">
      <li><b>Importancia:</b> Vital para diseño gráfico, edición de vídeo y videojuegos; se conecta al puerto <b>PCI Express</b>.</li>
      <li><b>Ejemplos:</b> Modelos de <b>NVIDIA GeForce</b> (RTX 4060) o <b>AMD Radeon</b> (RX 7800).</li>
    </ul>
    <div style="text-align: center; margin: 20px 0;">
      <img src="orgraf.png" style="max-width: 65%; border: 4px solid #004D40; border-radius: 10px;">
    </div>
    <hr style="border: 0; border-top: 2px solid #006064; width: 100%;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #5c85d6; font-size: 1.4em;">Placa Base</strong></div>
    <p style="margin-top: 10px;">Sirve de <b>conexión</b> entre todos los componentes; su tecnología condiciona la compatibilidad del sistema.</p>
    <ul style="font-size: 0.9em; line-height: 1.6em;">
      <li><b>CPU y RAM:</b> Soporta fabricantes (Intel/AMD) y tipos de memoria (DDR3, DDR4...).</li>
      <li><b>Integración:</b> Alberga ranuras de expansión, puertos <b>SATA</b>, la <b>pila</b> y conexiones frontales.</li>
    </ul>
    <div style="text-align: center; margin: 20px 0;">
      <img src="orplaca.png" style="max-width: 65%; border: 4px solid #004D40; border-radius: 10px;">
    </div>
    <hr style="border: 0; border-top: 2px solid #006064; width: 100%;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #7d8edb; font-size: 1.4em;">Módulos RAM</strong></div>
    <p style="margin-top: 10px;">Memoria rápida instalada en la placa base que indica la capacidad de trabajo del sistema operativo.</p>
    <ul style="font-size: 0.9em; line-height: 1.6em;">
      <li><b>Tecnología:</b> Se mira la velocidad y el tipo (DDR < DDR2 < DDR3).</li>
      <li><b>Linux:</b> El comando <b>free</b> muestra cuánta memoria se está usando.</li>
    </ul>
    <div style="text-align: center; margin: 20px 0;">
      <img src="ormodulosram.png" style="max-width: 65%; border: 4px solid #004D40; border-radius: 10px;">
    </div>
    <hr style="border: 0; border-top: 2px solid #006064; width: 100%;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #b366ff; font-size: 1.4em;">Puertos de expansión</strong></div>
    <p style="margin-top: 10px;">Ranuras integradas en la placa base para añadir tarjetas de funciones adicionales.</p>
    <ul style="font-size: 0.9em; line-height: 1.6em;">
      <li><b>PCI:</b> La muesca pequeña apunta hacia <b>dentro</b> (centro de la placa).</li>
      <li><b>PCI Express:</b> La muesca pequeña apunta hacia <b>fuera</b> (borde de la placa), el de la imagen es un <b>PCIEX16</b> que quiere decir que tiene 16 carriles, <b>puede tener x1, x4, x8 o x16</b>.</li>
      <li><b>AGP:</b> Se quedó <b>obsoleto</b>.</li>
    </ul>
    <div style="text-align: center; margin: 20px 0;">
      <img src="orpci.png" style="max-width: 65%; border: 4px solid #004D40; border-radius: 10px;">
    </div>
    <hr style="border: 0; border-top: 2px solid #006064; width: 100%;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #4682B4; font-size: 1.5em;">Almacenamiento</strong></div>
    <p style="margin-top: 10px;">Sistemas para guardar información. En Linux, las particiones se encuentran en <b>/dev/</b>.</p>
    
    <div style="margin-top: 20px;">
        <div style="text-align: center;"><strong style="color: #708090; font-size: 1.2em;">Discos Magnéticos & SSD</strong></div>
        <ul style="font-size: 0.9em; line-height: 1.6em; margin-bottom: 20px;">
          <li><b>Magnéticos (HDD):</b> Para datos masivos (fotos/vídeos). Usan conexión <b>SATA</b>.</li>
          <li><b>SSD:</b> Chips rápidos. La tendencia es el <b>NVMe (M.2)</b> para acceso instantáneo.</li>
          <li><b>Linux:</b> PATA (<b>hd</b>) y SATA/SSD (<b>sd</b>). Ej: <b>/dev/sdb2</b> (2º disco, 2ª partición).</li>
        </ul>

        <div style="display: flex; justify-content: space-around; align-items: flex-start; gap: 10px; margin: 20px 0;">
          <div style="text-align: center; width: 45%;">
            <span style="display: block; font-weight: bold; color: #708090; margin-bottom: 5px;">Disco Magnético</span>
            <img src="ordisc.png" style="width: 100%; border: 2px solid #004D40; border-radius: 10px;">
          </div>
          <div style="text-align: center; width: 45%;">
            <span style="display: block; font-weight: bold; color: #20B2AA; margin-bottom: 5px;">SSD</span>
            <img src="orssd.png" style="width: 100%; border: 2px solid #004D40; border-radius: 10px;">
          </div>
        </div>
    </div>
    <hr style="border: 0; border-top: 2px solid #006064; width: 100%; margin-top: 20px;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #FF69B4; font-size: 1.4em;">Periféricos</strong></div>
    <p style="margin-top: 10px;">Dispositivos no fundamentales para el funcionamiento interno, pero necesarios para la interacción exterior.</p>
    
    <div style="display: flex; justify-content: space-around; align-items: flex-start; gap: 10px; margin: 25px 0;">
      <div style="text-align: center; width: 31%;">
        <span style="display: block; font-weight: bold; color: #FF69B4; margin-bottom: 5px;">Entrada</span>
        <img src="orraton.png" style="width: 100%; border: 2px solid #004D40; border-radius: 10px;">
        <p style="font-size: 0.8em; margin-top: 5px;">Teclado o ratón.</p>
      </div>
      <div style="text-align: center; width: 31%;">
        <span style="display: block; font-weight: bold; color: #FF69B4; margin-bottom: 5px;">Salida</span>
        <img src="orpantalla.png" style="width: 100%; border: 2px solid #004D40; border-radius: 10px;">
        <p style="font-size: 0.8em; margin-top: 5px;">Monitor o impresora.</p>
      </div>
      <div style="text-align: center; width: 31%;">
        <span style="display: block; font-weight: bold; color: #FF69B4; margin-bottom: 5px;">Mixtos</span>
        <img src="orwifi.png" style="width: 100%; border: 2px solid #004D40; border-radius: 10px;">
        <p style="font-size: 0.8em; margin-top: 5px;">Entrada/Salida (Tarjeta de Red, WiFi).</p>
      </div>
    </div>
  </div>

</div>



<div style="padding: 25px; border: 3px solid #BF360C; border-radius: 15px; color: var(--text-normal); font-family: sans-serif; text-align: left;">

  <div style="text-align: center; margin-bottom: 30px;">
    <h1 style="color: white; font-size: 3em; font-weight: bold; margin: 0; text-shadow: -2px -2px 0 #BF360C, 2px -2px 0 #BF360C, -2px 2px 0 #BF360C, 2px 2px 0 #BF360C;">SOFTWARE</h1>
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #FF8F00; font-size: 1.4em;">D-Bus</strong></div>
    <p style="margin-top: 10px;">Sistema de <b>comunicación entre procesos</b> (IPC) que permite a las aplicaciones hablar entre sí de forma segura.</p>
    <div style="text-align: center; margin: 20px 0;">
      <img src="ordbus.png" style="max-width: 65%; border: 4px solid #BF360C; border-radius: 10px;">
    </div>
    <hr style="border: 0; border-top: 2px solid #BF360C; width: 100%;">
  </div>

  <div style="margin-bottom: 30px;">
    <div style="text-align: center;"><strong style="color: #4FC3F7; font-size: 1.4em;">Driver</strong></div>
    <p style="margin-top: 10px;">Software "traductor" entre el Sistema Operativo y el Hardware <b>para cosas que no se encuentran en el módulo principal del ordenador.</b> Indica como le comunica al SO sobre algo específico que de serie no tiene en cuenta y como usarlo.</p>
    <ul style="font-size: 0.9em; line-height: 1.6em;">
      <li>Dispositivos comunes (monitor, teclado) no suelen necesitar drivers específicos.</li>
      <li>Hardware moderno requiere drivers para que el SO sepa cómo comunicarse.</li>
    </ul>
    <div style="text-align: center; margin: 20px 0;">
      <img src="ordriver.png" style="max-width: 65%; border: 4px solid #BF360C; border-radius: 10px;">
    </div>
  </div>

</div>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>

# 🔁 3. Procesos

En un ordenador tenemos instalados múltiples programas, que significa que hay un código en nuestro disco duro para realizar algo pero aún no se está realizando, por tanto no se están ejecutando instrucciones en el procesador ni ocupando memoria; para que se transforme en un <b><u>proceso</u></b> tenemos que <b><u>ejecutar el programa</u></b>, haciendo que ese programa sea también un proceso a la espera de que le introduzca cosas.

Un mismo programa puede dar <b><u>varios procesos</u></b>, como cuando ejecuto el mismo programa otra vez; sería un mismo programa con <b><u>dos procesos diferentes</u></b>, ambos tendrán un <b><u>identificador de proceso</u></b> distinto, pudiendo hacer una referencia única a uno o a otro.

En consola se usa el comando **ps.** Dentro de este comando, tenemos la primera columna que es el **identificador,** la segunda es la **terminal** donde se ejecuta, la tercera es el **tiempo** que lleva acumulado en el sistema, es decir, el tiempo que lleva consumido en el sistema y la ultima el **comando** que ha iniciado dicho proceso.

Luego existen otros comandos como (prácticar estos comandos):

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;">

<tr style="background:rgba(47,47,47,0.7); color:#fff; font-weight:bold;"> <td style="border:1px solid #000; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td> <td style="border:1px solid #000; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td> </tr>

<tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>Ps</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Muestra información sobre los procesos en ejecución</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>Pstree</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Muestra los procesos en una jerarquía</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>Top</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Aparece información del sistema como la carga que tiene, cuántos procesos hay, quién está consumiendo más memoria</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>Htop</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Es el mismo que Top pero más "amigable" visualmente</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>Free</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Muestra el uso de memoria (integrado en Top)</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>Uptime</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Tiempo encendido y carga del sistema (integrado en Top)</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>Pgrep</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Muestra solo los procesos que cumplen un criterio, como filtrar con Grep</td> </tr> </table>

Si pulsamos con clic derecho podemos:
- <b><u>Detener</u></b>: se queda en <b>pausa</b> pero se <b>mantiene en memoria</b>.
- <b><u>Reanudar</u></b>: volver a reanudar después de detener.
- <b><u>Terminar</u></b>: envía una <b>señal al proceso</b> para que finalice, aunque puede quedarse en un bucle infinito o sin responder al cierre.
- <b><u>Matar</u></b>: <b>forzamos</b> que finalice sí o sí el proceso.
- <b><u>Prioridad</u></b>: se ejecuta con prioridad.

Aquí tienes la estructura actualizada. He mantenido el estilo y el color rojo rosado, integrando la información sobre cómo el sistema te notifica cuando lanzas un proceso al fondo:

<div style="border: 2px solid #D81B60; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>👺 Demonio / Segundo Plano:</b></span> <span style="font-size:18px">Es un proceso que corre sin bloquear la terminal. Al ejecutar un comando con <b>&</b>, la consola devuelve una línea como <code>[1] 4528</code>, donde el primer número indica la cantidad de trabajos en segundo plano y el segundo es el <b>PID (identificador único)</b>. Esto permite que el <b>demonio</b> trabaje de forma invisible mientras tú mantienes el control de la shell para seguir operando independientemente.</span> </div> </div>

## Procesos de Arranque en Linux

### 3.1 El Gestor de Arranque (GRUB)

El primer paso crítico en el encendido es el **GRUB** (_GNU GRand Unified Bootloader_). Es el encargado de cargar el sistema operativo en la memoria.

Para verificar qué archivo de imagen inicial está cargando tu máquina específicamente desde la configuración de GRUB, puedes ejecutar:

**<b>grep initrd /boot/grub/grub.cfg</b>**

---

### 3.2 Initramfs (Sistema de Archivos Inicial en RAM)

Antes de que el sistema operativo real tome el control, el Kernel necesita un entorno temporal.

Es un archivo comprimido (normalmente en **gzip**) que contiene un sistema de archivos básico.

Se carga en la memoria RAM para completar tareas de módulos y controladores antes de montar el sistema de archivos raíz (`/`) del disco duro e invocar al proceso `init`.

- **Configuración**: En el fichero de configuración de GRUB, verás una línea similar a:

	 **<b>initrd /boot/initrd.img-4.9.0-7-amd64</b>**


---

### 3.3 Revisión de Mensajes de Carga

Durante el arranque se cargan controladores y funciones. Podemos auditar estos mensajes con dos herramientas principales.

#### Herramienta: journalctl

Es la herramienta más potente para consultar el registro del sistema.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;"> <tr style="background:rgba(47,47,47,0.7); color:#fff; font-weight:bold;"> <td style="border:1px solid #000; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td> <td style="border:1px solid #000; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;">-b</td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Muestra los mensajes correspondientes al último arranque (boot).</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;">-k</td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Muestra exclusivamente los mensajes del Kernel (dmesg style).</td> </tr> </table>

#### Herramienta: dmesg

La herramienta clásica para mensajes del buffer del Kernel. Como la salida es formato texto, podemos filtrar con **<b>grep</b>**.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;"> <tr style="background:rgba(47,47,47,0.7); color:#fff; font-weight:bold;"> <td style="border:1px solid #000; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td> <td style="border:1px solid #000; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>-T</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Muestra las marcas de tiempo más claramente.</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>-k</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Solo mensajes del Kernel.</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>-l</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Filtra por niveles de aviso (warn, err, etc...).</td> </tr> </table>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>

# 📖 4. Registros del Sistema -LOGS

Muchos programas o servicios escriben mensajes en el sistema, estos ficheros de registro se suelen guardar en **/var/log.** 

Es fundamental saber donde se escriben y como consultarlos, podemos usar:

- **rsyslog:** Mejora de **syslog,** gestor tradicional que **gestiona diversos ficheros en texto plano.** 
	- Tiene su **fichero de configuración** en **/etc/rsyslog.conf** o en ficheros dentro de **/etc/rsyslog.d/.**
	- Lo que se guarda fundamentalmente son lineas que indican donde se va a guardar los tipos de mensaje, para indicar los tipos de mensaje tenemos dos partes <b><span style="color:#FF69B4;">facility</span><span style="color:#FFFFFF;">.</span><span style="color:#90EE90;">priority</span></b>

	<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;"> <tr style="background:rgba(47,47,47,0.7); color:#fff;"> <td colspan="3" style="border:1px solid #000; height:35px; text-align:left; vertical-align:middle; padding-left:8px;"> <b><span style="color:#FF69B4;">facility:</span></b> <b>Origen de los mensajes</b>, si es un mensaje de autorización / identificación / tarea cron... </td> </tr>

<tr> <td style="border:1px solid #000; width:33%; text-align:center; padding:8px;">auth</td> <td style="border:1px solid #000; width:33%; text-align:center; padding:8px;">authpriv</td> <td style="border:1px solid #000; width:33%; text-align:center; padding:8px;">cron</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;">daemon</td> <td style="border:1px solid #000; text-align:center; padding:8px;">ftp</td> <td style="border:1px solid #000; text-align:center; padding:8px;">kern</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;">lpr</td> <td style="border:1px solid #000; text-align:center; padding:8px;">mail</td> <td style="border:1px solid #000; text-align:center; padding:8px;">mark</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;">news</td> <td style="border:1px solid #000; text-align:center; padding:8px;">security</td> <td style="border:1px solid #000; text-align:center; padding:8px;">syslog</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;">user</td> <td style="border:1px solid #000; text-align:center; padding:8px;">uucp</td> <td style="border:1px solid #000; text-align:center; padding:8px;">local0 to local7</td> </tr> </table>

	<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;"> <tr style="background:rgba(47,47,47,0.7); color:#fff;"> <td colspan="3" style="border:1px solid #000; height:35px; text-align:left; vertical-align:middle; padding-left:8px;"> <b><span style="color:#90EE90;">priority:</span></b> Se ajustan según lo <b>crítico o importante</b> que sean esos mensajes </td> </tr>

<tr> <td style="border:1px solid #000; width:33%; text-align:center; padding:8px;">debug</td> <td style="border:1px solid #000; width:33%; text-align:center; padding:8px;">info</td> <td style="border:1px solid #000; width:33%; text-align:center; padding:8px;">notice</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;">warning (or warn)</td> <td style="border:1px solid #000; text-align:center; padding:8px;">err (or error)</td> <td style="border:1px solid #000; text-align:center; padding:8px;">crit</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;">alert</td> <td style="border:1px solid #000; text-align:center; padding:8px;">emerg (or panic)</td> <td style="border:1px solid #000; text-align:center; padding:8px;">-</td> </tr> </table>

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;"> <tr style="background:rgba(47,47,47,0.7); color:#fff; font-weight:bold;"> <td style="border:1px solid #000; height:35px; width:40%; text-align:center; vertical-align:middle;"><b>Ejemplo</b></td> <td style="border:1px solid #000; height:35px; width:60%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Descripción</b></td> </tr>

<tr> <td style="border:1px solid #000; text-align:center; padding:8px;"><b><span style="color:#FF69B4;">_</span>.<span style="color:#90EE90;">_</span></b></td> <td style="border:1px solid #000; text-align:left; padding:8px;">Todos los mensajes</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;"><b><span style="color:#FF69B4;">_</span>.<span style="color:#90EE90;">info</span></b></td> <td style="border:1px solid #000; text-align:left; padding:8px;">Todos los mensajes de info</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;"><b><span style="color:#FF69B4;">kern</span>.<span style="color:#90EE90;">_</span></b></td> <td style="border:1px solid #000; text-align:left; padding:8px;">Todos los mensajes del kernel</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;"><b><span style="color:#FF69B4;">mail</span>.<span style="color:#90EE90;">err</span></b></td> <td style="border:1px solid #000; text-align:left; padding:8px;">Los mensajes de error del correo</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;"><b><span style="color:#FF69B4;">cron,lpr</span>.<span style="color:#90EE90;">warn</span></b></td> <td style="border:1px solid #000; text-align:left; padding:8px;">Los warning de cron y de lpr</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;"><b><span style="color:#FF69B4;">cron</span>.<span style="color:#90EE90;">err</span>;<span style="color:#FF69B4;">cron</span>.!<span style="color:#90EE90;">alert</span></b></td> <td style="border:1px solid #000; text-align:left; padding:8px;">Los errores de cron pero NO las alertas</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;"><b><span style="color:#FF69B4;">mail</span>.=<span style="color:#90EE90;">err</span></b></td> <td style="border:1px solid #000; text-align:left; padding:8px;">Solo los errores de mail</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; padding:8px;"><b><span style="color:#FF69B4;">*</span>.<span style="color:#90EE90;">info</span>;<span style="color:#FF69B4;">mail</span>.<span style="color:#90EE90;">none</span>;<span style="color:#FF69B4;">lpr</span>.<span style="color:#90EE90;">none</span></b></td> <td style="border:1px solid #000; text-align:left; padding:8px;">Todos los mensajes de info excepto los de mail y lpr</td> </tr> </table>

- **Systemd-journalctl:** **Mantiene un registro más sofisticado y seguro,** pero menos abierto a otros programas. **Lo guarda en binarios** para que sean más complicados de eliminar, ya que si se nos cuela alguien escalando privilegios, en texto plano puede borrar su huella fácilmente.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden;"> <tr style="background:rgba(47,47,47,0.7); color:#fff; font-weight:bold;"> <td style="border:1px solid #000; height:35px; width:30%; text-align:center; vertical-align:middle;"><b>Opción</b></td> <td style="border:1px solid #000; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;"><b>Función</b></td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>-S, -U</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Permite especificar desde (<b>since</b>) y/o hasta cuándo (<b>until</b>). Acepta <b>YYYY-MM-DD [HH:MM:SS]</b>, yesterday, today, o rangos como -1h 15min.</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>-u [unit]</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Mensaje de una unidad (servicio) en concreto.</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>-k</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Mensajes del kernel.</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>-p</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Por tipo (emerg, alert, crit, err, warning, notice, info, debug).</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>PARAM=VALUE</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Filtra por parámetros internos del sistema. Abajo tres ejemplos:</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>_PID=VALUE</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Identificador del proceso que generó el log.</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>_UID=VALUE</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Identificador del usuario que ejecutó el proceso.</td> </tr> <tr> <td style="border:1px solid #000; text-align:center; vertical-align:middle;"><b>_COMM=VALUE</b></td> <td style="border:1px solid #000; text-align:left; vertical-align:middle; padding:8px;">Nombre del comando o ejecutable (ej: sshd).</td> </tr> </table>

Anteriormente se usaban programas más antiguos con un funcionamiento parecido a **rsyslog** que eran **syslog** y **syslog-ng.**