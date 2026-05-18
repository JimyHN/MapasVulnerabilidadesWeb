
Python es un lenguaje de programación que es:

- **Interpretado o de script**
	- Ya que no necesita una precompilación
- **Tipado dinámico**
	- Donde las variables no necesitan ser declaradas anteriormente de que tipo son, lo hace automáticamente.
- **POO (orientado a objetos)**

Usaremos **Anaconda,** ya que es el editor que utiliza <u><b>notebooks</b></u>

# CONCEPTOS BÁSICOS

Para declarar una variable:

**variable =expresion**

<table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
  <!-- Fila superior (gris oscuro semitransparente) -->
  <tr>
    <td colspan="4" style="border:1px solid #000; height:40px; font-weight:bold; text-align:center; vertical-align:middle; background-color: var(--background-secondary-alt); color: var(--text-normal);">
      <b>Tipos de datos</b>
    </td>
  </tr>

  <!-- Fila inferior (gris medio semitransparente) -->
  <tr>
    <td style="width:33%; border:1px solid #000; height:40px; text-align:center; vertical-align:middle;"><b>Números</b></td>
    <td style="width:33%; border:1px solid #000; height:40px; text-align:center; vertical-align:middle;"><b>Cadenas de texto</b></td>
    <td style="width:33%; border:1px solid #000; height:40px; text-align:center; vertical-align:middle;"><b>Valores booleanos</b></td>
  </tr>
</table>

# OPERACIONES BÁSICAS

<div class="centrado">
  <table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
    <colgroup>
      <col style="width: 30%;">
      <col style="width: 70%;">
    </colgroup>

    <thead>
      <tr style="background-color: var(--background-secondary-alt); color: var(--text-normal);">
        <th style="padding: 6px; border: 1px solid var(--background-modifier-border); text-align:center; vertical-align:middle;">Operación</th>
        <th style="padding: 6px; border: 1px solid var(--background-modifier-border); text-align:center; vertical-align:middle;">Detalles</th>
      </tr>
    </thead>

    <tbody>

      <!-- Exponenciación -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center; vertical-align:middle;">Exponenciación</td>
        <td style="border: 1px solid var(--background-modifier-border); padding:4px; text-align: justify;">
          Operador: <b>**</b><br>
          Aridad: Binario<br>
          Asociatividad: Por la derecha
        </td>
      </tr>

      <!-- Identidad -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center; vertical-align:middle;">Identidad</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>+</b><br>
          Aridad: Unario
        </td>
      </tr>

      <!-- Cambio de signo -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Cambio de signo</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>-</b><br>
          Aridad: Unario
        </td>
      </tr>

      <!-- Multiplicación -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Multiplicación</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>*</b><br>
          Aridad: Binario<br>
          Asociatividad: Por la izquierda
        </td>
      </tr>

      <!-- División -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">División</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>/</b><br>
          Aridad: Binario<br>
          Asociatividad: Por la izquierda
        </td>
      </tr>

      <!-- Módulo -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Módulo (o resto)</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>%</b><br>
          Aridad: Binario<br>
          Asociatividad: Por la izquierda
        </td>
      </tr>

      <!-- Suma -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Suma</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>+</b><br>
          Aridad: Binario<br>
          Asociatividad: Por la izquierda
        </td>
      </tr>

      <!-- Resta -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Resta</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>-</b><br>
          Aridad: Binario<br>
          Asociatividad: Por la izquierda
        </td>
      </tr>

      <!-- Igual que -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Igual que</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>==</b><br>
          Aridad: Binario
        </td>
      </tr>

      <!-- Distinto de -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Distinto de</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>!=</b><br>
          Aridad: Binario
        </td>
      </tr>

      <!-- Menor que -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Menor que</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>&lt;</b><br>
          Aridad: Binario
        </td>
      </tr>

      <!-- Menor o igual que -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Menor o igual que</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>&lt;=</b><br>
          Aridad: Binario
        </td>
      </tr>

      <!-- Mayor que -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Mayor que</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>&gt;</b><br>
          Aridad: Binario
        </td>
      </tr>

      <!-- Mayor o igual que -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Mayor o igual que</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>&gt;=</b><br>
          Aridad: Binario
        </td>
      </tr>

      <!-- Negación -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Negación</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>not</b><br>
          Aridad: Unario
        </td>
      </tr>

      <!-- Conjunción -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Conjunción</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>and</b><br>
          Aridad: Binario<br>
          Asociatividad: Por la izquierda
        </td>
      </tr>

      <!-- Disyunción -->
      <tr>
        <td style="border:1px solid #000; padding:4px; text-align:center;">Disyunción</td>
        <td style="border:1px solid var(--background-modifier-border); padding:4px; text-align:justify;">
          Operador: <b>or</b><br>
          Aridad: Binario<br>
          Asociatividad: Por la izquierda
        </td>
      </tr>

    </tbody>
  </table>
