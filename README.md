# Phantomjs
es un navegador sin interfaz grafica
### instrucciones 
1.descargar el archivo
2.agregarlo en las variables de entorno 
3.ejecutar comandos usando el prefijo phantomjs


Para comenzar instaciamos una variable que requiera **webpage** y ejecute el metodo **create();**

~~~javascript
var page = require('webpage').create(); ç
~~~

luego ejecutamos el metodo **page.open**, que recibe dos parametros, el primero es la url que queremos abrir y el segundo es una funcion anonima.  
~~~javascript
page.open(url,funccion) 
~~~
###### ejemplo.


~~~javascript
var page = require('webpage').create(); 
page.open('http://www.google.com', function(){
	console.log("se ha cargado la pagina")
})
~~~

para acceder a los agumentos del script hay que requerir el modulo **'system'**  
~~~javascript 
var system = require('system') 
~~~
###### ejemplo.

~~~javascript
var page = require('webpage').create();
var system = require('system');
page.open(system.arg[1], function(status){
	page.render('google.png');
	phantom.exit();
})

~~~
el metodo **page.render** hace una captura de pantalla de la pagina, toma como argumento el nombre de la imagen con la que queremos gardar la catura.  
~~~javascript
 page.render('nombre.extencion '); 
 ~~~
###### ejemplo.
~~~javascript
page.render('google.png');
~~~

el metodo **page.evaluate** se usa para ejecutar codigo javascript dentro del navegador y recibe una funcion anonima, que se encargara de realizar cada unas de la instrccione que estan dentro del ella.  
~~~javascript 
page.evaluate(function(){
// codigo ..
})
~~~
###### ejemplo.
~~~javascript
var page = require ('webpage').create();
var system = require ('system');
page.open(system.args[1], function(status){
	var titulo = page.evaluate(function(){
		return document.title;
});
console.log(titulo);
phantom.exit();
})
~~~
**page.includesJs** se utiliza para incluir algun script js, recice como parametros la url de donde se encuentra alojado el archivo y una funcion .  
~~~javascript 
page.includeJs('url', funcion) 
~~~
###### ejemplo.
~~~javascript 
page.includesJs('http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js', function(){
// codigo 
});
~~~
**page.onLoadFinished** es un metodo que se iguala a una funcion que se ejecutara cuando la pagina haya cargado.  
~~~javascript 
page.onLoadFinished = funcion; 
~~~
###### ejemplo.
~~~javascript
vpage.onLoadFinished  = function(){
	console.log("ha terminado de cargar la pagina");
	page.render('otrabusquedaenamazon.png')
}
page
~~~
### Resumen
**requires**  
var page = requiere('webpage').create();
var system = require('system'); 

**metodos de system**  
1. system.args: array con los argumentos


**metodos page** 
1. page.open: abre una pagina web.
2. page.render toma una captura de pantalla.
3. page.evaluate ejecuta javascript dentro de la pagina.
4. page.includesJs incluye archivos javacript dentro del documento.
5. page.onLoadFinished una funcion que se ejecuta al cargar la pagina.


para aprender mas sobre phantomjs viitar el siguiente video  https://www.youtube.com/watch?v=_IKh1IvIjZo&t=340s codalot phantomjs

