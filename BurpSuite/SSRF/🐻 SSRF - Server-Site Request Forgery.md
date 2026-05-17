
**Definición:** **SSRF (Server-Side Request Forgery)** El atacante engaña al servidor de la víctima para que haga peticiones a recursos internos o externos en nombre del propio servidor. El ataque viene desde dentro de la infraestructura. Ejemplo: consigues que el servidor haga una petición a `http://169.254.169.254` y te devuelva credenciales de AWS.

La falsificación de solicitudes en el lado del servidor es una vulnerabilidad de seguridad web que permite a un atacante hacer que la aplicación del lado del servidor realice solicitudes a una ubicación no deseada.

En un ataque SSRF típico, el atacante podría hacer que el servidor establezca una conexión a servicios solo internos dentro de la infraestructura de la organización. En otros casos, pueden forzar que el servidor se conecte a sistemas externos arbitrarios. Esto podría filtrar datos sensibles, como credenciales de autorización.

Un ataque SSRF exitoso puede a menudo resultar en acciones no autorizadas o acceso a datos dentro de la organización. Esto puede estar en la aplicación vulnerable o en otros sistemas back-end con los que la aplicación puede comunicarse. En algunas situaciones, la vulnerabilidad SSRF podría permitir a un atacante ejecutar comandos arbitrarios.

Un exploit SSRF que provoque conexiones a sistemas externos de terceros podría provocar ataques maliciosos posteriores. Estos pueden parecer originarse en la organización que aloja la aplicación vulnerable.

En el contexto de la ciberseguridad y el **SSRF (Server-Side Request Forgery)**, un **comando arbitrario** se refiere a cualquier instrucción o código que un atacante logra ejecutar en un servidor sin tener permiso legítimo para hacerlo.

**Ejemplo:** Comprobar el stock, cuando comprueba el stock de un producto, hace una llamada con una API KEY al servidor para recibir respuesta, tal que

```
POST /product/stock HTTP/1.0 
Content-Type: application/x-www-form-urlencoded 
Content-Length: 118 

stockApi=http://stock.weliketoshop.net:8080/product/stock/check%3FproductId%3D6%26storeId%3D1
```

Esto hace que el servidor haga una solicitud a la URL especificada, recupere el estado de stock y devuelva esto al usuario.

En este ejemplo, un atacante puede modificar la solicitud para especificar una URL local al servidor:

```
POST /product/stock HTTP/1.0 
Content-Type: application/x-www-form-urlencoded 
Content-Length: 118 

stockApi=http://localhost/admin
```

Luego existen casos similares, pero usando direcciones IP privadas no enrutables

```
POST /product/stock HTTP/1.0 
Content-Type: application/x-www-form-urlencoded 
Content-Length: 118 

stockApi=http://192.168.0.68/admin
```

# Enmascarar esa direccion localhost

### 1. IPs alternativas (Disfrazar el número)

El sistema prohíbe el texto `127.0.0.1`, pero las computadoras pueden leer la misma dirección de otras formas. Es como si prohibieran decir "10" y tú dijeras "X" (en números romanos) o "diez" (en letras).

- **`2130706433`**: Es la misma IP pero en formato decimal.

- **`127.1`**: Es una forma abreviada que muchos sistemas aceptan.

- El filtro busca el "127.0.0.1", no lo encuentra, te deja pasar, y cuando el servidor recibe el número raro, entiende que debe ir a sí mismo.


### 2. Usar un nombre de dominio propio

Tú registras un nombre de internet normal (como `mi-web-falsa.com`) pero lo configuras para que, cuando alguien pregunte por él, responda: _"Mi dirección es 127.0.0.1"_.

- El filtro ve `mi-web-falsa.com`, cree que es una web externa inofensiva y te deja pasar.

- Pero cuando el servidor intenta conectar, se da cuenta de que la IP final es la suya propia.


### 3. Ofuscación (Codificación)

Esto es como usar un lenguaje secreto. Si prohíben la palabra `admin`, puedes escribirla en código URL:

- `admin` se convierte en `%61%64%6d%69%6e`.

- El filtro busca la palabra "admin", no la ve (porque solo ve símbolos de porcentaje) y te deja pasar. Luego, el servidor "traduce" el código y ejecuta la entrada al panel de administrador.


### 4. Redirección (El "Caballo de Troya")