</div>


# FUNCIONES PREDEFINIDAS

<table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
  
  <!-- Fila superior -->
  <tr>
    <td colspan="2" style="
        border:1px solid #000;
        height:40px;
        font-weight:bold;
        text-align:center;
        vertical-align:middle;
        background-color: var(--background-secondary-alt);
        color: var(--text-normal);
      ">
      <b>Funciones predefinidas</b>
    </td>
  </tr>

  <!-- Filas de valores -->
  <tr>
    <td style="width:20%; border:1px solid #000; height:40px; vertical-align:middle;"><b>abs()</b></td>
    <td style="width:80%; border:1px solid #000; height:40px; vertical-align:middle;">calcula el valor absoluto de un número</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>float()</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">convertir a float</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>int()</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">convertir a int</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>str()</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">convertir a string</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>round()</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">redondeo, puede usarse con uno o dos argumentos</td>
  </tr>

</table>

# FUNCIONES IMPORT MATH

<table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
  
  <!-- Fila superior -->
  <tr>
    <td colspan="3" style="
        border:1px solid #000;
        height:40px;
        font-weight:bold;
        text-align:center;
        vertical-align:middle;
        background-color: var(--background-secondary-alt);
        color: var(--text-normal);
      ">
      <b>Funciones matemáticas</b>
    </td>
  </tr>

  <!-- Filas -->
  <tr>
    <td style="width:20%; border:1px solid #000; height:40px; vertical-align:middle;"><b>sin(x)</b></td>
    <td style="width:60%; border:1px solid #000; height:40px; vertical-align:middle;">Seno de x (expresado en radianes)</td>
    <td style="width:20%; border:1px solid #000; height:40px; vertical-align:middle;">math.sin(x)</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>cos(x)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Coseno de x (expresado en radianes)</td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">math.cos(x)</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>tan(x)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Tangente de x (expresado en radianes)</td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">math.tan(x)</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>exp(x)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">El número e elevado a x</td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">math.pow(numero,exponente)</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>ceil(x)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Redondeo hacia arriba de x (techo)</td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">math.ceil(x)</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>floor(x)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Redondeo hacia abajo de x (suelo)</td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">math.floor(x)</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>log(x)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Logaritmo natural (base e) de x</td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">math.log(x)</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>log10(x)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Logaritmo decimal (base 10) de x</td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">math.log10(x)</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>sqrt(x)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Raíz cuadrada de x</td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">math.sqrt(x)</td>
  </tr>
</table>

# FUNCIONES IMPORT RANDOM

<table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
  
  <!-- Fila superior -->
  <tr>
    <td colspan="3" style="
        border:1px solid #000;
        height:40px;
        font-weight:bold;
        text-align:center;
        vertical-align:middle;
        background-color: var(--background-secondary-alt);
        color: var(--text-normal);
      ">
      <b>Funciones matemáticas</b>
    </td>
  </tr>

  <tr>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>randint(a, b)</b></td>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;">Devuelve un entero aleatorio entre a y b (incluidos)</td>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;">random.randint(a, b)</td>
</tr>

<tr>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>randrange(a, b)</b></td>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;">Devuelve un entero aleatorio entre a y b (b excluido)</td>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;">random.randrange(a, b)</td>
</tr>

<tr>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>random()</b></td>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;">Devuelve un float aleatorio entre 0.0 y 1.0</td>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;">random.random()</td>
</tr>

<tr>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>uniform(a, b)</b></td>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;">Devuelve un float aleatorio entre a y b</td>
  <td style="border:1px solid #000; height:40px; vertical-align:middle;">random.uniform(a, b)</td>
</tr>

</table>


