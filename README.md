# ¿Cómo empezar sus proyectos?
Instrucciones básicas para empezar sus proyectos, recopilando lo aprendido en las auxiliares y respondiendo preguntas frecuentes.

- [1. Repositorio Git](#1-repositorio-git)
  * [1.1. Aceptar la invitación](#11-aceptar-la-invitaci-n)
  * [1.2. Clonar el repositorio en local](#12-clonar-el-repositorio-en-local)
  * [1.3. Probar el repositorio](#13-probar-el-repositorio)
- [2. Ambiente virtual](#2-ambiente-virtual)
  * [2.1. ¿Qué es un ambiente virtual?](#21--qu--es-un-ambiente-virtual-)
  * [2.2. Crear el ambiente virtual](#22-crear-el-ambiente-virtual)
  * [2.3. Activar el ambiente virtual](#23-activar-el-ambiente-virtual)
  * [2.4. Instalar Django en el ambiente](#24-instalar-django-en-el-ambiente)
  * [2.5. requirements.txt](#25-requirementstxt)
- [3. Proyecto de Django](#3-proyecto-de-django)

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
Una vez creado, debemos **activarlo**. Esto significa decirle a la consola que, al usar e instalar paquetes de Python, debe priorizar nuestro ambiente virtual en su PATH (i.e. las ubicaciones donde buscará los comandos que usamos).

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