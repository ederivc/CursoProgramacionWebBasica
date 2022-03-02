# Variables, Especificidad y Flexbox

## Variables

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

## Especificidad

La especificidad es la manera en que los navegadores web deciden cuáles propiedades de CSS son más relevantes para un elemento, y por lo tanto, cuáles reglas se le aplicarán al elemento.

Las reglas de especificidad se basan en los selectores de CSS que utilizamos.

Los siguientes selectores incrementan la especificidad, en orden:

1. Selectores de tipo (`h1`, `p`, `a`, `button`) y pseudo-elementos (`::before`, `::after`)
2. Selectores de clase (`.clase`, `.ejemplo`), atributos (`[type="radio"]`), y pseudo-clases (`:hover`)
3. Selectores de ID (e.g. `#ejemplo`)

El selector universal (`*`), combinadores (`+`, `>`, `~`, `||`) y la pseudo clase de negación (`:not()`) no tienen efecto sobre la especificidad.

Los estilos declarados en línea directamente en el HTML (`style="font-weight: bold;"`) siempre sobreescriben los estilos en los archivos CSS, y por lo tanto se puede decir que tienen la especificidad más alta

Cuando se utiliza la regla `important` en la declaración de un estilo, esta declaración sobrescribe cualquier otra declaración. Aunque _!important_ no está directamente relacionada con especificidad, interactúa directamente con ella. Usar _!important_, es una mala práctica que debería ser evitada porque complica la depuración de código al romper la cascada natural de estilos en la hoja de estilos.

```css
elemento {
  color: red !important;
}
```

Algunas reglas básicas:

- Siempre buscar una manera de utilizar especificidad antes de considerar utilizar `!important`.
- Únicamente utilizar `!important` en el css específico de una página, para sobreescribir css externo (como puede ser el de librerías como Bootstrap o normalize.css).
- Nunca usar `!important` en css para sobrescribir estilos definidos localmente en otro archivo.

Los estilos directamente establecidos sobre un elemento siempre tomarán precedencia sobre los estilos heredados, sin importar la especificidad de la regla heredada.

Consideremos el siguiente HTML y CSS.

```html
<html>
  <body id="parent">
    <h1>Here is a title!</h1>
  </body>
</html>
```

```css
#parent {
  color: green;
}

h1 {
  color: purple;
}
```

Si solo consideramos la regla CSS para `#parent`, el texto en el H1 se mostraría de color verde. Esto debido a que los elementos hijos heredan propiedades CSS de sus padres.

Sin embargo, al especificar en el CSS la regla para los elementos H1, ahora el texto se mostraría en color morado. Esto debido a que fue el color definido directamente sobre la etiqueta H1, sin importar el color que ha heredado de su padre.

## Flexbox

El modulo de cajas flexibles, conocido como "Flexbox", fue diseñado como una modelo de layout uni-dimensional, y como un método para acomodar y distribuir elementos en una interfaz gráfica.

Cuando se trabaja con flexbox, es necesario pensar en términos de dos ejes. El eje principal, y el eje transversal. El eje principal está definido por la propiedad `flex-direction`. EL eje transversal es el eje perpendicular al eje principal.

### Eje principal

El eje principal está definido por `flex-direction`, al cual le podemos dar cuatro posibles valores:

- row
- row-reverse
- column
- column-reverse

Al escoger `row` o `row-reverse`, el eje principal será en la dirección horizontal.

![flex row](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox/basics1.png)

Al escoger `column` o `column-reverse`, el eje principal será en la dirección vertical.

![flex column](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox/basics2.png)

### Contenedor flex

A un área de un documento que utiliza flexbox se le llama un contenedor flex, o _flex container_.

Para crear un contenedor flex, se debe establecer la propiedad `display` al valor `flex` o `flex-inline`. Al hacer esto los hijos del elemento se convertirán en elementos flex o _flex items_.

```css
.box {
  display: flex;
}
```

Como todas las propiedades CSS, los contenedores flex tienen una serie de valores iniciales por defecto.

- El eje principal del contenedor flex es horizontal. (Equivalente al valor `row`).
- Los elementos flex comienzan al borde del contenedor flex, en dirección del eje principal. (Equivalente al valor `flex-start`).
- Los elementos flex no crecen en la dirección del eje principal.
- Los elementos flex crecen para llenar el espacio disponible en la dirección del eje transversal.
- La propiedad `flex-basis` tiene el valor `auto`.
- La propiedad `flex-wrap` tiene el valor `nowrap`.

### Flex-direction

La propiedad `flex-direction` nos permite cambiar la dirección del eje principal.

```css
.box {
  display: flex;
  flex-direction: row;
}
```

### Flex-wrap

Aunque flexbox es un modelo uni-dimensional, es posible hacer que los elementos flex se acomoden en múltiples líneas. Al hacer esto, podemos considerar cada línea como un contenedor flex nuevo.

Para hacer que los elementos hagan _wrap_, es decir, salten a una nueva línea, usaremos la propiedad `flex-wrap`.

```css
.box {
  display: flex;
  flex-wrap: wrap;
}
```

