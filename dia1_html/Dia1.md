# HTML

El lenguaje HTML es un lenguaje de markup que describe páginas web, que serán mostradas en un navegador web.

Los navegadores reciben documentos HTML de un servidor web o del sistema local de archivos, y los muestra en pantalla. El HTML describe la estructura de una página web de manera semántica y organizada.

## Estructura básica mínima de un archivo HTML

Cada archivo HTML está conformado por una serie de etiquetas que describen su contenido.

Cada etiqueta se escribe entre símbolos de mayor y menor que (< >).

E.g. `<body>`

La mayoría de etiquetas deben tener una etiqueta de apertura y otra de cierre. Las etiquetas de cierre se caracterizan por tener un slash (`/`) antes del nombre de la etiqueta

E.g.

```html
<body></body>
```

A continuación se muestra un ejemplo mínim de un archivo HTML

```html
<!DOCTYPE html>

<html lang="es">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />

    <title>Curso de Programacion Web</title>
    <meta name="description" content="Curso de Programacion Web" />
    <meta name="author" content="" />
    <link rel="stylesheet" href="css/styles.css?v=1.0" />
  </head>

  <body>
    <h1>Titulo</h1>
    <p>Contenido</p>
    <script src="js/scripts.js"></script>
  </body>
</html>
```

## Etiquetas básicas

Estas etiquetas conforman la estructura básica de un documento HTML, y se usan en practicamente todos los archivos HTML.

### Doctype

La etiqueta `<!DOCTYPE html>` no tiene etiqueta de cierre. Esta etiqueta se usa para indicar a los navegadores web que el archivo que están leyendo es un documento HTML.

Todos los documentos HTML deben comenzar con esta etiqueta.

```html
<!DOCTYPE html>
```

### `<html>`

La etiqueta `<html>` representa la raíz del documento. Es la etiqueta de nivel superior, todas las demás etiquetas deben estar dentro de esta etiqueta, y esta etiqueta no puede estar dentro de ninguna otra etiqueta.

Esta etiqueta es necesaria en todos los documentos HTML.

Es recomendable indicar el idioma de la página web en esta etiqueta, para beneficio de los buscadores web, así como herramientas de accesibilidad.

```html
<html lang="es"></html>
```

### `<head>`

La etiqueta `<head>` se usa para indicar información adicional para los navegadores web.

```html
<head>
  <title>Título</title>
  <meta name="description" content="Descripción" />
  <meta name="author" content="Autor" />
  <link rel="stylesheet" href="css/styles.css" />
</head>
```

### `<body>`

La etiqueta `<body>` representa el contenido de la página web. Todas las demás etiquetas del contenido se colocan dentro de esta etiqueta.

Solo debe haber una etiqueta `<body>` en un archivo HTML.

```html
<body>
  <p>Contenido</p>
</body>
```

### `<link>`

La etiqueta `<link>` se utiliza para incluir otros recursos, como íconos, o estilos, en un archivo html

Para usar una hoja de estilos CSS:

```html
<link href="main.css" rel="stylesheet" />
```

Para utilizar un ícono de pestaña (favicon)

```html
<link rel="icon" href="favicon.ico" />
```

Existen otros usos para esta etiqueta, pero estos dos son los más comunes.

### `<script>`

La etiqueta `<script>` se utiliza para incluir un archivo de javascript en el archivo html, y ejecutar código en la página web.

```html
<script src="javascript.js"></script>
```

## Etiquetas más utilizadas

Estas etiquetas se usan para describir el contenido de una página web. Todas estas etiquetas se usan dentro de la etiqueta `<body>`.

### Encabezados

Los encabezados son etiquetas de título, las cuales definen los títulos y subtítulos de una página.

Existen 6 niveles de encabezados, cada uno más pequeño que el anterior.

- **H1**
  ```html
  <h1>Titulo H1</h1>
  ```
- **H2**
  ```html
  <h2>Titulo H2</h2>
  ```
- **H3**
  ```html
  <h3>Titulo H3</h3>
  ```
- **H4**
  ```html
  <h4>Titulo H4</h4>
  ```
- **H5**
  ```html
  <h5>Titulo H5</h5>
  ```
- **H6**
  ```html
  <h6>Titulo H6</h6>
  ```

Es recomendable usar los encabezados de manera semántica y jerárquica. Esto es, cada encabezado solo debería aparecer después de otro encabezado del nivel anterior, a excepción del encabezado de nivel 1.

Es recomendable solo incluir un encabezado de nivel 1.

Ejemplo de encabezados anidados