<table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
  <thead>
    <tr>
      <th>Especificador</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>%d</td>
      <td>entero</td>
      <td>Entero en base 10.</td>
    </tr>
    <tr>
      <td>%i</td>
      <td>entero</td>
      <td>Igual que %d; acepta decimal, octal o hex.</td>
    </tr>
    <tr>
      <td>%u</td>
      <td>entero</td>
      <td>Entero sin signo (obsoleto; en Python actúa como %d).</td>
    </tr>
    <tr>
      <td>%o</td>
      <td>entero</td>
      <td>Formato octal.</td>
    </tr>
    <tr>
      <td>%x</td>
      <td>entero</td>
      <td>Hexadecimal en minúsculas.</td>
    </tr>
    <tr>
      <td>%X</td>
      <td>entero</td>
      <td>Hexadecimal en mayúsculas.</td>
    </tr>
    <tr>
      <td>%f</td>
      <td>float</td>
      <td>Punto flotante (6 decimales por defecto).</td>
    </tr>
    <tr>
      <td>%F</td>
      <td>float</td>
      <td>Igual que %f.</td>
    </tr>
    <tr>
      <td>%e</td>
      <td>float</td>
      <td>Notación científica (minúsculas).</td>
    </tr>
    <tr>
      <td>%E</td>
      <td>float</td>
      <td>Notación científica (mayúsculas).</td>
    </tr>
    <tr>
      <td>%g</td>
      <td>float</td>
      <td>Usa %f o %e según convenga; elimina ceros innecesarios.</td>
    </tr>
    <tr>
      <td>%G</td>
      <td>float</td>
      <td>Igual que %g pero con E mayúscula.</td>
    </tr>
    <tr>
      <td>%c</td>
      <td>char</td>
      <td>Carácter basado en su código Unicode.</td>
    </tr>
    <tr>
      <td>%s</td>
      <td>string</td>
      <td>Convierte usando str().</td>
    </tr>
    <tr>
      <td>%r</td>
      <td>repr</td>
      <td>Convierte usando repr(); útil para depuración.</td>
    </tr>
  </tbody>
</table>

# CONDICIONALES

**if condicion:
	accion
elif condicion:
	accion
else
	accion**

## Casos de evaluacion

### Evaluar en línea

print("par" if edad%2 == 0 else "impar")

### Evaluar si un valor está entre varios posibles

tecla = 'S'
if tecla in('s','S','y','Y')
print("Ha seleccionado: S')

### Evaluar booleanos

respuesta = **True** (SIEMPRE EN MAYÚSCULA)
if respuesta: # Evalua si es True
	print("si")
else:
	print("no")

### Evaluar variables por tipo de datos
var1="ola"
var2=3
var3=3.14
var4=True
if type(var1) is str:
	print("'var1' es una cadena")


# BUCLES

## WHILE

**While condicion:
	accion**
	
count=0

<u>Ejemplos:</u>

While count<5:
	print(count, "is less than 5")
	count = count + 1

## FOR

**for variable in estructura:
	accion**

estructuras = cadenas, listas o diccionarios

<u>Ejemplos:</u>

for i in "ana,"maria,"sol":
	print (i)

lista="\[ "ana","mario","sol" \]"
for i in lista:
	print(i)

Dentro de for podemos usar in range()

for Condicion in range(5) -> por defecto, **Contador = 0**
for Condicion in range(0,10) -> de 0 a 9
for Contador in range(0,10,2) -> de 2 en 2 va saltando

# COLECCIONES Y LISTAS

lista = \[2,"DAM",False,\[1,2\]\]

print(type(lista))
print(type(lista\[1\]))

\[inicio:final\]
lista=\[4,8,1,2,3\]
print(lista=\[0:3\]) -> \[4, 8, 1\] ***LA 3 NO SE INCLUYE***

\[incio:final:salto\]
print(lista=\[3:1:-1\]) -> \[\[1,2\], False\]

<table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
  
  <!-- Fila superior -->
  <tr>
    <td colspan="2" style="
        border:1px solid #000;
        height:40px;
        font-weight:bold;
        text-align:center;
        vertical-align:middle;
        background-color: var(--background-secondary-alt);
        color: var(--text-normal);
      ">
      <b>Funciones predefinidas</b>
    </td>
  </tr>

  <!-- Filas adaptadas EXACTAMENTE a tus imágenes -->
  <tr>
    <td style="width:20%; border:1px solid #000; height:40px; vertical-align:middle;"><b>append(elemento)</b></td>
    <td style="width:80%; border:1px solid #000; height:40px; vertical-align:middle;">añade un elemento al final de la lista. Solo se puede añadir uno.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>extend(elementos)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">procesa la secuencia de elementos del parámetro y los añade uno a uno a la lista. Se pueden añadir muchos.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>insert(posición, elemento)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">añade un elemento en la posición que se indique en el primer parámetro.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>pop([posición])</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">si lo llamamos sin parámetro nos retorna y borra la información del último nodo de la lista. Si pasamos un entero este indica la posición.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>remove(elemento)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">borra el primer nodo que coincide con la información que se le pase como parámetro.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>count(elemento)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">retorna la cantidad de veces que se repite la información que se le pasa como parámetro.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>index(elemento,[inicio],[fin])</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">retorna la primera posición donde se encuentra el primer parámetro en la lista.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>sort()</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">ordena la lista de menor a mayor.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>reverse()</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">invierte el orden de los elementos de la lista.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>del()</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">si se necesita borrar un nodo de la lista.</td>
  </tr>

</table>

### ELIMINANDO

1)

