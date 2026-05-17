El impacto de las vulnerabilidades en la subida de archivos depende generalmente de dos factores clave:

- Qué aspecto del archivo el sitio web no valida correctamente, ya sea su tamaño, tipo, contenido, etc.
- ¿Qué restricciones se imponen al archivo una vez que se ha subido correctamente?

En el peor de los casos, el tipo de archivo no se valida correctamente y la configuración del servidor permite ejecutar ciertos tipos de archivo (como y ) como código. En este caso, un atacante podría potencialmente subir un archivo de código en el lado del servidor que funcione como un web shell, otorgándole efectivamente control total sobre el servidor. `.php``.jsp`

Si el nombre del archivo no se valida correctamente, esto podría permitir que un atacante sobrescriba archivos críticos simplemente subiendo un archivo con el mismo nombre. Si el servidor también es vulnerable al recorrido de directorios, esto podría significar que los atacantes incluso puedan subir archivos a ubicaciones inesperadas.

No asegurarse de que el tamaño del archivo se ajuste a los umbrales esperados también podría permitir una forma de ataque de denegación de servicio (DoS), en el que el atacante llena el espacio disponible en disco.

Podemos usar **ficheros** con extension ".htaccess" para dar permisos de que los archivos ".loquesea/inventado" sean leidos como un .php

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="fileu1.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

O, en caso de que busque **eliminar la palabra dada, como php** podemos hacer exploit.p.**php**hp para pasar el filtro

Uso del byte nulo, algunos idiomas como C dejan de leer a partir de %00, si existe un caso en el que solo permite .png o .jpg, podemos usar "exploit.php%00.png"

Por mucho que cambies el Content-Type a png o lo que sea (/image/png), el servidor puede leer el php y comprobar si tiene tamaño, cosa que no tiene, y entiende que no es un png

Si no, tambien las cabeceras hexadecimales se pueden cambiar, como las de los png que siempre empiezan por ``` FF D8 FF ```

---

Los marcos modernos están más curtidos contra este tipo de ataques. Generalmente no suben archivos directamente a su destino previsto en el sistema de archivos. En su lugar, toman precauciones como subir primero a un directorio temporal y sandboxeado y aleatorizar el nombre para evitar sobrescribir archivos existentes. Luego realizan la validación de este archivo temporal y solo lo transfieren a su destino cuando se considera seguro hacerlo.

Dicho esto, los desarrolladores a veces implementan su propio procesamiento de las subidas de archivos de forma independiente de cualquier framework. No solo es bastante complejo de hacer bien, sino que también puede introducir condiciones peligrosas de carrera que permiten a un atacante saltarse completamente incluso la validación más robusta.

Por ejemplo, algunos sitios web suben el archivo directamente al sistema principal y luego lo eliminan de nuevo si no pasa la validación. Este tipo de comportamiento es habitual en sitios web que dependen de software antivirus y similares para detectar malware. Esto puede tardar solo unos milisegundos, pero durante el corto tiempo que el archivo esté en el servidor, el atacante puede potencialmente ejecutarlo igualmente.

Estas vulnerabilidades suelen ser extremadamente sutiles, lo que dificulta su detección durante las pruebas de caja negra a menos que encuentres la forma de filtrar el código fuente relevante.