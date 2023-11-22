![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png  "logotipo de The Bridge")


# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)

### HTML, CSS,  JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

# Tema 5 - Eventos

¿Para qué puede ser útil tener tantos selectores que hagan acciones? Son útiles cuando los utilizamos con los eventos. Los eventos se producen cuando ocurre una acción,(como por ejemplo hacer click o pasar el ratón por encima) no todos los eventos los desencadena el usuario (como por ejemplo cuando fineliza un video). 

 Existen muchos tipos de eventos, el cual escogeremos según la necesidad que tengamos. 

Aquí tienes una lista de todos los eventos que existen en el DOM: https://www.w3schools.com/jsref/dom_obj_event.asp. Como ves hay una gran variedad, aunque existen algunos más comunes:

- **click**: este evento se produce cuando el usuario pulsa sobre algún elemento.
- **change**: este evento ocurre cuando el contenido que hay dentro de un input cambia. 
- **mousedown**: este evento se produce cuando el usuario está presionando con el puntero el elemento al que hemos asociado este evento. 
- **mouseenter**: el evento ocurre cuando el ratón del usuario pasa por encima del elemento al que hemos asociado el evento. 
- **mouseleave**: el evento se produce cuando el usuario que había pasado el ratón por encima del elemento, deja de hacerlo. 
- **mouseover**: este evento tiene el mismo comportamiento que mouseenter, a diferencia de que tiene también en cuenta a sus hijos para esa acción. 
- **mouseout**: este evento tiene el mismo comportamiento que mouseleave, a diferencia de que tiene también en cuenta a sus hijos para esa acción. 
- **mouseUp**: este evento se produce cuando el usuario deja de pulsar el elemento al que hemos asociado el evento. Si volviéramos a presionar sobre él, el evento ya no se produciría hasta que de nuevo, se dejara de presionar el elemento.  
- **scroll**: el evento se produce cuando el usuario baja la barra de navegación. 
- **submit**: este evento se produce cuando el usuario envía un formulario, pulsando el botón de typo submit. 

Debemos tener en cuenta algo muy importante, y es que en el caso de que añadamos los eventos directamente como atributo a la etiqueta en html, los eventos llevarán asociado un prefijo: on. En el caso de que lo hagamos con javascript, no utilizaremos ese prefijo.

Para añadir un evento a un elemento por javascript existe el método addEventListener(), el cual es capaz de controlar si ese evento se produce. Es lo que llamaríamos un detector o escuchador de eventos, que está esperando a que la acción se produzca para ejecutar la acción que nosotros le indicamos. 

## Sintaxis

```html
    <div id='boton'>Elemento</div>
```


```javascript
   const boton=document.querySelector('#boton')
   boton.addEventListener('click',mostrarMensaje);


	function mostrarMensaje(){
		console.log('este es el mensaje');
	}
```
**Pasando argumentos a la función**
```javascript
  boton.addEventListener('click',()=>{
		mostrarMensaje('mensaje desde el evento')
	});


	function mostrarMensaje(mensaje){
		console.log(mensaje);
    }
```

**Con función anónima**
```javascript
boton.addEventListener('click',()=>{
    console.log('este es el mensaje');
})
```

## Algunos eventos


### Eventos del objeto windows

```javascript
    //La función se ejecuta cuando windows está cargado

window.addEventListener('load',()=>{

  const boton=document.querySelector('#boton');
  boton.style.background='red';

})

```

### Eventos del objeto document

```javascript
    //La función se ejecuta cuando todo en dom está cargado

document.addEventListener('DOMContentLoaded',(event)=>{
	const boton=document.querySelector('#boton');
	boton.style.background='red';

})

```

### Eventos de ratón

- click		-> click;
- dblclick	-> doble click;
- mouseenter	-> Cuando se entra en el área del objeto de referencia;
- mouseleave	-> Cuando se sale del área del objeto de referencia;
- mouseup		-> Cuando se suelta el ratón;
- mousedown	-> Cuando se presiona el ratón;
- mousemove	-> Cuando el ratón se mueve dentro del área del elemento de referencia;

```javascript

const caja=document.querySelector('#caja');

caja.addEventListener('click',()=>{
	console.log('se dispara el evento')
})

```

### Eventos de teclado

- keyup		-> cuando se suelta una tecla;
- keydown		-> cuando se presiona una tecla;
```javascript

const body=document.querySelector('body');

document.addEventListener('keyup',(ev)=>{
	console.log(ev)

	if(ev.keyCode==87){
		body.style.background='red';
	}else if(ev.keyCode==68){
		body.style.background='green';
	}else if(ev.keyCode==88){
		body.style.background='blue';
	}else if(ev.keyCode==65){
		body.style.background='yellow';
	}else{
		body.style.background='white';
	}
})

```

### Eventos de inputs

- focus		-> cuando activamos el input
- blur		-> cuando desactivamos el input
- copy		-> cuando se hace una copia
- cut			-> cuando se corta
- paste		-> cuando se pega
- input 		-> consjunto de casi todos los eventos de input

```javascript
const campo=document.querySelector('#campo');
const parrafo=document.querySelector('#parrafo');


campo.addEventListener('paste',(ev)=>{
	onsole.log(ev)
    console.log(' se dispara el evento')
})

parrafo.addEventListener('cut',(ev)=>{
	console.log(ev)
	console.log(' Se ha cortado')
})


```
**Validación en línea**

```javascript

campo.addEventListener('input',(ev)=>{

	console.log(ev);
	console.log(ev.target.type);
	console.log(ev.target.value);

	if(ev.target.value=='main'){
		ev.target.style.color='green';
		console.log('Correcto')
	}else{
		ev.target.style.color='red';
		console.log('Incorrecto')
	}
})

```

### Delegación de eventos
Consiste en poner a un ancestro a la escucha del evento

```html
<div id="padre"></div>
```

```javascript

const padre=document.querySelector('#padre');

document.addEventListener('click',(ev)=>{

	if(ev.target.id=='hijo1'){
		console.log(ev.target)
	}

	/*if(ev.target.classList.contains('verde')){
		console.log(ev.target)
		console.log('sobre verde')
	}*/

	if (ev.target.matches('.verde')){
		console.log(ev.target)
		console.log('sobre verde')
	}

})

//Creamos de forma dinámica los elementos hijos
function crearElementos(){
padre.innerHTML=`<div id="hijo1">hijo 1</div>
		<div id="hijo2">hijo 2</div>
		<div id="hijo3" class='verde'>hijo 3</div>
		<div id="hijo4">hijo 4</div>
		<div id="hijo5" class='verde'>hijo 5</div>`
}

crearElementos();
```

- [Más Información Eventos](https://developer.mozilla.org/es/docs/Web/Events)
- [DOM - Events](https://www.w3schools.com/js/js_htmldom_events.asp)
- [DOM - addEventListener](https://www.w3schools.com/js/js_htmldom_eventlistener.asp)