Tú le pides al servidor que visite una URL que tú controlas (ej. `http://tu-servidor.com/ataque`).

1. El filtro revisa `tu-servidor.com`, ve que es legal y permite la conexión.

2. Tu servidor está configurado para que, en cuanto llegue la víctima, le diga: _"¡Sorpresa! Ahora vete a http://localhost/admin"_.

3. Muchos filtros solo revisan la **primera** dirección, pero no la dirección a la que te mandan después (la redirección).

# Lista blanca

Esto es el siguiente nivel de dificultad. Mientras que la **lista negra** prohíbe palabras, la **lista blanca** es mucho más estricta: solo permite peticiones que contengan un dominio específico (por ejemplo, el dominio de la empresa).

### 1. Uso del carácter `@` (Credenciales falsas)

En la estructura de una URL, puedes poner un usuario y contraseña antes del host usando el `@`.

- **Formato:** `https://usuario:contraseña@servidor-real.com`
- **El truco:** `https://servidor-esperado.com@tu-servidor-malicioso.com`
- **Resultado:** El filtro ve que empieza por "servidor-esperado" y te deja pasar, pero el navegador o el servidor de backend ignoran todo lo que está antes del `@` y terminan conectándose a **tu servidor**.


---

### 2. Uso del carácter `#` (Fragmentos)

El símbolo `#` indica un "fragmento" o ancla dentro de una página. Los navegadores no envían al servidor nada de lo que vaya después del `#`.

- **El truco:** `https://tu-servidor-malicioso.com#servidor-esperado.com`
- **Resultado:** El filtro busca el dominio permitido, lo encuentra después del `#` y dice "OK". Pero el componente que hace la petición real se detiene en el `#` y solo visita `tu-servidor-malicioso.com`.

---

### 3. Jerarquía DNS (Subdominios)

Puedes crear un subdominio en un servidor que tú controles que se llame exactamente como el servidor permitido.

- **El truco:** `https://servidor-esperado.com.tu-servidor.com`
- **Resultado:** El filtro ve que la cadena empieza con el nombre permitido. Sin embargo, en internet, el dominio real es el que está al final (`tu-servidor.com`). Es como si crearas una carpeta llamada "Google" dentro de tu propio disco duro; no eres Google, solo es el nombre de tu carpeta.

---

### 4. Codificación para confundir (Inconsistencias)

Esta es la técnica más avanzada y se basa en que el **Filtro** y el **Servidor de Backend** leen la URL de forma distinta.

Imagina este escenario:

1. Envías: `http://localhost%23@servidor-esperado.com`
2. El **Filtro** decodifica el `%23` y ve un `#`. Cree que todo lo que sigue es un fragmento irrelevante y que el host principal es `localhost` (o viceversa, según cómo esté programado).
3. El **Backend** quizás decodifica dos veces o interpreta el `@` de forma prioritaria, terminando en un lugar distinto al que el filtro validó.

### ¿Qué es una Redirección Abierta (Open Redirection)?

Es cuando una página legal tiene un parámetro (normalmente llamado `path`, `url`, o `next`) que te manda a otro sitio automáticamente.

- **Ejemplo legal:** `https://web-segura.com/login?redirect=/inicio` (Cuando te logueas, te manda a `/inicio`).
    
- **Vulnerabilidad:** Si esa página te permite poner **cualquier sitio**, como `https://web-segura.com/login?redirect=http://evil-user.net`, tienes una redirección abierta.


---

### Cómo se usa para saltar un SSRF

Imagina que el filtro de seguridad es un guardia muy estricto que dice: _"Solo dejo pasar peticiones que vayan a `web-segura.com`"_.

1. **El engaño:** Tú no le pides al guardia ir a `192.168.0.68/admin` (porque te bloquearía). Le pides ir a una página de `web-segura.com` que sabes que tiene una redirección.
    
2. **La petición:** Envías algo como: `stockApi=http://web-segura.com/product/next?path=http://192.168.0.68/admin`
    
3. **La validación:** El guardia (filtro) mira la URL, ve que empieza por `http://web-segura.com`, dice "Vale, esta web es de confianza" y deja pasar la petición.
    
4. **La ejecución:** El servidor principal hace la petición a esa URL. Al llegar, la página `/next` le responde: _"¡Hola! Ahora muévete a [http://192.168.0.68/admin](https://www.google.com/search?q=http://192.168.0.68/admin)"_.
    
