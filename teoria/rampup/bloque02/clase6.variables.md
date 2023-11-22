![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png  "logotipo de The Bridge")


# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)

### HTML, CSS,  JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

#Tema 6 - Variables (propiedades personalizadas)
En CSS, las propiedades personalizadas (también conocidas como variables) son entidades definidas por autores de CSS que contienen valores específicos que se pueden volver a utilizar en un documento. Se establecen mediante la notación de propiedades personalizadas (por ejemplo, --main-color: black;) y se acceden mediante la función var() (por ejemplo, color: var (--main-color);).

## Uso básico
Una buena práctica común es declarar variables en la pseudo-clase :root, y así aplicarlas globalmente al documento HTML

```css
:root {
  --main-bg-color: brown;
}
```

Para acceder al valor de una propiedad personalizada usamos el nombre de la propiedad dentro de la función var()

```css
elemento {
  background-color: var(--main-bg-color);
}

```


## Herencia de propiedades personalizadas
Las propiedades personalizadas heredan. Lo que significa que si no se establece ningún valor para una propiedad personalizada en un elemento dado, se utiliza el valor de su elemento padre. 

```html
<div class="uno">
  <div class="dos">
    <div class="tres"></div>
    <div class="cuatro"></div>
  </div>
</div>

```

```css
.dos {
  --test: 10px;
}

.tres {
  --test: 2em;
}

```

Vemos el resultado del ejemplo anterior:
- Para el elemento class="dos": 10px
- Para el elemento class="tres": 2em
- Para el elemento class="cuatro": 10px (heredado de su padre)

## Valores de sustitución de propiedades personalizadas
Utilizando var() podemos definir múltiples valores de sustitución (fallback) que se usarán cuando la variable dada no está definida aún.

La función var() sólo acepta dos parámetros, el primero es el valor a sustituir y el segundo, el valor de reserva

```
.dos {
  color: var(--my-var, red); /* Rojo (red) si --my-var no esta definida */
}

.tres {
  background-color: var(--my-var, var(--my-background, pink)); /* Rosa (pink) si my-var y --my-background no están definidas */
}

.tres {
  background-color: var(--my-var, --my-background, pink); /* Invalido: "--background, pink" */
}

```

[Variables en CSS](https://developer.mozilla.org/es/docs/Web/CSS/Using_CSS_custom_properties)
