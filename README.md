# ¿Cómo empezar sus proyectos?
Instrucciones básicas para empezar sus proyectos, recopilando lo aprendido en las auxiliares y respondiendo preguntas frecuentes.

## 1. Repositorio Git
### 1.1 Aceptar la invitación
Lo primero que deben hacer será unirse al equipo que preparamos para ustedes en la [organización de Github](https://github.com/DCC-CC4401) de este ramo. La invitación les debería haber llegado por correo, usando los usuarios que indicaron en el formulario que respondieron a inicio de semestre. Si no tienen la invitación o se equivocaron de usuario, consulten con sus auxiliares.

En esta organización se encuentran los repositorios de cada grupo, sobre los que deberán trabajar y subir sus proyectos para que el equipo docente tenga acceso. Es un poco enredado, pero la estructura básicamente es que la **Organization** "DCC-CC4401" tiene **Teams** (e.g. "2022-1 Grupo 1") y cada Team tiene asignado su **Repository** (e.g. "DCC-CC4401/2022-1-Grupo-1").

### 1.2 Clonar el repositorio en local
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

Una vez clonado el repositorio, debería crearles una carpeta vacía en su computador (con una carpeta ".git" oculta). Esta carpeta ahora está conectada con el repositorio de Github. Para probar, pueden crear dentro de la carpeta un archivo de texto de nombre "README.md" con algún contenido cualquiera y pushearlo al servidor como aprendimos. Si no lo recuerdan, en resumen es:
```
git add README.md
git commit -m "First commit, add README"
git push
```

> Recuerden que si más de una persona intenta hacer push, no les va a dejar, porque tienen que hacer pull de todos los cambios actualizados antes de poder pushear. Si no tienen claro esto aún, intenten revisar los videos y la actividad de la [Auxiliar 1](https://github.com/Aux-Ing-1/Auxiliar1-GIT) otra vez.

Si todo salió bien, debería aparecer su README en el repositorio de Github, y automáticamente muestra su contenido en la descripción del repo.

![image](https://user-images.githubusercontent.com/22943973/162326079-925b7d80-34de-4b5b-8332-090a28f5b625.png)
