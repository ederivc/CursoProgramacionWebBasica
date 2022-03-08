# Django

## Instalación de librerías en python

Para utilizar librerías en python, haremos uso de la herramienta `pip`, y `venv`. En Windows, estas herramientas vienen con python. En Linux, estas herramientas deben instalarse aparte.

Para instalar una librería, basta con ejecutar el siguiente comando en una consola

```
pip install nombreLibreria
```

Sin embargo, debemos evitar hacer esto, ya que esto instala librerías en el entorno global de python, lo cual puede traer problemas, si diferentes programas necesitan diferentes librerías.

Para manejar correctamente las librerías, debemos crear un entorno virtual (venv)

### Entornos Virtuales

Los entornos virtuales son versiones de python que están aisladas de la instalación global de python. En otras palabras, estas versiones son locales a nuestro proyecto.

Para crear un entorno virtual, se ejecuta el siguiente comando:

```
python -m venv directorio
```

Donde directorio es la carpeta donde se creará el entorno virtual. Para este curso, usaremos el directorio `.venv`.

Una vez creado el entorno virtual, debemos activarlo. El entorno virtual se activa de manera distinta en cada plataforma.

Para windows, en CMD:

```
.venv\Scripts\activate
```

Para windows, en Powershell:

```
.venv\Scripts\Activate.ps1
```

Para linux, en bash:

```
source .venv/bin/activate
```

Es importante tener en cuenta que el entorno virtual NO se puede compartir, y no se debe incluir en el control de versiones. Cada desarrollador debe crear su propio entorno virtual en su PC.

## Instalación de Django

Para instalar django, basta con ejecutar el siguiente comando.

```
pip install Django
```

## Crear un Proyecto de Django

```
django-admin startproject PROJECT_NAME
```

Esto nos creará un directorio con la siguiente estructura

```
PROJECT_NAME/
    manage.py
    PROJECT_NAME/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```

Como recomendación, sugerimos utilizar el siguiente comando, dentro de la carpeta del proyecto, para tener una estructura más limpia:

```
django-admin startproject config .
```

Suponiendo que lo hemos ejecutado dentro de la carpeta PROJECT_NAME, obtendremos la siguiente estructura:

```
PROJECT_NAME/
    manage.py
    config/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```

Después, crearemos una app de django.

`python manage.py startapp APP_NAME`

Esto nos crea la siguiente estructura:

```
PROJECT_NAME/
    manage.py
    config/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
    APP_NAME/
        __init__.py
        admin.py
        apps.py
        migrations/
            __init__.py
        models.py
        tests.py
        views.py
```

## Ejecutar la aplicación de Django

Antes de correr por primera vez la aplicación, deberemos añadirla a la lista de aplicaciones en `PROJECT_NAME/settings.py` o `config/settings.py`.