5. **El impacto:** Como el servidor de backend suele confiar en las redirecciones, sigue la orden y acaba entrando en el sistema interno privado que querías atacar.


# SSRF CIEGO

Las vulnerabilidades SSRF ciegas ocurren si puedes hacer que una aplicación emita una solicitud HTTP de back-end a una URL proporcionada, pero la respuesta de la solicitud de back-end no se devuelve en la respuesta front-end de la aplicación.

El SSRF ciego es más difícil de explotar, pero a veces conduce a la ejecución remota completa de código en el servidor u otros componentes del backend.

(Este proceso me lo salto porque necesito el Collaborator para crear un dominio y mandarme la info directamente y es necesario el premium)

# SOLUCIONES

Aquí entramos en la parte de **"detective"** de la ciberseguridad. Estas capturas explican que no siempre vas a encontrar un parámetro obvio llamado `url=http://...`. A veces, el SSRF está escondido en lugares donde no parece haber una URL.

Aquí tienes el desglose de los dos conceptos principales:

---

## 1. URLs parciales (El "rompecabezas")

A veces, la aplicación no te deja escribir la URL entera, sino solo una **pieza**. El servidor toma tu pieza y la pega dentro de una URL interna que tú no ves.

- **Cómo funciona:** Imagina que el servidor tiene programado esto internamente: `"https://api.empresa.com/v1/" + [TU_DATO]`
    
- **Tu ataque:** Si tú envías como dato `../../admin`, el servidor acabará solicitando: `https://api.empresa.com/v1/../../admin` -> lo que se traduce en `https://api.empresa.com/admin`.
    
- **El problema:** Como no controlas el principio de la URL (el host), estás limitado a lo que haya en ese servidor específico. Sin embargo, usando técnicas de "Path Traversal" (`../`), puedes moverte por sus carpetas internas.
    

---

## 2. Superficie de ataque oculta (Formatos de datos)

Aquí es donde se pone interesante. Muchos archivos que enviamos a un servidor (como XML, PDFs o incluso imágenes) no son solo "datos", sino que tienen instrucciones internas que el servidor lee.

### El caso del XML (XXE a SSRF)

El formato XML permite definir algo llamado **Entidades Externas**. Es una instrucción que le dice al servidor: _"Oye, para leer este archivo, primero tienes que descargar este otro dato de esta URL"_.

- **El ataque:** Tú envías un XML normal, pero dentro escondes una línea que dice: _"Trae el archivo secreto de [http://192.168.0.1/admin](https://www.google.com/search?q=http://192.168.0.1/admin)"_.
    
- **El resultado:** El servidor, al intentar "entender" tu XML, hace la petición secreta por ti. Esto se llama **XXE (XML External Entity)**, y es una de las formas más comunes de causar un SSRF "escondido".
    

---

## 3. ¿Dónde más se esconde?

Aparte de lo que dicen tus capturas, hay otros lugares "invisibles":

- **Archivos PDF:** Si una web genera facturas en PDF a partir de lo que tú escribes, el motor que genera el PDF puede ser engañado para que incluya contenido de una URL interna.
    
- **Metadatos de imágenes:** Al subir una foto, el servidor puede intentar leer la ubicación GPS o el autor. Si manipulas esos campos con una URL, el servidor podría intentar visitarla.
    
- **Webhooks:** Servicios que te dicen "avísame cuando pase X cosa enviando un aviso a esta URL".

### ¿Qué es el cabezal `Referer`?

Cuando navegas por internet y haces clic en un enlace que te lleva de la **Web A** a la **Web B**, tu navegador envía automáticamente un mensaje a la **Web B** diciendo: _"Oye, este usuario viene de la Web A"_. Ese mensaje se guarda en el cabezal llamado `Referer`.

### ¿Por qué es una superficie de ataque?

Muchos sitios web modernos usan herramientas de analítica (como una versión interna de Google Analytics). Cuando el servidor ve que vienes de una URL desconocida, **intenta visitarla por su cuenta** para:

- Ver qué tipo de página es.
    
- Revisar qué dicen de ellos (el "texto ancla" del enlace).
    
- Categorizar la procedencia del tráfico.
    

**El problema de seguridad:** El servidor toma la URL que tú le des en el `Referer` y hace una petición HTTP hacia ella. Como esa petición la hace el servidor desde su propia red, ¡pum!, tienes un **SSRF**.