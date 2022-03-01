# CSS

El lenguaje CSS (Cascading Style Sheets) es un lenguaje de hoja de estilos, que describe la presentación o apariencia de un documento
HTML.

## Modelo de Cajas

En una página web, cuando colocamos elementos para mostrarlos en pantallas, éstos siguen un modelo de "Cajas" para dibujarse en pantalla. Para cada elemento se calcula una caja rectangular. El elemento se mostrará dentro de esta caja.

![Modelo de Cajas, MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model/box-model.png)

### Contenido

El rectángulo interior de la caja es el contenido en si. Este rectángulo ajusta su tamaño en base a su contenido.

### Padding

El padding es el espacio extra _interior_ del elemento. Es el espacio que hay entre el borde, y el contenido.

### Borde

Es el contorno exterior de un elemento.

A continuación se muestra un texto, con padding y con un borde amarillo.

![Padding, MDN](https://i.imgur.com/8JdelN2.png)

### Margen

El margen es el espacio extra _exterior_ del elemento. Es el espacio que hay entre el borde, y otros elementos.

En esta imagen, los elementos mostrados no tienen ningún margen

![Margen, MDN](https://i.imgur.com/mNLKYFa.png)

En esta otra imagen, al elemento con borde amarillo se ha aplicado un margen de 16px.

![Margen, MDN](https://i.imgur.com/gLwawOq.png)

## Componentes Básicos de CSS

### Unidades de Medida

CSS tiene varias unidades de medida que podemos usar para definir el tamaño de las cosas. Aunque existen muchas, nos enfocaremos en las siguientes:

- % - Porcentaje. Es una unidad relativa al tamaño del elemento padre.
- px - Pixeles. Esta unidad NO es un pixel físico de la pantalla, es un pixel lógico. Equivale a 1/96 de una pulgada
- vh - 1% de la altura de la ventana gráfica
- vw - 1% del ancho de la ventana gráfica
- rem - Tamaño de la letra del elemento raíz. Normalmente 16px.
- em - Referencia el tamaño de letra del elemento padre

Para tamaños de fuentes, es recomendado siempre utilzar las unidades rem.

### Selectores

Los selectores de css son patrones utilizados para seleccionar uno o varios elementos, a los que se aplicarán los estilos definidos.

Existen una gran cantidad de selectores que puedes consultar en [W3 Schools](https://www.w3schools.com/cssref/css_selectors.asp). Aquí solo mencionaremos los más importantes

```css
.claseX {
  /* Estilos que se aplicaran a elementos con esta clase */
}
```

```css
#idX {
  /* Estilos que se aplicaran a elementos con este ID */
}
```

```css
button {
  /* Estilos que se aplicaran a todos los elementos del tipo button */
}
```

```css
* {
  /* Caracter especial, selecciona todos los elementos */
}
```

```css
button.claseX {
  /* Selecciona todos los elementos del tipo button que tengan la clase especificada */
}
```

```css
div p {
  /* Selecciona todos los elementos <p> que estén dentro de un elemento <div> */
}
```

### Shorthands o Abreviaturas

Para la mayoría de propiedades de CSS, existen abreviaturas (shorthands) que nos sirven para establecer muchas propiedades al mismo tiempo.

Por ejemplo, para la propiedad margin, podemos especificar cada propiedad por separado:

```css
elemento {
  margin-right: 10px;
  margin-left: 10px;
  margin-bottom: 10px;
  margin-top: 10px;
}
```

O podemos especificar todas al mismo tiempo

```css
elemento {
  margin: 10px;
}
```

Tambien podemos especificar desde dos hasta cuatro valores, en cuyo caso se asignan de la siguiente manera:

- 2 valores

  ![CSS 2 valores](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties/border2.png)

- 3 valores

  ![CSS 3 valores](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties/border3.png)

- 4 valores

  ![CSS 4 valores](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties/border4.png)

Algunos elementos tienen abreviaturas especificas diferentes, que puedes consultar en la documentacion.

### Display

La propiedad `display` define como se muestra un elemenot. Establece si un elemento se trata como un bloque o un elemento en línea, así como la estructura que tendrán sus hijos, como grid o flex.

- **Elementos en bloque**: El elemento genera un cuadro de elemento de bloque, lo que genera saltos de línea tanto antes como después del elemento cuando se encuentra en flujo normal. \
  El elemento ocupa todo el espacio horizontal disponible.

```css
element {
  display: block;
}
```

- **Elementos en línea**: El elemento genera uno o más cuadros de elementos en línea que no generan saltos de línea antes o después de ellos mismos. En flujo normal, el siguiente elemento estará en la misma línea si hay espacio.

```css
element {
  display: inline;
}
```

- **None**: El elemento será ocultado de la pantalla.

```css
element {
  display: none;
}
```

- **Flex**: El elemento se comporta como un elemento en bloque y establece su contenido de acuerdo al modelo de flexbox.

```css
element {
  display: flex;
}
```

- **Grid**: El elemento se comporta como un elemento en bloque y establece su contenido de acuerdo al modelo de grid.

```css
element {
  display: grid;
}
```

### Width (Ancho) y Height (Altura)

Las propiedades `width` y `height` definen las medidas del ancho y alto, respectivamente, de un elemento.

```css
.xyz {
  width: 100px;
  height: 50px;
  /* Aplica un ancho de 100px y una altura de 50px
   a todos los elementos con la clase xyz */
}
```

Si se usa el valor especial auto, y se especifica solo una de las propiedades, la otra se calcula automaticamente, respetando las proporciones de la imagen.

```css
.xyz {
  width: 100px;
  height: auto;
  /* Aplica un ancho de 100px y una altura calculada
  automáticamente a todos los elementos con la clase xyz */
}
```

### Bordes

La abreviatura _border_ define las siguientes propiedades de CSS:

- border-color: Define el color del borde de un elemento
  - Si no especifica el color, el valor por defecto es: _current_color_
- border-style: Define el estilo de la línea del borde de un elemento
  - Si no se especifica el estilo, el valor por defecto es: _none_
- border-width: Define el ancho del borde de un elemento
  - Si no se especifica el ancho, el valor por defecto es: _medio_

La propiedad `border` puede ser especificada utilizando uno, dos o tres valores de la siguiente manera:

```css
elemento {
  /*      ancho | estilo | color */
  border: medium dashed green;

  border: solid;

  border: 2px dotted;

  border: outset #f33;
}
```

Atributo utilizado para dar color a todos los bordes de algún elemento

```css
.elemento-verde {
  border-color: #000;
  /* Aplica borde negro a los botones con la clase elemento-verde */
}
```

### Márgenes

La propiedad `margin` espeficia los márgenes de un elemento.

```css
.contenedor {
  /* Aplica 10px de márgen hacia todos los lados a los elementos con la clase contenedor */
  margin: 10px;

  /* Centra el contenido del bloque horizontalmente y pone un margen vertical de 10px */
  margin: 10px auto;
}
```

### Padding

La propiedad `padding` establece un espacio entre el borde y el contenido de un elemento

```css
.contenedor {
  padding: 15px;
  /* Aplica 15px de padding hacia todos los lados a los elementos con la clase contenedor */
}
```

### Color

Atributo utilizado para dar color al texto

```css
p {
  color: red;
  /* Aplica color rojo a los elementos párrafo */
}
```

### Background-Color

Atributo utilizado para dar color de fondo a los elementos

```css
.boton-verde {
  background-color: green;
  /* Aplica fondo verde a los elementos con la clase boton-verde */
}
```

### Fuentes y Texto

La propiedad `font-family` refiere a la fuente que utiliza el texto. Todos los elementos heredan las mismas `font-family` y `font-size` definidos en el elemento html.

La propiedad `font-weight` define el grueso o el peso de la letra, algunos de los pesos disponibles son:

- bold
- normal
- Un valor numérico entre 100 y 900

```css
html {
  font-size: 10px;
  font-family: "Open Sans", sans-serif;
  font-weight: bold;
}
```

La propiedad `text-align` establece la alineación horizontal del texto dentro de un elemento.

```css
elemento {
  /* Alinea el texto a la izquierda */
  text-align: start;

  /* Alinea el texto a la derecha */
  text-align: end;

  /* Centra el texto */
  text-align: center;

  /* Justifica el texto */
  text-align: justify;
}
```

## Ejercicio del Día 2 (CSS)

Para reforzar los conocimientos adquiridos, se les pedirá que realicen un ejercicio, utilizando lo aprendido en esta sección.

### Descripción del Ejercicio

Deberás crear una archivo CSS (`styles.css`) con el cual deberás mejorar el diseño del archivo (`pagina.html`) del Ejercicio del Día 1 para cumplir las siguientes características:

- Cambiar el tipo de fuente de todo el texto.
- Al documento entero (body)

  - Establecer un ancho de 60% del ancho de la ventana grafica.
  - Centrar el contenido del body en la venta
  - Cambiar el color de fondo por el color que prefieras
    Recomendado: #ddd

- Cambiar las dimensiones de la imagen. Establecer la anchura como de 200px, y la altura automaticamente.

- Al Titulo, aplicar:

  - Tamaño de fuente de 36px
  - Ancho del 100%
  - Centrarlo
  - Borde solido de color negro de 4px
  - Aplicar este borde _**solo**_ a la parte inferior
    (_Investigar_)

- Al Indice, aplicar:

  - Borde sólido de color gris, con un ancho de 2px.
  - Haz que el borde sea redondeado (_Investigar_)
  - Padding vertical de 10px, y horizontal de 25px.
  - Margen inferior de 20px.

- A la sinopsis, aplicar:

  - Justificar el texto
  - Tamaño de letra de 20px

- A la lista del elenco, aplicar:

  - Cambiar el estilo de las viñetas para que sean cuadradas (_Investigar_)

- A la tabla, aplicar:
  - Un margen negro de 1px a cada celda.
  - Dar padding de 10px a cada celda
  - Colocar el texto de la primera columna en negritas (_Investigar_)
