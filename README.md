###Preprocesadores-html
Investigacion sobre el preprocesador JADE. Por Laura Gonzales, Josué Solís y Antony Romero.
# Prepocesador JADE

Jade es el motor de plantillas implementado por JavaScript para node.js, y es un pre-procesador de código HTML, lo que nos permite escribir HTML de manera muy sencilla con una sintaxis muy simple.

Algunos requisitos:
*   node.js
*   Npm

Dentro de los beneficios que nos brinda Jade estan:
* Usa identación de sangría
* Nos muestra lista de errores y no genera código html hasta que esten corregidos
* Un código más limpio
* No hay que escribir tags html  </>
    * Por ejemplo solo debemos escribir la etiquete sin los <>: 
        * p Esto sale en un párrafo 

* Podemos crear variables agregando " - " delante del nombre.
* Además podemos crear arrays u objetos.
    * Escribiendolos de la siguiente forma:
        *   -array = ['perro', 'gato', 'gallina']
        *   -myObject = {nombre:'chocolate', tipo='salchicha', preferencia:'gallina'}
    * Y para utilizarlos es:
        * h1 #{array[1]}
        * h3 #{myObject.nombre}
        
* Usar funciones
* Fácil anidación

### Variables
*   Estas se esciben de la siguiente manera:
           -myVariable = 'probando'
           -readMore = 'read more'
* Y para llamarlas lo escribimos de esta forma:
        * a(href='#') #{readMore}
        * h1 #{myVariable}

#### Objetos
* Escribiendolos de la siguiente forma:
    * -array = ['perro', 'gato', 'gallina']
    *  -myObject = {nombre:'chocolate', tipo='salchicha', preferencia:'gallina'}
* Y para utilizarlos es:
    * h1 #{array[1]}
    * h3 #{myObject.nombre}


###Texto

<pre>p Esto es texto de una línea

p
  |Esto es
  |texto
  |multilínea
  
p.
  Esto también
  es texto
  multilínea</pre>
  
<pre>
	<p>texto en una sola linea</p>
</pre>

<pre><p>
	este texto
	sera
	multilinea
</p></pre>

<p>
	este texto
	tambien es
	multilinea!
</p>


###Escaping

<pre>//declaración de variable
- saludo = "hola <em>Mundo</em>"

//markup
ul
  li Hola <em>mundo</em>
  li = saludo
  li != saludo
  li #{saludo}
  li !{saludo}

p \#{Escapando estos símbolos}</pre>

###Mejores Características

###IF
<pre>//declaracion de variable
- auntenticado = true

//condicional IF
if autenticado == true
  h1 Bienvenido : Charles
else
  h1 Bienvenido : Visitante</pre>
  
###UNLESS
<pre>//declaracion de variable
- hasErrors = false

//condicional Unless
unless hasErrors
  p.yellow No se encontraron errores.</pre>
  
###FOR
<pre>//declaracion de variable
- peliculas = ['Avengers', 'UP', 'The Hobbit']

//markup
ul
  for pelicula in peliculas
    li=pelicula
  else
    li no tenemos peliculas :(
  
  ul#vocales
    for letra in ['a', 'b', 'c', 'd', 'e']
      li = letra</pre>

###EACH
<pre>//declaracion de variable
- estaciones = ['invierno', 'otoño', 'verano', 'primavera']

//markup
select(name="estaciones")
  option(value="")Seleccione una estación
  each estacion, i in estaciones
    option(value=i) Estación #{estacion}</pre>

###CASE
<pre>//declaracion de variable
-seccion = "nosotros"

//markup
case seccion
  when "home"
    div (class="home")
  when "nosotros"
    div (class = "nosotros")
  default
    div (class="default")</pre>

###MIXINS
<pre>//declaramos un array
-users = {}
-users.push = ({nombre: "Jorge", email:"jorge.sanchez@gmail.com"})
-users.push = ({nombre: "Mario", email:"mario.gomez@gmail.com"})

//declaramos el mixin
mixin fila(nombre, email)
  li #{nombre} (#{email})

//markup
ul.users
  for user in users
    +fila(users.nombre, user.email)</pre>

###CODE
<pre>//declaramos las variables
-page = {}
-page.title = "Titulo de la página"
-page.description = "Descripción de la página"

//markup
doctype html
html (lang = "es")
head
  title = page.title
  - if (page.description){
  meta(name="descripción" content="#{page.description}")
  -}
body
  p lorem ipsum dolor...</pre>


##### Referencias
* http://jade-lang.com/
* http://frontendlabs.io/70--jade-language-node-template-engine-and-html-preprocessor
* https://speakerdeck.com/player/f0a8cbd01dce0131047b4ece5468c54b#
* http://learn.shayhowe.com/advanced-html-css/preprocessors/
