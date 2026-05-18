# 📊 1. Tablas

En esta sección se introducirán tablas con contenidos a recordar en cualquier momento

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #87CEEB;">

<tr style="background:#87CEEB; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #87CEEB; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Parámetros Especiales del Script</b> </td> </tr>

<tr style="background:rgba(135, 206, 235, 0.2); color:#0076A3; font-weight:bold;"> <td style="border:1px solid #87CEEB; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #87CEEB; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #87CEEB; text-align:center; vertical-align:middle;"><b>$n</b></td> <td style="border:1px solid #87CEEB; text-align:left; vertical-align:middle; padding:8px;">Información de un parámetro en concreto.</td> </tr>

<tr> <td style="border:1px solid #87CEEB; text-align:center; vertical-align:middle;"><b>$*</b></td> <td style="border:1px solid #87CEEB; text-align:left; vertical-align:middle; padding:8px;">Cada uno de los parámetros con los que se ha invocado el script.</td> </tr>

<tr> <td style="border:1px solid #87CEEB; text-align:center; vertical-align:middle;"><b>$@</b></td> <td style="border:1px solid #87CEEB; text-align:left; vertical-align:middle; padding:8px;">Igual que $*, se supone que es una Lista con un elemento por cada parámetro.</td> </tr>

<tr> <td style="border:1px solid #87CEEB; text-align:center; vertical-align:middle;"><b>$#</b></td> <td style="border:1px solid #87CEEB; text-align:left; vertical-align:middle; padding:8px;">El número de parámetros con los que se ha invocado el Script.</td> </tr> </table>
---

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #000080;">

<tr style="background:#000080; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #000080; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Variables de Entorno y Ejecución</b> </td> </tr>

<tr style="background:rgba(0, 0, 128, 0.1); color:#000080; font-weight:bold;"> <td style="border:1px solid #000080; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #000080; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #000080; text-align:center; vertical-align:middle;"><b>$0</b></td> <td style="border:1px solid #000080; text-align:left; vertical-align:middle; padding:8px;">El nombre del fichero.</td> </tr>

<tr> <td style="border:1px solid #000080; text-align:center; vertical-align:middle;"><b>$$</b></td> <td style="border:1px solid #000080; text-align:left; vertical-align:middle; padding:8px;">PID del proceso (Identificador del proceso) que se le ha asignado al script en ejecución.</td> </tr>

<tr> <td style="border:1px solid #000080; text-align:center; vertical-align:middle;"><b>$?</b></td> <td style="border:1px solid #000080; text-align:left; vertical-align:middle; padding:8px;">Resultado devuelto por el último proceso ejecutado. Para comprobar si ha ido bien o no el proceso anterior, nos devolvería <b><u>Verdadero o Falso.</u></b></td> </tr>

<tr> <td style="border:1px solid #000080; text-align:center; vertical-align:middle;"><b>$PATH</b></td> <td style="border:1px solid #000080; text-align:left; vertical-align:middle; padding:8px;">Ruta de los directorios donde va a ir a buscar el sistema los ficheros ejecutables.</td> </tr>

<tr> <td style="border:1px solid #000080; text-align:center; vertical-align:middle;"><b>printenv</b></td> <td style="border:1px solid #000080; text-align:left; vertical-align:middle; padding:8px;">Conocer todas las variables disponibles.</td> </tr> </table>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #A0522D;">

<tr style="background:#A0522D; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #A0522D; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Manejo de Arrays en Bash</b> </td> </tr>

<tr style="background:rgba(160, 82, 45, 0.1); color:#A0522D; font-weight:bold;"> <td style="border:1px solid #A0522D; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #A0522D; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #A0522D; text-align:center; vertical-align:middle;"><b>miarray=(d1 d2 d3)</b></td> <td style="border:1px solid #A0522D; text-align:left; vertical-align:middle; padding:8px;">Declarar un array.</td> </tr>

<tr> <td style="border:1px solid #A0522D; text-align:center; vertical-align:middle;"><b>${miarray[indice]}</b></td> <td style="border:1px solid #A0522D; text-align:left; vertical-align:middle; padding:8px;">Lectura del array por índices.</td> </tr>

<tr> <td style="border:1px solid #A0522D; text-align:center; vertical-align:middle;"><b>${miarray[*]}</b></td> <td style="border:1px solid #A0522D; text-align:left; vertical-align:middle; padding:8px;">Mostrar todos los elementos.</td> </tr>

<tr> <td style="border:1px solid #A0522D; text-align:center; vertical-align:middle;"><b>${miarray[@]}</b></td> <td style="border:1px solid #A0522D; text-align:left; vertical-align:middle; padding:8px;">Igual que el de arriba, mostrar todos los elementos.</td> </tr>

