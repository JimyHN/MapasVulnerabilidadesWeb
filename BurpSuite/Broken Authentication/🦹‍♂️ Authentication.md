
La autenticación es el proceso de verificar la identidad de un usuario o cliente. Los sitios web pueden estar expuestos a cualquiera que esté conectado a internet. Esto hace que mecanismos de autenticación robustos sean fundamentales para una seguridad web eficaz.

Existen tres tipos principales de autenticación:

- Algo **que sepas**, como una contraseña o la respuesta a una pregunta de seguridad. A veces se les denomina "factores de conocimiento".
- Algo que **tienes**, es un objeto físico como un teléfono móvil o un token de seguridad. A veces se les llama "factores de posesión".
- Algo que **eres** o haces. Por ejemplo, tus datos biométricos o patrones de comportamiento. A estos a veces se les llama "factores de inherencia".

**La autenticación es el proceso de verificar que un usuario es quien dice ser. La autorización implica verificar si un usuario puede hacer algo.**

Por ejemplo, la autenticación determina si alguien que intenta acceder a un sitio web con ese nombre de usuario es realmente la misma persona que creó la cuenta.

Una vez autenticado, sus permisos determinan a qué están autorizados a hacer. Por ejemplo, pueden estar autorizados para acceder a información personal de otros usuarios o realizar acciones como eliminar la cuenta de otro usuario.

La mayoría de las vulnerabilidades en los mecanismos de autenticación se producen de dos maneras:

- Los mecanismos de autenticación son débiles porque no protegen adecuadamente contra ataques de fuerza bruta.
- Fallos lógicos o una mala codificación en la implementación permiten que los mecanismos de autenticación sean completamente ignorados por un atacante. Esto a veces se denomina "autenticación rota".

# Mecanismos para comprobar vulnerabilidad

### 1. Respuesta de Errores (Enumeración)

El objetivo es detectar si el servidor "delata" la existencia de un usuario por su comportamiento.

- **Diferencia de Mensajes:** Envía un usuario real y uno falso.
    
    - **Dónde mirar:** Pestaña `Response` -> `Render` o `Raw`. Busca frases distintas como _"Invalid password"_ vs _"Invalid user"_.
        
- **Diferencia de Tiempos:** Envía varias peticiones con contraseña muy larga.
    
    - **Dónde mirar:** Esquina inferior derecha del **Repeater** (milisegundos). Si el real tarda +50ms constantes, hay respuesta positiva.
        
- **Diferencia en Length:** Compara el tamaño de las respuestas.
    
    - **Dónde mirar:** Columna `Length` en el **Intruder**. Un cambio de 1 o 2 bytes suele significar que el mensaje de error ha cambiado internamente.
        

### 2. Mecanismos de Bloqueo (Brute Force Bypass)

Ver si el servidor tiene protecciones contra ataques masivos y cómo saltarlas.

- **Cabeceras de IP:** Si te bloquea (Error 429 o 403), añade `X-Forwarded-For: 127.0.0.1` o IPs aleatorias.
    
    - **Método:** Usa el **Intruder** con el payload de IPs para rotar la cabecera en cada petición.
        
- **Ataques de "Relleno" (Stuffing):** Intenta resetear el contador de fallos.
    
    - **Método:** Envía 2 intentos fallidos y 1 exitoso (con tu propia cuenta). Si tras el exitoso puedes fallar otras 2 veces sin bloqueo, el contador es vulnerable a reseteo.
        
- **Lógica de Bloqueo:** ¿Es por IP, por cuenta o por navegador?
    
    - **Método:** Cuando te bloquee, cambia de IP (VPN) o de navegador (User-Agent). Si el bloqueo persiste, están bloqueando la **cuenta** del usuario.

- **Bloqueo de cuentas a usuarios existentes**

	- **Método:** Probar si una cuenta existente, al fallar muchas veces la contraseña, se bloquea, mientras que una que no existe, no se bloquea
        

### 3. Vulnerabilidades Lógicas (Flujo de Diseño)

Buscar errores en el orden en que el servidor procesa los datos.

- **Validación Incompleta:** En formularios de cambio de clave.
    
    - **Método:** Introduce una "clave actual" incorrecta pero deja las "claves nuevas" vacías o desiguales. Si el error es _"Las contraseñas nuevas no coinciden"_, el servidor es vulnerable porque valida los datos nuevos **antes** de comprobar si eres el dueño de la cuenta.
        
