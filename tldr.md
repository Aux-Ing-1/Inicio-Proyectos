# ¿Cómo empezar sus proyectos?
### Versión "Too Long; Didn't Read".
### Por si ya saben lo que están haciendo y solo quieren los comandos.

(La numeración de los títulos se salta algunos, para calzar con la guía completa)

- [1. Repositorio Git](#1-repositorio-git)
  * [1.1. Aceptar la invitación](#11-aceptar-la-invitación)
  * [1.2. Clonar el repositorio en local](#12-clonar-el-repositorio-en-local)
- [2. Ambiente virtual](#2-ambiente-virtual)
  * [2.2. Crear el ambiente virtual](#22-crear-el-ambiente-virtual)
  * [2.3. Activar el ambiente virtual](#23-activar-el-ambiente-virtual)
  * [2.4. Instalar Django en el ambiente](#24-instalar-django-en-el-ambiente)
  * [2.5. requirements.txt](#25-requirementstxt)
- [3. Proyecto de Django](#3-proyecto-de-django)
  * [3.1. Crear el proyecto](#31-crear-el-proyecto)
  * [3.2. Crear una "app"](#32-crear-una-app)
  * [3.3. Correr el proyecto](#33-correr-el-proyecto)
  * [3.4. Admin de Django](#34-admin-de-django)

## 1. Repositorio Git
### 1.1. Aceptar invitación
Aceptar la invitación que les llegó por correo. Si no les ha llegado, envíen sus usuarios de Github a sus auxiliares.
### 1.2. Clonar repositorio
Buscar la dirección HTTPS .git del repositorio de su grupo y en la carpeta donde quieran tener el proyecto usar:
```
git clone [su-dirección-.git]
```
En esa carpeta deberán trabajar, y al hacer push se subirá a su repo del curso.

---
## 2. Ambiente virtual
> ⚠️ Si no sabes qué es esto, lee la sección correspondiente en la [guía completa](https://github.com/Aux-Ing-1/Inicio-Proyectos) antes de hacerlo.
### 2.2. Crear ambiente virtual
Para crear el ambiente, navega por consola hasta la carpeta en que quieras crearlo y escribe:
```
python -m venv myenv
```

### 2.3 Activar ambiente virtual
**[Se debe activar cada vez que se abre la consola.]**

Windows:
```
myvenv\Scripts\activate
```
Linux:
```
source myvenv\bin\activate
```

Al activarse, la ruta en la consola mostrará el ambiente:
```
(myenv) C:\Documentos\Ingenieria1\Inicio-Proyectos>
```
### 2.4. Instalar Django en el ambiente
Con el ambiente **ACTIVADO**:
```
pip install django==3.2.12
```
> Pueden quitar el `==3.2.12` para instalar Django 4.0. Pero es muy nuevo y no podemos asegurar que sea compatible con nuestro material.

---

### 2.5. requirements.txt
> ⚠️ Si no sabes qué es esto, lee la sección correspondiente en la [guía completa](https://github.com/Aux-Ing-1/Inicio-Proyectos) antes de hacerlo.

Para crear requirements.txt:
```
pip freeze > requirements.txt
```

Para instalar desde requirements.txt:
```
pip install -r requirements.txt
```

---
## 3. Proyecto de Django
### 3.1. Crear el proyecto
```
django-admin startproject [nombre_del_proyecto]
```
### 3.2. Crear una "app"
> ⚠️ Si no sabes qué es esto, lee la sección correspondiente en la [guía completa](https://github.com/Aux-Ing-1/Inicio-Proyectos) antes de hacerlo.
```
cd [nombre_del_proyecto]    <--- Entrar a la carpeta del proyecto
python manage.py startapp [nombre_de_app]
```

### 3.3. Correr el proyecto
Hacer y aplicar migraciones:
```
python manage.py makemigrations
python manage.py migrate
```
Correr servidor:
```
python manage.py runserver
```
Ingresar a http://127.0.0.1:8000/

### 3.4. Admin de Django
> ⚠️ Si no sabes qué es esto, lee la sección correspondiente en la [guía completa](https://github.com/Aux-Ing-1/Inicio-Proyectos) antes de hacerlo.

En el archivo `admin.py` de cada app, registrar los modelos:
``` python
from django.contrib import admin
from [nombre_de_app].models import [NombreModelo]

# Register your models here.
admin.site.register([NombreModelo])
```

Para crear un usuario admin:
```
python manage.py createsuperuser
```