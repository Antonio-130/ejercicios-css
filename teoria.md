> Copia de `02-css/README.md` del repo **UTN-programacion3**, que es la única fuente de verdad. No edites este archivo: cualquier cambio se hace en el repo de la UTN y se vuelve a copiar acá.

## Apuntes de CSS

### 1. Definición

CSS (Cascading Style Sheets) es el lenguaje utilizado para definir la apariencia y el diseño de un documento HTML. Permite aplicar estilos a los elementos mediante reglas de estilo.

#### 1.1

```css
selector {
  propiedad: valor;
}
```

### 2. Formas de Aplicar CSS

Existen tres formas de aplicar CSS en un documento HTML:

#### 2.1 CSS en Línea

Se usa el atributo `style` dentro de una etiqueta HTML.

```html
<p style="color: blue; font-size: 20px;">Texto en azul y tamaño 20px.</p>
```

#### 2.2 CSS Interno

Se usa dentro de la etiqueta `<style>` en el `<head>` del documento HTML.

```html
<style>
  p {
    color: blue;
    font-size: 20px;
  }
</style>
```

#### 2.3 CSS Externo

Se enlaza un archivo `.css` con la etiqueta `<link>` en el `<head>` del documento HTML.

```html
<link rel="stylesheet" href="styles.css" />
```

En `styles.css`:

```css
p {
  color: blue;
  font-size: 20px;
}
```

### 3. Selectores en CSS

**‼️La especificidad en CSS es un sistema de jerarquía que determina qué reglas de estilo tienen prioridad sobre otras cuando se aplican múltiples reglas a un mismo elemento.**

#### Cálculo de especificidad:

- **Selectores de tipo y pseudoelementos (`h1`, `p`, `::before`)**: 1 punto
- **Selectores de clase, atributos y pseudoclases (`.clase`, `[atributo]`, `:hover`)**: 10 puntos
- **Selectores de ID (`#id`)**: 100 puntos
- **Estilos en línea (`style="color: red;"`)**: 1000 puntos

Ejemplo de especificidad:

```html
<h1 class="clase-titulo" id="id-titulo">Hola soy un re título</h1>
```

```css
h1 {
  color: blue;
} /* 1 punto */
.clase-titulo {
  color: green;
} /* 10 puntos */
#id-titulo {
  color: red;
} /* 100 puntos */
```

**El color final será rojo, ya que el selector de ID tiene mayor especificidad.**

#### Selector universal `*`

- selecciona todos los elementos de un documento HTML
- su nivel de especificidad es el mas bajo de todos.

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

#### 3.1 Selector de Etiqueta

Selecciona todos los elementos que tegan la etiqueta `<h1>`

```css
h1 {
  color: red;
}
```

#### 3.2 Selector de Clase

Se usa `.` antes del nombre de la clase. Selecciona todos los elementos que tengan ese mismo nombre de clase

```css
.destacado {
  font-weight: bold;
}
```

```html
<p class="destacado">Este texto ahora está en negrita.</p>
```

#### 3.3 Selector de ID

Se usa `#` antes del nombre del ID. Es un selector único, solo se puede usar en 1 solo elemento de un archivo html

```css
#titulo {
  text-align: center;
}
```

```html
<h1 id="titulo">Un re título</h1>
```

#### 3.4 Selectores Agrupados

Permiten aplicar los mismos estilos a varios elementos.

```css
h1,
p {
  color: green;
}
```

#### 3.5 Selectores Anidados

Seleccionan elementos dentro de otros elementos.

```css
div p {
  color: blue;
}
```

### 4. Propiedades Básicas

#### 4.1 Color de Texto y Fondo

```css
p {
  color: white;
  background-color: black;
}
```

#### 4.2 Tamaño y Tipo de Fuente

```css
p {
  font-size: 16px;
  font-family: System-ui, sans-serif;
}
```

#### 4.3 Alineación de Texto

```css
h1 {
  text-align: center;
}
```

### 4.4 Margin y Padding

#### Hay 3 formas diferentes de usar `margin` y `padding`:

**1. Propiedades individuales:**

```css
margin-top: 10px;
margin-right: 20px;
margin-bottom: 30px;
margin-left: 40px;
```

```css
padding-top: 10px;
padding-right: 20px;
padding-bottom: 30px;
padding-left: 40px;
```

**2. Margen/Padding en dos direcciones:**

```css
margin: 10px 20px; /* Arriba/Abajo 10px, Izquierda/Derecha 20px */
```

```css
padding: 10px 20px; /* Arriba/Abajo 10px, Izquierda/Derecha 20px */
```

**3. Margen/Padding con shorthand:**

```css
margin: 10px 20px 30px 40px; /* Arriba 10px, Derecha 20px, Abajo 30px, Izquierda 40px */
```

