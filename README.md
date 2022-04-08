# ¿Cómo empezar sus proyectos?
Instrucciones básicas para empezar sus proyectos, recopilando lo aprendido en las auxiliares y respondiendo preguntas frecuentes.

- [1. Repositorio Git](#1-repositorio-git)
  * [1.1. Aceptar la invitación](#11-aceptar-la-invitación)
  * [1.2. Clonar el repositorio en local](#12-clonar-el-repositorio-en-local)
  * [1.3. Probar el repositorio](#13-probar-el-repositorio)
- [2. Ambiente virtual](#2-ambiente-virtual)
  * [2.1. ¿Qué es un ambiente virtual?](#21-qué-es-un-ambiente-virtual)
  * [2.2. Crear el ambiente virtual](#22-crear-el-ambiente-virtual)
  * [2.3. Activar el ambiente virtual](#23-activar-el-ambiente-virtual)
  * [2.4. Instalar Django en el ambiente](#24-instalar-django-en-el-ambiente)
  * [2.5. requirements.txt](#25-requirementstxt)
- [3. Proyecto de Django](#3-proyecto-de-django)
  * [3.1. Crear el proyecto](#31-crear-el-proyecto)
  * [3.2. Crear una "app"](#32-crear-una-app)
  * [3.3. Correr el proyecto](#33-correr-el-proyecto)
  * [3.4. Admin de Django](#34-admin-de-django)
  * [3.5. Resumen de Django](#35-resumen-de-django)

## 1. Repositorio Git
### 1.1. Aceptar la invitación
Lo primero que deben hacer será unirse al equipo que preparamos para ustedes en la [organización de Github](https://github.com/DCC-CC4401) de este ramo. La invitación les debería haber llegado por correo, usando los usuarios que indicaron en el formulario que respondieron a inicio de semestre. Si no tienen la invitación o se equivocaron de usuario, consulten con sus auxiliares.

En esta organización se encuentran los repositorios de cada grupo, sobre los que deberán trabajar y subir sus proyectos para que el equipo docente tenga acceso. Es un poco enredado, pero la estructura básicamente es que la **Organization** "DCC-CC4401" tiene **Teams** (e.g. "2022-1 Grupo 1") y cada Team tiene asignado su **Repository** (e.g. "DCC-CC4401/2022-1-Grupo-1").

---
### 1.2. Clonar el repositorio en local
Una vez aceptada la invitación, busquen su repositorio dentro de la organización y verán algo como esto:

![image](https://user-images.githubusercontent.com/22943973/162325845-5f77eda2-c8a3-4709-8776-370139e5ff94.png)

Acá nos indican varias formas de inicializar el repo en nuestros computadores locales. La más sencilla es como lo hicimos en el auxiliar 1. Copien la URL que aparece en Quick Setup y luego en su consola local, dentro de la carpeta en que quieran tener el proyecto, escriban:
```
git clone https://github.com/...
```
Reemplazando por la URL que copiaron.

También, por su cuenta, pueden clonar usando la interfaz del editor con el que estén trabajando o de otras interfaces gráficas de git (Github Desktop, GitKraken, etc), pero no las cubriremos en este tutorial.

Nota: Si su repositorio ya tiene contenido, no verán lo mismo de la imagen anterior. En su lugar, pueden obtener la URL para clonar en el siguiente menú:

![image](https://user-images.githubusercontent.com/22943973/162326025-3d9077b4-fac7-467b-847e-f993e8ac848c.png)

Una vez clonado el repositorio, debería crearles una carpeta vacía en su computador (con una carpeta ".git" oculta). Esta carpeta ahora está conectada con el repositorio de Github.

---
### 1.3. Probar el repositorio

 Para probar que el repositorio local está conectado con el de Github, pueden crear dentro de la carpeta un archivo de texto de nombre "README.md" con algún contenido cualquiera y pushearlo al servidor como aprendimos. Si no lo recuerdan, en resumen es:
```
git add README.md
git commit -m "First commit, add README"
git push
```

> Recuerden que si más de una persona intenta hacer push, no les va a dejar, porque tienen que hacer pull de todos los cambios actualizados antes de poder pushear. Si no tienen claro esto aún, intenten revisar los videos y la actividad de la [Auxiliar 1](https://github.com/Aux-Ing-1/Auxiliar1-GIT) otra vez.

Si todo salió bien, debería aparecer su README en el repositorio de Github, y automáticamente muestra su contenido en la descripción del repo.

![image](https://user-images.githubusercontent.com/22943973/162326079-925b7d80-34de-4b5b-8332-090a28f5b625.png)

---
## 2. Ambiente virtual
### 2.1. ¿Qué es un ambiente virtual?
En la Auxiliar 2 aprendimos que un proyecto de Python puede tener muchas librerías, o distintos proyectos podrían requerir diferentes versiones de Python por temas de compatibilidad. Para evitar que nuestra instalación global de Python quede llena de librerías que no todos los proyectos usan y que podrían tener conflictos entre sí, existen los **ambientes virtuales**.

Un **ambiente virtual** es básicamente una carpeta donde se encuentra auto-contenido todo lo necesario para un proyecto de Python, incluyendo Python mismo y [pip](https://pypi.org/project/pip/), el instalador de paquetes y librerías. De esta forma, se encapsulan los requerimientos de cada proyecto y no interfieren con otros ni con la instalación global de Python en el computador. Literalmente, el ambiente no es más que **una carpeta** dentro del computador. Si se borra, el ambiente deja de existir.

---
### 2.2. Crear el ambiente virtual
Existen varios módulos de Python para manejar ambientes virtuales (venv, virtualenv, pipenv, etc). En este caso usaremos **venv**.

Para crear el ambiente, navega por consola hasta la carpeta en que quieras crearlo y escribe:
```
python -m venv myvenv
```
el parámetro `-m venv` es para indicar que estamos usando el _módulo venv_, y `myvenv` es el nombre que le daremos al ambiente. Pueden escoger otro nombre si quieren, y dado que esto es local, no es necesario que sea el mismo que el del resto del equipo.

> ¿Dónde crear el ambiente? Una opción es tener una carpeta en cualquier parte de tu computador con todos los ambientes virtuales que crees para tus proyectos, nombrados adecuadamente para evitar conflictos. Otra opción es crearlo dentro de la misma carpeta raíz del proyecto. Si haces esto último, considera que Git lo tomará como parte del proyecto y podría subirse al repositorio. Más adelante hablaremos sobre cómo y por qué hay que evitar subir el ambiente al repo.

> No uses nombres ni rutas con acentos o caracteres especiales.

---
### 2.3. Activar el ambiente virtual
Una vez creado, debemos **activarlo**. Esto significa decirle a la consola que, al usar e instalar paquetes de Python, debe priorizar nuestro ambiente virtual en su PATH (i.e. las ubicaciones donde buscará los comandos que usamos). **IMPORTANTE: Deben activar el ambiente cada vez que vuelvan a abrir la consola.**

La forma de activarlo cambia según tu sistema operativo y/o consola.

Windows:
```
myvenv\Scripts\activate
```
Linux:
```
source myvenv\bin\activate
```
Ambos son considerando que estás en la carpeta en que lo instalaste.
> Puede que tu SO o consola funcionen distinto. Si no te resulta, consulta [este tutorial de djangogirls](https://tutorial.djangogirls.org/es/django_installation/#trabajar-con-virtualenv) en la sección "Trabajar con virtualenv", donde hay más alternativas.

Una vez activado, en la ruta que indica tu consola se debería agregar el nombre del ambiente entre paréntesis. Por ejemplo:
```
(myenv) C:\Documentos\Ingenieria1\Inicio-Proyectos>
```
> Igual que con git, algunos IDE o editores tienen su propia interfaz para manejar ambientes. Tampoco cubriremos eso en este tutorial.

---
### 2.4. Instalar Django en el ambiente
Teniendo activado el ambiente, podemos usar el _pip_ que viene incluído en él para instalar los paquetes que necesitemos, en particular Django. Para esto, usamos el siguiente comando (Háganlo solo si el ambiente está **activado**, fíjense que salga su nombre entre paréntesis en la ruta):
```
pip install django==3.2.12
```
> ATENCIÓN: A fines de 2021 salió Django 4.0, pero dado que no tenemos 100% claro que sea compatible con el material de este curso, y que sus proyectos son de un tamaño pequeño como para beneficiarse mucho de las últimas actualizaciones, preferimos recomendarles que se mantengan con Django 3.2. De todas formas, si por alguna razón quieren usar la última versión, basta con que borren el `==3.2.12` del comando anterior. En teoría no debería causarles mayores problemas.

Con eso su ambiente ya debiera tener Django y sus dependencias, y podrían empezar a usarlo en su proyecto.

---
### 2.5. requirements.txt
Como mencionamos en algún momento, no es buena idea compartir su ambiente dentro del repositorio, ya que cada computador podría tener compatibilidades distintas según su sistema operativo.

En su lugar, la forma correcta de procurar que todo el equipo tenga las mismas librerías y sus versiones, es con el archivo `requirements.txt`. Este archivo tendrá un registro de todos los paquetes y versiones del proyecto, para que luego cada uno pueda instalarlos adecuadamente en su sistema.

Para crear un archivo de requirements, usamos el siguiente comando **en la carpeta raíz de nuestro proyecto**:
```
pip freeze > requirements.txt
```
Esto creará un archivo con los paquetes instalados, que debería verse más o menos así:
```
[Archivo de ejemplo, el suyo podría ser distinto. ¡No copiar!]
asgiref==3.5.0
Django==3.2.12
pytz==2022.1
sqlparse==0.4.2
```
**Este archivo SÍ pueden subirlo al repositorio.**

Luego, cuando alguien descargue el proyecto, **y ya tenga ACTIVADO su ambiente virtual**, en lugar de instalar Django u otras librerías a mano, debe hacer:
```
pip install -r requirements.txt
```
Esto instalará de una vez todo lo que esté declarado en el archivo, con las versiones adecuadas.

> Noten que requirements.txt es solo un archivo de texto. Pueden editarlo manualmente para cambiar el stack de librerías de su proyecto.

---
## 3. Proyecto de Django
### 3.1. Crear el proyecto
Teniendo nuestro repositorio enlazado y nuestro ambiente virtual activado, podemos crear nuestro proyecto.

**OJO: Basta con que UNA persona inicialice el proyecto de Django.** Luego lo pushea al repo y los demás hacen pull de eso para tenerlo en su computador.

Para empezar, **[con el ambiente activado]**, usamos el siguiente comando:
```
django-admin startproject [nombre_del_proyecto]
```
> El nombre debe usar solo minúsculas y guión bajo _. 

Esto creará la siguiente estructura en su sistema:
```
[Nombre-Del-Repositorio]
|── [nombre_del_proyecto]
|   |── __init__.py
|   |── asgi.py
|   |── settings.py
|   |── urls.py
|   |── wsgi.py
|── manage.py
```

---
### 3.2. Crear una "app"
Recordemos que dentro de un proyecto de Django podemos tener distintas _apps_. Una app, a diferencia de lo que el nombre sugiere, no es necesariamente una aplicación completa, sino solamente una forma de modularizar distintas secciones de su proyecto.

Podrían tener todo su proyecto en una sola app, o separarlo en distintos módulos para mejorar la organización de su código. Por ejemplo, si su proyecto fuera U-Cursos, podrían tener una app para `usuarios`, otra para `cursos`, otra para `foro`, o una para `horario`. La división puede ser en términos de funcionalidad, de datos, de ubicación en el sitio web, de equipo de trabajo, o de cualquier criterio que ustedes estimen conveniente para organizar. Consideren las _apps_ más como _módulos_ que como _aplicaciones_.

Dicho esto, deberán crear al menos una app, de la siguiente forma:
```
cd [nombre_del_proyecto]    <--- Entrar a la carpeta del proyecto
python manage.py startapp [nombre_de_app]
```

Y su estructura quedará así:
```
[Nombre-Del-Repositorio]
|── [nombre_del_proyecto]
|   |── ...
|── [nombre_de_app]
|   |── __init__.py
|   |── admin.py
|   |── apps.py
|   |── models.py
|   |── tests.py
|   |── views.py
|── manage.py
```

Una vez creada la app, deberán registrarla como parte del proyecto buscando y agregando lo siguiente en `settings.py`:
``` python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    '[nombre_de_app]',   # <--- Esto es lo que deben agregar
]
```

---

### 3.3. Correr el proyecto
Antes de echar a andar el proyecto es necesario aplicar la primera capa de _migraciones_. Para esto hacemos lo siguiente:
```
python manage.py makemigrations
python manage.py migrate
```
> Más info sobre migraciones [en el 3.5.2](#352-modelos-y-migraciones).

Al hacer eso deberían aplicarse varias migraciones, con un **OK** al final de cada una.

Luego, para correr el servidor deben hacer:
```
python manage.py runserver
```

Si todo salió bien, deberías ver el mensaje:
```
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```
Y si ingresas a http://127.0.0.1:8000/ (equivalente a http://localhost:8000/), deberías ver el mensaje de bienvenida de Django.

![image](https://user-images.githubusercontent.com/22943973/162346808-5e48e838-54d7-4c28-aeaf-b9d831d03801.png)

---
### 3.4. Admin de Django
Django viene con una interfaz de administración que permite gestionar la base de datos visualmente. Esto es muy útil cuando están construyendo su aplicación y aún no tienen implementada la creación de elementos. De esta forma, pueden crear, modificar y borrar directamente sus datos para testear sus interfaces.

![image](https://user-images.githubusercontent.com/22943973/162347670-46e7d087-317b-47b4-a155-cceef7c9b017.png)

Para poder usarla, debes _registrar_ los modelos que quieres que aparezcan en ella. Para esto deben editar el archivo `admin.py` de cada app, y agregar los models que quieran gestionar en el admin.
``` python
from django.contrib import admin
from [nombre_de_app].models import [NombreModelo]

# Register your models here.
admin.site.register([NombreModelo])
```
Pueden hacerlo con todas las apps y modelos que estimen necesario.

Para poder ingresar al admin es necesario tener un usuario con permisos de admin. Dado que no tenemos interfaz para crear usuarios, lo hacemos por consola:
```
python manage.py createsuperuser
```
Les pedirá un username, un correo y una password. Dado que todo esto está local en su computador y no hay riesgo de hackeo, les recomendamos usar algo sencillo como user: admin, pass: admin. El correo puede ser vacío o cualquier cosa, no tiene ninguna utilidad por el momento y no se enviará nada. Es posible que les tire warnings por la seguridad de la contraseña, pero puede hacerse un bypass (saltárselo) de todas formas.

Con este usuario podrán ingresar al admin. Desde ahí pueden crear otros usuarios no-admin para testear su página.

> Recuerden que todo esto es local. Cada persona en su computador tendrá sus propios usuarios y data. Por default esto se guarda en db.sqlite3, archivo que idealmente NO deberían subir al repositorio.

---
### 3.5. Resumen de Django
Ahora ya tienen todo listo para empezar su proyecto. Si todavía no saben bien como proseguir, les recomendamos fuertemente ver el video de la Auxiliar 2 y hacer [la actividad](https://github.com/Aux-Ing-1/Auxiliar2-Django), donde pueden aprender cómo funciona la estructura de Django con un ejemplo concreto.

De todas formas, les dejamos un pequeño resumen de la teoría tras Django:
#### 3.5.1. Estructura
Los archivos más importantes son:
- `[proyecto]/manage.py`: Este es el archivo con el que se corren los comandos del proyecto, como `runserver`, `createsuperuser`, `migrate`, etc.
- `[proyecto]/[proyecto]/settings.py`: Define todas las variables de configuración del proyecto. Tengan cuidado al modificarlo.
- `[proyecto]/[proyecto]/urls.py`: Asigna qué views o funciones se llamáran para cada URL del sitio.
- `[proyecto]/[app]/admin.py`: Aquí se registran los modelos que quieren gestionar a través del admin de Django.
- `[proyecto]/[app]/models.py`: Modelos de la base de datos, en forma de clases de Python.
- `[proyecto]/[app]/urls.py`: Dentro de una app también pueden haber URLs específicas de esa app. Éstas deben importarse en el `urls.py` a nivel de proyecto.
- `[proyecto]/[app]/views.py`: Funciones de Python que serán llamadas al recibir requests a las URLs asignadas.

Los archivos `__init__.py` son necesarios para que Python reconozca los módulos. Los archivos `asgi.py` y `wsgi.py` no son relevantes a este curso. El archivo `test.py` tampoco, pues no se esperan tests unitarios.
#### 3.5.2. Modelos y migraciones
Los models son una representación en Python de una base de datos. Con ellos, no es necesario hacer consultas de tipo _SELECT FROM WHERE_, sino que se usa el mismo lenguaje Python para consultar. Haciendo la analogía, cada model es una tabla, y cada columna de esa tabla es un _field_ o _campo_ en Django. Existen varios tipos de fields, como `IntegerField`, `DatetimeField`, `CharField` para tipos primitivos, y otros como `ForeignKey` y `ManyToManyField`, que representan llaves foráneas de la base de datos, para relacionar tablas entre sí. Pueden leer [la documentación](https://docs.djangoproject.com/en/3.2/ref/models/fields/) para saber más sobre los fields.

Las migraciones son una especie de control de versiones (como git), pero para la base de datos. Cada vez que hacen un cambio en la definición de un modelo (e.g. agregar un campo `profesor` al modelo `Curso`), es necesario crear una nueva "migración" usando `python manage.py makemigrations`, y luego para aplicar las migraciones creadas se debe usar `python manage.py migrate`. 

Considera que `makemigrations` es análogo en git a hacer `add` para preparar los cambios, y `migrate` es como confirmar los cambios con un `commit`.

#### 3.5.3. Views
Las views o vistas, a diferencia de lo que podría indicar el nombre, no son la parte visual del proyecto. Una view en Django es un controlador, la parte funcional del sistema. Acá es donde definen las funciones en Python que serán llamadas por el servidor cuando lleguen las requests de los clientes. Cada view debe siempre retornar algún tipo de HTTP Response, que es la respuesta que se enviará de vuelta al cliente. Esta respuesta puede ser solo data cruda (en el caso de un servidor API), pero en nuestro caso la respuesta implica renderizar un _template_, llenarlo con la data y enviar ya construida la página HTML completa que se mostrará al usuario.

Todo lo que ocurre en las views ocurre en el **backend**, es decir, en el computador que está corriendo el servidor de Django, por lo que acá puedes implementar cualquier funcionalidad que podrías hacer con el lenguaje Python, con la capacidad de tu servidor (tu computador).

#### 3.5.4. Templates
Los templates sí son la parte visual de la aplicación. Son la forma en la que Django, un framework de backend/servidor, también puede servir como frontend. Están hechos en HTML (+ CSS y JavaScript), pero se mezclan con una sintáxis particular de Django (`{% así %}`) para poder incrustar data dinámicamente, construir la página y enviarla al cliente.

Los templates pueden incluir código JavaScript. Recuerden que JS es un lenguaje de cliente, por lo que se ejecuta **en el computador del usuario** y no en el servidor, con todas las limitaciones que ello implica.

#### 3.5.5. URLs
En las URLs se define qué funciones (views) se llamarán según qué enlace está solicitando el usuario. Éstas pueden ser dinámicas, por ejemplo, la URL `https://www.u-cursos.cl/ingenieria/2022/1/CC4401/1/integrantes` le entrega como argumento dinámico a la view que estamos solicitando `año=2022`, `semestre=1`, `curso=CC4401`, `sección=1`. Luego la view puede usar estos argumentos para consultar la base de datos y filtrar los integrantes, para enviar la respuesta de vuelta.

#### 3.5.6. Flujo
Finalmente, el flujo general de Django es el siguiente:
- Usuario ingresa a una página, mediante una **URL**.
- El servidor recibe la solicitud y chequea qué **view** le corresponde a dicha URL.
- La **view** procesa la solicitud y realiza algún tipo de operación funcional con la data.
- La **view** puede consultar la base de datos a través de los **models**.
- La **view** incrusta los datos obtenidos/procesados en un **template** en HTML.
- Se envía una respuesta al cliente con la página HTML ya construida para mostrársela.

---
Esperamos que este documento les sirva como guía para sus proyectos. Cualquier otra duda, problema o sugerencia respecto a la guía, háganselo saber a sus auxiliares.

¡Éxito! :D