- **Pasos Saltables:** En procesos de registro o checkout.
    
    - **Método:** Mira la URL, si me mandan a /login2, y luego a /my-account con un id, intentar saltar ese login2 para comprobar si ya estoy iniciado sesión directamente
        
- **Parámetros Ocultos:** Modificar privilegios.
    
    - **Método:** En el **Proxy**, busca campos como `admin=false`, `role=user` o `price=100` y cámbialos antes de que salgan hacia el servidor.

- Token viaja con username, deberia de tener dado por hecho el user sin username

- Los tokens solo pueden usarse una vez y durar maximo 10 minutos 
    

### 4. Gestión de Sesiones y Cookies

Analizar si la "llave" de acceso es segura y persistente.

- **Cookie predecible:** Fijarse en la cookie, viaja en texto plano de manera muy predecible? podemos usurpar identidad

- **2FA:** Si el codigo es sencillo de falsificar, no tiene bloqueo y la Cookie es predecible, simplemente hacemos un ataque de fuerza bruta

- **Persistencia:** Haz logout y luego intenta usar la cookie vieja.
    
    - **Método:** Copia el header `Cookie` antes de cerrar sesión, cierra sesión, y vuelve a enviar la petición en el **Repeater** con esa cookie. Si responde 200 OK, la sesión no muere en el servidor.
        
- **Predictibilidad:** Analizar el valor de la cookie.
    
    - **Método:** Pasa la cookie al **Decoder**. Prueba Base64, Hex o busca patrones. Si ves tu nombre de usuario o un timestamp, puedes suplantar a otros.
        
- **Seguridad (Flags):** Ver los atributos de la cookie.
    
    - **Dónde mirar:** Header `Set-Cookie`. Debe tener `; HttpOnly` (no accesible por JS) y `; Secure` (solo HTTPS).

- **Stay Logged in:**

	- Comprobar el hash del logged in, suele ser deducible
        

### 5. Recuperación de Contraseña (Olvido de Clave)

Atacar el eslabón más débil del acceso.

- **Token Predictible:** Analizar el enlace que llega al correo.
    
    - **Método:** Pide 3 recuperaciones seguidas. Si el token cambia poco (ej: `token=1001`, `1002`), usa el **Intruder** para adivinar el token de otro usuario.
        
- **Host Header Injection:** Engañar al servidor para que envíe el token a tu IP.
    
    - **Método:** En la petición de "Olvido mi contraseña", cambia el header `Host: victim.com` por `Host: tu-servidor-atacker.com`. Si el servidor genera el link usando ese Host, el usuario recibirá un correo con un link hacia TI, y tú capturarás su token.


# Enumeración de nombres de usuario

Al intentar forzar una página de inicio de sesión, debes prestar especial atención a cualquier diferencia en:

- **Códigos de estado**: Durante un ataque de fuerza bruta, el código HTTP devuelto probablemente sea el mismo para la gran mayoría de las suposiciones porque la mayoría serán erróneas. Si una suposición devuelve un código de estado diferente, esto es una fuerte indicación de que el nombre de usuario era correcto. Es buena práctica que los sitios web siempre devuelvan el mismo código de estado independientemente del resultado, pero esta práctica no siempre se cumple.
- **Mensajes de error**: A veces el mensaje de error devuelto varía dependiendo de si tanto el nombre de usuario como la contraseña son incorrectos o si solo la contraseña era incorrecta. Es buena práctica que los sitios web utilicen mensajes genéricos idénticos en ambos casos, aunque a veces aparecen pequeños errores de escritura. Un solo carácter fuera de lugar hace que los dos mensajes sean distintos, incluso en casos donde el carácter no es visible en la página renderizada.
- **Tiempos de respuesta**: Si la mayoría de las solicitudes se gestionaron con un tiempo de respuesta similar, cualquiera que se desvíe de esto sugiere que algo diferente estaba ocurriendo entre bastidores. Esto es otra señal de que el nombre de usuario adivinado podría ser correcto. Por ejemplo, un sitio web solo puede comprobar si la contraseña es correcta si el nombre de usuario es válido. Este paso extra podría provocar un ligero aumento en el tiempo de respuesta. Esto puede ser sutil, pero un atacante puede hacer que este retraso sea más evidente introduciendo una contraseña excesivamente larga que la web tarda considerablemente más en gestionar.

# Bloqueo de IP

Una manera de provocar que no nos bloquee la IP es añadir, en la petición justo después de Host, la siguiente cabecera

`X-Forwarded-For: ip`

