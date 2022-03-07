# Python

Python es un lenguaje de programación orientado a objetos, de tipado dinámico, fácil de aprender.

En este curso cubriremos la funcionalidad básica de python, comparándolo con otros lenguajes de programación. Sin embargo, recomendamos que leas el tutorial de python, para tener una mejor compresión del lenguaje.

[Tutorial de Python](https://docs.python.org/3/tutorial/)

## El intérprete de Python

Podemos ejecutar código de dos maneras. Una es haciéndo uso del intérprete. Si tenemos instalado python, y escribimos en la consola `python`, podremos acceder a un intérprete, el cual ejecutará el código conforme lo escribamos.

En este sentido, python es diferente a Java y C++, y similar a Javascript, ya que es un lenguaje interpretado, que no necesita ser compilado antes de ejecutarse.

La otra manera de ejecutar un archivo de python es con el comando `python`, seguido de la ruta del archivo que queremos ejecutar.

`python archivo.py`

## Tipos

En python, tenemos algunos los siguientes tipos básicos:

- bool
- int
- float _(Equivalente a `double` en Java)_
- str
- list
- tuple
- set
- dict
- None

### list

Una lista en python es un arreglo dinámico. Las listas pueden contener cualquier objeto, sin importar su tipo.

```python
[0, 1, 2, 3, 4]
```

### tuple

Un tuplo en python es exactamente igual a una lista, excepto que tiene la característica de ser inmutable. Es decir, una vez creado, un tuplo no puede ser modificado.

```python
(0, 1, 2, 3, 4)
```

### set

Un set en python es un conjunto. Una secuencia de objetos, similar a una lista, pero que difiere en que está optimizado para saber si un objeto pertenece al conjunto.

A diferencia de una lista, no podemos sacar elementos de un conjunto usando un índice. Sólo podemos sacar todos los elementos de conjunto, y revisar si un elemento se encuentra en el conjunto.

```python
{0, 1, 2, 3, 4, 5}
```

### dict

Un diccionario en python es un hashmap o hashtable. Es una estructura de datos que asocia una llave con un valor. Si le proporcionamos una llave, nos devuelve su valor correspondiente.

```python
diccionario = {}
diccionario["nombre"] = "Manzana"
diccionario["precio"] = 200
```

Nótese que a pesar de que las llaves son la sintaxis para crear conjuntos, un par de llaves vacías crea un diccionario vacío, y no un conjunto.

Para crear un conjunto vacío, podemos hacer uso de `set()`

### None

`None` es el valor nulo, equivalente a `null` en Java. Denota que un valor no existe.

## Funciones básicas

```python
# Imprimir a consola y leer de la consola
print("Esto se imprime a la consola")
# Toma entrada del teclado desde la consola, y la guarda en x.
entrada = input()

lista = [0, 1, 2, 3]
x = 10

# Casteos de tipos
int(x) # Convierte x a entero
float(x) # Convierte x a decimal
str(x) # Convierte x a una cadena

# Funciones miscelaneas
abs(x) # Valor absoluto de X
len(lista) # Longitud (cantidad de elementos) de una secuencia o lista
min(lista) # Valor mínimo de una lista o secuencia
max(lista) # Valor máximo de una lista o secuencia
all(lista) # Verdadero si todos los elementos de la secuencia son verdaderos
any(lista) # Verdadero si cualquier elemento de la secuencia es verdadero
```

## Operadores

En python, los operadores son prácticamente los mismos que en otros lenguajes. Entre las pocas excepciones se encuentran:

- `**` operador de exponenciación
- `//` operador de división entera

Además, en python los operadores de comparaciones lógicas son palabras, en vez de símbolos

- `and` (en vez de `&&`)
- `or` (en vez de `||`)
- `not` (en vez de `!`)

## Herramientas de control de flujo

### `if`

Nótese que las condicionales en python no necesitan paréntesis

```python
if x < 0:
    print("X menor a cero")
elif x == 0:
    print("X es cero")
elif x == 1:
    print("X es uno")
else:
    print("X es mayor a uno")
```

### `for` y `while`

En python no existe el for convencional de Java. Todos los for son como el `for..of` de Java o Javascript.

En python, `for` itera sobre cualquier secuencia, ya sean listas, cadenas de texto o cualquier otra estructura; en el orden en el que aparecen en la secuencia.

```python
words = ["cat", "window", "car"]
for w in words:
    print(w)

# Imprime las palabas una a la vez
```

El `while` de python es exactamente igual al de Java. Se ejecuta mientras su condición sea verdadera.

```python
x = 10
while (x > 0):
    x = x - 1
```

### `range`

Cuando necesitamos iterar sobre una secuencia de números, podemos utilizar la función `range()` para generar una progresión aritmética.

```python
for i in range(5):
    print(i)

# Imprime los números del 0 al 4

for i in range(10, 20):
    print(i)

# Imprime los números del 10 al 19
```

### `break`, `continue` y `pass`

La sentencia `break`, termina un ciclo, en el caso de tener ciclos anidados, `break` termina el ciclo más anidado.

```python
for i in range(10):
    if i == 2:
        break
```

La declaración `continue`, continúa con la siguiente iteración del ciclo, sin ejecutar el resto del código del ciclo actual.

```python
for i in range(10):
    if i == 2:
        continue
        print(i)
        # Esta línea nunca se ejecuta
```

La sentencia `pass` no hace nada. Se puede utilizar cuando se requiere una sentencia por la sintaxis pero el programa no requiere ninguna acción.

```python
for i in range(10):
    if i == 2:
        pass
```

### Funciones

La palabra `def` se usa para definir funciones, seguida del nombre de la función y la lista de parámetros entre paréntesis

```python
def suma(a, b):
    return a + b
```

Las funciones pueden tener valores por default

```python
def suma(a, b=5):
    return a + b
```

En python, podemos llamar a una función con argumentos posicionales:

```python
suma(5, 8)
```

O con argumentos con nombre

```python
suma(a=5, b=8)
```

## Manejo de excepciones

Al igual que en Java, en python podemos lanzar y atrapar excepcios. En vez de `try` y `catch`, usamos `try` y `except`. También, opcionalmente, podemos incluir un `finally`, al igual que en Java.

```python
try:
    # Código que puede arrojar una excepción
except Exception as e:
    # Código para manejar la expeción
finally:
    # Código que se ejecuta en ambos casos
```

## Clases

En python, podemos crear clases de la siguiente manera:

```python
class Rectangle:
    # Constructor
    def __init__(self, width, height):
        self.width = width
        self.height = height

    # Metodo
    def area(self):
        return self.witdh * self.height
```

En python, todos los métodos de una clase llevan como primer argumento `self`. Éste hace referencia a la instancia de la clase.

Para asignar variables a una instancia de la clase, se las asignamos al objeto self dentro del constructor.

### Herencia

Para hacer herencia en python, la sintaxis es la siguiente:

```python
class NombreClaseDerivada(NombreClaseBase):
    # Cuerpo de la clase
```

A direrencia de Java, en python existe la herencia múltiple. Una clase con múltiples clases base se define de la siguiente manera:

```python
class NombreClaseDerivada(Base1, Base2, Base3):
    # Cuerpo de la clase
```

### Variables privadas

En python, no existen las variables privadas, variables que no puedan ser accedidas fuera de un objeto. Sin embargo, existe una convención que menciona que cualquier variable que se desee que no sea pública, debe tener su nombre precedido por un guión bajo.

```python
class Rectangle:
    # Constructor
    def __init__(self, width, height):
        self.width = width
        self._height = height

    # Metodo
    def area(self):
        return self.witdh * self._height
```
