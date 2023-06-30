> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
* GUIA PARA CREAR UN CRUD CON DJANGO
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -


> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTE N°1 INSATALACION DE DEPENDECIAS
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1 Instalar:
Git
Xammp
SqlYog
Python
Visual Studio Code
Instalar la extesnion Python para Visual Studio Code

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
2 Con visual studio code abrir la carpeta
donde se guardara nuestro proyecto.
 
4 Instalar Django de manera global(terminal):

pip install Django==3.2.8

5 Crear proyecto Django:

django-admin.py startproject sistema .			 

8 Correr el servidor para confirmar que el pruyecto
se ha creado satisfactoriamente(terminal):

py manage.py runserver

9 Detener el servidor(terminal):

Control+c

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
10 Crear un entorno virtual (terminal):

py -m venv env

11 Activar entorno virtual(terminal):

env\scripts\activate

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
12 Instalar complementos en el entorno virtual(terminal):

pip install Django==3.2.8
pip install Pillow==9.3.0
pip install PyMySQL==1.0.2
pip install sqlparse==0.4.3

nota: recuerda que para instala las dependecias
debes estar conectado a internet.

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
13 Activar el servidor MySQL(xampp).

14 Crear una base de datos para el proyecto(sqlyog).

15 Conectar la base de datos con Django:

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'veterinaria_db',
        'USER': 'root',
        'PASSWORD': '',
        'HOST': 'localhost',
        'PORT': '3306'
    }
}

16 Importart modulo MySQL en sistema>_init_.py

import pymysql
pymysql.install_as_MySQLdb()

17 Correr el servidor(terminal) para verificar
que no haya ningun error de la conxion.
Si el servidor corre sin ningun problema
sisgnifica que la conexion ha sido exitosa, de
lo contraio aparece un mesaje de error en
la terminal.

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
17 Hacer migraciones de los modelos(tablas)
que vienen por defecto en nuestro proyecto(terminal).
Si todo esta bien deberian crearse unas tablas
en nuestra base de datos(revisar en sqlyog).

py manage.py migrate

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

18 Crear superusuario(terminal):

py manage.py createsuperuser


username:admin
email:yobanichicunque@gmail.com
password:12345

19 Ir a la base de datos en sqlyog, abrir la tabla auth_user,
y en los siguientes campos poner el nombre y apellido del usuario:

name:Yobani
lastname:Chicunque

20 Ir al Panel de administracion y loguearse con
username y password:

username:admin
password:12345

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
24 Crear dos aplicaciones
una app llamada mascota y la otra adopcion(terminal):


py manage.py startapp nombre-apliacion


25 Añadir la aplicacion en la configuracion del proyecto
en sistema>settings.py

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'adopcion',
    'mascota',
]
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
26 Configurar el lenguaje en sistema>settings.py

LANGUAGE_CODE = 'es-co'

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
21 Hacer modelos y relaciones 
en adopcion/models.py y mascota>models.py

from django.db import models


# Create your models here.


class Persona(models.Model):
    nombre = models.CharField(max_length=100)
    apellidos = models.CharField(max_length=100)
    edad = models.IntegerField()
    telefono = models.CharField(max_length=12)
    correo = models.EmailField()
    domicilio = models.TextField()

    def __str__(self):
        return '{} {}'.format(self.nombre, self.apellidos)

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
21 Hacer modelos y relaciones 
en  mascota>models.py

from django.db import models
from adopcion.models import Persona #Importamos el modelo Persona de la app adopcion


# Create your models here.


class Vacuna(models.Model):
    nombre = models.CharField(max_length=100)

    def __str__(self):
        return '{}'.format(self.nombre)


class Mascota(models.Model):
    nombre = models.CharField(max_length=100)
    sexo = models.CharField(max_length=20)
    edad_aproximada = models.IntegerField()
    fecha_rescate = models.DateField()
    persona = models.ForeignKey(
        Persona, null=True, blank=True, on_delete=models.CASCADE)
    vacuna = models.ManyToManyField(
        Vacuna, blank=True)

    def __str__(self):
        return '{}'.format(self.nombre)

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
22 Hacer las migraciones de los modelos(terminal):

