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