```html
<h1>Titulo Principal</h1>
<h2>Titulo de Sección</h2>
<h3>Titulo de Subsección</h3>
<h3>Otro Titulo de Subsección</h3>
<h2>Otra Sección</h2>
```

### Párrafos

La etiqueta `<p>` es utilizada para la creación de párrafos.

Los párrafos siempre empiezan en una nueva línea, y los navegadores web automáticamente añaden espacio en blanco (márgenes) antes y después de un párrafo.

Por lo general, la mayoría del texto del contenido principal de una página se incluye dentro de una etiqueta de párrafo (`<p>`)

```html
<p>Párrafo</p>
```

### Div

La etiqueta `<div>` se utiliza para la creación de secciones o contenedores para otros elementos.

Por si sola, esta etiqueta no tiene ningún efecto en el contenido ni representa nada.

Esta etiqueta se utiliza principalmente para organizar e identificar las partes de la página web, para posteriormente cambiar su estilo y apariencia usando CSS.

```html
<div>
  <h1>Contenido dentro de un div</h1>
  <p>Párrafo</p>
</div>

<div>
  <h1>Contenido dentro de otro div</h1>
  <p>Párrafo</p>
</div>
```

### Botones

La etiqueta `<button>` se utiliza para la creación de botones, a los cuales se les puede hacer click.

```html
<button>Botón</button>
```

### Span

La etiqueta `<span>` se utiliza como contenedor para una parte de un texto o una parte de un documento.

Al igual que la etiqueta `<div>`, no significa nada por si sola. Se utiliza para dar estilos a ciertas secciones, usando CSS.

La diferencia principal entre `<div>` y `<span>`, es que `<div>` crea un elemento de tipo "block", mientras que `<span>` crea un elemento "inline".

Los elementos de tipo "block" ocupan el espacio horizontal completo. Elementos que aparezcan después, estarán en una nueva línea, y tendrán un cierto margen de espacio.

Los elementos de tipo "inline" ocupan solamente el espacio necesario, no generan márgenes, y no afectan al resto del documento.

```html
<p>
  Principio de un parrafo.
  <span>Este texto esta contenido dentro de un span</span>
  Final de un parrafo
</p>
```

### Links

La etiqueta `<a>` define un hipervínculo, un enlace hacia otra página web, o algún recurso, ya sea en internet, o en el propio sistema, como un archivo local.

El atributo `href` indica hacia donde apunta el hipervínculo. El texto dentro de la etiqueta es el texto que se muestra, en vez del hipervínculo.

```html
<a href="https://www.youtube.com/">Link hacia YouTube</a>
```

### Listas

Las etiquetas `<ol>` y `<ul>` se utilizan para crear listas. La etiqueta `<li>` se utiliza para crear elementos dentro de una lista.

Existen dos tipos de listas:

- **Listas ordenadas**: son aquellas que nos muestran los elementos en una lista numerada. Se crean con la etiqueta `<ol>`
- **Listas desordenadas**: nos sirven para mostrar elementos precedidos por una viñeta. Para definir una lista desordenada utilizamos la etiqueta `<ul>`

Cada elemento dentro de una lista, sin importar el tipo de lista que utilicemos se define con la etiqueta `<li>`

Ejemplo de lista ordenada

```html
<ol>
  <li>Julio</li>
  <li>Carmen</li>
  <li>Ignacio</li>
  <li>Elena</li>
</ol>
```

Ejemplo de lista desordenada

```html
<ul>
  <li>Julio</li>
  <li>Carmen</li>
  <li>Ignacio</li>
  <li>Elena</li>
</ul>
```

Las listas se pueden anidar. Esto es, podemos meter listas dentro de listas.

Ejemplo de lista anidada:

```html
<ul>
  <li>
    Carnívoros
    <ul>
      <li>León</li>
      <li>Buitre</li>
      <li>Hiena</li>
    </ul>
  </li>
  <li>
    Herbívoros
    <ul>
      <li>Cabra</li>
      <li>Vaca</li>
    </ul>
  </li>
  <li>
    Omnívoros
    <ul>
      <li>Oso</li>
      <li>Urraca</li>
    </ul>
  </li>
</ul>
```

### Imágenes

La etiqueta `<img>` se utiliza para insertar una imágen en una página web.

El atributo `src` indica la url de la imagen.

El atributo `alt` es el texto que aparece cuando se coloca el cursor sobre la imagen. También se muestra cuando no se pudo cargar la imagen, o para herramientas de accesibilidad, como los lectores de pantalla. Por esta razón, es recomendable que todas las imágenes tengan un atributo alt.

```html
<img src="imagen.png" alt="Descripción de la imagen" />
```

### Videos

La etiqueta `<video>` se utiliza para insertar un video en una página web.

