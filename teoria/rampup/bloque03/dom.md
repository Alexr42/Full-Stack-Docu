![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png  "logotipo de The Bridge")


# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)

### HTML, CSS,  JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

#  DOM 


# **Tema 4** -  DOM, eventos, nodos y navegación

## ¿Qué es el DOM de HTML y para qué sirve? 
***
El DOM nos permite manipular elementos de HTML. Es un estándar que utilizamos para acceder a los documentos que se han creado en HTML. Al cargarse la página se crea lo que llamamos DOM (Document Object Model), que es un árbol de Objetos los cuales son los distintos elementos (o etiquetas) que nosotros hemos creado o estamos creando al manipular el DOM, es decir, todos los elementos en HTML son objetos. 

La manipulación del DOM es útil para cambiar estilos, añadir nuevos elementos, eventos... Gracias a que el HTML se crea a partir de este estándar (DOM), podemos manejarlo con javascript y por lo tanto utilizar propiedades, métodos y eventos para trabajar con él. 

Veamos a continuación cómo se vería representado un árbol DOM al cargarse. 

#### ¿Cómo se vería representado?

![img](https://www.w3schools.com/js/pic_htmltree.gif)


## Métodos y propiedades del DOM
***
Los métodos del DOM son las funciones que harán que podamos manipular el DOM, es decir, los elementos que hay en HTML y las propiedades son los valores de los elementos de HTML que se pueden modificar. Existen distintos métodos que veremos a continuación. 

Los métodos los aplicaremos al objeto Document, que como vimos anteriormente, es a partir de donde se crea el árbol DOM. Aplicando métodos al Objeto desde donde se construye el arbol, podremos acceder a todas sus propiedades y elementos. 

## Acceder a elementos del DOM

**Acceder por id:**

document.getElementByID('id') -> devuelve un elemento único
```js
const caja1=document.getElementById('caja1');

caja1.style.color='red';
caja1.style.fontSize='3rem';
```
	
**Acceder por su clase**
	
document.getElementsByClassName('clase') -> HTMLCollection (objeto)

```js
const rojos=document.getElementsByClassName('rojo');

for(let rojo of rojos){
	console.log(rojo)
	rojo.style.background='red';
}
```

**Acceder por su etiqueta**

document.getElementsByTagName('etiqueta') -> HTMLCollection (objeto)

```js
const divs=document.getElementsByTagName('div');

for(let caja of divs){
	console.log(caja)
	caja.style.border='1px solid black';
}


```


**ACCEDER POR UN SELECTOR VÁLIDO**

document.querySelector('selectorValido') -> devuelve el primer elemento que tenga coincidencia con el selector

```js
const caja2=document.querySelector('#caja2');
	
caja2.style.fontFamily='verdana';
```

document.querySelectorAll('selectorValido') -> devuelve NodeList (un conjunto) (array);

```js
const verdes=document.querySelectorAll('.verde');

for(let caja of verdes){
	console.log(caja)
	caja.style.background='green';
	caja.style.color='white';
}
```

## Modificar elementos del DOM
	
**Métodos**

elemento.getAttribute('attributo') -> accede al valor de un atributo

```js
const caja1=document.getElementById('caja1');

console.log(caja1.getAttribute('data-color'));
```

elemento.setAttribute('attributo','valor') -> si el elemento tiene ese atributo cambiamos su valor,si no lo tiene se asigna atributo y valor

```js
const caja1=document.getElementById('caja1');
caja1.setAttribute('data-color','azul');
caja1.setAttribute('data-forma','redondo');
```

elemento.removeAttribute('atributo') ->Elimina el atributo
```js
const caja1=document.getElementById('caja1');
caja1.removeAttribute('class');
```	

**Atributos directos**

.id
.style
.value

.checked
.selected

.required

.dataset -> contiene una coleccion de data-atributes.

.innerHTML ->contiene el código html de un elemento del DOM
.textContent ->contiene el texto de un elemento del DOM

```js
caja1.style.color='blue';

console.log(caja1.dataset)

caja1.dataset.forma='cuadrado';

console.log(caja1.innerHTML);
console.log(caja1.textContent);

// caja1.innerHTML='<p>otro contenido</p>';
caja1.textContent='<p>otro contenido</p>';
```

## Trabajo con clases

**Añadir clases** 

```javascript
caja.classList.add('borde');
```
**Eliminar clases** 

```javascript
caja.classList.remove('rojo');
```
**Saber si un elemento contiene una clase**
```javascript
console.log(caja.classList.contains('cosa'));
```

**Reemplazar clases**

```javascript
 caja.classList.replace(claseVieja,claseNueva)
```
**Alternar una clase**
Si el elemento tiene la clase se la quita y si no la tiene se la pone
```javascript
caja.classList.toggle('nombreClase');
```

## Crear
**Crea un element node**
```javascript
 document.createElement(nombreEtiqueta)
```

**Crea un fragment**
Crea una colección de elementos html
```javascript
document.createDocumentFragment()
```

## Insertar nodos

**Añade al final del elemento de referencia, puede añadir texto y elementos html**
```javascript
referencia.append('elemento') 
```
**Añade al final del elemento de referencia, sólo añade elementos html**
```javascript
referencia.appendChild('elemento')
```

**Añade al principio del elemento de referencia, puede añadir texto y elementos html**
```javascript
referencia.prepend('elemento') 
```

**Añade como heramano siguiente del elemento de referencia, puede añadir texto y elementos html**
```javascript
referencia.after('elemento') 
```

**Añade al principio del elemento de referencia, puede añadir texto y elementos html**
```javascript
referencia.before('elemento') 
```

## Clonar nodos
**cloneNode()**

```javascript
//capturar el elemento del DOM que queramos clonar
let paraClonar=document.querySelector('.paraClonar');
//crear Clone
let clon=paraClonar.cloneNode(true);
//añadir el clon al DOM
paraClonar.after(clon)
```


##Eliminar nodos

**remove elimina el elemento**
```javascript
nombreElemento.remove();
```
**Elimina un hijo del elemento**

```javascript
nombreElemento.removeChild(nombreElemento.children[0])
```

**Vaciar un elemento del dom la forma mas sencilla**
```javascript
nombreElemento.innerHTML='';
```


#### Recursos
- [DOM HTML](https://www.w3schools.com/js/js_htmldom.asp)
- [Métodos HTML](https://www.w3schools.com/js/js_htmldom_methods.asp)
- [DOM - Document](https://www.w3schools.com/js/js_htmldom_document.asp)
- [DOM - Element](https://www.w3schools.com/js/js_htmldom_elements.asp)
- [DOM - HTML](https://www.w3schools.com/js/js_htmldom_html.asp)
- [DOM- HTML](http://www.codexexempla.org/curso/curso_4_3_d.php)