```css
padding: 10px 20px 30px 40px;
```

#### 4.5 Bordes

Los bordes en CSS permiten definir el contorno de un elemento. Se pueden personalizar en grosor, estilo y color.

**Ejemplo básico shorthand:**

```css
div {
  border: 2px solid red;
}
```

**Donde `border` es una propiedad que recibe 3 parámetros => ancho - tipo - color**

**Propiedades individuales:**

```css
div {
  border-width: 2px; /* Ancho del borde */
  border-style: solid; /* Tipo del borde */
  border-color: red; /* Color del borde */
}
```

**Tipos de bordes disponibles:**

```css
border-style: solid; /* Línea sólida */
border-style: dashed; /* Línea punteada */
border-style: dotted; /* Línea de puntos */
border-style: double; /* Doble línea */
border-style: groove; /* Apariencia de tallado */
border-style: ridge; /* Apariencia de relieve */
border-style: inset; /* Apariencia de hundido */
border-style: outset; /* Apariencia de elevado */
```

**Bordes en lados específicos:**

```css
div {
  border-top: 2px solid blue;
  border-right: 3px dashed green;
  border-bottom: 4px double orange;
  border-left: 5px dotted purple;
}
```

**Bordes redondeados:**

```css
div {
  border-radius: 10px; /* Bordes redondeados */
}
```

**Bordes con diferentes radios en cada esquina:**

```css
div {
  border-top-left-radius: 5px;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 15px;
  border-bottom-left-radius: 20px;
}
```

#### 4.6 Sombras de caja

```css
div {
  box-shadow: 4px 4px 10px rgba(255, 255, 255, 0.5);
}
```

##### Los valores que toma son los siguientes:

1. desplazamiento horizontal (x) de la sombra (con valores positivos se mueve a la derecha y con negativos a la izquierda)
2. desplazamiento vertical (y) de la sombra (con valores positivos se mueve hacia abajo y con negativos hacia arriba)
3. difuminado de la sombra (blur)
4. color de la sombra

#### 4.6 Ancho y Alto

Las propiedades `width` y `height` permiten definir el tamaño de un elemento.

**Ejemplo básico:**

```css
div {
  width: 200px;
  height: 100px;
}
```

**Unidades de medida:**

- `px` (píxeles)
- `%` (porcentaje respecto al elemento contenedor)
- `em` (relativo al tamaño de fuente del elemento padre)
- `rem` (equivale al tamaño de fuente del elemento raíz (html)).
- `vw` (porcentaje del ancho de la ventana del navegador)
- `vh` (porcentaje del alto de la ventana del navegador)
- `auto` (ajusta automáticamente el tamaño según el contenido)

**Ejemplos:**

```css
div {
  width: 50%; /* 50% del contenedor padre */
  height: 30vh; /* 30% de la altura de la ventana */
}
```

**Uso de `max-width`, `min-width`, `max-height` y `min-height`:**

```css
div {
  min-width: 100px; /* Ancho mínimo */
  max-width: 500px; /* Ancho máximo */
  min-height: 50px; /* Alto mínimo */
  max-height: 300px; /* Alto máximo */
}
```

**Relación de aspecto con `aspect-ratio`:**

Permite fijar la proporción entre ancho y alto; la altura se calcula sola.

```css
.video {
  width: 100%;
  aspect-ratio: 16 / 9; /* ancho / alto */
}

.avatar {
  width: 80px;
  aspect-ratio: 1; /* cuadrado perfecto */
}
```

### 4.7 Propiedades de Background

**Propiedades individuales:**

```css
background-color: #f0f0f0;
background-image: url("imagen.jpg");
background-repeat: no-repeat;
background-position: center;
background-size: cover;
background-attachment: fixed;
```

**Uso del shorthand `background`**

```css
background: #f0f0f0 url("imagen.jpg") no-repeat center/cover fixed;
```

## 5. Propiedades Avanzadas en CSS

### 5.1 Filtros (Filter)

```css
filter: blur(5px);
filter: brightness(150%);
filter: contrast(120%);
filter: grayscale(50%);
filter: sepia(80%);
filter: hue-rotate(90deg);
filter: invert(100%);
filter: opacity(0.5);
filter: saturate(200%);
```

### 5.2 Transformaciones (Transform)

```css
transform: rotate(45deg);
transform: scale(1.5);
transform: translate(50px, 100px);
transform: skew(20deg, 10deg);
```

### 6. Modelo de Caja en CSS

Cada elemento en CSS se representa como una caja rectangular compuesta por:

- **Contenido**: Texto o elementos dentro de la caja.
- **Padding**: Espacio entre el contenido y el borde.
- **Borde**: Contorno del elemento.
- **Margen**: Espacio externo entre elementos.