lista = \[10, 20, 30]

lista.pop(0)

print(lista)

2)

lista = \[10, 20, 30]

del lista\[0]

print(lista)

3)

lista = \[10, 20, 30]

lista = lista\[1:]

print(lista)

4)

if eliminado in equipo:
    equipo.remove(eliminado)
    print(f"¡Hasta luego {eliminado}! ¡Vuelve pronto!")
    mostrar_equipo(equipo)

# FUNCIONES EN CADENAS

## Concatenar
mensaje1 = 'Hola' + 'mundo'
print(mensaje1)
Hola mundo

## Multiplicar
mensaje2a='Hola'\*3
print(mensaje2a)
hola hola hola

## Añadir
mensaje = 'ola'
mensaje += ' '
mensaje+='mundo'

hola mundo

## Encontrar
mensaje = 'hola Mundo'
mensaje5a=mensaje.find("mundo")

cuenta caracter a caracter
devolveria 5

## Reemplazar
mensaje="penepene"
mena=mensaje.replace("p", "pizza")

pizzaenepizzaene

## Longitud
len(cadena)

## strip()
Devuelve una copia de la cadena **sin espacio  inicial y final**

rstrip() solo derecha
lstrip() solo izquierda

## swapcase()
devuelve la cadena con mayusculas a minusculas y minusculas a mayusculas

## title()
cadena con primera mayuscula

## endswith(sub\[,start\[end]\])
retorna verdadero o falso si la cadena **termina** con la cadena especificada
S='hola mundo'
print s.endswith("do")
	True
print s.endswith("d")
	False

## startswith(sub\[,start\[end]\])
similar al anterior pero empezando
print s.starswith("h")
	True

## Split
Divide una cadena usando un separador (por defecto, el espacio) y devuelve **una lista con las partes resultantes**.

texto = "Hola mundo desde Python"
resultado = texto.split()

print(resultado)

\['Hola', 'mundo', 'desde', 'Python'\]

**Ejemplo 1:**

cadena = "pepito:5,6:7:8"
partes = cadena.split(":")
print(partes)

\['pepito', '5,6', '7', '8']

**Ejemplo 2:**

cadena = "pepito:5,6:7:8"
partes = cadena.split(":")

nombre = partes\[0]
a, b = partes\[1].split(",")
c = partes\[2]
d = partes\[3]

print(nombre, a, b, c, d)

pepito 5 6 7 8
# DICCIONARIOS

Son colecciones que relacionan una clave y un valor

Clase={"SGE": Valentina, "AD": Marta}

Clase = {} //constructor vacio

Cuando creemos dicho diccionario debeos tener en cuneta que envez de usar indices numericos, acedemos mediante claves

print(Clase\["SGE"\])

## Métodos

### Ver si una clave existe en el diccionario

clave in diccionario

### Añadir elementos al diccionario

clase \["clave nueva"\] = "valor nuevo"

### Borrar elementos

del diccionario \["clave"\]

### Borrar diccionario entero

del diccionario
ó
diccionario.clear()

## FOR PARA DICCIONARIOS

for clave in diccionario:
	print(clave, ": ", diccionario\[clave\])

Usando metodo **items()** obtenemos una lista de tuplas (clave, valor), que pdemos usar en el for:

for (clave, valor) in diccionario.items():
	print(clave,": ", valor)