El **X-Forwarded-For (XFF)** es una cabecera HTTP estándar de facto que se utiliza para identificar la dirección IP original de un cliente que se conecta a un servidor web a través de un proxy HTTP o un equilibrador de carga (load balancer).

### Cómo funciona el proceso

1. **El Cliente envía la petición:** Tu IP es, por ejemplo, `203.0.113.19`.
    
2. **El Proxy la recibe:** El proxy (con IP `10.0.0.5`) toma tu petición y añade la cabecera: `X-Forwarded-For: 203.0.113.19`
    
3. **El Servidor la lee:** El servidor recibe la conexión desde la IP `10.0.0.5`, pero mira dentro de las cabeceras HTTP, ve el campo `X-Forwarded-For` y dice: _"Ah, el usuario real es 203.0.113.19"_.

### Por qué es peligroso (IP Spoofing)

Aquí es donde entran los laboratorios de Burp Suite que estás haciendo. El campo `X-Forwarded-For` **es una cabecera de texto que el usuario puede manipular**.

- **El Engaño:** Si el servidor confía ciegamente en lo que dice esta cabecera sin verificar si viene de un proxy de confianza, tú puedes enviar una petición con: `X-Forwarded-For: 1.1.1.1`
    
- **El Resultado:** El servidor creerá que eres `1.1.1.1`. Si te bloquean por hacer fuerza bruta, simplemente cambias la cabecera a `1.1.1.2` y el servidor "limpia" tu historial de intentos porque cree que eres otra persona.

# Bloqueo de cuenta

Ante un bloqueo de cuenta por intentos fallidos o lo que sea, se puede sortear de la siguiente forma:

1. Establece una lista de nombres de usuario candidatos que probablemente sean válidos. Esto puede ser mediante la enumeración de nombres de usuario o simplemente basándose en una lista de nombres de usuario comunes.
2. Decide una lista muy pequeña de contraseñas que creas que al menos un usuario puede tener. Lo más importante es que el número de contraseñas que selecciones no debe superar el número de intentos de inicio de sesión permitidos. Por ejemplo, si has calculado que el límite es de 3 intentos, tienes que elegir un máximo de 3 intentos con contraseña.
3. Usando una herramienta como Burp Intruder, prueba cada una de las contraseñas seleccionadas con cada nombre de usuario candidato. De este modo, puedes intentar forzar todas las cuentas sin activar el bloqueo de cuenta. Solo necesitas que un solo usuario use una de las tres contraseñas para comprometer una cuenta.

# Autenticación en dos factores

Existe la posibilidad de que la pagina que nos mandan para autenticar con 2FA, se pueda saltar, si nos fijamos, cuando iniciamos sesión, en la URL pone luego /login2 y luego /myaccount_id=wiener.

Conociendo la información de inicio de sesión de carlos con su contraseña, simplemente en la pantalla de /login2, lo borramos y ponemos /myaccount y fuera.

Luego con la pestaña de mantenme conectado igual, genera un hash que se puede intuir, paginas lo que hacen es coger la contraseña y codificarla en MD5

**MD5 siempre son 32 caracteres, usa caracteres hexadecimales, con lo cual de letras es hasta la f, y sin simbolos**

Luego se puede usar XSS para sacar las cookies y hacer un decode y todo eso

# Cambio de contraseña

Un método más robusto para restablecer contraseñas es enviar una URL única a los usuarios que les lleve a una página de restablecimiento de contraseña. Las implementaciones menos seguras de este método utilizan una URL con un parámetro fácilmente adivinable para identificar qué cuenta se está restableciendo, por ejemplo:

`http://vulnerable-website.com/reset-password?user=victim-user`

Una mejor implementación de este proceso es generar un token de alta entropía y difícil de adivinar y crear la URL de reinicio a partir de eso. En el mejor de los casos, esta URL no debería dar pistas sobre qué contraseña de usuario se está restableciendo.

`http://vulnerable-website.com/reset-password?token=a0ba0d1cb3b63d13822572fcff1a241895d893f659164d4cc550b421ebdd48a8`

Básicamente, a veces cuando mandas la contraseña, se usa un token como validación, pero suda pollas del token, cambia el username y a cascarla

Sin embargo, si la URL se genera dinámicamente, hacemos estas cosas

### 1. Preparación y Análisis

- Abre el laboratorio y asegúrate de tener **Burp Suite** configurado.
    
- Ve a la página de "Forgot password?" e introduce tu propio usuario (`wiener`) para ver cómo funciona el proceso.
    
