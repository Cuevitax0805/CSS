# CSS

# CSS — HOJAS DE ESTILO, VARIABLES Y ESTRUCTURAS

## 1. Introducción a CSS

**CSS (Cascading Style Sheets)** es un lenguaje utilizado para definir la presentación visual de documentos HTML.

Mientras HTML se encarga de organizar y estructurar el contenido de una página web, CSS permite controlar su apariencia: colores, tamaños, fuentes, espacios, posiciones, distribución de elementos y adaptabilidad a diferentes dispositivos.

### ¿Para qué sirve CSS?

- Cambiar colores y fondos.
- Definir tamaños y tipos de letra.
- Organizar elementos en una página.
- Crear diseños adaptables a móviles, tabletas y ordenadores.
- Añadir transiciones y animaciones.
- Separar la estructura HTML de su presentación visual.

### Relación entre HTML y CSS

```html
<!-- HTML: estructura -->
<h1 class="titulo">Hola, mundo</h1>
<p>Esta es mi primera página web.</p>
```

```css
/* CSS: presentación */
.titulo {
    color: blue;
    font-size: 32px;
}
```

---

## 2. Formas de utilizar CSS en HTML

Existen tres formas principales de aplicar estilos CSS.

### 2.1. CSS en línea (Inline CSS)

Se escribe directamente dentro del atributo `style` de un elemento HTML.

```html
<h1 style="color: blue; font-size: 32px;">
    Hola, mundo
</h1>
```

Es útil para pruebas rápidas, pero no es recomendable para proyectos grandes porque mezcla estructura y presentación.

### 2.2. CSS interno (Internal CSS)

Se escribe dentro de la etiqueta `<style>` en el documento HTML.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Mi página</title>

    <style>
        h1 {
            color: blue;
            font-size: 32px;
        }
    </style>
</head>
<body>

    <h1>Hola, mundo</h1>

</body>
</html>
```

Es adecuado para páginas pequeñas o ejemplos sencillos.

### 2.3. CSS externo (External CSS)

Los estilos se guardan en un archivo independiente con extensión `.css` y se conectan al documento HTML mediante `<link>`.

**index.html**

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Mi página</title>

    <link rel="stylesheet" href="css/style.css">
</head>
<body>

    <h1 class="titulo">Hola, mundo</h1>

</body>
</html>
```

**css/style.css**

```css
.titulo {
    color: blue;
    font-size: 32px;
}
```

Esta es la forma recomendada para organizar proyectos web.

---

## 3. Sintaxis básica de CSS

Una regla CSS está formada por un selector y un bloque de declaraciones.

```css
selector {
    propiedad: valor;
}
```

### Partes de una regla CSS

- **Selector:** identifica el elemento HTML que recibirá los estilos.
- **Propiedad:** indica qué característica se desea modificar.
- **Valor:** establece cómo se verá esa característica.
- **Declaración:** combinación de una propiedad y su valor.

Ejemplo:

```css
p {
    color: red;
    font-size: 18px;
    text-align: center;
}
```

En este caso, todos los elementos `<p>` tendrán texto rojo, tamaño de 18 píxeles y alineación centrada.

### Comentarios

Los comentarios permiten documentar el código y no se muestran en la página.

```css
/* Este es un comentario CSS */

/*
    También podemos escribir
    comentarios de varias líneas.
*/
```

---

## 4. Selectores CSS

Los selectores permiten identificar los elementos HTML a los que queremos aplicar estilos.

### 4.1. Selector universal

Selecciona todos los elementos de la página.

```css
* {
    margin: 0;
    padding: 0;
}
```

### 4.2. Selector de etiqueta

Selecciona todos los elementos de un tipo determinado.

```css
h1 {
    color: blue;
}

p {
    font-size: 16px;
}
```

### 4.3. Selector de clase

Selecciona los elementos que tengan una clase específica. Se representa con un punto `.`.

```html
<p class="texto">Primer párrafo</p>
<p class="texto">Segundo párrafo</p>
```

```css
.texto {
    color: green;
}
```

Una clase puede utilizarse en varios elementos HTML.

### 4.4. Selector de ID

Selecciona un elemento mediante su identificador. Se representa con `#`.

```html
<div id="contenedor">
    Contenido principal
</div>
```

```css
#contenedor {
    background-color: lightgray;
}
```

Un ID debe ser único dentro del documento HTML.

### 4.5. Selector agrupado

Permite aplicar los mismos estilos a varios selectores.

```css
h1, h2, p {
    font-family: Arial, sans-serif;
}
```

### 4.6. Selector descendiente

