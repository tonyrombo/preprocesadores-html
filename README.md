#Preprocesadores-html
Investigacion sobre el preprocesador JADE. Por Laura Gonzales, Josué Solís y Antony Romero.

¿Que es JADE?

Es un motor de plantillas de alto rendimiento muy influenciado por HAML, ha sido implementado con javascript principalmente para trabajar con nodeJS.
Adicionalmente es un preprocesador de código HTML.

Pre-Requisitos

Node JS (http://nodejs.org)
NPM (https://npmjs.org)
Express JS [opcional] (https://expressjs.com)

Algunas Ventajas

Sangrías - Jade utiliza sangrias en vez de texto para indicar donde empiezan los elementos y los bloques de código.
Evita Bugs - Si nuestro código tiene errores de indentado o de algún otro tipo, JADE nos mostrará una lista de errores encontrados y no generará ningún documento HTML hasta que se hayan resuelto. Con esto se evitan muchos errores de HTML, como los cierres de etiquetas y otros errores comunes que siempre vemos en el desarrollo de HTML.
Código Limpio - Da como resultado plantillas m/eas limpias.


Comentarios en JADE

//Comentario de una línea.

//-Comentario de una línea invisible

//comentario
en bloque
h1Hola
h2Mundo

//comentario
en bloque invisible.
h1título
h2subtítulo

Doctype

doctype
doctype html
doctype transitional
doctype strict
doctype basic

Anidamiento

ul
  li
    a(href="#")uno
  li
    a(href="#")dos
  li
    a(href="#")tres


Anidamiento con expansión de bloque

ul
  li:a(href="#")uno
  li:a(href="#")dos
  li:a(href="#")tres
  
Id's y Clases

h1#title
div.content
form(action="post/new", name=frmNew, method="post")
  input#txtNombre(type="text" placeholder="Nombre")
  input(id="txtEmail" type="email" placeholder="Email")
  button.btn(type="submit")Enviar
  button(class="send" type="reset")Reset
  
Variables

//declaración de variables
- titulo = "Paso 3"
- yo = {}
- yo.nombre = "Daniel"
- yo.apellido = "Fallas"
- yo.edad = 35
- booleano = false
- ruc = "Ruc"
- Boleta = "Boleta"

//markup
h1= titulo
h2= "Sr" + yo.nombre + " " + to.apellido
h3 Tiene + #{yo.edad} años de edad
h4= "Su nombre es de " + yo.nombre.edad + "letras!"
h5= Y ud eligió: #{booleano ? ruc : boleta}

//Declarando variables con JS puro
- name = "Jorge Sanchez"
- bodyClasses = ["user", "aunteticated"]

//markup
body(class="bodyClasses")
  input(type="text", value="Hello #{name}")
  input(checked=true, disable=false)
  input(
    type="checkbox",
    name="agreement",
    checked
  )
  
Texto

p Esto es texto de una línea

p
  |Esto es
  |texto
  |multilínea
  
p.
  Esto también
  es texto
  multilínea
  
Escaping

//declaración de variable
- saludo = "hola <em>Mundo</em>"

//markup
ul
  li Hola <em>mundo</em>
  li = saludo
  li != saludo
  li #{saludo}
  li !{saludo}

p \#{Escapando estos símbolos}

Mejores Características

IF
//declaracion de variable
- auntenticado = true

//condicional IF
if autenticado == true
  h1 Bienvenido : Charles
else
  h1 Bienvenido : Visitante
  
UNLESS
//declaracion de variable
- hasErrors = false

//condicional Unless
unless hasErrors
  p.yellow No se encontraron errores.
  
FOR
//declaracion de variable
- peliculas = ['Avengers', 'UP', 'The Hobbit']

//markup
ul
  for pelicula in peliculas
    li=pelicula
  else
    li no tenemos peliculas :(
  
  ul#vocales
    for letra in ['a', 'b', 'c', 'd', 'e']
      li = letra

EACH
//declaracion de variable
- estaciones = ['invierno', 'otoño', 'verano', 'primavera']

//markup
select(name="estaciones")
  option(value="")Seleccione una estación
  each estacion, i in estaciones
    option(value=i) Estación #{estacion}

CASE
//declaracion de variable
-seccion = "nosotros"

//markup
case seccion
  when "home"
    div (class="home")
  when "nosotros"
    div (class = "nosotros")
  default
    div (class="default")

MIXINS
//declaramos un array
-users = {}
-users.push = ({nombre: "Jorge", email:"jorge.sanchez@gmail.com"})
-users.push = ({nombre: "Mario", email:"mario.gomez@gmail.com"})

//declaramos el mixin
mixin fila(nombre, email)
  li #{nombre} (#{email})

//markup
ul.users
  for user in users
    +fila(users.nombre, user.email)

CODE
//declaramos las variables
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
  p lorem ipsum dolor...

INCLUDE
//layout.jade