Usando enumerate se puede obtener el indice de posiciion junto a su clave correspondiente

for i,v in enumerate(diccionario):
	print(i, v)

## ORDENACION

### POR CLAVE

sorted(diccionario)
sorted(diccionario, reverse=True) //descendente

### POR VALORES

from operator import itemgetter

compra={'leche':2, 'cafe':1, 'quesos':5}
print(sorted(compra.items(), key=itemgetter(1)))

ordena por el valor, ya que itemgetter(1) miramaos la posicion 1 de las minilistas

# FUNCIONES

# PRIMER ORDEN O PROPIAS

Función: def funcion(parametro1, parametro2)
	cuerpo funcion

usamos return para devolver, si no se usa nada devuelve None, las funciones SIEMPRE devuelven algo

determinar que uno de los parametros tenga valor cuando se pide por parentesis, VALORES POR DEFECTO

def multiplicar(num_1, num_2=2): CORRECTO

def multiplicar(num_1=2, num_2): INCORRECTO, SE PONE EL VALOR POR DEFECTO AL FINAL

dentro del return se pueden poner varios valores

## PARAMETROS ARBITRARIOS

Estos argumentos llegaran a la función en gorma de LISTA, si una función espera recibir parámetros fijos o arbitrarios, los arbitrarios siempre deben suceder a los fijos.

def recorrer_parametros_arbitrarios(parametro_fijo, \*arbitrarios):
	print(parametro_fijo)
		for argumento in arbitrarios:
			print(argumento)

recorrer_parametros_arbitrarios('Fixed', 'arbitrario1', 'arbitrario2', 'arbitrario3')

**ARBITRARIO ES EL CONCEPTO POR EL QUE PODEMOS PASAR NINGUNO/UNO/N ELEMENTOS**

Por lo que el primer print seria de Fixed y luego para el restro de arbitrarios entraria el for en cada uno de ellos

con el asterisco tratamos al parametro como arbitrarios, con dos asteriscos como clave:valor como los diccionarios

def varios(param1, param2, \*\*otros):
	for i in otros.items():
		print(i)
	print(param1)
	print(param2)

varios(1,2,tercero=3) 

## Ejemplo diccionario como parametro

def mostrar_diccionario(datos):
    for clave, valor in datos.items():
        print(f"Clave: {clave} → Valor: {valor}")


empleados = {"emp1": "Pepe", "emp2": "Sara", "emp3": "Miguel"}

mostrar_diccionario(empleados)

Clave: emp1 → Valor: Pepe
Clave: emp2 → Valor: Sara
Clave: emp3 → Valor: Miguel

## Funciones lambda

anónimas, solo expresiones, distintas a las anteriores funciones porque son proporcionadas por python y no podemos usar ni bucles ni return

Lambda \<parámetros\>:\<expresión\>\<expresión\>\<parámetros\>

Ejemplo:
	print( (lambda x: x\*2) (3) )
	Sol = 6

#  ALTO ORDEN O DE PYTHON (PROPIAS DE PYTHON)

<table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
  
  <!-- Fila superior -->
  <tr>
    <td colspan="2" style="
        border:1px solid #000;
        height:40px;
        font-weight:bold;
        text-align:center;
        vertical-align:middle;
        background-color: var(--background-secondary-alt);
        color: var(--text-normal);
      ">
      <b>Funciones de Alto orden</b>
    </td>
  </tr>

  <!-- Filas adaptadas EXACTAMENTE a tus imágenes -->
  <tr>
    <td style="width:20%; border:1px solid #000; height:40px; vertical-align:middle;"><b>map (func, lista)</b></td>
    <td style="width:80%; border:1px solid #000; height:40px; vertical-align:middle;">Devuelve una lista aplicando func a cada elemento.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>reduce (func, lista, (primero))</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Devuelve un valor aplicando la operación binaria func.</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>filter (pred, lista)</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Devuelve una lista filtrando con el predicado.</td>
  </tr>
  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>Ejemplo</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">lista = [2,4,6,8]
    
print(list(map(lambda x:x*2,lista)))</td>
  </tr>
</table>

para reduce hay que meter:

import functools
lista=\[2,4,6,8]
print(functools.reduce(lambda x,y:x+y, lista)) 

que nos dara 20, 2+4 = 6 + 6 = 12 + 8 = 20