```css
div {
  width: 200px;
  padding: 10px;
  border: 5px solid black;
  margin: 20px;
}
```

### 7. Posicionamiento en CSS

- `static`: Posición por defecto.
- `relative`: Relativa a su posición original.
- `absolute`: Relativa a su ancestro más cercano con posición relativa.
- `fixed`: Se mantiene fijo en pantalla.
- `sticky`: Se comporta como `relative` hasta un umbral de desplazamiento.

### 7.1 Posicionamiento Estático (Por Defecto)

```css
div {
  position: static;
}
```

### 7.2 Posicionamiento Relative

```css
div {
  position: relative;
  top: 20px;
  left: 10px;
}
```

### 7.3 Posicionamiento Absolute

```css
div {
  position: absolute;
  top: 50px;
  left: 50px;
}
```

### 7.4 Posicionamiento Fixed

```css
header {
  position: fixed;
  top: 0;
  width: 100%;
}
```

### 7.5 Posicionamiento

```css
nav {
  position: sticky;
  top: 0;
}
```

### 8 Pseudoclases y Pseudoelementos

#### 8.1 Pseudoclases

Las pseudoclases permiten aplicar estilos a un elemento en función de su estado o posición dentro del documento.

**Ejemplos de pseudoclases comunes:**

- `:hover` (cuando el mouse pasa sobre un elemento)
- `:focus` (cuando un elemento está enfocado)
- `:nth-child(n)` (selecciona elementos según su posición)

**Ejemplo de uso:**

```css
/* Cambia el color del texto cuando el usuario pasa el mouse sobre el enlace */
a:hover {
  color: red;
}

/* Aplica un borde cuando un input está enfocado */
input:focus {
  border: 2px solid blue;
}

/* Selecciona el tercer elemento de una lista */
li:nth-child(3) {
  font-weight: bold;
}
```

**Otras pseudoclases útiles:**

```css
/* Selecciona el primer elemento de su tipo dentro de un contenedor */
p:first-of-type {
  color: green;
}

/* Selecciona los elementos pares de una lista */
tr:nth-child(even) {
  background-color: lightgray;
}

/* Selecciona el último hijo de un contenedor */
div:last-child {
  margin-bottom: 20px;
}
```

---

#### 8.2 Pseudoelementos

Los pseudoelementos permiten aplicar estilos a partes específicas de un elemento sin necesidad de modificar el HTML.

**Ejemplos de pseudoelementos comunes:**

- `::before` (inserta contenido antes del elemento)
- `::after` (inserta contenido después del elemento)

**Ejemplo de uso:**

```css
/* Inserta un texto antes de cada párrafo */
p::before {
  content: "Inicio: ";
  font-weight: bold;
}

/* Inserta una flecha después de los enlaces */
a::after {
  content: " →";
  color: gray;
}
```

**Otros usos comunes:**

```css
/* Simula una lista numerada agregando números antes de cada elemento */
li::before {
  content: counter(item) ". ";
  counter-increment: item;
}

/* Resalta la primera letra de un párrafo */
p::first-letter {
  font-size: 2em;
  color: blue;
}

/* Aplica un estilo a la primera línea de un párrafo */
p::first-line {
  font-weight: bold;
}
```

## 9 Flexbox en CSS

Flexbox es un método de diseño **unidimensional** para organizar elementos en filas o columnas.

### Propiedades del Flex Container:

- `display: flex;`
- `flex-direction: row | column | row-reverse | column-reverse;`
- `justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;`
- `align-items: flex-start | flex-end | center | stretch | baseline;`
- `flex-wrap: nowrap | wrap | wrap-reverse;`

### Propiedades del Flex Item:

- `flex-grow: 1;` (Controla la expansión del elemento)
- `flex-shrink: 1;` (Controla la reducción del elemento)
- `flex-basis: auto;` (Tamaño inicial antes de aplicar `flex-grow` y `flex-shrink`)
- `align-self: auto | flex-start | flex-end | center | baseline | stretch;`

#### Ejemplo en HTML:

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

#### Propiedades del Flex Container:

```css
.container {
  display: flex;
  flex-direction: row; /* o column, row-reverse, column-reverse */
  justify-content: space-between; /* o flex-start, flex-end, center, space-around, space-evenly */
  align-items: center; /* o flex-start, flex-end, stretch, baseline */
  flex-wrap: wrap; /* o nowrap, wrap-reverse */
}
```

#### Propiedades del Flex Item:

```css
.item {
  flex-grow: 1; /* Expande proporcionalmente */
  flex-shrink: 1; /* Reduce proporcionalmente */
  flex-basis: 100px; /* Tamaño base antes de aplicar flex-grow y flex-shrink */
  align-self: center; /* o flex-start, flex-end, baseline, stretch */
}
```

## 10 Grid en CSS