Selecciona elementos que se encuentran dentro de otro elemento, sin importar cuántos niveles los separen.

```css
div p {
    color: red;
}
```

### 4.7. Selector de hijo directo

Selecciona únicamente los elementos que son hijos directos del elemento indicado.

```css
div > p {
    color: blue;
}
```

### 4.8. Selector de hermano adyacente

Selecciona el elemento que aparece inmediatamente después de otro y comparte el mismo padre.

```css
h2 + p {
    color: gray;
}
```

### 4.9. Selector de hermanos generales

Selecciona los elementos hermanos que aparecen después del elemento indicado.

```css
h2 ~ p {
    color: green;
}
```

---

## 5. Pseudoclases y pseudoelementos

Permiten aplicar estilos dependiendo del estado de un elemento o de una parte específica de su contenido.

### 5.1. Pseudoclases

Se representan con dos puntos `:`.

```css
/* Cuando el cursor pasa sobre un botón */
button:hover {
    background-color: blue;
    color: white;
}

/* Cuando se pulsa un botón */
button:active {
    transform: scale(0.95);
}

/* Cuando un campo recibe el foco */
input:focus {
    border: 2px solid blue;
}

/* Selecciona el primer elemento */
li:first-child {
    color: red;
}

/* Selecciona el último elemento */
li:last-child {
    color: green;
}

/* Selecciona elementos pares */
li:nth-child(even) {
    background-color: lightgray;
}

/* Selecciona elementos impares */
li:nth-child(odd) {
    background-color: white;
}
```

### 5.2. Pseudoelementos

Se representan generalmente con dos puntos dobles `::` y permiten modificar partes de un elemento.

```css
/* Primera letra de un párrafo */
p::first-letter {
    font-size: 30px;
}

/* Primera línea de un párrafo */
p::first-line {
    font-weight: bold;
}

/* Inserta contenido antes */
h2::before {
    content: "★ ";
}

/* Inserta contenido después */
h2::after {
    content: " ✓";
}

/* Personaliza el texto seleccionado */
::selection {
    background-color: yellow;
    color: black;
}
```

---

## 6. Variables CSS

Las variables CSS permiten almacenar valores reutilizables, como colores, tamaños, fuentes y medidas.

Se conocen técnicamente como **propiedades personalizadas (Custom Properties)**.

Se declaran utilizando dos guiones `--` y normalmente se definen dentro de `:root` para que estén disponibles globalmente.

```css
:root {
    --color-principal: #3498db;
    --color-secundario: #2ecc71;
    --color-fondo: #f4f4f4;
    --color-texto: #222222;

    --fuente-principal: Arial, sans-serif;

    --tamanio-titulo: 32px;
    --espaciado: 20px;
}
```

### 6.1. Cómo utilizar las variables

Se utiliza la función `var()`.

```css
body {
    background-color: var(--color-fondo);
    color: var(--color-texto);
    font-family: var(--fuente-principal);
}

h1 {
    color: var(--color-principal);
    font-size: var(--tamanio-titulo);
}

button {
    background-color: var(--color-secundario);
    padding: var(--espaciado);
}
```

### 6.2. Valores alternativos (Fallback)

Se puede establecer un valor alternativo cuando una variable no está definida o no es válida.

```css
p {
    color: var(--color-texto, black);
}
```

### 6.3. Variables locales

Las variables también pueden declararse dentro de un selector y utilizarse en ese elemento y sus descendientes.

```css
.card {
    --color-card: #eeeeee;

    background-color: var(--color-card);
}

.card h2 {
    color: var(--color-card);
}
```

### 6.4. Modificar variables

Las variables pueden cambiarse dependiendo de una clase o condición.

```css
:root {
    --fondo: white;
    --texto: black;
}

.tema-oscuro {
    --fondo: #222222;
    --texto: white;
}

body {
    background-color: var(--fondo);
    color: var(--texto);
}
```

### 6.5. Diferencia entre variables CSS y variables de otros lenguajes

Las variables CSS no funcionan exactamente igual que las variables de Java, PHP o JavaScript.

- Se declaran dentro de reglas CSS.
- Sus nombres comienzan con `--`.
- Se consultan mediante `var()`.
- Pueden heredarse.
- Su valor puede variar según el elemento y la cascada.

---

## 7. Colores en CSS

CSS ofrece diferentes formas de representar colores.

### 7.1. Nombres de colores

```css
h1 {
    color: red;
    background-color: black;
}
```

### 7.2. Hexadecimal

Se representa mediante el símbolo `#`.

```css
h1 {
    color: #ffffff;
    background-color: #000000;
}
```