### Flex-flow

Podemos combinar las propiedades `flex-direction` y `flex-wrap` en la propiedad abreviada `flex-flow`.

```css
.box {
  display: flex;
  flex-flow: row wrap;
  /* Esto es equivalente a establecer:
  flex-direction: row;
  flex-wrap: wrap; */
}
```

### Flex-items

Para tener más control sobre los elementos flex, podemos modificarlos de manera directa. Esto lo hacemos a través de las siguientes tres propiedades:

- flex-basis
- flex-grow
- flex-shrink

#### Flex-basis

Flex-basis define el tamaño inicial de un elemento flex. El valor por defecto de esta propiedad es _auto_, lo cual provoca que el navegador establezca el tamaño en base a la altura o anchura del elemento.

Si los elementos no tienen un tamaño definido, entonces el tamaño del contenido es usado para el flex-basis. Es por esto que al momento de definir el _display: flex_ en el padre para crear los flex items, todos se mueven en un renglón y toman únicamente el espacio que necesitan para mostrar su contenido.

Esta propiedad acepta valores como valores tamaños (1, 10px, 1rem), valores numéricos (0, 1) o porcentajes (50%, 100%).

```css
.box {
  display: flex;
}

.box > * {
  flex-basis: 100%;
}
```

#### Flex-grow

Cuando el valor de esta propiedad se establece a un entero positivo (generalmente 1), los elementos flex tienen permitido crecer en dirección del eje principal, en concordancia con su `flex-basis`. Esto provoca que los objetos se estiren y tomen todo el espacio disponible en el eje, o una proporción del espacio disponible si hay más objetos que tienen permitido crecer.

La propiedad `flex-grow` puede ser utilizada para distribuir el espacio proporcionalmente.

En el siguiente ejemplo, tenemos tres elementos flex (primero, segundo, tercero). Le damos un valor de `flex-grow` de 2 al primero, y a los otros les establecemos un valor de 1 a cada uno. Al momento de distribuir el espacio disponible entre los elementos, tendremos 4 partes en total (2 + 1 + 1). 2 partes del espacio serán dadas al primer elemento y 1 parte a cada uno de los otros dos.

```css
.padre {
  display: flex;
}

/* El valor por defecto de flex-grow es 0 */

.primero {
  flex-grow: 2;
}

.segundo,
.tercero {
  flex-grow: 1;
}
```

#### Flex-shrink

Mientras que la propiedad `flex-grow` se encarga de distribuir el espacio disponible en el eje principal, haciendo crecer los elementos, `flex-shrink` controla cómo pueden reducir su tamaño los elementos.

Si no tenemos espacio en el contenedor para mostrar todos los objetos, y se estableció un valor de entero positivo para `flex-shrink`, entonces los objetos pueden reducir su tamaño más allá de su `flex-basis`.

```css
.box {
  display: flex;
}

.box > * {
  flex-shrink: 1;
  /* El valor por defecto de flex-shrink es 1 */
}
```

### Flex

La manera más común de establecer las propiedades de `flex-grow`, `flex-shrink` y `flex-basis` es mediante la abreviación `flex`. `flex` permite establecer los tres valores en ese orden: grow, shrink y basis.

```css
.box {
  display: flex;
}

.box > * {
  flex: 1;
  /* Esto es equivalente a:
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 0; */
}
```

### Align-items

La propiedad `align-items` define como se alinean los elementos en el eje transversal. Su valor inicial es `stretch`. Este valor hace que los elementos crezcan en el eje transversal para ocupar todo el espacio disponible.

Los posibles valores que puede tomar `align-items` son:

- stretch
- flex-start
- flex-end
- center

### Jusitify-content

La propiedad `justify-content` define como se alinean los elementos en el eje principal. Su valor inicial es `flex-start`, el cual hace que los elementos se acomoden al principio del borde del contenedor.

Los posibles valores que puede tomar align-content son:

- flex-start
- flex-end
- center
- space-around
- space-between
- space-evenly

## Ejercicio del Día 3 (Flexbox)

Para reforzar los conocimientos adquiridos, se les pedirá que realicen un ejercicio, utilizando lo aprendido en esta sección.

### Descripción del Ejercicio

Deberás modificar tus archivos creados en el Ejercicio del Día 2 para cumplir las siguientes características:

- Modificar la sección de información para que sean dos columnas, la primera columna debe contener la imágen de la serie o película seleccionada mientras que la segunda debe contener el texto redactado para la sinopsis.
- Crear una sección con dos columnas que contenga:
  - En la primera columna, deben utilizar un display flex para mostrar el elenco: su nombre y una imagen de la persona justo debajo del texto
  - En la segunda columna, debera estar dividia en otras dos columnas verticales. En una deberas mostrar la tabla de información general, y en la otra la sección del trailer

La distribución de los elementos que se debe obtener puede observarse en la siguiente imágen, se colocaron bordes de color alrededor de cada elemento para facilitar su identificación:

![Imagen con bordes](https://i.imgur.com/3zdxjCQ.png)

![Imagen sin bordes](https://i.imgur.com/OulSopU.png)
