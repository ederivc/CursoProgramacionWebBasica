# CSS

## Componentes Básicos de CSS

### Display

La propiedad display establece si un elemento se trata como un bloque o un elemento en línea, así como la estructura que tendrán sus hijos, como grid o flex.

- **Elementos en bloque**: El elemento genera un cuadro de elemento de bloque, lo que genera saltos de línea tanto antes como después del elemento cuando se encuentra en flujo normal.

```css
element {
  display: block;
}
```

- **Elementos en línea**: El elemento genera uno o más cuadors de elementos en línea que no generan saltos de línea antes o después de ellos mismos. En flujo normal, el siguiente elemento estará en la misma línea si hay espacio.

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

### Selectores

Patrones utilizados para seleccionar uno o varios elementos.

```css
.clase-botones {
  /* Estilos que se aplicaran a botones con dicha clase */
}
```

```css
#idBoton {
  /* Estilos que se aplicaran a botones con dicho ID */
}
```

```css
button {
  /* Estilos que se aplicaran a todos los botones */
}
```

```css
* {
  /* Selecciona todos los elementos */
}
```

```css
element.clase {
  /* Selecciona todos los elementos que tengan la clase especificada */
}
```

```css
div p {
  /* Selecciona todos los elementos <p> que estén dentro de un elemento <div> */
}
```

### Unidades

Para tamaños de fuentes, es recomendado siempre utilzar 'rem'

- vh - 1% de la altura de la ventana gráfica
- vw - 1% del ancho de la ventana gráfica
- rem - Tamaño de la letra del elemento raíz
- em - Referencia al tamaño de letra del elemento padre
- px - Pixeles

### Márgenes

Atributo utilizado para establecer los márgenes de algún elementos

```css
.contenedor {
  margin: 10px;
  /* Aplica 10px de márgen hacia todos los lados a los elementos con la clase contenedor */
}
```

### Padding

Atributo que establece un espacio entre el borde y el contenido de un elemento

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
  /* Aplica fondo verde a los botones con la clase boton-verde */
}
```

### Border-Color

Atributo utilizado para dar color a todos los bordes de algún elemento

```css
.boton-verde {
  border-color: #000;
  /* Aplica borde negro a los botones con la clase boton-verde */
}
```

### Width y Height

La propiedad widh define el ancho que tendrá cierto elemento, mientras que la propiedad height se refiere al alto del elemento.

```css
.boton-verde {
  width: 10rem;
  height: 4rem;
  /* Aplica un ancho de 10rem y un alto de 4rem a los botones con la clase boton-verde */
}
```

### Fuentes y Texto

La propiedad _font-family_ refiere a la fuente que utiliza el texto. Todos los elementos heredan las mismas _font-family_ y _font-size_ definidos en el elemento html.

```css
html {
  font-size: 10px;
  font-family: "Open Sans", sans-serif;
}
```

### Variables

Las propiedades personalizadas o variables son definidas utilizando una notación específica comenzando por un doble guión (--) y deben ser declaradas dentro de un bloque de declaración, e.g.

```css
elemento {
  --main-bg-color: brown;
}
```

Pueden son generalmente declaradas dentro de la pseudo clase ':root' para que puedan ser aplicadas de manera global de la siguiente manera:

```css
:root {
  --main-bg-color: brown;
}
```

Para acceder al valor de una variable, se debe especificar el nombre de variable dentro de la función `var()`:

```css
element {
  background-color: var(--main-bg-color);
}
```