### 7.3. RGB

Representa los colores mediante los componentes rojo, verde y azul.

```css
p {
    color: rgb(255, 0, 0);
}
```

### 7.4. RGBA

Añade un canal alfa para controlar la transparencia.

```css
div {
    background-color: rgba(0, 0, 0, 0.5);
}
```

### 7.5. HSL

Representa los colores mediante tono, saturación y luminosidad.

```css
h1 {
    color: hsl(210, 100%, 50%);
}
```

---

## 8. Tipografía y texto

CSS permite controlar la apariencia de los textos.

| Propiedad | Función |
|---|---|
| `font-family` | Tipo de fuente |
| `font-size` | Tamaño del texto |
| `font-weight` | Grosor de la fuente |
| `font-style` | Estilo normal o cursiva |
| `color` | Color del texto |
| `text-align` | Alineación |
| `text-decoration` | Decoración del texto |
| `text-transform` | Transformación de mayúsculas y minúsculas |
| `line-height` | Altura de línea |
| `letter-spacing` | Espaciado entre letras |
| `word-spacing` | Espaciado entre palabras |

Ejemplo:

```css
h1 {
    font-family: Arial, sans-serif;
    font-size: 36px;
    font-weight: bold;
    text-align: center;
    text-transform: uppercase;
}

p {
    font-size: 16px;
    line-height: 1.6;
    letter-spacing: 1px;
}
```

### Fuentes externas

Se pueden importar fuentes desde servicios como Google Fonts.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
```

```css
body {
    font-family: "Roboto", sans-serif;
}
```

---

## 9. Unidades de medida

CSS utiliza unidades para definir tamaños, distancias y dimensiones.

### 9.1. Unidades absolutas

| Unidad | Descripción |
|---|---|
| `px` | Píxeles CSS |
| `cm` | Centímetros |
| `mm` | Milímetros |
| `in` | Pulgadas |
| `pt` | Puntos tipográficos |
| `pc` | Picas |

Ejemplo:

```css
h1 {
    font-size: 32px;
}
```

### 9.2. Unidades relativas

| Unidad | Descripción |
|---|---|
| `%` | Porcentaje relativo al contexto de la propiedad |
| `em` | Relativo al tamaño de fuente del elemento de referencia |
| `rem` | Relativo al tamaño de fuente del elemento raíz |
| `vw` | Porcentaje del ancho de la ventana |
| `vh` | Porcentaje de la altura de la ventana |
| `vmin` | Porcentaje del menor lado de la ventana |
| `vmax` | Porcentaje del mayor lado de la ventana |
| `ch` | Relativo al ancho del carácter cero de la fuente |

Ejemplo:

```css
html {
    font-size: 16px;
}

h1 {
    font-size: 2rem;
}

.container {
    width: 80%;
    min-height: 100vh;
}
```

### 9.3. Funciones de tamaño

CSS incluye funciones para calcular y controlar dimensiones.

```css
.container {
    width: calc(100% - 40px);
}

.card {
    width: min(100%, 500px);
}