El elemento `<source>` dentro de la etiqueta `<video>` especifica la url del video.

Los atributos `width` y `height` especifican el ancho y la altura, respectivamente.

El atributo `controls` muestra los controles de pausa

```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4" />
</video>
```

### Tablas

Para crear una tabla, es necesario utilizar la etiqueta `<table>` para delimitarla.

Algunas de las etiquetas más comúnes dentro de las tablas son:

- `<tr>` - Representa filas en una tabla
- `<th>` - Se utiliza para añadir una celda de encabezado
- `<td>` - Representa una celda normal en la tabla
- `<thead>` - Añade un encabezado separado para la tabla
- `<tbody>` - Contiene el contenido principal
- `<tfoot>` - Crea un footer separado
- `<caption>` - Inserta un nombre a la tabla

Ejemplo de una tabla simple con encabezados

```html
<table>
  <tr>
    <th>First Name</th>
    <th>Last Name</th>
    <th>Email Address</th>
  </tr>
  <tr>
    <td>Hillary</td>
    <td>Nyakundi</td>
    <td>tables@mail.com</td>
  </tr>
  <tr>
    <td>Lary</td>
    <td>Mak</td>
    <td>developer@mail.com</td>
  </tr>
</table>
```

Ejemplo de una tabla con caption

```html
<table>
  <caption>
    Free Coding Resources
  </caption>
  <tr>
    <th>Sites</th>
    <th>Youtube Channels</th>
    <th>Mobile Appss</th>
  </tr>
  <tr>
    <td>Freecode Camp</td>
    <td>Freecode Camp</td>
    <td>Enki</td>
  </tr>
  <tr>
    <td>W3Schools</td>
    <td>Academind</td>
    <td>Programming Hero</td>
  </tr>
  <tr>
    <td>Khan Academy</td>
    <td>The Coding Train</td>
    <td>Solo learn</td>
  </tr>
</table>
```

Ejemplo de una tabla completa, con `<thead>`, `<tbody>` y `<tfoot>`

```html
<table>
  <thead>
    <tr>
      <th colspan="2">October</th>
      <th colspan="2">November</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Sales</td>
      <td>Profit</td>
      <td>Sales</td>
      <td>Profit</td>
    </tr>
    <tr>
      <td>$200,00</td>
      <td>$50,00</td>
      <td>$300,000</td>
      <td>$70,000</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <th colspan="4">November was more produstive</th>
    </tr>
  </tfoot>
</table>
```

## Ejercicio del Día 1 (HTML)

Para reforzar los conocimientos adquiridos, se les pedirá que realicen un ejercicio, utilizando lo aprendido en esta sección.

### Descripción del Ejercicio

Deberás crear una archivo HTML (`pagina.html`), el cual debe cumplir las siguientes características:

- El título mostrado en la pestaña del navegador debe ser "**Curso de Programación Web**"
- La página debe tener como título principal "Reseña de la película o serie <Nombre de película o serie>". Elige una película o serie de tu preferencia
- A continuación, incluye uno o más parrafos, con una descripción o sinopsis de la película o serie.
- Después, inserta una imagen de la película o serie.
- Introduce una sección con un título "Reparto / Elenco".
  - En esta sección, introduce una lista sin orden, con los nombres de algunos de los actores de la película o serie (3 a 6).
- Introduce una sección con un título "Información General"

  - En esta sección, coloca una tabla, sin encabezados, con la siguiente información:

    | Información | Ejemplo      |
    | ----------- | ------------ |
    | Título      | Alien        |
    | Año         | 1979         |
    | Género      | Horror       |
    | Director    | Ridley Scott |

  - Introduce una subsección "Trailer"
    - En esta sección, introduce un párrafo con el siguiente texto "Presiona aquí para ver el trailer". Donde el texto "aquí", debe ser un hipervínculo que lleve al trailer de la película o serie.

- Introduce una sección "Recomendaciones Adicionales"
  - En esta sección, coloca una lista ordenada, con el Top 5 de películas o series que recomiendes

### Extra (no es opcional)

Los siguientes puntos no se explicaron en esta sección, pero se les pide que busquen como realizarlos.

- Pon los títulos de las secciones en negrita y en cursiva / itálica, usando HTML (sin usar CSS).
- Pon un salto de línea en el párrafo de la descripción o sinopsis, sin crear otro párrafo (usando un elemento HTML).

### Extra (este si es opcional)

Coloca un índice después del título.

El índice debe ser una lista de las secciones de la página. Al dar click en cada elemento, se debe dirigir o moverse a esa parte de la página.

_(Pista: necesitas hacer uso del atributo id de los elementos)_