<tr> <td style="border:1px solid #A0522D; text-align:center; vertical-align:middle;"><b>${#miarray[@]}</b></td> <td style="border:1px solid #A0522D; text-align:left; vertical-align:middle; padding:8px;">Mostrar la cantidad de elementos.</td> </tr>

<tr> <td style="border:1px solid #A0522D; text-align:center; vertical-align:middle;"><b>${!miarray[@]}</b></td> <td style="border:1px solid #A0522D; text-align:left; vertical-align:middle; padding:8px;">Mostrar todos los índices.</td> </tr>

<tr> <td style="border:1px solid #A0522D; text-align:center; vertical-align:middle;"><b>unset miarray[indice]</b></td> <td style="border:1px solid #A0522D; text-align:left; vertical-align:middle; padding:8px;">Eliminar una posición.</td> </tr> </table>
---

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #008B8B;">

<tr style="background:#008B8B; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #008B8B; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Evaluación de Condiciones (Sintaxis)</b> </td> </tr>

<tr style="background:rgba(0, 139, 139, 0.1); color:#008B8B; font-weight:bold;"> <td style="border:1px solid #008B8B; height:35px; width:40%; text-align:center; vertical-align:middle;">Método</td> <td style="border:1px solid #008B8B; height:35px; width:60%; text-align:left; vertical-align:middle; padding-left:8px;">Estructura Visual</td> </tr>

<tr> <td style="border:1px solid #008B8B; text-align:center; vertical-align:middle;"><b>Comando Directo</b></td> <td style="border:1px solid #008B8B; text-align:left; vertical-align:middle; padding:12px;"> <code style="background:#f4f4f4; padding:4px 8px; border-radius:4px; color:#008B8B; font-weight:bold;">test</code> $V_1$ <small>(op)</small> $V_2$ </td> </tr>

<tr> <td style="border:1px solid #008B8B; text-align:center; vertical-align:middle;"><b>Notación de Corchetes</b></td> <td style="border:1px solid #008B8B; text-align:left; vertical-align:middle; padding:12px;"> <code style="background:#f4f4f4; padding:4px 8px; border-radius:4px; color:#008B8B; font-weight:bold;">[</code> $V_1$ <small>(op)</small> $V_2$ <code style="background:#f4f4f4; padding:4px 8px; border-radius:4px; color:#008B8B; font-weight:bold;">]</code> </td> </tr>

<tr style="background:rgba(0, 139, 139, 0.05);"> <td colspan="2" style="border:1px solid #008B8B; text-align:center; padding:10px; font-size: 0.9em; color:#555;"> <i>Nota: En la versión de corchetes, los espacios después de <b>[</b> y antes de <b>]</b> son obligatorios.</i> </td> </tr> </table>


---

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #F08080;">

<tr style="background:#F08080; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #F08080; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Comparaciones Numéricas y Aleatorios</b> </td> </tr>

<tr style="background:rgba(240, 128, 128, 0.1); color:#F08080; font-weight:bold;"> <td style="border:1px solid #F08080; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #F08080; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #F08080; text-align:center; vertical-align:middle;"><b>-eq</b></td> <td style="border:1px solid #F08080; text-align:left; vertical-align:middle; padding:8px;">Igual que</td> </tr>

<tr> <td style="border:1px solid #F08080; text-align:center; vertical-align:middle;"><b>-ge</b></td> <td style="border:1px solid #F08080; text-align:left; vertical-align:middle; padding:8px;">Mayor o igual que</td> </tr>

<tr> <td style="border:1px solid #F08080; text-align:center; vertical-align:middle;"><b>-gt</b></td> <td style="border:1px solid #F08080; text-align:left; vertical-align:middle; padding:8px;">Mayor que</td> </tr>

<tr> <td style="border:1px solid #F08080; text-align:center; vertical-align:middle;"><b>-le</b></td> <td style="border:1px solid #F08080; text-align:left; vertical-align:middle; padding:8px;">Menor o igual que</td> </tr>

<tr> <td style="border:1px solid #F08080; text-align:center; vertical-align:middle;"><b>-lt</b></td> <td style="border:1px solid #F08080; text-align:left; vertical-align:middle; padding:8px;">Menor que</td> </tr>

<tr> <td style="border:1px solid #F08080; text-align:center; vertical-align:middle;"><b>-ne</b></td> <td style="border:1px solid #F08080; text-align:left; vertical-align:middle; padding:8px;">No igual</td> </tr>

<tr> <td style="border:1px solid #F08080; text-align:center; vertical-align:middle;"><b>$(($RANDOM%30))</b></td> <td style="border:1px solid #F08080; text-align:left; vertical-align:middle; padding:8px;">Genera número aleatorio entre 0-29</td> </tr> </table>
---

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #800080;">

<tr style="background:#800080; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #800080; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Operaciones con Cadenas y Expresiones</b> </td> </tr>

<tr style="background:rgba(128, 0, 128, 0.1); color:#800080; font-weight:bold;"> <td style="border:1px solid #800080; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #800080; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>=</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">igual</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>&gt;</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">mayor que</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>&lt;</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">menor que</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>!=</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">diferente</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>-n</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">Cierto si la longitud de la cadena es diferente de 0</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>! Expresión</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">Cierto si la Expresión es falsa</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>Expresion1 -a Expresion2</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">AND</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>Espresion1 -o Expresion2</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">OR</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>${#var}</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">Devuelve la longitud de la cadena que contiene $var</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>${var:posicion}</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">Desde la posición indicada hasta el final de la cadena</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>${var:posicion:longitud}</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">Desde la posicion con la longitud indicada</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>${var#patrón}</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">Elimina desde el inicio, la parte <u>más corta</u> que coincida con <b>patrón</b>, si se pone <b>##</b> elimina la parte más larga</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>${var%patrón}</b></td> <td style="border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;">Igual que el anterior, pero elimina desde el final de $var</td> </tr>

<tr> <td style="border:1px solid #800080; text-align:center; vertical-align:middle;"><b>${var/patrón/cadena}&lt;/b&gt;&lt;/td&gt; &lt;td style=&quot;border:1px solid #800080; text-align:left; vertical-align:middle; padding:8px;&quot;&gt;&lt;b&gt;&lt;u&gt;Sustituye la primera ocurrencia&lt;/u&gt;&lt;/b&gt; que coincide con &lt;b&gt;patrón&lt;/b&gt; por &lt;b&gt;cadena.&lt;/b&gt; &lt;b&gt;${var//patrón/cadena}</b> <b><u>sustituye todas las ocurrencias</b></u></td> </tr>

</table>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>


<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #006400;">

<tr style="background:#006400; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #006400; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Dentro del if</b> </td> </tr>

<tr style="background:rgba(0, 100, 0, 0.1); color:#006400; font-weight:bold;"> <td style="border:1px solid #006400; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #006400; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #006400; text-align:center; vertical-align:middle;"><b>-d (Ruta)</b></td> <td style="border:1px solid #006400; text-align:left; vertical-align:middle; padding:8px;">Cierto si la Ruta existe y es un directorio</td> </tr>

<tr> <td style="border:1px solid #006400; text-align:center; vertical-align:middle;"><b>-e (Ruta)</b></td> <td style="border:1px solid #006400; text-align:left; vertical-align:middle; padding:8px;">Cierto si la Ruta existe y sea el elemento que sea</td> </tr>

<tr> <td style="border:1px solid #006400; text-align:center; vertical-align:middle;"><b>-f (Ruta)</b></td> <td style="border:1px solid #006400; text-align:left; vertical-align:middle; padding:8px;">Cierto si la Ruta existe y es un fichero normal</td> </tr>

<tr> <td style="border:1px solid #006400; text-align:center; vertical-align:middle;"><b>-r (Ruta)</b></td> <td style="border:1px solid #006400; text-align:left; vertical-align:middle; padding:8px;">Cierto si la Ruta existe y se puede leer</td> </tr>

<tr> <td style="border:1px solid #006400; text-align:center; vertical-align:middle;"><b>-w (Ruta)</b></td> <td style="border:1px solid #006400; text-align:left; vertical-align:middle; padding:8px;">Cierto si la Ruta existe y se puede escribir</td> </tr>

<tr> <td style="border:1px solid #006400; text-align:center; vertical-align:middle;"><b>-x (Ruta)</b></td> <td style="border:1px solid #006400; text-align:left; vertical-align:middle; padding:8px;">Cierto si la Ruta existe y se puede ejecutar</td> </tr>

<tr> <td style="border:1px solid #006400; text-align:center; vertical-align:middle;"><b>-s (Ruta)</b></td> <td style="border:1px solid #006400; text-align:left; vertical-align:middle; padding:8px;">Cierto si la Ruta existe y su tamaño es mayor que 0</td> </tr> </table>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #ff8c00;">

<tr style="background:#ff8c00; color:#fff; font-weight:bold;"> <td colspan="3" style="border:1px solid #ff8c00; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Gestión de Permisos y Propietarios</b> </td> </tr>

<tr style="background:rgba(255, 140, 0, 0.1); color:#ff8c00; font-weight:bold;"> <td style="border:1px solid #ff8c00; height:35px; width:20%; text-align:center; vertical-align:middle;">Comando</td> <td style="border:1px solid #ff8c00; height:35px; width:40%; text-align:left; vertical-align:middle; padding-left:8px;">Definición</td> <td style="border:1px solid #ff8c00; height:35px; width:40%; text-align:left; vertical-align:middle; padding-left:8px;">Ejemplos</td> </tr>

<tr> <td style="border:1px solid #ff8c00; text-align:center; vertical-align:middle;"><b>chmod</b></td> <td style="border:1px solid #ff8c00; text-align:left; vertical-align:middle; padding:8px;">Cambia los permisos de lectura, escritura y ejecución para el usuario, grupo y otros.</td> <td style="border:1px solid #ff8c00; text-align:left; vertical-align:middle; padding:8px;"><b>chmod u-rw,g+x,o=w ejemplo.txt</b>

  
  

<b>chmod 756 ejemplo.txt</b></td> </tr>

<tr> <td style="border:1px solid #ff8c00; text-align:center; vertical-align:middle;"><b>chown</b></td> <td style="border:1px solid #ff8c00; text-align:left; vertical-align:middle; padding:8px;">Cambia el usuario propietario y/o el grupo de un archivo o directorio.</td> <td style="border:1px solid #ff8c00; text-align:left; vertical-align:middle; padding:8px;"><b>chown usuario ejemplo.txt</b>

  
  

<b>chown usuario:grupo ejemplo.txt</b></td> </tr>

<tr> <td style="border:1px solid #ff8c00; text-align:center; vertical-align:middle;"><b>chgrp</b></td> <td style="border:1px solid #ff8c00; text-align:left; vertical-align:middle; padding:8px;">Cambia únicamente el grupo asociado a un archivo o directorio.</td> <td style="border:1px solid #ff8c00; text-align:left; vertical-align:middle; padding:8px;"><b>chgrp grupo ejemplo.txt</b></td> </tr> </table>
---
# Permisos especiales

- **SetUID:** El programa que lo tiene, se ejecuta con los permisos del <b><u>usuario propietario</u></b> de dicho fichero, no de quien posea los permisos en ese momento. Se representa con una **"s".** Chmod u+s. <b><u>Realmente no es que le demos permiso al propietario, ya que el dueño los tiene todos, es que permite que otros, "se disfracen" del dueño y puedan leerlo</u>, el ejemplo de fdisk, desde root puedo, pero si hago un SUID, desde jaime tambien puedo.</b>
  Se usa por ejemplo para poder cambiar la contraseña o realizar ciertas tareas que requieren de contraseña de root, sin la contraseña. 
	- De forma octal es chmod +4000 y si no es chmod u+s
		- Se pueden sumar en todo momento, +7000 (SUID + SGID + TB)

- **SetGID:** Igual que el **setUID** pero con los permisos del grupo. <b>En caso de ser directorio los elementos creados pertenecerán al grupo del directorio y no al grupo del usuario que crea el elemento.</b> Se escrube con chmod g+s. 
	- De forma octal es chmod +2000 y si no chmod g+s
		- Se pueden sumar en todo momento, +3000 (SGID + TB)

- **Sticky Bit:** En el directorio que lo tenga activado, los ficheros que contenga **sólo podrán ser borrados por sus propiertarios.** Se representa por **t** en el permiso de ejecución de "otros."
	- De forma octal es chmod +1000 y si no chmod o+t
		- Se pueden sumar en todo momento, +5000 (SUID + TB)

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #4A4A4A;">

<tr style="background:#4A4A4A; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #4A4A4A; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Gestión de Sesiones y Usuarios</b> </td> </tr>

<tr style="background:rgba(74, 74, 74, 0.1); color:#4A4A4A; font-weight:bold;"> <td style="border:1px solid #4A4A4A; height:35px; width:30%; text-align:center; vertical-align:middle;">Comando</td> <td style="border:1px solid #4A4A4A; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función Principal</td> </tr>

<tr> <td style="border:1px solid #4A4A4A; text-align:center; vertical-align:middle;"><b>su</b></td> <td style="border:1px solid #4A4A4A; text-align:left; vertical-align:middle; padding:8px;">Cambia de usuario. Si no se indica nombre o se usa <b>su -</b>, cambia a <b>root</b> (el guion inicia sesión con el entorno de ese usuario).</td> </tr>

<tr> <td style="border:1px solid #4A4A4A; text-align:center; vertical-align:middle;"><b>who</b></td> <td style="border:1px solid #4A4A4A; text-align:left; vertical-align:middle; padding:8px;">Muestra información sobre los logins actuales en el sistema: quién está conectado, desde dónde y cuándo entró.</td> </tr>

<tr> <td style="border:1px solid #4A4A4A; text-align:center; vertical-align:middle;"><b>w</b></td> <td style="border:1px solid #4A4A4A; text-align:left; vertical-align:middle; padding:8px;">Ofrece más información que <i>who</i>. Muestra quién está conectado, qué proceso está ejecutando en ese momento y la carga del sistema (uptime).</td> </tr>

<tr> <td style="border:1px solid #4A4A4A; text-align:center; vertical-align:middle;"><b>last</b></td> <td style="border:1px solid #4A4A4A; text-align:left; vertical-align:middle; padding:8px;">Lista los últimos accesos que ha tenido el sistema, incluyendo reinicios y sesiones ya cerradas (lee el archivo /var/log/wtmp).</td> </tr> </table>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
# Usuarios y grupos

**Los usuarios** se encuentran en <span style="color:#db7093;"><b>/etc/passwd</b></span>

Se usa el comandos <b>useradd</b>

<span style="color:#a52a2a;"><b>usuario</b></span>:<span style="color:#8b0000;"><b>X</b></span>:<span style="color:#c04000;"><b>UID</b></span>:<span style="color:#d2691e;"><b>GID</b></span>:<span style="color:#b22222;"><b>datos_personales</b></span>:<span style="color:#cd5c5c;"><b>directorio_home</b></span>:<span style="color:#bc8f8f;"><b>shell</b></span>

- <span style="color:#a52a2a;"><b>usuario</b></span>: Nombre de la cuenta del usuario.
- <span style="color:#8b0000;"><b>X</b></span>: Indica que su contraseña ya no está en este fichero, está en otro, concretamente <span style="color:#db7093;"><b>/etc/shadow</b></span>.
- <span style="color:#c04000;"><b>UID</b></span>: Identificador de usuario.
- <span style="color:#d2691e;"><b>GID</b></span>: Identificador de grupo.
- <span style="color:#b22222;"><b>datos_personales</b></span>: Información adicional (nombre completo, número, etc.).
- <span style="color:#cd5c5c;"><b>directorio_home</b></span>: Ruta de la carpeta personal del usuario.
- <span style="color:#bc8f8f;"><b>shell</b></span>: Intérprete de comandos asignado.


<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #db7093;">

<tr style="background:#db7093; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #db7093; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>useradd [opciones] nombre_usuario</b> </td> </tr>

<tr style="background:rgba(219, 112, 147, 0.2); color:#db7093; font-weight:bold;"> <td style="border:1px solid #db7093; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #db7093; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #db7093; text-align:center; vertical-align:middle;"><b>-d</b></td> <td style="border:1px solid #db7093; text-align:left; vertical-align:middle; padding:8px;">Define la ruta del directorio <b>home</b>. Solo indica la ruta, no crea la carpeta por sí mismo.</td> </tr> <tr> <td style="border:1px solid #db7093; text-align:center; vertical-align:middle;"><b>-m</b></td> <td style="border:1px solid #db7093; text-align:left; vertical-align:middle; padding:8px;"><b>Crea</b> el directorio home del usuario si este no existe.</td> </tr> <tr> <td style="border:1px solid #db7093; text-align:center; vertical-align:middle;"><b>-g</b></td> <td style="border:1px solid #db7093; text-align:left; vertical-align:middle; padding:8px;">Define el <b>grupo principal</b> (Primary Group) del usuario.</td> </tr> <tr> <td style="border:1px solid #db7093; text-align:center; vertical-align:middle;"><b>-G</b></td> <td style="border:1px solid #db7093; text-align:left; vertical-align:middle; padding:8px;">Lista de <b>grupos secundarios</b> (separados por comas) a los que pertenecerá el usuario.</td> </tr> <tr> <td style="border:1px solid #db7093; text-align:center; vertical-align:middle;"><b>-s</b></td> <td style="border:1px solid #db7093; text-align:left; vertical-align:middle; padding:8px;">Especifica el <b>intérprete de comandos</b> (Shell) por defecto (ej. /bin/bash).</td> </tr> <tr> <td style="border:1px solid #db7093; text-align:center; vertical-align:middle;"><b>-k</b></td> <td style="border:1px solid #db7093; text-align:left; vertical-align:middle; padding:8px;">Define el directorio de <b>plantilla</b> (Skeleton). Se suele usar <b>/etc/skel</b>; los archivos aquí dentro se copiarán al nuevo home.</td> </tr> </table>

---

**Las contraseñas** se encuentran en <span style="color:#90ee90;"><b>/etc/shadow</b></span>

Siempre se guardan las contraseñas **CIFRADAS**, nunca en **texto plano**. Se gestionan mediante el comando <b>passwd</b>.

<span style="color:#2e8b57;"><b>alumno</b></span>:<span style="color:#3cb371;"><b>contraseña_cifrada</b></span>:<span style="color:#66cdaa;"><b>dias_desde_cambio</b></span>:<span style="color:#8fbc8f;"><b>min_dias</b></span>:<span style="color:#20b2aa;"><b>max_dias</b></span>:<span style="color:#008080;"><b>dias_aviso</b></span>:<span style="color:#556b2f;"><b>dias_inactividad_hasta_bloqueo</b></span>

- <span style="color:#2e8b57;"><b>alumno</b></span>: Nombre del usuario.
- <span style="color:#3cb371;"><b>contraseña_cifrada</b></span>: Si aparece una "**!**" entre el usuario y la contraseña, indica que la cuenta está deshabilitada y no puede entrar al sistema. Esto se gestiona con:
    - Bloqueo: <code style="background:transparent; border:1px solid #90ee90; padding:2px;">passwd -l usuario</code>
    - Desbloqueo: <code style="background:transparent; border:1px solid #90ee90; padding:2px;">passwd -u usuario</code>

- <span style="color:#66cdaa;"><b>dias_desde_cambio</b></span>: Número de días transcurridos desde el último cambio de contraseña.
- <span style="color:#8fbc8f;"><b>min_dias</b></span>: Mínimo de días necesarios para poder cambiarla de nuevo.
- <span style="color:#20b2aa;"><b>max_dias</b></span>: Máximo de días de validez de la contraseña.
- <span style="color:#008080;"><b>dias_aviso</b></span>: Días de antelación con los que el sistema avisa de la próxima caducidad.
- <span style="color:#556b2f;"><b>dias_inactividad_hasta_bloqueo</b></span>: Días que pueden pasar desde que caduca la contraseña hasta que la cuenta se bloquea totalmente.


La contraseña cifrada utiliza un formato dividido por "**$**" que indica **$id$salt$hashed**:

1. **El $id** indica el **algoritmo de cifrado**:
    
    - **$1$**: MD5
    - **$2a$** o **$2y$**: Blowfish
    - **$5$**: SHA-256
    - **$6$**: SHA-512

2. **El salt**: Sirve para que la codificación de una misma palabra (ej. "silla") no se repita. Evita que un hacker use tablas precalculadas, ya que el cifrado varía de forma aleatoria según el sistema.
    
3. **El hashes**: Es el resultado final de la contraseña calculado junto con el _salt_.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #90ee90;">

<tr style="background:#90ee90; color:#1a1a1a; font-weight:bold;"> <td colspan="2" style="border:1px solid #90ee90; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>passwd [opciones] [nombre_usuario]</b> </td> </tr>

<tr style="background:rgba(144, 238, 144, 0.2); color:#2e8b57; font-weight:bold;"> <td style="border:1px solid #90ee90; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #90ee90; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>(sin opción)</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;">Cambia la contraseña del usuario actual (o del usuario especificado si eres root).</td> </tr> <tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>-l</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;"><b>Bloquea</b> (Lock) la cuenta del usuario añadiendo un "!" al hash de la contraseña en /etc/shadow.</td> </tr> <tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>-u</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;"><b>Desbloquea</b> (Unlock) la cuenta del usuario si estaba bloqueada previamente.</td> </tr> <tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>-d</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;"><b>Elimina</b> (Delete) la contraseña del usuario. La cuenta queda sin clave (permite login sin password).</td> </tr> <tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>-e</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;">Fuerza la <b>expiración</b> inmediata; el usuario deberá cambiar la clave en el próximo login.</td> </tr> <tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>-n (días)</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;">Establece el número <b>mínimo</b> de días entre cambios de contraseña.</td> </tr> <tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>-x (días)</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;">Establece el número <b>máximo</b> de días que una contraseña es válida.</td> </tr> <tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>-w (días)</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;">Establece los días de <b>aviso</b> (Warning) antes de la expiración.</td> </tr> <tr> <td style="border:1px solid #90ee90; text-align:center; vertical-align:middle;"><b>-S</b></td> <td style="border:1px solid #90ee90; text-align:left; vertical-align:middle; padding:8px;">Muestra el <b>estado</b> (Status) de la cuenta (bloqueos, fechas de cambio, etc.).</td> </tr> </table>

---

**Los grupos** se encuentran en <span style="color:#4682B4;"><b>/etc/group</b></span>

<span style="color:#1E90FF;"><b>nombre_grupo</b></span>:<span style="color:#4169E1;"><b>x</b></span>:<span style="color:#5F9EA0;"><b>GID</b></span>:<span style="color:#6495ED;"><b>lista_miembros</b></span>

- <span style="color:#1E90FF;"><b>nombre_grupo</b></span>: Nombre identificativo del grupo.
- <span style="color:#4169E1;"><b>x</b></span>: Sería la contraseña metida en <span style="color:#4682B4;"><b>/etc/gshadow</b></span>.
- <span style="color:#5F9EA0;"><b>GID</b></span>: Identificador de grupo (Ejemplo: 1002).
- <span style="color:#6495ED;"><b>lista_miembros</b></span>: Lista de nombre de usuarios separados por comas que pertenecen de forma secundaria; en <span style="color:#4682B4;"><b>/etc/passwd</b></span> sale el grupo principal en el GID.


<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #4682B4;">

<tr style="background:#4682B4; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #4682B4; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>groupadd [opciones] nombre_grupo</b> </td> </tr>

<tr style="background:rgba(70, 130, 180, 0.2); color:#4682B4; font-weight:bold;"> <td style="border:1px solid #4682B4; height:35px; width:30%; text-align:center; vertical-align:middle;">Opción</td> <td style="border:1px solid #4682B4; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #4682B4; text-align:center; vertical-align:middle;"><b>-g (GID)</b></td> <td style="border:1px solid #4682B4; text-align:left; vertical-align:middle; padding:8px;">Permite elegir un <b>ID de grupo</b> (GID) específico. Si no se pone, el sistema asigna el siguiente libre (normalmente a partir de 1000).</td> </tr> <tr> <td style="border:1px solid #4682B4; text-align:center; vertical-align:middle;"><b>-o</b></td> <td style="border:1px solid #4682B4; text-align:left; vertical-align:middle; padding:8px;">Permite crear un grupo con un <b>GID duplicado</b> (se usa junto con -g). No es recomendable por seguridad, pero el sistema lo permite.</td> </tr> <tr> <td style="border:1px solid #4682B4; text-align:center; vertical-align:middle;"><b>-r</b></td> <td style="border:1px solid #4682B4; text-align:left; vertical-align:middle; padding:8px;">Crea un <b>grupo de sistema</b>. Se le asignará un GID bajo (normalmente entre 1 y 999).</td> </tr> <tr> <td style="border:1px solid #4682B4; text-align:center; vertical-align:middle;"><b>-p</b></td> <td style="border:1px solid #4682B4; text-align:left; vertical-align:middle; padding:8px;">Define una <b>contraseña encriptada</b> para el grupo (uso poco frecuente en la práctica).</td> </tr> <tr> <td style="border:1px solid #4682B4; text-align:center; vertical-align:middle;"><b>-f</b></td> <td style="border:1px solid #4682B4; text-align:left; vertical-align:middle; padding:8px;">Fuerza la salida con éxito si el grupo ya existe y cancela el GID si ya está en uso.</td> </tr> </table>

---

Este directorio actúa como la "maqueta" inicial para la configuración de cada cuenta nueva en el sistema:

<span style="color:#DA70D6;"><b>/etc/skel/</b></span>: El directorio por defecto cuyo contenido se copia a los nuevos directorios personales de los usuarios; es la funcionalidad de la opción <span style="color:#BA55D3;"><b>-k</b></span> que mencionamos anteriormente en <span style="color:#9370DB;"><b>useradd</b></span>.

- <span style="color:#DA70D6;"><b>/etc/skel/</b></span>: Ruta del sistema que contiene archivos de configuración básicos (como `.bashrc` o `.profile`).
- <span style="color:#BA55D3;"><b>-k</b></span>: Parámetro que permite especificar manualmente esta u otra carpeta de plantilla durante la creación del usuario.
- <span style="color:#9370DB;"><b>Copia automática</b></span>: Al usar la opción `-m`, todo lo que esté dentro de esta ruta aparecerá mágicamente en el nuevo `/home/usuario`.

Aquí tienes la tabla de **Administración y Consulta de Identidades** adaptada con el tono **Rosa/Morado Orchid** (`#DA70D6`) que definimos para la sección de `/etc/skel/`.

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #DA70D6;">

<tr style="background:#DA70D6; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #DA70D6; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Administración y Consulta de Identidades</b> </td> </tr>

<tr style="background:rgba(218, 112, 214, 0.2); color:#ba55d3; font-weight:bold;"> <td style="border:1px solid #DA70D6; height:35px; width:30%; text-align:center; vertical-align:middle;">Comando</td> <td style="border:1px solid #DA70D6; height:35px; width:70%; text-align:left; vertical-align:middle; padding-left:8px;">Función</td> </tr>

<tr> <td style="border:1px solid #DA70D6; text-align:center; vertical-align:middle;"><b>getent</b></td> <td style="border:1px solid #DA70D6; text-align:left; vertical-align:middle; padding:8px;">Consulta las bases de datos del sistema (passwd, group, shadow). Ejemplo: <b>getent passwd usuario</b> o <b>getent group clase.</b></td> </tr> <tr> <td style="border:1px solid #DA70D6; text-align:center; vertical-align:middle;"><b>usermod</b></td> <td style="border:1px solid #DA70D6; text-align:left; vertical-align:middle; padding:8px;"><b>Modifica</b> una cuenta de usuario ya existente (cambiar grupos, nombre, shell o directorio home).</td> </tr> <tr> <td style="border:1px solid #DA70D6; text-align:center; vertical-align:middle;"><b>userdel</b></td> <td style="border:1px solid #DA70D6; text-align:left; vertical-align:middle; padding:8px;"><b>Elimina</b> un usuario. Con la opción <b>-r</b> elimina también su directorio home y sus archivos de correo (spool).</td> </tr> <tr> <td style="border:1px solid #DA70D6; text-align:center; vertical-align:middle;"><b>groupmod</b></td> <td style="border:1px solid #DA70D6; text-align:left; vertical-align:middle; padding:8px;"><b>Modifica</b> un grupo existente (cambiar su nombre o su identificador GID).</td> </tr> <tr> <td style="border:1px solid #DA70D6; text-align:center; vertical-align:middle;"><b>groupdel</b></td> <td style="border:1px solid #DA70D6; text-align:left; vertical-align:middle; padding:8px;"><b>Borra</b> un grupo del sistema. Nota: No se puede borrar el grupo primario de un usuario existente.</td> </tr> </table>

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
# Enlaces

**ln** crea un enlace a un elmento del sistema de ficheros, sin opciones creamos un **enlace duro** y con **-s** creamos un **enlace blando.**
- **Enlace duro:** Puntero a la información de disco. 
	- Si hago fichero1 y fichero2, **Aumenta el numero de la izquierda cuando hago ls.** 
	- **Si modifico** fichero1 se modifica fichero2.
	- **Si borro uno,** el otro no le pasa nada. 
	- Cuando hago enlaces fuertes a nuevos ficheros, **el espacio en disco es el mismo.**
		- *Fiarse de du -sh . más que de ls -lh.*

- **Enlace blando:** Puntero a la ruta. 
	- **Si elimino el original,** el que apunta al original dará error de que no lo encuentra, no puede vivir sin el original.

A los **directorios SIEMPRE se les hará un enlace simbólico.**

**Ejemplo:** 
- **ln /etc/apt/sources.list ~/repos**
	- Crea un <b><u>enlace fuerte</b></u> llamado <b><u>repos</u></b> que tendrá la <b><u>misma información</b></u> que el <b><u>sources.list.</b></u>
- **ln -s /var/cache/apt/archives/ /paquetes/**
	- Crea un <b><u>enlace simbólico</b></u> llamado <b><u>paquetes,</u></b> que <b><u>irá</u></b> a <b><u>/var/cache/apt/archives/.</b></u> 

<table style="width:100%; border-spacing:0; border-collapse:collapse;"> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> <tr style="height:3px; background-color:#444444;"><td style="padding:0; border:none;"></td></tr> <tr style="height:2px; background-color:#808080;"><td style="padding:0; border:none;"></td></tr> </table>
# EXTRA

Si tenemos una variable nombre=1 y hacemos
direccion="nombre"
estamos creando un puntero, y para pasarlo como puntero, luego en la variable habria que usarla tal que ${!direccion}

dentro de un if, o un for o lo que sea, usar $() significa **Ejecuta esto y sustituyelo por su salida**
por eso en un for usamos $(seq 1 3), y en un if, no podriamos poner $(ls /bin), seria if ls "\$direccion", las comillas siempre estan bien, porque sin ellas seria ls /usr/bin/mis poemas.txt,  llamando a **dos archivos diferentes, uno mis y otro poemas,** y con las "" lo trata como **un único bloque.**

<table style="width:90%; border-collapse:collapse; margin:0 auto; margin-bottom:12px; border-radius:6px; overflow:hidden; border: 2px solid #004d40;">

<tr style="background:#004d40; color:#fff; font-weight:bold;"> <td colspan="2" style="border:1px solid #004d40; height:45px; text-align:center; vertical-align:middle; font-family: monospace; font-size: 1.1em;"> <b>Entorno S4vitar (bspwm + Kitty + sxhkd)</b> </td> </tr>

<tr style="background:rgba(0, 77, 64, 0.1); color:#004d40; font-weight:bold;"> <td style="border:1px solid #004d40; height:35px; width:40%; text-align:center; vertical-align:middle;">Atajo de Teclado</td> <td style="border:1px solid #004d40; height:35px; width:60%; text-align:left; vertical-align:middle; padding-left:8px;">Acción en el Entorno</td> </tr>

<tr style="background:rgba(0, 77, 64, 0.05);"> <td colspan="2" style="border:1px solid #004d40; text-align:center; font-weight:bold; color:#004d40;">Gestión de Ventanas y Sistema</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + Enter</b></td> <td style="border:1px solid #004d40; padding:8px;">Abrir una nueva terminal (<b>Kitty</b>).</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + W</b></td> <td style="border:1px solid #004d40; padding:8px;">Cerrar la ventana/terminal actual.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + Alt + R</b></td> <td style="border:1px solid #004d40; padding:8px;">Reiniciar la configuración de <b>bspwm</b> y <b>sxhkd</b>.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + Alt + Q</b></td> <td style="border:1px solid #004d40; padding:8px;">Cerrar sesión (Salir al gestor de acceso).</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + F</b></td> <td style="border:1px solid #004d40; padding:8px;">Poner la ventana en <b>pantalla completa</b>.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + T / S / F</b></td> <td style="border:1px solid #004d40; padding:8px;">Cambiar estado: <b>Tiled</b> (mosaico), <b>Floating</b> (flotante), <b>Fullscreen</b>.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + HJKL / Flechas</b></td> <td style="border:1px solid #004d40; padding:8px;">Cambiar el foco entre ventanas abiertas.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + Shift + HJKL</b></td> <td style="border:1px solid #004d40; padding:8px;">Intercambiar posición de las ventanas.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + [1-9]</b></td> <td style="border:1px solid #004d40; padding:8px;">Cambiar al escritorio de trabajo número <b>n</b>.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + Shift + [1-9]</b></td> <td style="border:1px solid #004d40; padding:8px;">Mover la ventana seleccionada al escritorio <b>n</b>.</td> </tr>

<tr style="background:rgba(0, 77, 64, 0.05);"> <td colspan="2" style="border:1px solid #004d40; text-align:center; font-weight:bold; color:#004d40;">Terminal Kitty (Avanzado)</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Ctrl + Shift + Enter</b></td> <td style="border:1px solid #004d40; padding:8px;">Abrir nueva terminal dividiendo la actual (<b>Split</b>).</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Ctrl + Shift + T</b></td> <td style="border:1px solid #004d40; padding:8px;">Abrir una nueva <b>pestaña</b> dentro de Kitty.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Ctrl + Shift + Q</b></td> <td style="border:1px solid #004d40; padding:8px;">Cerrar la pestaña o split actual.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Ctrl + Shift + L</b></td> <td style="border:1px solid #004d40; padding:8px;">Cambiar la disposición de las ventanas (Layout) en Kitty.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Ctrl + Shift + Alt + T</b></td> <td style="border:1px solid #004d40; padding:8px;">Renombrar la pestaña actual para organización.</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Ctrl + Shift + Flechas</b></td> <td style="border:1px solid #004d40; padding:8px;">Navegar entre las diferentes pestañas abiertas.</td> </tr>

<tr style="background:rgba(0, 77, 64, 0.05);"> <td colspan="2" style="border:1px solid #004d40; text-align:center; font-weight:bold; color:#004d40;">Buscadores y Herramientas</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + D</b></td> <td style="border:1px solid #004d40; padding:8px;">Lanzar <b>Rofi</b> (Buscador visual de aplicaciones instaladas).</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + Alt + D</b></td> <td style="border:1px solid #004d40; padding:8px;">Lanzar <b>Rofi</b> en modo "run" (ejecutar comandos directamente).</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + Alt + P</b></td> <td style="border:1px solid #004d40; padding:8px;">Menú de <b>Power</b> (Apagar, Reiniciar, Suspender).</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + N</b></td> <td style="border:1px solid #004d40; padding:8px;">Abrir el gestor de archivos (usualmente <b>Thunar</b>).</td> </tr>

<tr> <td style="border:1px solid #004d40; text-align:center;"><b>Windows + Alt + X</b></td> <td style="border:1px solid #004d40; padding:8px;">Bloqueo de pantalla manual.</td> </tr>

</table>
