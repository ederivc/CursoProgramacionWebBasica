# Javascript

Javascript es el lenguaje de programación orientado a objetos que usan las páginas web para ejecutar código en un navegador web.

## Introducción a Javascript

Asumiendo que ya sabes programar en otros lenguajes de programación, como Java, C++ o Python, a continuación se muestran acciones comunes que realizamos en otros lenguajes de programación, y la forma de realizarlas en Javascript.

Para probar todos estos ejemplos, puedes abrir una nueva pestaña de tu navegador, para abrir las herramientas de desarrollador, y acceder a una consola de Javascript.

### Print (console.log)

Para imprimir a la consola del navegador, podemos hacer uso de `console.log()`. Esto es similar a hacer `print()` en python, o `System.out.println()` en Java.

```javascript
console.log("Esto se muestra en la consola")
```

### Alert

Si queremos mostrar un mensaje en el navegador sin abrir la consola, podemos usar `alert()`. Esta función es similar a `console.log()`, pero muestra la información en un diálogo, en vez de en la consola.

### Tipos de datos

Al igual que en otros lenguajes de programación, Javascript tiene tipos de datos primitivos. Estos son:

- **number**. Para todos los tipos de números. No hay distinción entre enteros y flotantes. Todos los números en Javascript son `double` de 64 bits, igual que los `double` de Java.
- **boolean**. Verdadero y falso (`true`, `false`). Exactamente igual que en otros lenguajes.
- **string**. Una cadena, igual que en otros lenguajes. Javascript no tiene el tipo `char`, solo cadenas.
- **null**. Un valor nulo. Igual al null de Java o al None de Python.
- **undefined**. Un valor no definido. No tiene equivalencia directa en otros lenguajes. A diferencia de `null`, que denota explícitamente la ausencia de un valor, podemos decir que `undefined` lo hace implícitamente. Las variables sin definir o sin valor asignado, y las funciones que no retornan un valor explícito, se evalúan a `undefined`.

A diferencia de lenguajes como Java o C++, y al igual que Python, Javascript es un lenguaje de tipado dinámico. No es necesario especificar los tipos de las variables al declarlas.

### Declarar variables

En Javascript, podemos declarar una variable global usando `var`.

```javascript
var x = 100;
```

Debido a que el _scope_ de var solamente es a nivel global o de función, en Javascript moderno se evita hacer uso de var.

En vez de var utilizamos `let` y `const`. La siguiente declaración en Javascript:

```javascript
const x = 100;
let x = 100;
```

Es equivalente a esta declaración en Java:

```java
final int x = 100;
int x = 100;
```

La diferencia entre `let` y `const`, es que `const` no nos permite modificar o reasignar el valor de la variable, mientras que `let` si nos lo permite.

### Arreglos

Los arreglos de Javascript se construyen igual que los de Python, e igual a los arreglos de Java.

```javascript
const arreglo = [1, 2, 3, 4, 5];
```

### Operadores

En Javascript, los operadores aritméticos y de comparación son prácticamente iguales a los de otros lenguajes como Java. Sin embargo, hay una excepción importante.

Existen dos operadores de igualdad. Uno es la igualdad doble `==` y el otro es la igualdad triple `===`. Ambos operadores son iguales a `==` en python, y a `.equals()` en Java.

La diferencia entre ellos, es que la igualdad doble coerce los tipos, es una igualdad "floja", mientras que la igualdad triple no coerce los tipos, es una igualdad estricta.

Con la igualdad doble, las siguientes expresiones evalúan a `true`. Con la igualdad triple, todas evalúan a `false`.

```javascript
0 == "0"
"0" == 0
0 == false
1 == true
"" == false
0 == ""
null == undefined
```

Debido a la confusión que esto puede ocasionar, y a las reglas poco intuitivas de coersión de tipos, recomendamos utilizar siempre la igualdad triple. La única excepción es el caso de

```javascript
null == undefined
```

Existen situaciones en las que queremos revisar si una variable es `null` o `undefined`, sin que nos importe cuál de las dos es. En estos casos, como `null` es igual a `undefined` en la igualdad doble, podemos utilizar cualquiera de los dos valores para revisar ambos.

```javascript
if (x == undefined) {
    // Ambas condiciones son equivalentes
}
if (x == null) {

}
```

### Ciclos

Los ciclos en Javascript son idénticos a los de Java.

Ciclo for:

```javascript
for (let i = 0; i < 10; i++) {
  console.log(i);
}
```

Ciclo while:

```javascript
let x = 0
while (x < 10) {
  console.log(x);
  x += 1;
}
```

SI queremos recorrer un iterable, como un arreglo, podemos usar for of:

```javascript
const arreglo = [0, 1, 2, 3, 4, 5]
for (const x of arreglo) {
    console.log(xx);
}
```

### Funciones

Existen dos maneras de declarar funciones en JS. Una es muy similar a un método en Java:

```javascript
function functionName(argument1, argument2)
{
  // cuerpo de la función
  return argument1 * argument2
}
```

La otra es lo que se conoce como _arrow functions_, funciones flecha.

```javascript
(argument1, argument2) => {
  argument1 * argument2
};
```

Ambas funciones son equivalentes, excepto que la segunda forma es _anónima_. Esto es, la función no tiene un nombre asignado.

A pesar de esto, podemos asignar una función flecha a una variable, y se comporta de manera similar a una función normal.

La diferencia principal entre ambos tipos de funciones, es que las funciones flechas no modifican el valor de `this` dentro de la función.

### Clases

Para definir una clase en Javascript, se hace de manera similar a Java.

```javascript
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  // Method
  calcArea() {
    return this.height * this.width;
  }
}
```

## Interactuando con el DOM

Para interactuar con los elementos HTML de una página web, debemos interactuar con el DOM (Document Object Model).

Podemos guardar un elemento HTML en una variable, para interactuar con el:

```javascript
const element = document.getElementById("id");
```

Una vez que tenemos el elemento en una variable, podemos manipular directamente sus propiedades. Por ejemplo, su estilo:

```javascript
const element = document.getElementById("id");
element.style.color = "red";
```

Una de las interacciones más comunes que realizaremos son con botones u otros elementos, y su propiedad `onclick()`:

```javascript
const button = document.getElementById("buttonId");
button.onclick = () => {
  alert("Boton Presionado");
};
```

Otra manipulación muy común que se realiza es cambiar la propiedad display de un elemento, para ocultarlo y mostrarlo en base a cierta lógica.

```javascript
const elemento = document.getElementById("elementoId");
// Ocultar elemento
elemento.style.display = "none";
// Mostrar elemento
elemento.style.display = "block";
```
