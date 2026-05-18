
# 🚀 1. La evolución de Linux

En 1994 Linus Torvalds lanza el núcleo de un sistema operativo muy similar a UNIX (creado para grandes computadoras) pero compatible con PC

**Ver documental:** [Documental Codigo Linux (youtube.com)](https://www.youtube.com/watch?v=cwptTf-64Uo)

En 1992 adopta la **Licencia Pública General (GPL)** permitiendo el uso, modificación, redistribución y copia, se empieza a crear una comunidad

**Uniendo Linux (el núcleo o Kernel) con otros programas libres que siguen la filosofía GNU, aparecen SO completos, como por ejemplo:**

- 1993: Slackware y Debian (apoyado por comunidad)
- 1994: Red Hat (tiene una empresa por detras)
- 2002: Arch
- 2004: Ubuntu (de Debian)

En wikipedia se ven las distribuciones que han surgido de las madres, que son **Debian, Slackware y RedHat.** Luego existen distribuciones menores (no han salido de aqui tantas distribuciones como los otros 3, pero tampoco son hijos de los 3 padres anteriores) como **Arch o Android,** luego además existen otras que murieron.

Por tanto definción de:

<div style="border: 2px solid #5dade2; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>📝 Distribución:</b></span> <span style="font-size:18px">Es un SO con kernel de Linux y una selección de aplicaciones creada y mantenidas por una empresa o comunidad de usuarios.</span> </div> <div style="font-size:18px; margin-bottom: 15px;">Hay dos grandes familias:</div> <div style="display: flex; gap: 20px; justify-content: space-between;"> <div style="flex: 1; padding: 5px;"> <b style="color: #bb8fce;">Derivadas de Debian:</b><br> <span style="font-size:14px;">Gestionan el software con ficheros .deb y comandos dpkg, apt, ...</span><br> <i>Ubuntu, Kali, Mint, MX Linx, Parrot, etc.</i> </div> <div style="flex: 1; padding: 5px;"> <b style="color: #f48fb1;">Derivadas de Red Hat:</b><br> <span style="font-size:14px;">Gestionan el software con ficheros .rpm y comandos rpm, yum, dnf, ...</span><br> <i>Fedora, CentOS, Scientific Linux, etc.</i> </div> </div> <div style="margin-top: 15px; font-size:16px; border-top: 1px solid #5dade2; padding-top: 10px;"> <b>Otras dignas de mención son:</b> Arch, Manjaro, Suse... </div> </div>


**Debian GNU/Linux:** Fue lanzada por Ian Murdock, Es muy estable y utilizada en servidores. Por defecto no proporcionan ningún software propietario, es decir, que el software y sus repositorios que usa no sea propietario de una empresa siendo fieles a la filosofía GNU.

**Ubuntu:** Creado por Mark Shuttleworth y su empresa Canonical, Su objetivo esta hacer hacer una distribución mas fácil e intenta actualizar mucho cada pocos meses, cada dos años sacan una versión que ellos mismos consideran muy estable y a la que darán soporte, eso se conoce como LTS.

**Red Hat:** Desarrollada y emitida por la empresa Red Hat, en 2019 IBM compró Red Hat, ofrece soporte y licencias de pago y ahora se llama Red Hat Enterprise Linux (RHEL).

**Suse:** Distribución equivalente a Red Hat pero europea, Alemania, tiene una herramienta llamada Just, que permitía poner los Linux en cualquier lado independientemente del hardware, tiene una versión comercial y otra gratuita.

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
## 🌊 Versatilidad de Linux

Linux tiene un sistema modular, puedo quitar y poner partes para adaptarlo, si adapto ese kernel estamos hablando de **sistemas embebidos,** permitiendo que pueda funcionar en ordenadores, moviles, relojes, etc. Permite una **modularidad.**

Un ejemplo es **Android,** debido a que Google quería meterse en dispositivos móviles, para ello cogió su kernel Linux y lo adapto para poder usarse en móviles.

Otro ejemplo es la **Raspbian,** la cual es una RaspberryPi de Debian. La RaspberryPi es una placa muy económica con una modificación para funcionar en mini ordenadores, muy útil para robótica, para conectar a auriculares, centro multimedia, es un hardware para acceder a un mini ordenador.

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="Raspbian.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

Otro área donde Linux ha tenido mucha influencia es en el **cloud computing.** Empresas como AWS, Azure, GCP, etc. Ofrecen distribuciones Linux que se pueden utilizar a la carta. Gracias a las licencias y a la modularidad de Linux.

La mejora de hardware permite que los ordenadores no tengan un unico SO, si no muchos, y **virtualizando** creamos un entorno completo como si fuera un hardware completo real, permitiendo que tengamos varios SO en una misma maquina.

Luego surgieron los **contenedores,** que son como maquinas virtuales pero que comparten cosas entre los diferentes SO, pueden compartir kernel, son muchos mas ligeros que las VM y sencillos

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
# 🤝 2. Principales Aplicaciones de código abierto o software libre

**Al usar un software libre, podemos usar el mismo software en diferentes SO, esta disponible para aplicar y compilar en cualquier plataforma**

El software en Linux se distribuye de dos maneras:
- **1. Mediante código fuente:** Instalando software a partir del código fuente, adaptando el código a mi máquina.
	- **Ventajas:** Se puede compilar optimizando el rendimiento para un sistema concreto, modificable y personalizable
	- **Desventajas:** Necesita los programas necesarios para interpretar el código y las librerías requeridas. Instalación mas lenta y complicada.
- **2. Archivos instalables llamados paquetes:** Contienen múltiples ficheros compactos y cuando lo instalas sabe donde tiene que ir cada fichero dentro de los diferentes directorios del SO.
	- **Ventajas:** Más fácil de instalar y administrar
	- **Desventajas:** Tiene que haber un paquete especifico para cada plataforma, pensado para una arquitectura concreta, porque no son compatibles entre si, no funciona uno x86 en arm, o un mips en x64...

Para facilitar mas su utilización, se habilitaron servidores que funcionan 24/7 donde contienen los paquetes para que en cualquier momento una persona pueda habilitarlos en su ordenador, esto son los conocidos **repositorios.** 

Tenemos los **Paquetes .deb:**
- Se usan en **Debian.**
- Administran los paquetes con el comando **dpkg.**
- Utilizan los **repositorios** con **apt *(o apt-get, apt-cache...)***
y los **Paquetes .rpm:**
- Se usan en **Red Hat** y sus derivadas.
- Administran los paquetes con el comando **rpm.**
- Utilizan repositorios con **yum *(dnf o zypper)***

<table style="width: 100%; border-collapse: collapse; text-align: center; border: none; font-family: sans-serif;"> <thead> <tr style="background-color: rgba(26, 26, 26, 0.7); color: #2e86c1; border-bottom: 4px solid rgba(128, 128, 128, 0.3);"> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">Acciones</th> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">.DEB</th> <th style="padding: 12px; border: none;text-align:center; vertical-align:middle;">.RPM</th> </tr> </thead> <tbody style="color: inherit;"> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Actualizar la lista de paquetes</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">apt update</td> <td style="padding: 10px; border: none; color: gray; font-style: italic;text-align:center; vertical-align:middle;">(no es necesario)</td> </tr> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Buscar un paquete</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">apt search "paquete"</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">yum search "paquete"</td> </tr> <tr style="border-bottom: 1px solid rgba(128, 128, 128, 0.3);"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Instalar</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">apt install "paquete"</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">yum install "paquete"</td> </tr> <tr style="border: none;"> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">Borrar</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">apt remove "paquete"</td> <td style="padding: 10px; border: none;text-align:center; vertical-align:middle;">yum remove "paquete"</td> </tr> </tbody> </table>


## 📄 Aplicaciones ofimáticas

Al principio existía OpenOffice.org pero fue comprada por Oracle, se abandono OpenOffice y surgió Libreoffice, es mejor que el de Microsoft ya que es libre y no te obligan a estar continuamente adaptándote vendiéndote versiones nuevas, dentro de LibreOffice tiene:
- **Writer:** Es el procesador de texto
- **Calc:** Es la hoja de calculo
- **Impress:** Creación de presentaciones
- **Draw:** Dibujado vectorial
- **Math:** Editor de formulas matemáticas
- **Base:** Para bases de datos

## 📽️ Aplicaciones multimedia

Hay distribuciones, como **Ubuntu Studio,** usada específicamente para servicios multimedia, tenemos:
- **GIMP:** Editor de imágenes de mapa de bits, como Photoshop
- **Inkscape:** Imágenes vectoriales, como Adobe
- **Audacity:** Editor de audio con formatos .wav, .mp3, .ogg, etc
- **Blender:** Modelar o crear animaciones 3D.
- **VLC:** Reproductor de musica
- **ImageMagick:** Entorno de comando, acciones sobre imágenes o ficheros para redimensionar o modificar sobre muchas imágenes, como 10.000 imágenes por un comando hago una transformación a todas de golpe

## 🌐 Internet

El programa mas utilizado en internet es el navegador, los dos más famosos en Linux son Chrome y Firefox.

También encontramos otros como:
- **Thunderbird:** Cliente de correo electrónico
- **Filezilla:** Cliente, aunque también esta en servidor, sirve para transferir ficheros, descargar o subir FTP
- **Transmission:** Para descargar ficheros Torrent

## 🖥️ Servidores

- **Navegación web:** Linux siempre tuvo mucho mas éxito en servidores que en usuarios domésticos, sobre todo usando navegación web, cuando accedemos a la web, es porque un programa escucha nuestra petición y nos devuelve nuestro código HTML que nuestro ordenador interpreta y muestra su pagina web. Ese ordenador estará ejecutando un servidor web, que recoge la petición, accede a las bases de datos y disco duro, produce un resultado y lo lanza para que el navegador lo interprete, los servidores mas famosos son **Apache, Nginx o Lighttpd**

- **Lenguajes Back-End:** Al inicio las paginas eran estáticas, donde no podías cambiar nada de la pagina, luego se paso a poder interactuar con la pagina para ofrecer información personalizada, distinta, actualizada... para que se pueda tiene que tener un lenguaje de programación en el servidor diferente a HTML porque este no puede, estos lenguajes se conocen como lenguajes de back-end como **PHP, JavaScript, Python, ASP o Java.**

- **Bases de datos:** Todas las web modernas es indispensable poder acceder a bases de datos como **MySQL, MariaDB *(derivado de MySQL)* o PostgreSQL**

- **Información privada en la nube:** Se puede crear una "nube privada" con información de todo, ese tipo de software en Linux nos lo ofrece **ownCloud o Nextcloud** 

## ⌨️ Lenguajes de programación

Maneras de escribir código fuente para que se ejecute en un ordenador, son instrucciones que realizan operaciones matematico-lógicas.

- **JavaScript:** **Enorme uso de internet,** JavaScript se centra en la web, es un lenguaje que inicialmente solo se ejecutaba en el navegador pero evoluciono para poder ejecutarlo en la parte del cliente como en la parte de servidor (Back-End).
- **C/C++:** Centrado en la **creación de programas muy eficientes** a la hora de gestionar recursos y acceder al hardware
- **Java:** **Versatilidad,** programando Java puedo ejecutar ese mismo programa/paquete en una barbaridad de entornos diferentes, ese fichero es compatible gracias a su **máquina virtual JVM**, con esto puedo hacer programas para ordenador, oficina, móviles, servidores...
- **Python:** **Sintaxis muy sencilla,** es un lenguaje muy común en **Big Data, IA, DeepLearning, etc...** 
- **PHP:** Muchísimos programas/webs/blogs como **Wordpress, Prestashop o Moodle** están escritos en PHP.

Un concepto muy importante y comun es **LAMP**, cuando alguien dice que esta aplicacion o entorno es **LAMP** quiere decir que se ejecuta en **L**inux, con servidor web **A**pache, con base de datos **M**ySql (o **M**ariaDB) y con lenguaje **P**HP.

**Es por ello que cuando quiero ejecutar un programa/aplicacion/web como Worpress o lo que sea, todos necesitan de un SO donde ejecutarse, un Servidor WEB, con una BDD y un Lenguaje de programación.**

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
# 🧑‍⚖️ 3. Licencias y Código abierto

Existen 4 libertades para que un software sea libre:
- **Libertad 0:** Ejecutarlo **cuando/como/donde** quiera.
- **Libertad 1:** Estudiar como funciona y poder modificarlo para adaptarse a necesidades, se tiene que poder **acceder al código fuente.**
- **Libertad 2:** Poder **redistribuir copias** a <u>donde/quien quiera.</u>
- **Libertad 3:** **Distribuir copias** de <u>versiones modificadas.</u>

<b>OPEN SOURCE (CÓDIGO ABIERTO) <u>NO</u> ES LO MISMO QUE SOFTWARE LIBRE</b>

Open Source <u>solo</u> tiene que cumplir que podamos acceder al código fuente del mismo, podemos ver el código pero no tienen porque cumplirse las otras 3 libertades.

Para ello se crearon sus propias licencias para regular como modificar y distribuir un código open Source

Hay dos abreviaturas esenciales para entender esto:
- **FOSS:** **F**ree and **O**pen **S**ource **S**oftware
- **FLOSS:** **F**ree/**L**ibre and **O**pen **S**ource **S**oftware
	- ¿Cómo se gana dinero con FLOSS?
		- Instalación, soporte y personalización del software
		- Trabajar en empresas de este software, te pagan tu sueldo
		- Donaciones o Crowdfunding (colaboracion de grupo de personas para financiar un proyecto)
		- Dual Licensing (doble licencia, te ofrezco una versión gratis y otra de pago mas completa)
		- Cloud Computing, SaaS, etc.

<div style="border: 2px solid #5dade2; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>©️ Copyleft: </b></span> <span style="font-size:18px">Impulsado por la <b>FSF</b> <i>(<b>F</b>ree <b>S</b>oftware <b>F</b>oundation),</i> el autor exige que los beneficiarios del producto preserven las mismas libertades de distribución de copias y derivados.</span> </div> </div>

Dentro de las licencias tenemos:

- **GNU General Public License (GPL):** Creada por la **FSF.** Ofrece libertad de usar, estudiar, compartir y modificar el software. Es **copyleft,** por lo que sus obras derivadas también tendrán que ser GPL, es decir, si cojo un producto GPL también tendrá que ser un producto GPL.

- **FreeBSD License:** Está dentro de las licencias **"permisivas"** ya que no incluye el **copyleft.** Por lo tanto se puede hacer cualquier cosa con el código, como venderlo o comprarlo, pero **sí incluyen una cláusula de exención de responsabilidad y exigen que se mantenga,** es decir, que no se hacen responsables de daños que se pueda ocasionar, como dato a parte, MacOS esta basado en **BSD.**

- **Creative Commons (CC):** Se aplican más al autor que al software, y se pueden aplicar a todo material con derechos de autor, tiene varias variantes:
	- **Attribution (CC BY):** Autoriza cualquier uso pero debes **mencionar al autor,** atribuir cual es la autoría de esa obra.
	- **Attribution ShareAlike (CC BY-SA):** A parte de decir el autor, si haces una obra derivada, tambien permitas que otros la utilicen. **Compartir la licencia.**
	- **Attribution No-Derivs (CC BY-ND):** Puedes redistribuir el contenido, **pero a parte de citar al autor,** **el producto no lo puedes cambiar ni modificar.** Manteniendo la autoridad de la obra.
	- **Attribution-NonCommercial (CC BY-NC):** Igual que CC BY, pero **no se puede utilizar para ganar dinero,** se puede para fines personales u otras cosas, pero **nada de venderlo ni de campañas publicitarias.**
	- **Attribution-NonComercial-ShareAlike (CC-BY-NC-SA):** Aquí mezclamos lo que hemos comentado en las anteriores, por la que aquí mantenemos al autor, donde permitamos que otros usuarios puedan compartir la obra y sin fines comerciales. **No se use para fines comerciales y se comparta la licencia.**
	- **Attribution-NonCommercial-No-Derivs (CC-BY-NC-ND):** **Puedes distribuir sin poder modificarla ni con fines comerciales.**
	- **No Rights Reservados (CC0):** Versión de CC de **dominio público.** No obliga a mencionar el autor

	<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="Licencias.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
# 🏗️ 4. Estructura

<div style="border-radius:10px; padding:12px; box-sizing:border-box;">
  <div style="display:flex; align-items:flex-start; justify-content:flex-start; gap:20px;">
    <div style="flex:1;">
      <p style="margin:0 0 6px 0;">
        Partimos de un <b>Hardware</b>
    </p>
    <p style="margin:0 0 6px 0;">
        Después avanzaríamos al <b>Kernel,</b> que es el <b>intermediario principal</b> entre el hardware y los programas. Ejemplo: Linux, HURD
    </p>
    <p style="margin:0 0 6px 0;">
	    Pasamos al <b>Shell</b> que es un entorno de <b>comandos,</b> el cual recoge la orden que escribimos y emite un resultado. Ejemplos: Bash, CSH, SH, KSH
    </p>
    <p style="margin:0 0 6px 0;">
        Ahora entraría el <b>Interfaz gráfico</b> para un uso mas sencillo y visual, gracias a esto nos aparecen ventanas, iconos, etc. Dentro de este <b>entorno gráfico</b> entran <b>Sistema de Ventanas, Gestor de Ventanas y Escritorio.</b> En estos entornos destacan Gnome o KDE y escritorios ligeros como XFCE o LXDE
    </p>
    </div>
    <div style="flex:0 0 auto;">
      <img src="EstructuraLinux.png" style="width:350px; border-radius:8px;">
    </div>
  </div>
</div>

**Gnome:** Es el escritorio usado por defecto , utiliza librerías gráficas llamas GTK y están escritas en el lenguaje C.

**KDE:** Es el preferido por usuarios más avanzados, lo que es mas complejo, usa librerías Qt y esta escrito en C++.

Normalmente, suelen ser compatibles los programas escritos en Qt o GTK en diferentes entornos (Gnome o KDE).

# 🖲️ Interprete de comandos

Tenemos diferentes tipos, como Shell, consola, terminal, CLI, etc. Permite la **multitarea,** es decir, mediante CONTROL+ALT+F(1...9) nos permite **abrir diferentes terminales.**

Cuando ocurre un error al iniciar el ordenador, de permisos, tarjeta, etc. Impidiendo iniciar el entorno gráfico, <u>la única manera de rescatarlo es mediante consola.</u>

Aquí tienes el código de Obsidian ajustado con los nuevos cambios de color. He unificado los operadores en rosa y el texto descriptivo en blanco para que contraste mejor con el fondo oscuro.

<div style="border: 2px solid #1B5E20; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif; background-color: #1e1e1e;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"> <b style="color: #90EE90;">alumno@mipc</b> <span style="color: #ffffff;">:</span> <span style="color: #5dade2;">~</span> <span style="color: #ffffff;">$</span> <span style="color: #a9a9a9;">||</span> </span> <span style="font-size:18px; margin-left: 10px;"> <span style="color: #90EE90;">nombreUsuario@nombreSO</span> <span style="color: #ff69b4;">+</span> <span style="color: #ffa500;">"</span><span style="color: #ffffff;">:</span><span style="color: #ffa500;">"</span> <span style="color: #ff69b4;">+</span> <span style="color: #ffa500;">"</span><span style="color: #5dade2;">~</span><span style="color: #ffa500;">"</span> <span style="color: #ff69b4;">=</span> <span style="color: #ffffff;">trabajando en mi directorio personal</span> <span style="color: #ff69b4;">+</span> <span style="color: #ffa500;">"</span><span style="color: #ffffff;">$</span><span style="color: #ffa500;">"</span> <span style="color: #ff69b4;">=</span> <span style="color: #ffffff;">usuario sin privilegios</span> </span> </div> </div>

Linux tiene un protagonismo destacado en servidores, <b><u>se estima que más del 70% de los servidores web usan Linux.</u></b>

Existen maneras de dinamizar los servidores a partir de diferentes conceptos:
- **IaaS (Infraestructure as a Service):** Puedo tener un servidor de AWS, Azure, GCP, y en esa misma tarde voy a tener un servidor para mi, sin tener que hacer nada yo de instalaciones ni nada. **Contratamos de forma dinámica.** Podemos usar **OpenStack** para gestionar diferentes servidores como uno solo.
- **PaaS (Platform as a Service):** Una muy habitual para lanzar aplicaciones son las mencionadas anteriormente las **LAMP.** Con PaaS **podemos contratar una plataforma para que funcione nuestra aplicación.** Por ejemplo alquilar un entorno Python o Java para nuestra aplicación de Python o Java.
- **SaaS (Software as a Service):** Utilizar un software sin tenerlo instalado en el ordenador, **lo usamos bajo demanda,** por ejemplo Gmail o Dropbox, donde tenemos una interfaz web como la de Gmail, pero todo las ordenes se producen en los servidores de Google.

***Mencionar de la Seccion 3:***

<div style="border: 2px solid #5dade2; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>🔐 Globbing: </b></span> <span style="font-size:18px"> Hacer referencia a <b>varios elementos utilizando comodines</b> <i>(Lo que se usa cuando haces un ls es?rit*)</i> y se puede hacer mediante <b>Asteriscos</b> <i>(Lo que sea),</i> <b>Interrogación</b> <i>(Algo obligatorio),</i> <b>Corchetes</b> <i>(Cualquier carácter dentro de los corchetes)</i>; dentro de estos últimos, puede ser por <b>Rangos:</b> <i>Indicando el inicio y final separados por un guion,</i> <b>Negación:</b> <i>Poniendo ^ al inicio de los caracteres <b>NO</b> validos</i> y finalmente las <b>Clases:</b> <i>Grupos de caracteres predefinidos.</i> </span> </div> </div>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
# 🧹 Linux en entorno doméstico y de oficina

A las empresas les interesa hacer un seguimiento de que hacemos, si buscamos coches, nos saldrán anuncios de coches en nuestro **navegador.** Para hacer eso, ponen ficheros muy pequeños con identificadores en forma de texto llamados **cookies,** así cuando accedemos a una web, esta accede a las cookies y saben que mostrarnos. Grandes empresas como Facebook, Google, etc. pueden aumentar esto, **monitorizando todas nuestras acciones en Internet.** 

También es muy común que abra una sesión de Google y ya se me identifique en todos lados.

Todos los navegadores tienen la **pestaña anónima,** la cual no es anónima, siempre dejas un rastro, pero es un poco mas privado en comparación con una normal, guardando menos cantidad de cookies.

Dentro del tema de **contraseñas,** mencionar que por muy buena que sea tu contraseña, siempre puede surgir una brecha en una compañía como Twitter, y te pillen todo, lo suyo es tener un **gestor de contraseñas** que se encarga de generarme diferentes contraseñas para abrir las cosas, y únicamente necesitamos sabernos una única contraseña para abrir el gestor de contraseñas.

<div style="border: 2px solid #5dade2; padding: 15px; border-radius: 12px; display: block; font-family: sans-serif;"> <div style="margin-bottom: 15px;"> <span style="font-size:20px"><b>🔐 Cifrado: </b></span> <span style="font-size:18px"><b>Modificar los datos originales</b> para que, si alguien no autorizado los intercepta, <b><u>sea incapaz de saber que datos son.</b></u> Sin embargo, el usuario legítimo usa un <b>mecanismo para poder descifrarlos.</b> </span> </div> </div>

Esto se realiza con información sensible, como al registrarnos en un formulario, la contraseña tiene que viajar de forma cifrada para que sea imperceptible, para ello se usan mecanismos de **cifrado y descifrado de datos.**
- **TLS (Sucesor de SSL):** **Cifra prácticamente todas las comunicaciones con un servidor,** dejando de seguir un protocolo HTTP y pasando a HTTP**S,** esa **S** es de **Segura.**
- **GnuPG:** Sirve para **cifrar ficheros o datos,** como un documento de office, que nos llevamos en el pendrive o disco. Cifra de una manera muy compleja evitando que se pueda romper mediante fuerza bruta.
- **Dm-crypt o EncFS:** Sirve para **cifrar directamente un disco entero,** ya no solo un fichero si no todo el hardware que contiene dichos ficheros, como un disco duro, un pendrive...

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
# Copias de seguridad

Realizamos las copias con el comando **"tar"** y existen 3 tipos de copias de seguridad:

- **Totales:** Copiamos <u>todos</u> los datos.
- **Diferenciales:** Se copian <u>solo los que se hayan modificado desde una <b>fecha indicada.</b></u> Se utiliza la opción -N seguido de la fecha.
- **Incrementales:** Se copian <u>solo los ficheros que se han modificado <b>desde la última copia.</u></b> Se utiliza la opción -g seguido de la ruta del fichero de registro.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #9ACD32;">

<tr style="background:#9ACD32; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #9ACD32; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Comando tar y Compresión de Archivos</b> </td> </tr>

<tr style="background:rgba(154, 205, 50, 0.1); color:#6B8E23; font-weight:bold;"> <td style="border:1px solid #9ACD32; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #9ACD32; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- c</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Compacta</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- x</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Expande (extrae)</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- f</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Escribe o lee de un fichero</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- z</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Comprime o descomprime con gunzip</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- j</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Comprime o descomprime con bzip2</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- P</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Utiliza rutas absolutas (por defecto serán relativas), para extraerlo en un sitio específico, pero hay que saber lo que haces por evitar sobrescribir cosas</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- p</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Preserva los permisos de los ficheros originales</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- r</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Añade elementos a un fichero compactado</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- t</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Muestra la información que contiene un fichero tar</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- v</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Muestra como se comprime/descomprime la informacion</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- vv</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">Muestra el doble de información que <b>- v</b></td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- k</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">En caso de comprimir con <b>gzip, bzip2 o xz</b> para hacer que el fichero a comprimir no desaparezca cuando comprimes.</td> </tr>

<tr> <td style="border:1px solid #9ACD32; text-align:center; vertical-align:middle;"><b>- d</b></td> <td style="border:1px solid #9ACD32; text-align:left; vertical-align:middle; padding:8px;">En caso de descomprimir con <b>gunzip bzip2 o unxz</b> para hacer que el fichero contenedor a descomprimir no desaparezca cuando descomprimes.</td> </tr> </table>

# Redirecciones

Para redireccionar cosas, podemos hacerlo de la siguiente manera

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #9932CC;">

<tr style="background:#9932CC; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #9932CC; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Redirecciones de E/S (Input/Output)</b> </td> </tr>

<tr style="background:rgba(153, 50, 204, 0.1); color:#9932CC; font-weight:bold;"> <td style="border:1px solid #9932CC; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #9932CC; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #9932CC; text-align:center; vertical-align:middle;"><b>&gt;</b></td> <td style="border:1px solid #9932CC; text-align:left; vertical-align:middle; padding:8px;">Si el fichero existe, <b>lo sobreescribe,</b> si no, <b>crea uno nuevo.</b></td> </tr>

<tr> <td style="border:1px solid #9932CC; text-align:center; vertical-align:middle;"><b>&gt;&gt;</b></td> <td style="border:1px solid #9932CC; text-align:left; vertical-align:middle; padding:8px;">Si existe el fichero, añade los datos <b>al final.</b></td> </tr>

<tr> <td style="border:1px solid #9932CC; text-align:center; vertical-align:middle;"><b>&lt;</b></td> <td style="border:1px solid #9932CC; text-align:left; vertical-align:middle; padding:8px;">Redirige la entrada de texto <b>al comando anterior.</b>

  

Ejemplo: <code style="color:#9932CC;">sort &lt; listado</code></td> </tr>

<tr> <td style="border:1px solid #9932CC; text-align:center; vertical-align:middle;"><b>2&gt; || 2&gt;&gt;</b></td> <td style="border:1px solid #9932CC; text-align:left; vertical-align:middle; padding:8px;">Redirige <b>los mensajes de error.</b></td> </tr>

<tr> <td style="border:1px solid #9932CC; text-align:center; vertical-align:middle;"><b>&amp;&gt; || &amp;&gt;&gt;</b></td> <td style="border:1px solid #9932CC; text-align:left; vertical-align:middle; padding:8px;">Redirige <b>todos los mensajes.</b> (Salida estándar y errores)</td> </tr>

</table>

# Caracteres especiales

- **"^":** Que empiece con la letra o letras.
- **"$":** Que acabe con esa letra o letras, el $ va al final **siempre.**
- **".":** Permite cualquier caracter, si quisiesemos usar el "." como caracter, habria que poner \.
- **Corchetes:** 
	- uno de estos caracteres: \[aerd\]
	- un rango de numeros o caracteres \[4-8\]
	- el de esta posicion, y el de esta otra \[3,5\]
	- Exclusión \[^]: Lo que este seguido del sombrerito es que NO puede ser 
	- Clases: tabla posterior
	
<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #008080;">

<tr style="background:#008080; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #008080; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Clases de Caracteres POSIX</b> </td> </tr>

<tr style="background:rgba(0, 128, 128, 0.1); color:#008080; font-weight:bold;"> <td style="border:1px solid #008080; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #008080; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:alnum:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Letras y dígitos.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:alpha:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Letras.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:blank:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Espacios en blanco.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:cntrl:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Caracteres de control.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:space:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Los espacios en blanco verticales y horizontales.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:graph:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Caracteres imprimibles, <u>sin incluir espacio en blanco.</u></td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:print:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Caracteres imprimibles, <u>incluyendo espacio en blanco.</u></td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:digit:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Dígitos.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:lower:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Letras minúsculas.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:upper:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Letras mayúsculas.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:punct:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Signos de puntuación.</td> </tr>

<tr> <td style="border:1px solid #008080; text-align:center; vertical-align:middle;"><b>[:xdigit:]</b></td> <td style="border:1px solid #008080; text-align:left; vertical-align:middle; padding:8px;">Dígitos hexadecimales.</td> </tr>

</table>

# Repeticiones extendidas

IMPORTANTE, SOLO SON VALIDAS LAS REPETICIONES EXTENDIDAS SI USAMOS 
- **grep -E 'instrucción'** (importante las comillas individuales).
- **grep --color -E 'instrucción'** para ponerlo con color
- **sed -r 'instrucción'** (importante las comillas individuales).

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #FFBF00;">

<tr style="background:#FFBF00; color:#fff; font-weight:bold;"> <td colspan="3" style="border:1px solid #FFBF00; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Cuantificadores (Repeticiones)</b> </td> </tr>

<tr style="background:rgba(255, 191, 0, 0.1); color:#B8860B; font-weight:bold;"> <td style="border:1px solid #FFBF00; height:35px; width:20%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #FFBF00; height:35px; width:60%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> <td style="border:1px solid #FFBF00; height:35px; width:20%; text-align:center; vertical-align:middle;">Rango</td> </tr>

<tr> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;"><b>X*</b></td> <td style="border:1px solid #FFBF00; text-align:left; vertical-align:middle; padding:8px;">Ese carácter se puede repetir 0 o más veces.</td> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;">[0 , &infin;]</td> </tr>

<tr> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;"><b>X?</b></td> <td style="border:1px solid #FFBF00; text-align:left; vertical-align:middle; padding:8px;">Puede estar o no estar, pero solo puede estar 1 vez.</td> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;">[0 , 1]</td> </tr>

<tr> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;"><b>X+</b></td> <td style="border:1px solid #FFBF00; text-align:left; vertical-align:middle; padding:8px;">Es obligatorio que esté, y se puede repetir más veces.</td> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;">[1 , N]</td> </tr>

<tr> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;"><b>{n}</b></td> <td style="border:1px solid #FFBF00; text-align:left; vertical-align:middle; padding:8px;">Repetición exacta de n veces.</td> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;">[N , N]</td> </tr>

<tr> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;"><b>{n,}</b></td> <td style="border:1px solid #FFBF00; text-align:left; vertical-align:middle; padding:8px;">Repetición mínima de n veces y como máximo las que sean.</td> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;">[N, &infin;]</td> </tr>

<tr> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;"><b>{,n}</b></td> <td style="border:1px solid #FFBF00; text-align:left; vertical-align:middle; padding:8px;">Repetición como máximo n veces y mínimo ninguna.</td> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;">[0 , N]</td> </tr>

<tr> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;"><b>{n,m}</b></td> <td style="border:1px solid #FFBF00; text-align:left; vertical-align:middle; padding:8px;">Rango de repeticiones definido entre n y m.</td> <td style="border:1px solid #FFBF00; text-align:center; vertical-align:middle;">[N , M]</td> </tr> </table>

# NVIM

Es el primer editor de texto para la consola de Linux. Es importante concerlo porque está en **TODAS** las distribuciones y modos de arranque.

Actualmente es más común usar Vim (Vi mejorado) que Vi

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #B87333;">

<tr style="background:#B87333; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #B87333; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Editor de Texto Vi / Vim</b> </td> </tr>

<tr style="background:rgba(184, 115, 51, 0.1); color:#B87333; font-weight:bold;"> <td style="border:1px solid #B87333; height:35px; width:30%; text-align:center; vertical-align:middle;">Modo / Comando</td> <td style="border:1px solid #B87333; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función / Acción</td> </tr>

<tr style="background:rgba(184, 115, 51, 0.2);"> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;"><b>Modo Comando</b></td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Modo inicial. Se regresa a él pulsando <b>ESC</b>. Permite navegar y editar.</td> </tr>

<tr> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;">H, J, K, L / Cursores</td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Desplazarse por el texto (Izquierda, Abajo, Arriba, Derecha).</td> </tr>

<tr> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;">dd / yy / p</td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Borrar línea (<b>dd</b>), Copiar línea (<b>yy</b>) y Pegar (<b>p</b>).</td> </tr>

<tr> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;">o / u</td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Añadir línea debajo (<b>o</b>) y Deshacer última acción (<b>u</b>).</td> </tr>

<tr> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;">/texto o ?texto</td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Búsqueda hacia abajo (<b>/</b>) o hacia arriba (<b>?</b>).</td> </tr>

<tr> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;">i / a</td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Insertar antes del cursor (<b>i</b>) o después del cursor (<b>a</b>).</td> </tr>

<tr> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;">v / ZZ</td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Selección visual (<b>v</b>) y Guardar y salir rápido (<b>ZZ</b>).</td> </tr>

<tr style="background:rgba(184, 115, 51, 0.2);"> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;"><b>Modo Insertar</b></td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Permite escribir texto de forma normal.</td> </tr>

<tr style="background:rgba(184, 115, 51, 0.2);"> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;"><b>Modo EX ( : )</b></td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Modo de línea de comandos para órdenes del sistema.</td> </tr>

<tr> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;">:q / :w / :wq</td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Salir (<b>q</b>), Guardar (<b>w</b>) o Guardar y salir (<b>wq</b>).</td> </tr>

<tr> <td style="border:1px solid #B87333; text-align:center; vertical-align:middle;">:q!</td> <td style="border:1px solid #B87333; text-align:left; vertical-align:middle; padding:8px;">Forzar acción: Salir sin guardar los cambios.</td> </tr> </table>

# Atajos de la BASH


<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #5E2D5E;">

<tr style="background:#5E2D5E; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #5E2D5E; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Atajos de Teclado y Control de Bash</b> </td> </tr>

<tr style="background:rgba(94, 45, 94, 0.1); color:#5E2D5E; font-weight:bold;"> <td style="border:1px solid #5E2D5E; height:35px; width:30%; text-align:center; vertical-align:middle;">Atajo / Control</td> <td style="border:1px solid #5E2D5E; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>TAB</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Autocompleta nombres de comandos, archivos o rutas.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + R</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Busca de forma interactiva en el historial de comandos.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + L</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Limpia la pantalla de la terminal (mantiene el texto arriba).</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + A / E</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Mueve el cursor al principio (A) o al final (E) de la línea.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + U / K</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Borra desde el cursor hasta el inicio (U) o hasta el final (K).</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + W</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Borra la palabra anterior al cursor.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + Y</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Pega (yank) el último texto borrado con Ctrl+U, K o W.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + C</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Cancela y detiene el proceso actual inmediatamente.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + Z</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Pausa el proceso y lo envía al segundo plano.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>Ctrl + D</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Cierra la terminal o envía un EOF (fin de archivo).</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>!!</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Ejecuta de nuevo el último comando introducido.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>!$</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Sustituye por el último argumento del comando anterior.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>!n</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Ejecuta el comando número "n" del historial.</td> </tr>

<tr> <td style="border:1px solid #5E2D5E; text-align:center; vertical-align:middle;"><b>!texto</b></td> <td style="border:1px solid #5E2D5E; text-align:left; vertical-align:middle; padding:8px;">Ejecuta el último comando que empiece por "texto".</td> </tr> </table>