- Revisa tu correo en el **Exploit Server** (botón "Email client"). Verás un enlace tipo: `[https://ID-LABORATORIO.web-security-academy.net/forgot-password?temp-forgot-password-token=XYZ](https://ID-LABORATORIO.web-security-academy.net/forgot-password?temp-forgot-password-token=XYZ)`
    

### 2. Interceptación y Prueba del Header

- En Burp, busca la petición `POST /forgot-password`.
    
- Envíala al **Repeater** (Ctrl+R).
    
- Añade el encabezado `X-Forwarded-Host: google.com` a la petición.
    
- Envía la petición y revisa de nuevo tu correo en el Exploit Server. Si el enlace ahora apunta a `google.com` en lugar del dominio del laboratorio, ¡la vulnerabilidad está confirmada!
    

### 3. Ejecución del Ataque

1. **Copia la URL de tu Exploit Server** (solo la parte del dominio, ejemplo: `exploit-ID.exploit-server.net`).
    
2. En el **Repeater**, asegúrate de tener el encabezado: `X-Forwarded-Host: TU-ID-DE-EXPLOIT.exploit-server.net`
    
3. Cambia el parámetro del cuerpo de la petición de `username=wiener` a **`username=carlos`**.
    
4. Haz clic en **Send**.
    

### 4. Captura del Token

1. Ve al **Exploit Server** y haz clic en **Access log**.
    
2. Busca una petición `GET` reciente. Verás algo como: `GET /forgot-password?temp-forgot-password-token=TOKEN_ROBADO_DE_CARLOS`
    
3. **Copia ese token** con mucho cuidado.
    

### 5. Suplantación y Resolución

1. Ahora necesitas un enlace de restablecimiento válido del dominio original. Puedes usar el que te llegó a tu propio correo anteriormente.
    
2. Pega esa URL en tu navegador, pero **sustituye el valor del token** por el que le acabas de robar a Carlos.
    
3. Al cargar la página, el sistema te permitirá escribir una **nueva contraseña**. Pon la que quieras (ej. `hacked123`).
    
4. Finalmente, ve al login normal del laboratorio e inicia sesión como **carlos** con tu nueva contraseña.

# 6. Forgot password

- Si envia la solicitud basandose en el nombre, podemos intentar envenenar la sesión con X-Forwarded-Host: nuestro email, para que nos lleve a esa sesion


El **X-Forwarded** hace: Ese encabezado es la clave del ataque. Básicamente, le estás diciendo al servidor: _"Oye, aunque me estás respondiendo a mí, genera cualquier enlace interno usando este dominio de mi servidor de exploits en lugar del tuyo"_.

Si el servidor confía ciegamente en ese encabezado (lo cual hace este middleware vulnerable), enviará un correo a Carlos donde el botón de "Reset Password" no llevará a la web del laboratorio, sino a **tu** servidor.

**`X-Forwarded-Host` (El que usamos antes)**: Se usa para engañar al servidor sobre su propio nombre. Le dijimos: _"Tú te llamas servidor-de-exploit.com"_. El servidor se lo creyó y generó un enlace de recuperación apuntando a tu servidor. **Fue un ataque de "Envenenamiento" (Poisoning).**

# JWT Token (JSON Web Token)

- Estándar abierto (RFC 7519) para transmitir información de forma segura entre partes
- Compuesto por tres partes separadas por puntos: <b>Header.Payload.Signature</b>
	- **Header:** Algoritmo de firma (HS256, RS256) y tipo de token
	- **Payload:** Claims con datos del usuario (sub, name, role, exp, iat)
	- **Signature:** Firma criptográfica que verifica la integridad del token
- **Es stateless:** El servidor no necesita almacenar sesiones, todo está en el token

# Formas de explotarlo
## 1. Algoritmo None

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="algnone.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="algnone2.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

# 2. Cracking de secreto débil

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="debilalg.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

# 3. Key confusion

Cuando un servidor usa RS256 verifica tokens con la clave publica RSA, pero si tambien acepta HS256 podemos aprovecharnos, hay que obtener la clave publica que siempre esta disponbible, lo firmamos con HS256 con la clave publica como secreto, cuándo el servidor lo reciba, si acepta HS256 usara la misma clave publica para la forma HMAC

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="Keyconfusion.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

Flujo de ataque

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="Keyconfusion2.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>

# USAR HERRAMIENTA JWT_TOOL

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="JWTHerramienta.png" alt="Imagen 1" style="width: 100%; border-radius: 8px;">
</div>