py manage.py makemigrations
py manage.py migrate

Nota: Para hacer modificaciones de los modelos(tablas), por ejemplo, 
cambiar el nombre de los camposse edita el el modelo creado y se 
ejecutarn los dos comandos anteriores. Recuerda que para hacer hacer
las migraciones de los modelos de tus aplicaciones es necesario haber
creado un super usuario

py manage.py makemigrations
py manage.py migrate
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
23 Registrar los modelos en el admin.py de cada
aplicacion


##Regitrar modelos en app persona

from django.contrib import admin
from .models import Persona

admin.site.register(Persona)


##Regitrar modelos en app mascota

from django.contrib import admin
from .models import Vacuna, Mascota

admin.site.register(Vacuna)
admin.site.register(Mascota)


Nota: con esto puedo hacer pruebas desde el user(admin) para saber si se estan guardando mis registros
en mi tablas de la base de datos, sin antes haber creado un formulario de registro
en html.
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
25 Abrir shell Django y Hacer Querysets(consultas) de la base de datos

py manage.py shell

26 importar los modelos de la aplicacion, para poder hacer consultas(Querysets)
(shell Django)

from adopcion.models import Persona
from mascota.models import Vacuna, Mascota

27 hacer consultas(Querysets) en la shell Django. La siguiente consulta
muestra todos los registros del Modelo Mascota

Mascota.objects.all()

28 insertar registros en la sehll Django. Exiten dos formas de insertar
registros

-Forma numero 1(forma recomedada)

Mascota.objects.create(nombre="Daniel1",
edad=24,
foto="imagenes/daniel.jpg",
fecha="2023-01-25",
correo="daniel@gmail.com")

#El registro se guarda automaticamente

Forma numero 2

p2=Persona(nombre="Daniel2",
edad=24,
foto="imagenes/daniel.jpg",
fecha="2023-01-25",
correo="daniel@gmail.com")
p2.save() #Para guardar el registro


30 Asignar un modelo como llave foranea(de uno a muchos) en un registro

p1=Persona.objects.get(id=1)#instacio(declaro) una variable que almacene
#un registro en especifico.
#En este caso sera la persona con el id=1, es decir Daniel1.

Mascota.objects.create(nombre="Coco",
sexo="Macho",
edad_aproximada=2,
fecha_rescate="2023-01-25",
persona=p1)


31 Asigna un modelo como llave foranea(de muchos a muchos) 
en un registro

mascota1=Mascota.objects.get(id=1)

v1=Vacuna.objects.get(id=1)

v2=Vacuna.objects.get(id=2)

v3=Vacuna.objects.get(id=3)

mascota1.vacuna.add(v1,v2,v3)

35 Hacer consultas con shell (Querysets)

Obtener todos los registros que guarda una tabla y mostrarlos en
la shell

Mascota.objects.all()

Hacer un filtro en la consulta.Es decir que obtenga  unos 
registros en concreto o que yo especifique en el filtro.

Mascota.objects.filter(id=2)

Hacer un filtro para que obtenga los registros cuando
un registro tenga determinada letra, numero o palabra o frase.
Para ello debemos indica el nombre del campo seguido de dos 
guiones bajos y lapalabra contains.


Mascota.objects.filter(nombre__contains="z")

nota: buscar en la documentacion de Django como hacer mas
consultas de diferentes tipos.


> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTE N°2 CONFIGURACION DE URLs Y PRIMERA VIEW
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
* Creacion de una vistas y urls

1 mportar HttpResponse en views

from django.http import HttpResponse

2 Luego crear un funcion que imprima una frase en el
navegador

def index(request):
    return HttpResponse("Hola mascota")