```python
INSTALLED_APPS = [
    'APP_NAME',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

Para ejecutar una aplicación de Django, primeramente debemos preparar la base de datos. Por defecto, Django usa un archivo de sqlite como base de datos, por lo que durante el desarrollo no es necesario instalar una base de datos como mysql o postgres.

```
python manage.py makemigrations
python manage.py migrate
```

Cada vez que realicemos cambios a los modelos de la base de datos de Django, debemos ejecutar estos comandos para ejecutar los cambios.

Para ejecutar el servidor de la aplicación, se usa el siguiente comando.accedidas

```
python manage.py runserver
```

## `Views`

Una `view` puede ser vista como un "tipo" de página dentro de la aplicación de Django, normalmente cumple con una función específica y tiene un `template` específico.

En django, las páginas web y otro contenido son entregados por `views`. Cada `view` es representada por una función o método. Django escogerá la `view` revisando la URL solicitada.

```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Esta es una respuesta HTML")
```

## `Templates`

Los templates son una manera conveniente de generar HTML de manera dinámica. Estos templates contienen partes estáticas así como una sintaxis especial para describir como se insertará el contenido dinámico.

### Contexto

Cada plantilla se renderiza con un contexto. El contexto es un diccionario de python.

### Variables

Las variables son definidas en el diccionario de contexto pasado al template.

Para acceder a atributos de una variable, es posible utilizar un punto (.) y como subíndice ([]).

```jinja
{{ foo.bar }}
{{ foo["bar"] }}
```

Las llaves dobles no son parte de la variable, sino la sentencia para imprimir. Al acceder a una variable dentro de una etiqueta no es necesario poner llaves alrededor de la variable.

Al acceder a un atributo o variable que no existe, se obtendrá un valor indefinido. Lo que se hace con ese valor indefinido depende de la configuración: el comportamiento por defecto es evaluarlo como una cadena vacía si se imprime o se itera y crear una excepción para todas las demás operaciones.

### Filtros

Las variables pueden ser modificadas por filtros. Los filtros son separados de la variable por el símbolo de barra (|), y muchos de ellos tienen argumentos adicionales opcionales entre paréntesis. Se pueden encadenar múltiples filtros donde la salida de un filtro es la entrada del siguiente.

Se puede consulta una lista de los filtros incorporados en jinja en el siguiente [link](https://jinja.palletsprojects.com/en/3.0.x/templates/#builtin-filters)

## `Routes`

Para hacer que las views que creamos estén disponibles en nuestra página web, tenemos que colocarlas en el archivo de urls. Para esto crearemos el archivo `APP_NAME/urls.py`, con el siguiente contenido.

```python
from django.urls import path

from . import views

urlpatterns = [
    # /polls/
    path('', views.index, name='index'),
    path('person/<int:person_id>/', views.person, name='detail'),
    path('book/<int:book_id>/', views.book, name='detail'),
]
```

Luego, deberemos asegurarnos de incluir este archivo de urls en el archivo principal de urls (PROJECT_NAME/urls.py o config/urls.py)

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('books/', include('APP_NAME.urls')),
    path('admin/', admin.site.urls),
]
```

## `Models`

Cada modelo está representado por una clase que hereda de `django.db.models.Model`. Cada modelo tiene un número de variables donde cada una representa un campo en el modelo de la base de datos.

Cada campo es representado por una instancia de la clase Field, especificando el tipo de dato que tiene cada variable. Cada nombre de variable que especifiquemos será utilizado por django para declarar el nombre de la columna en la base de datos.

```python
from django.db import models

class Person(models.Model):
    name = models.CharField(max_length=200)

class Book(models.Model):
    name = models.CharField(max_length=200)
    person = models.ForeignKey(Person, on_delete=models.CASCADE, related_name="books")
```

Dentro de cada app que creemos, existirá un archivo `models.py`.

## Migraciones de la base de datos

El proceso de realizar cambios en los modelos de la base de datos consta de tres pasos:

1. Cambiar los modelos (en models.py)
2. Ejecutar el comando `python manage.py makemigrations` para crear las migraciones de dichos cambios
3. Ejecutar el comando `python manage.py migrate` para aplicar dichos cambios a la base de datos

### `makemigrations`

Cuando nosotros realicemos cambios en los modelos de la base de datos, debemos utilizar el comando `python manage.py makemigrations` para decirle a django que hemos realizado cambios y queremos que sean guardados en una migración.

Las migraciones son la forma que tiene django de guardar cambios en los modelos, contienen las instrucciones necesarias para django para poder manipular la base de datos y reflejar los cambios que hemos realizado en los modelos.

```
python manage.py makemigrations
```

### `migrate`

El comando `python manage.py migrate` es la manera de aplicar los cambios establecidos en las migraciones sobre la base de datos. Este comando toma todas las migraciones que no han sido aplicadas y las ejecuta sobre la base de datos, sincronizando los cambios que hayamos realizado.

```
python manage.py migrate
```

## `Static files`