Ejemplo para filter:

def positivos(numeros):

	return list(filter(lambda n:n>=0, numeros))

print positivos(\[2,3,-4,5,6]))


# FICHEROS

## Condiciones importantes a conocer

### Abrir el fichero

f = open('nombre del archivo', 'modo')
	operacion
f = close()

desde la version 2.5 podemos usar WITH acompañado de open para olvidarnos de cerrarlo ya que SE CIERRA AUTOMATICAMENTE

with open('archivo', 'modo') as f
	operacion

#### Modos de apertura

R -> Solo lectura
W-> Solo escritura si existe ese fichero
	wb -> escribirlo en formato binario
A ->Modo escritura, si existe el fichero lo añade al final
R+ -> Lectura y Escritura
Añade + para que haga las dos cosas

<table style="
    border-collapse: collapse;
    width: 100%;
    border: 1px solid var(--background-modifier-border);
    border-radius: 8px;
    overflow: hidden;
    text-align: center;
    margin: 0 auto;
  ">
  
  <!-- Fila superior -->
  <tr>
    <td colspan="2" style="
        border:1px solid #000;
        height:40px;
        font-weight:bold;
        text-align:center;
        vertical-align:middle;
        background-color: var(--background-secondary-alt);
        color: var(--text-normal);
      ">
      <b>Atributos de ficheros de texto</b>
    </td>
  </tr>

  <!-- Filas adaptadas EXACTAMENTE a tus imágenes -->
  <tr>
    <td style="width:20%; border:1px solid #000; height:40px; vertical-align:middle;"><b>archivo.closed</b></td>
    <td style="width:80%; border:1px solid #000; height:40px; vertical-align:middle;">Devuelve true su esta cerrado y falso si no</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>archivo.mode</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Devuelve el modo de acceso con el que se abrió el archivo</td>
  </tr>

  <tr>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;"><b>archivo.name</b></td>
    <td style="border:1px solid #000; height:40px; vertical-align:middle;">Devuelve el nombre del archivo</td>
  </tr>
</table>

fo = open("codehero.txt", "wb")
print ("Nombre: ", fo.name)
print ("Cerrado: ", fo.closed)
print ("Modo: ", fo.mode)

## OPERACIONES

### Lectura

fichero.read(): Leera todo el contenido del fichero

fichero.read(num_bytes): Leera un numero de bytes concretos, por ejemplo, fichero.read(100)

fichero.readLines(): Devuelve la siguiente linea, si se vuelve a llamar, devolvera la siguiente linea y asi sucesivamente

### Seek or Tell

que pasa si hago readlines pero quiero ir al principio, final, o punto intermedio especifico

Seek(byte): mueve el puntero al byte indicado

Tell():retorna la posicion actual del puntero

Ejemplo:

archivo = open("a.txt", "r")
linea1 = archivo.readline()
print linea1
mas = archivo.tell()
print (mas)
print (archivo.readline(mas))

### Escritura

write(cadena): escribe toda la cadena dento del archivo

writelines(secuencia): De manera iterable, sin ir solo, escribe los elementos uno por linea, listas tuplas

# ORIENTACIÓN A OBJETOS

<u>float y enteros</u> son **LOS UNICOS que NO SON OBJETOS**

Clases

class nombre(object): lo del paréntesis es opcional para indicar que hereda de una clase superior, en este caso object

## métodos mágicos

tienen doble guion bajo

def \_\_init\_\_(self, ...): Es el constructor de la case, donde establecemos los valores iniciales

def \_\_str\_\_(self): Método especial para mostrar por pantalla los valores de mis atributos

SIEMPRE tienen que venir con self, que es como el this, en cualquier método de la clase

**Ejemplo:**
class Studen():
	name="Albert"
	age = "20"
	def \_\_str\_\_(self):
		print("mi nombre" + self.name)

student = Student()

otros metodos:

\_\_getattr\_\_: getter
\_\_setattr\_\_: setter
\_\_delattr\_\_: Eliminar atributo

![[{FE959FFC-A7F1-437D-905E-1B0C403DADB4}.png]]

# HERENCIA

SIMPLE

class ClaseDerivada(clasebase):
	declaracion1
	declaracion2
	...

MULTIPLE

class ClaseDerivada(Base1, Base2, Base3)

![[{7B7C6D66-0D19-47B9-9E05-2A141ACB89D2}.png]]