3 Nota: En las settings la varible ROOT_URLCONF se le asigna la ubicacion de 
las url globales del proyecto. Esta variable se crea automaticamente
cuando creamos el protyecto. Y es importante para poder mostrar
las vistas de nuestras aplicaciones

ROOT_URLCONF = 'sistema.urls'

4 Crear el archivo urls.py en mascota.py
donde podremos listar todas las url de la aplicacion y ponemos
los siguinente

from django.urls import path
from . import views #importa todas las vistas de views.py

urlpatterns = [
    path('', views.index, name="index_mascota"), #Creamos nuestra primer vista
]

5 Incluir las urls de las aplicaiones dentro de las url globales
en sistema>urls.py. Para ello importamos include e incluimos
las urls de nuestra aplicion(es)

from django.urls import include

path('', include('mascota.urls')),
path('adopcion/', include('adopcion.urls')),

6 Corre el servido para ensayar si esta 
las vista y las urls estan funcionando 
correctamente

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTE N°3 SISTEMA DE PLANTILLAS 
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

1 Confurar achivo settings.py para poder leer 
todas los templates, ya sea en una carpeta alojada
en la raiz del proyecto o en la carpeta template de 
cada aplicacion.

import os

TEMPLATES = [
    {
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        'APP_DIRS': True,
    },
]

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTE N°4 HERENCIA DE PLANTILLAS E INCLUDES
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

1 Crear la carpeta templates en la raiz del proyecto,
es decir, en sistema/

2 Crear la carpeta base en sistema/templates/

3 Crear el archivo layout.html en sistema/templates/base/

4 Crear los siguinetes bloques

<head>
    <title>{% block title %}Document{% endblock %}</title>
</head>

<body>
    {% block header %}
    <h2>Este es es el header base</h2>
    {% endblock %}

    {% block content %}
    <h2>Este es el contenido base</h2>
    {% endblock %}

    {% block footer %}
    <h2>Este es el footer base</h2>
    {% endblock  %}
 </body>

5 Crear la carpeta mascota en sistema/templates/

6 Crear el archivo index.html en sistema/templates/mascota

7 Heredamos los elementos de layout.hml en sistema/templates/mascota/index.html, para ello ponemos el 
siguiente codigo:

{% extends 'base/layout.html' %}

8 Nuestra vista index en sisetma/mascota/views.py
le indicamos a la vista que queremos renderizar el
archivo index.html ubicado en sistema/templates/mascota/

def index(request):
    return render(request, 'mascota/index.html')

8 Sobrescribimos el contenido del layout.html en mascota/index.html

{% block title %}App Mascota{% endblock  %}

{% block header %}
<h2>Header de la App Mascota</h2>
{% endblock  %}

{% block content %}
<h2>Contenido de la App Mascota</h2>
{% endblock %}

{% block footer %}
<h2>Footer de la App Mascota</h2>
{% endblock  %}

9 Crear un archivo header.html en sistema/base/
con el sisguiente contenido:

<header>
    <h2>Este es el header base</h2>
</header>

...en icluirlo en el layout.html de sistema/base/

{% block header %}
{% include 'base/header.html' %}
{% endblock  %}

10 Nota importante: Crear dos bloque extra para el head
y para los archivo javascript de esta manera no sobrecarcamos
el loyout.html con archivos css y js que no necesita.



Ejmplo

<head>
    {% block extrahead %}
    {% endblock  %}

</head>
<body>
 

    {% block extrajs %}
    {% endblock  %}

</body>

</html>


> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTE N°5 ETIQUETA {% load static %}
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

1 Poner la etiqueta {% load static %} en la primera linea
de codigo del archivo layout.html. Esta etiqueta 
permite cargar los archivos css y js.
Ejmeplo:

{% load static %}
<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTE N°6 CONFIGURCION DE ARCHVIOS ESTATICOS
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

METODO 1 NO PRODUCCION: Simplemente Añadir los cdn

Si no es para produccion simplemente añades los 
cdn de bootrap. Ejemplo:

<head>

    <!-- Bootstrap CSS v5.2.1 -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-iYQeCzEYFbKjA/T2uDLTpkwGzCiq6soy8tYaI1GyVh/UjpbCx/TYkiZhlZB6+fzT" crossorigin="anonymous">
</head>


<body>

    <!-- Bootstrap JavaScript Libraries -->
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js"
        integrity="sha384-oBqDVmMz9ATKxIep9tiCxS/Z9fNfEXiDAYTujMAeBAsjFuCZSmKbSSUnQlmh/jp3" crossorigin="anonymous">
        </script>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/js/bootstrap.min.js"
        integrity="sha384-7VPbUDkoPSGFnVtYi0QogXtr74QeVeeIs99Qfg5YCF+TidwNdjvaKZX19NZ/e6oz" crossorigin="anonymous">
        </script>
</body>

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
METODO 2 PARA PRODUCCION: Cargar los archivos desde una carpeta
static en la raiz del proyeto 

1 Crear la carpeta static en la raiz del proyecto, y
dentro de la carpeta static/ crear dos caspetas: la
carpeta css y la carpeta js

2 agregar el archvio bootstrap.min.css en la carpeta css
y agregar el archivo bootstrap.min.js en la carpeta js

3 Le indicamos  Djanco donde debe buscar los 
archivos estaticos, para ello ponemos el siguinete codigo
en sistema/settings..py

STATIC_URL = '/static/'
STATICFILES_DIRS = (os.path.join(BASE_DIR, 'static'),)
MEDIA_ROOT = os.path.join(BASE_DIR, '')
MEDIA_URL = '/imagenes/'

4 en sistema/base/layout.html le indicamos donde estan
ubicados nuestros archivos staticos de bootstrap.min.css y
bootstrap.min.js. Adicional a eso agregar la cdn de jquery.
Recuerda que  tambien puedes poner rutas de otros 
archivos ccs o js que tu hayas creado.

<head>

    <!-- Bootstrap CSS v5.2.3 -->
    <link rel="stylesheet" href="{% static 'css/bootstrap.min.css' %}">
</head>

<body>

    <!-- Bootstrap JavaScript Libraries -->
    <script src="https://code.jquery.com/jquery-1.10.2.min.js"></script>
    <script src="{% static 'js/bootstrap.min.js' %}"></script>
</body>


> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTE N°6 Formularios y vistas basadas en funciones crear(720P_HD)
Crear formularios con forms.py para agregar registros a nuestros
modelos
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

1 Crear mascota_form.html en sistema/templtes/mascota/

2 Crear forms.py en sistema/mascota/ y ponemos lo siguiente:

from django import forms #De django importamos los forms
from mascota.models import Mascota #de la app mascota se importa el modelo Mascota

class MascotaForm(forms.ModelForm):
    class Meta:
        
        model = Mascota
        
        #Indicamos que campos vamos a utilizar para el modelo
        fields = [
            'nombre',
            'sexo',
            'edad_aproximada',
            'fecha_rescate',
            'persona',
            'vacuna',
        ]

        #Crear lables para cada campo
        labels = {
            'nombre': 'Nombre',
            'sexo': 'Sexo',
            'edad_aproximada': 'Edad aproximada',
            'fecha_rescate': 'Fecha rescate',
            'persona': 'Adoptante',
            'vacuna': 'Vacunas',
        }
        
        #Crear y especificar el tipo de input de cada campo 
        widgets = {
            'nombre': forms.TextInput(attrs={'class': 'form-control'}),
            'sexo': forms.TextInput(attrs={'class': 'form-control'}),
            'edad_aproximada': forms.TextInput(attrs={'class': 'form-control'}),
            'fecha_rescate': forms.TextInput(attrs={'class': 'form-control'}),
            'persona': forms.Select(attrs={'class': 'form-control'}), #Para llaves foranes de uno a muchos
            'vacuna': forms.CheckboxSelectMultiple(), #Para campos de muchos a muchos
        }

voy en el minuto 7:30 de del video 12 