CSS Grid es un sistema de diseño **bidimensional** que permite organizar elementos en filas y columnas.

### Propiedades del Grid Container:

- `display: grid;`
- `grid-template-columns: repeat(3, 1fr);`
- `grid-template-rows: repeat(2, auto);`
- `gap: 10px;`
- `justify-items: start | end | center | stretch;`
- `align-items: start | end | center | stretch;`

### Propiedades del Grid Item:

- `grid-column: 1 / span 2;`
- `grid-row: 1 / span 2;`
- `justify-self: start | end | center | stretch;`
- `align-self: start | end | center | stretch;`

#### Ejemplo en HTML:

```html
<div class="grid-container">
  <div class="grid-item">A</div>
  <div class="grid-item">B</div>
  <div class="grid-item">C</div>
  <div class="grid-item">D</div>
  <div class="grid-item">E</div>
  <div class="grid-item">F</div>
</div>
```

#### Propiedades del Grid Container:

```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columnas de igual tamaño */
  grid-template-rows: repeat(2, auto); /* 2 filas con altura automática */
  gap: 10px; /* Espaciado entre celdas */
  justify-items: center; /* o start, end, stretch */
  align-items: center; /* o start, end, stretch */
}
```

#### Propiedades del Grid Item:

```css
.grid-item {
  grid-column: 1 / span 2; /* Ocupa dos columnas */
  grid-row: 1 / span 2; /* Ocupa dos filas */
  justify-self: center; /* o start, end, stretch */
  align-self: center; /* o start, end, stretch */
}
```

### 11. Media Queries

Permiten hacer diseños responsivos.

```css
@media (max-width: 600px) {
  body {
    background-color: lightgray;
  }
}
```

### 12. Animaciones y Transiciones

#### 12.1 Transiciones

```css
div {
  transition: all 0.5s ease-in-out;
}
```

#### 12.2 Animaciones

```css
@keyframes mover {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(100px);
  }
}

.box {
  animation: mover 2s infinite alternate;
}
```

### 13. Variables CSS (Custom Properties)

Las variables CSS permiten guardar un valor con un nombre y reutilizarlo. Se definen empezando con `--` y se usan con la función `var()`.

```css
:root {
  --color-primario: #2a9d8f;
  --espacio: 16px;
}

.boton {
  background-color: var(--color-primario);
  padding: var(--espacio);
}
```

**Ámbito (scope):** una variable existe en el elemento donde se define y en todos sus descendientes. Definirlas en `:root` (el elemento `<html>`) las hace globales.

**Valor de respaldo (fallback):** si la variable no está definida, se puede indicar un valor por defecto separándolo con una coma:

```css
color: var(--color-texto, #222);
```

**Ventaja:** cambiar el valor en un solo lugar actualiza todo el sitio. Es la base de los temas (claro / oscuro).

### 14. Funciones CSS

**`calc()`** permite hacer cuentas mezclando unidades. Los operadores `+` y `-` necesitan espacios alrededor.

```css
.ancho-completo {
  width: calc(100% - 40px);
}
```

**`min()` y `max()`** eligen el menor o el mayor de sus argumentos:

```css
.caja {
  width: min(100%, 600px); /* nunca más de 600px */
  font-size: max(16px, 1.2vw); /* nunca menos de 16px */
}
```

**`clamp(minimo, ideal, maximo)`** deja que un valor se adapte, pero acotado entre un mínimo y un máximo:

```css
h1 {
  font-size: clamp(1.5rem, 4vw, 3rem);
}
```

El orden de los argumentos importa: mínimo, preferido, máximo.

### 15. Selectores Modernos

**`:is()`** agrupa selectores y es tolerante: si uno de ellos es inválido, no rompe toda la regla.

```css
:is(h1, h2, h3) {
  line-height: 1.2;
}
```

**`:where()`** es igual a `:is()`, pero con especificidad cero (no "pesa" en la cascada).

```css
:where(.lista) {
  margin-bottom: 8px;
}
```

**`:not()`** selecciona los elementos que NO coinciden con lo que está entre paréntesis.

```css
.item:not(.oferta) {
  opacity: 0.8;
}
```

**`:has()`** selecciona un elemento según lo que contiene (el "selector de padre").

```css
.tarjeta:has(.etiqueta) {
  border: 2px solid gold;
}
```

**Importante:** una lista de selectores normal (`a, .b, .c`) se cae entera si uno de sus selectores es inválido. `:is()` y `:where()` evitan ese problema.

### 📚 Enlaces a Documentación Oficial

[MDN Web Docs](https://developer.mozilla.org/es/docs/Web/CSS) Todo sobre CSS

[Flexbox Froggy](https://flexboxfroggy.com/#es) Aprender Flex

[Grid Garden](https://cssgridgarden.com/#es) Aprende Grid