h1 {
    font-size: clamp(24px, 4vw, 48px);
}
```

- `calc()`: realiza operaciones matemáticas.
- `min()`: utiliza el menor valor.
- `max()`: utiliza el mayor valor.
- `clamp()`: establece un valor mínimo, preferido y máximo.

---

## 10. Modelo de caja (Box Model)

Todos los elementos HTML se representan mediante cajas.

El modelo de caja determina cómo se calcula el espacio que ocupa un elemento.

Está compuesto por cuatro partes:

1. **Content:** contenido del elemento.
2. **Padding:** espacio interno entre el contenido y el borde.
3. **Border:** borde del elemento.
4. **Margin:** espacio externo alrededor del elemento.

```css
.caja {
    width: 300px;
    height: 150px;

    padding: 20px;
    border: 2px solid black;
    margin: 30px;

    background-color: lightblue;
}
```

### 10.1. Box-sizing

La propiedad `box-sizing` determina cómo se calcula el tamaño total de una caja.

```css
* {
    box-sizing: border-box;
}
```

Con `border-box`, el ancho y alto definidos incluyen el contenido, el padding y el borde.

Es una práctica habitual establecer esta regla al inicio de un proyecto.

---

## 11. Márgenes, rellenos y bordes

### 11.1. Margin

Controla el espacio exterior de un elemento.

```css
div {
    margin: 20px;
}
```

También se pueden especificar lados individuales:

```css
div {
    margin-top: 10px;
    margin-right: 20px;
    margin-bottom: 30px;
    margin-left: 40px;
}
```

### 11.2. Padding

Controla el espacio interior de un elemento.

```css
div {
    padding: 20px;
}
```

### 11.3. Border

Define el borde de un elemento.

```css
div {
    border: 2px solid black;
    border-radius: 10px;
}
```

### 11.4. Propiedades individuales del borde

```css
div {
    border-width: 2px;
    border-style: solid;
    border-color: blue;
}
```

### 11.5. Outline

Dibuja un contorno exterior que no ocupa espacio dentro del modelo de caja.

```css
input:focus {
    outline: 2px solid blue;
    outline-offset: 3px;
}
```

---

## 12. Fondos e imágenes

CSS permite establecer colores, imágenes y otros efectos de fondo.

### 12.1. Color de fondo

```css
body {
    background-color: #f4f4f4;
}
```

### 12.2. Imagen de fondo

```css
body {
    background-image: url("../assets/fondo.jpg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
```

### 12.3. Propiedades principales

| Propiedad | Función |
|---|---|
| `background-color` | Color de fondo |
| `background-image` | Imagen de fondo |
| `background-size` | Tamaño de la imagen |
| `background-position` | Posición de la imagen |
| `background-repeat` | Repetición de la imagen |
| `background-attachment` | Comportamiento del fondo al desplazarse |

### 12.4. Gradientes

Permiten crear transiciones entre colores.

```css
.fondo {
    background: linear-gradient(to right, blue, purple);
}
```

Gradiente radial:

```css
.fondo {
    background: radial-gradient(circle, white, blue);
}
```

---

## 13. Display: tipos de visualización

La propiedad `display` determina cómo se comporta un elemento dentro del diseño.

### 13.1. Block

Ocupa normalmente todo el ancho disponible y comienza en una nueva línea.

```css
div {
    display: block;
}
```

Ejemplos HTML habituales: `div`, `p`, `h1`.

### 13.2. Inline

Se coloca dentro del flujo del texto y no comienza una nueva línea.

```css
span {
    display: inline;
}
```

Ejemplos HTML habituales: `span`, `a`, `strong`.

### 13.3. Inline-block

Se comporta como un elemento en línea, pero permite controlar dimensiones y otros aspectos de la caja.

```css
button {
    display: inline-block;
    width: 120px;
    padding: 10px;
}
```

### 13.4. None

Oculta el elemento y lo elimina del flujo del documento.

```css
.elemento {
    display: none;
}
```

### 13.5. Otros valores

```css
.container {
    display: flex;
}

.grid {
    display: grid;
}

.table {
    display: table;
}
```

---

## 14. Posicionamiento de elementos

La propiedad `position` permite controlar la ubicación de los elementos.

### 14.1. Static

Es el posicionamiento predeterminado.

```css
div {
    position: static;
}
```

### 14.2. Relative

Permite desplazar un elemento respecto a su posición original sin eliminarlo del flujo normal.

```css
div {
    position: relative;
    top: 10px;
    left: 20px;
}
```

### 14.3. Absolute

Posiciona un elemento respecto a su ancestro posicionado más cercano. Si no existe, utiliza el bloque contenedor inicial.

```css
.contenedor {
    position: relative;
}

.elemento {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

### 14.4. Fixed

Posiciona un elemento respecto a la ventana del navegador y permanece en esa posición durante el desplazamiento.

```css
.boton {
    position: fixed;
    bottom: 20px;
    right: 20px;
}
```

### 14.5. Sticky

Combina el comportamiento relativo con el posicionamiento fijo cuando se alcanza un umbral de desplazamiento.

```css
header {
    position: sticky;
    top: 0;
}
```

### 14.6. Z-index

Controla el orden de superposición de elementos posicionados y de determinados elementos dentro de contextos de apilamiento.

```css
.modal {
    position: fixed;
    z-index: 1000;
}
```

Un valor mayor no siempre significa que un elemento aparecerá por encima de cualquier otro: también intervienen los contextos de apilamiento.

---

## 15. Flexbox

**Flexbox (Flexible Box Layout)** es un sistema de diseño unidimensional que permite distribuir y alinear elementos en filas o columnas.

Es especialmente útil para menús, barras de navegación, tarjetas y componentes.

### 15.1. Activar Flexbox

```css
.contenedor {
    display: flex;
}
```

### 15.2. Propiedades del contenedor

```css
.contenedor {
    display: flex;

    flex-direction: row;
    justify-content: center;
    align-items: center;

    flex-wrap: wrap;
    gap: 20px;
}
```

| Propiedad | Función |
|---|---|
| `flex-direction` | Define la dirección de los elementos |
| `justify-content` | Distribuye los elementos en el eje principal |
| `align-items` | Alinea los elementos en el eje transversal |
| `align-content` | Distribuye las líneas cuando existe espacio disponible |
| `flex-wrap` | Permite o impide que los elementos salten de línea |
| `gap` | Establece separación entre elementos |

### 15.3. Valores de flex-direction

```css
.contenedor {
    flex-direction: row;
}
```

- `row`: fila horizontal.
- `row-reverse`: fila horizontal invertida.
- `column`: columna vertical.
- `column-reverse`: columna vertical invertida.

### 15.4. Justify-content

```css
.contenedor {
    justify-content: space-between;
}
```

Valores habituales:

- `flex-start`
- `flex-end`
- `center`
- `space-between`
- `space-around`
- `space-evenly`

### 15.5. Propiedades de los elementos

```css
.elemento {
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 200px;
}
```

También se puede utilizar la propiedad abreviada:

```css
.elemento {
    flex: 1 1 200px;
}
```

### 15.6. Ejemplo práctico

**HTML**

```html
<div class="contenedor">
    <div class="caja">Caja 1</div>
    <div class="caja">Caja 2</div>
    <div class="caja">Caja 3</div>
</div>
```

**CSS**

```css
.contenedor {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
    flex-wrap: wrap;
}

.caja {
    width: 150px;
    padding: 30px;
    background-color: steelblue;
    color: white;
    text-align: center;
}
```

---

## 16. CSS Grid

**CSS Grid Layout** es un sistema de diseño bidimensional que permite organizar elementos mediante filas y columnas.

Es especialmente útil para distribuir secciones completas de una página.

### 16.1. Activar Grid

```css
.contenedor {
    display: grid;
}
```

### 16.2. Definir columnas y filas

```css
.contenedor {
    display: grid;

    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 100px 200px;

    gap: 20px;
}
```

### 16.3. Unidades fr

La unidad `fr` representa una fracción del espacio disponible dentro del contenedor Grid.

```css
.contenedor {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
}
```

La segunda columna recibe el doble de espacio que cada una de las otras dos, considerando el espacio disponible.

### 16.4. Repetir columnas

```css
.contenedor {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
}
```

### 16.5. Columnas adaptables

```css
.contenedor {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
}
```

Esta estructura permite que las columnas se adapten al espacio disponible.

### 16.6. Ejemplo práctico

**HTML**

```html
<div class="grid-container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
</div>
```

**CSS**

```css
.grid-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
}

.item {
    padding: 30px;
    background-color: purple;
    color: white;
    text-align: center;
}
```

---

## 17. Diseño responsive

El diseño responsive permite adaptar una página web a diferentes tamaños de pantalla.

Se utiliza principalmente mediante media queries, unidades relativas y estructuras flexibles.

### 17.1. Media Queries

Las media queries permiten aplicar estilos dependiendo de características del dispositivo o de la ventana, como su ancho.

```css
/* Estilos generales */
body {
    font-size: 18px;
}

/* Pantallas de hasta 768px */
@media (max-width: 768px) {
    body {
        font-size: 16px;
    }
}

/* Pantallas de hasta 480px */
@media (max-width: 480px) {
    body {
        font-size: 14px;
    }
}
```

### 17.2. Meta viewport

Para que una página se adapte correctamente a dispositivos móviles, se debe incluir esta etiqueta en el HTML.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### 17.3. Imágenes adaptables

```css
img {
    max-width: 100%;
    height: auto;
}
```

### 17.4. Ejemplo de diseño adaptable

```css
.contenedor {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}

/* Tablet */
@media (max-width: 768px) {
    .contenedor {
        grid-template-columns: repeat(2, 1fr);
    }
}

/* Móvil */
@media (max-width: 480px) {
    .contenedor {
        grid-template-columns: 1fr;
    }
}
```

---

## 18. Transiciones y transformaciones

CSS permite crear efectos visuales y movimientos sin necesidad de utilizar JavaScript.

### 18.1. Transitions

Permiten establecer una transición gradual entre diferentes estados de una propiedad.

```css
button {
    background-color: blue;
    transition: background-color 0.3s ease;
}

button:hover {
    background-color: purple;
}
```

Propiedades principales:

- `transition-property`
- `transition-duration`
- `transition-timing-function`
- `transition-delay`

### 18.2. Transform

Permite modificar visualmente la posición, escala, rotación o inclinación de un elemento.

```css
.caja {
    transform: translateX(20px);
}
```

Ejemplos:

```css
/* Desplazamiento */
.caja {
    transform: translate(20px, 10px);
}

/* Escala */
.caja {
    transform: scale(1.2);
}

/* Rotación */
.caja {
    transform: rotate(45deg);
}

/* Inclinación */
.caja {
    transform: skew(10deg);
}
```

### 18.3. Combinar transformaciones

```css
.caja:hover {
    transform: translateY(-5px) scale(1.05);
}
```

---

## 19. Animaciones CSS

Las animaciones permiten modificar propiedades a lo largo del tiempo.

Se definen mediante `@keyframes`.

### 19.1. Crear una animación

```css
@keyframes aparecer {
    from {
        opacity: 0;
    }

    to {
        opacity: 1;
    }
}
```

### 19.2. Aplicar la animación

```css
.elemento {
    animation: aparecer 2s ease-in-out;
}
```

### 19.3. Propiedades de animación

| Propiedad | Función |
|---|---|
| `animation-name` | Nombre de la animación |
| `animation-duration` | Duración |
| `animation-delay` | Tiempo de espera |
| `animation-iteration-count` | Número de repeticiones |
| `animation-direction` | Dirección |
| `animation-timing-function` | Curva de velocidad |
| `animation-fill-mode` | Estado antes o después de la animación |

### 19.4. Animación infinita

```css
@keyframes movimiento {
    0% {
        transform: translateX(0);
    }

    50% {
        transform: translateX(100px);
    }

    100% {
        transform: translateX(0);
    }
}

.caja {
    animation: movimiento 3s infinite;
}
```

### 19.5. Respetar las preferencias de movimiento

Algunos usuarios prefieren reducir las animaciones. Se puede respetar esa preferencia mediante:

```css
@media (prefers-reduced-motion: reduce) {
    *,
    *::before,
    *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
        scroll-behavior: auto !important;
    }
}
```

---

## 20. Formularios y botones

CSS permite personalizar los campos de entrada, botones y otros elementos de formularios.

### 20.1. Campos de entrada

```css
input {
    width: 100%;
    padding: 12px;

    border: 1px solid #cccccc;
    border-radius: 5px;

    font-size: 16px;
}
```

### 20.2. Estados de los campos

```css
input:focus {
    border-color: blue;
    outline: none;
}

input:disabled {
    background-color: #eeeeee;
    cursor: not-allowed;
}

input:invalid {
    border-color: red;
}

input:valid {
    border-color: green;
}
```

### 20.3. Botones

```css
button {
    padding: 12px 24px;

    background-color: #3498db;
    color: white;

    border: none;
    border-radius: 5px;

    cursor: pointer;
    transition: background-color 0.3s ease;
}

button:hover {
    background-color: #217dbb;
}

button:active {
    transform: scale(0.98);
}
```

---

## 21. Imágenes y multimedia

CSS permite controlar la presentación de imágenes y elementos multimedia.

### 21.1. Ajustar imágenes

```css
img {
    width: 300px;
    height: 200px;
    object-fit: cover;
}
```

Valores habituales de `object-fit`:

- `fill`: estira el contenido para llenar la caja.
- `contain`: mantiene la proporción y muestra todo el contenido.
- `cover`: mantiene la proporción y llena la caja, recortando si es necesario.
- `none`: conserva el tamaño intrínseco.
- `scale-down`: utiliza el resultado más pequeño entre `none` y `contain`.

### 21.2. Posición de la imagen

```css
img {
    object-fit: cover;
    object-position: center;
}
```

### 21.3. Sombras

```css
.card {
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}
```

### 21.4. Opacidad

```css
img {
    opacity: 0.8;
}
```

---

## 22. Funciones y características adicionales de CSS

CSS cuenta con funciones que permiten crear estilos más flexibles.

### 22.1. `var()`

Recupera el valor de una variable.

```css
color: var(--color-principal);
```

### 22.2. `calc()`

Realiza operaciones matemáticas.

```css
width: calc(100% - 50px);
```

### 22.3. `clamp()`

Establece valores mínimos, preferidos y máximos.

```css
font-size: clamp(16px, 3vw, 32px);
```

### 22.4. `min()` y `max()`

Permiten utilizar el menor o mayor valor de una lista.

```css
width: min(90%, 1200px);

height: max(300px, 50vh);
```

### 22.5. `filter()`

Aplica efectos visuales a imágenes y otros elementos.

```css
img {
    filter: grayscale(100%);
}
```

Otros filtros:

```css
img {
    filter: blur(2px);
    filter: brightness(120%);
    filter: contrast(150%);
    filter: sepia(100%);
}
```

### 22.6. `cursor`

Modifica el aspecto del cursor al pasar sobre un elemento.

```css
button {
    cursor: pointer;
}
```

---

## 23. Cascada, especificidad y herencia

CSS significa hojas de estilo en cascada porque las reglas pueden combinarse y competir entre sí.

Cuando varias reglas afectan a un mismo elemento, el navegador determina cuál aplicar teniendo en cuenta diferentes factores.

### 23.1. Cascada

La cascada considera, entre otros factores:

- Origen de la regla.
- Importancia.
- Capas de cascada.
- Especificidad.
- Orden de aparición.

### 23.2. Especificidad

La especificidad determina qué selector tiene mayor prioridad dentro de la cascada.

Como referencia general:

| Selector | Especificidad |
|---|---|
| Etiqueta (`p`) | 0-0-1 |
| Clase (`.texto`) | 0-1-0 |
| ID (`#principal`) | 1-0-0 |
| Estilo en línea | Prioridad superior a los selectores normales |

Ejemplo:

```css
p {
    color: red;
}

.texto {
    color: blue;
}

#principal {
    color: green;
}
```

```html
<p id="principal" class="texto">
    Este texto será verde.
</p>
```

El selector de ID tiene mayor especificidad que el selector de clase y el de etiqueta.

### 23.3. Herencia

Algunas propiedades se transmiten desde un elemento padre a sus descendientes.

Ejemplo:

```css
body {
    color: black;
    font-family: Arial, sans-serif;
}
```

Los elementos descendientes heredarán normalmente estas propiedades, salvo que otra regla las modifique.

### 23.4. Valores especiales

```css
.elemento {
    color: inherit;
    background-color: initial;
    font-size: unset;
}
```

- `inherit`: utiliza el valor heredado del padre.
- `initial`: utiliza el valor inicial definido por CSS.
- `unset`: se comporta como `inherit` si la propiedad se hereda y como `initial` si no.
- `revert`: revierte el valor al resultado de una capa anterior de la cascada.

### 23.5. !important

Permite marcar una declaración como importante dentro de la cascada.

```css
p {
    color: red !important;
}
```

Debe utilizarse con moderación porque dificulta el mantenimiento y la sobrescritura de estilos.

---

## 24. Organización de archivos CSS

Para mantener un proyecto ordenado, es recomendable separar los archivos según su función.

### Ejemplo de estructura

```text
proyecto/
│
├── index.html
│
├── css/
│   ├── style.css
│   ├── variables.css
│   ├── reset.css
│   ├── layout.css
│   ├── components.css
│   └── responsive.css
│
├── assets/
│   ├── images/
│   └── icons/
│
└── js/
    └── script.js
```

### Función de cada archivo

| Archivo | Función |
|---|---|
| `style.css` | Archivo principal |
| `variables.css` | Variables globales |
| `reset.css` | Normalización de estilos |
| `layout.css` | Estructura y distribución |
| `components.css` | Botones, tarjetas, menús y componentes |
| `responsive.css` | Adaptación a diferentes pantallas |

### Importar otros archivos CSS

Se pueden conectar varios archivos mediante `@import`.

```css
@import url("variables.css");
@import url("reset.css");
@import url("layout.css");
@import url("components.css");
@import url("responsive.css");
```

También se pueden conectar directamente desde HTML con varias etiquetas `<link>`. Para proyectos habituales, esta última opción suele facilitar la carga y el mantenimiento.

---

## 25. Ejemplo completo: página web con HTML y CSS

Este ejemplo combina variables, selectores, Flexbox, Grid, botones y diseño responsive.

### 25.1. Archivo HTML

**index.html**

```html
<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Mi página CSS</title>

    <link rel="stylesheet" href="css/style.css">
</head>

<body>

    <header class="header">

        <h1 class="logo">Mi Página</h1>

        <nav class="menu">
            <a href="#">Inicio</a>
            <a href="#">Servicios</a>
            <a href="#">Contacto</a>
        </nav>

    </header>

    <main class="container">

        <section class="presentacion">

            <h2>Bienvenido</h2>

            <p>
                Este es un ejemplo de una página web
                desarrollada utilizando HTML y CSS.
            </p>

            <button class="boton">
                Conocer más
            </button>

        </section>

        <section class="tarjetas">

            <article class="card">
                <h3>HTML</h3>
                <p>Estructura de la página web.</p>
            </article>

            <article class="card">
                <h3>CSS</h3>
                <p>Diseño y presentación visual.</p>
            </article>

            <article class="card">
                <h3>JavaScript</h3>
                <p>Interactividad y comportamiento.</p>
            </article>

        </section>

    </main>

    <footer class="footer">
        <p>Proyecto de aprendizaje HTML y CSS.</p>
    </footer>

</body>
</html>
```

### 25.2. Archivo CSS

**css/style.css**

```css
/* VARIABLES */
:root {
    --color-principal: #3498db;
    --color-secundario: #2c3e50;
    --color-fondo: #f4f4f4;
    --color-texto: #222222;

    --espaciado: 20px;
    --radio: 10px;
}

/* CONFIGURACIÓN GENERAL */
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background-color: var(--color-fondo);
    color: var(--color-texto);
}

/* HEADER */
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;

    padding: var(--espaciado);
    background-color: var(--color-secundario);
    color: white;
}

.logo {
    font-size: 24px;
}

.menu {
    display: flex;
    gap: 20px;
}

.menu a {
    color: white;
    text-decoration: none;
}

/* CONTENEDOR PRINCIPAL */
.container {
    width: min(90%, 1200px);
    margin: 30px auto;
}

/* PRESENTACIÓN */
.presentacion {
    padding: 40px;
    text-align: center;
}

.presentacion h2 {
    margin-bottom: 15px;
    color: var(--color-principal);
}

.presentacion p {
    margin-bottom: 20px;
    line-height: 1.6;
}

/* BOTÓN */
.boton {
    padding: 12px 24px;

    background-color: var(--color-principal);
    color: white;

    border: none;
    border-radius: var(--radio);

    cursor: pointer;
    transition: background-color 0.3s ease;
}

.boton:hover {
    background-color: #217dbb;
}

/* TARJETAS */
.tarjetas {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: var(--espaciado);
}

.card {
    padding: 25px;
    background-color: white;
    border-radius: var(--radio);
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.card h3 {
    margin-bottom: 10px;
    color: var(--color-principal);
}

/* FOOTER */
.footer {
    padding: var(--espaciado);
    background-color: var(--color-secundario);
    color: white;
    text-align: center;
}

/* RESPONSIVE */
@media (max-width: 768px) {

    .header {
        flex-direction: column;
        gap: 15px;
    }

    .tarjetas {
        grid-template-columns: repeat(2, 1fr);
    }

}

@media (max-width: 480px) {

    .tarjetas {
        grid-template-columns: 1fr;
    }

    .menu {
        flex-wrap: wrap;
        justify-content: center;
    }

}
```

---

## 26. Buenas prácticas en CSS

Para escribir código limpio, organizado y fácil de mantener, se recomienda:

1. Utilizar archivos CSS externos.
2. Evitar repetir las mismas propiedades innecesariamente.
3. Utilizar variables para colores, tamaños y valores reutilizables.
4. Organizar el código mediante comentarios y secciones.
5. Utilizar clases con nombres descriptivos.
6. Evitar abusar de los selectores ID para aplicar estilos.
7. Utilizar Flexbox y Grid cuando sean adecuados para distribuir elementos.
8. Diseñar pensando primero en diferentes tamaños de pantalla.
9. Evitar el uso excesivo de `!important`.
10. Mantener una estructura de carpetas organizada.
11. Comprobar la accesibilidad, el contraste y los estados de interacción.
12. Utilizar herramientas de desarrollo del navegador para inspeccionar y depurar estilos.
13. Evitar animaciones innecesarias y respetar las preferencias de movimiento.
14. Mantener una nomenclatura coherente en las clases.
15. Eliminar reglas que ya no se utilizan.

---

## 27. Recursos para aprender CSS

- [MDN Web Docs — CSS](https://developer.mozilla.org/es/docs/Web/CSS): documentación y ejemplos de CSS.
- [W3Schools — CSS](https://www.w3schools.com/css/): tutoriales y ejercicios.
- [CSS-Tricks](https://css-tricks.com/): artículos y guías de diseño.
- [Can I Use](https://caniuse.com/): compatibilidad de características CSS en navegadores.
- [Flexbox Froggy](https://flexboxfroggy.com/#es): juego interactivo para aprender Flexbox.
- [Grid Garden](https://cssgridgarden.com/#es): juego interactivo para aprender CSS Grid.
- [W3C CSS Validator](https://jigsaw.w3.org/css-validator/): validador de hojas de estilo.

---

## 28. Objetivo del repositorio

Este repositorio tiene como objetivo recopilar y documentar los fundamentos de CSS, desde su sintaxis básica hasta la creación de estructuras visuales y diseños adaptables.

Se utiliza como material de consulta y aprendizaje para comprender cómo funcionan las hojas de estilo, cómo se relacionan con HTML y cómo construir interfaces web organizadas, reutilizables y responsive.

**Aprendiendo · Practicando · Construyendo**
