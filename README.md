# TUTORIAL de [GIT / GITHUB]

Documentación personal para recordar los comandos, sus usos y procedimientos de ejecución mas frecuentes.

Notas:

1. Un guión (-) se usa para la letra.
2. Dos guiones (--) se usa para colocar una palabra.
3. HEAD: indica la version mas reciente de un commit, es un apuntador.
4. Los comandos que se usan como parches son: rebase, revert y cherry-pick.

## :star:NOTAS DE [GIT]:star:

### :key:COMANDOS GENERALES

---

__* git (definición):__
    Software que guarda y administra la información de versiones del proyecto en equipo local.

__* git version:__
    Indica la version de git instalada.

__* git init:__
    Inicia en la carpeta del proyecto un repositorio, que es una base de datos donde se guardan los cambios de cualquier archivo (archivo planos o códigos). Al ejecutar este comando en la carpeta del proyecto se genera automáticamente un carpeta oculta (.git/). Los archivos al inicio del proyecto se encuentran sin rastreos (untracked).

__* Ayuda Local de Git para los comandos:__
    Para obtener mas información de un comando se debe ejecutar el argumento (--help).

__* git add [nombre del archivo]:__
    Este comando le indica a la bases de datos para el sistema de control de versiones que un archivo específico existe, es decir comienza a hacerle un seguimiento a ese archivo en cuestión, y el mismo se ubica en el "staging area (area temporal de preparación)". Los archivos pasan a estar rastreados (tracked).

__* git add [.]:__
    Igual que el anterior, pero se aplica a varios archivos a la vez y los ubica en el "staying area (area temporal de preparación)". Los archivos pasan a estar rastreados (tracked).

__* git config:__
   Este comando permite acceder a los ajustes de configuración de git.
>Los argumentos usados para este comando son:
>__--list:__ muestra en lista todas las variables de configuración establecidas junto con sus valores en el archivo de configuración.
>
>__--show-origin:__ muestra en detalle todas las opciones de configuración guardadas y la ruta de ubicación.
>
>__--global:__ opciones de configuración global; se realiza el cambio de la configuración de los archivos de los usuarios globales; una de las primeras acciones a realizar es la configuración del nombre y la dirección del correo electrónico, asi como la creación de alias (invocación de comandos largos).

__* git commit:__
    Este comando envía los últimos cambios del archivo a la base de datos del sistema de control de versiones, es decir hace referencia al respaldo o hace una captura fotográfica del proyecto. Los archivos del proyecto pasan a ser rastreados (tracked) en el repositorio local.
>Los argumentos usados para este comando son:
>__1- Documentación de los Commit:__
>__-m "texto" :__ permite dejar un mensaje acorde a los cambios realizados.
>
>__-am "texto" :__ permite añadir los archivos al "staging area" y hacer un commit al mismo tiempo. Este argumento solo se aplica para los archivos que se este haciendo seguimiento.
>
>__2- Reconstrucción de los Commit:__
__--amend:__ es una manera práctica de modificar el commit mas reciente y su mensaje en la misma rama donde se esta trabajando, sin tener que ejecutar un nuevo commit. Pasos para ejecutar este comando:
    1. Añadir el archivo modificado al "staying area".
    2. Ejecutar el comando "commit --amend"
>
>__--amend -m "texto":__ permite editar el anterior mensaje desde la línea de comando del commit sin cambiar la instantánea.
>
>__--amend --no-edit:__ permite hacer la corrección del codigo (añadir información) pero sin modificar el mensaje del commit existente.
>
>__Nota:__ usar estos comandos es considerado una mala práctica, despues de haber ejecutado los comandos push y/o pull al repositorio remoto.

__* git status:__
    Este comando muestra el estatus de la bases de datos, indicando si los archivos están haciéndole seguimiento o no, si se encuentran en la bases de datos o no.

> Los argumentos usados para este comando son:
>__-s:__ muestra los archivos que no se le están haciendo seguimiento y no se le conoce el estatus y se identifica con los signos de interrogación.

__* git show:__
    Este comando muestra todos los cambios históricos realizados (incluyendo las líneas de código modificada, cuando se realizó el cambio y quién ejecutó esos cambios) de un commit. También se puede observar donde esta el HEAD que indica el ultimo commit realizado.
    Ademas puede mostrar un objeto Git de una manera simple y legible para los humanos.

__* git diff:__
    Este comando compará y muestra las diferencias de modificaciones entre dos commit.

__* git log:__
   Este comando muestra la historia entera de un archivo, es decir, lista los commit mas recientes se muestran al principio de la lista. La información que muestra de un commit es:

+ Identificador del commit
+ Autor
+ Fecha de Realización
+ Mensaje enviado

>Los argumentos usados para este comando son:
>__--all__: muestra por pantalla todos los commit realizados históricamente en el proyecto.
>
>__--stat:__ imprime tras cada confirmación una lista de archivos modificados, indicando cuántos han sido modificados y cuántas líneas han sido añadidas y eliminadas para cada uno de ellos, y un resumen de toda esta información.
>
>__--graph:__ Este comando muestra en detalle un listado en forma gráfica (ASCII) la historia de las ramas, uniones, y otros.
>
>__--oneline:__ Permite ver mas cantidad de commit y facilita seguir la secuencia por pantalla. Esta opción en realidad es un atajo de escribir estas dos opciones:
>
>       pretty = oneline --abbrev-commit
>
> Donde:
> __--pretty:__ modifica el formato de salida.
>
> __--oneline:__ La primera indica justamente que pongas un commit por linea.
>
>__--abbrev-commit:__ indica que muestres la cadena resumida con el identificador del commit.
>
>---
>__-g:__ permite ver información del comando reflog en el formato de "git log" usando el siguiente comando "git log -g".
>
>__-#:__ limita el numero de commits a consultar, se se ingresa el símbolo "-" y un numero como opción.
>
>__-S [palabra]:__ se usa para buscar informacion en la historia de los commit, de cuando existió o se introdujo en el /los commit.

__* git shortlog:__
    Este comando se utiliza para resumir la salida de git log. Toma muchas de las mismas opciones que el comando [git log], pero solo presentará un resumen de los commits agrupados por autor (cada miembro del equipo).

>Otros argumentos usados para este comando son:
>__-sn:__ muestra los miembros del equipo que han hecho ciertos commit.
>
>__-sn --all:__ muestra un listado de todos los commit realizados y los borrados.
>
>__-sn --all --no-merge:__ muestra un listado de todos los commit realizados, eliminando los merge.

__* git rm:__
    El comando rm (remove) borra los archivos del "staging area", sin eliminar su historial del sistema de versiones. Para recuperar el archivo eliminado (viajar en el tiempo), necesitamos retroceder en la historia del proyecto, recuperar el último commit y obtener la última confirmación antes de la eliminación del archivo.
    Hay que tomar en cuenta que git rm no puede usarse sin evaluarlo antes. Se deberá usar uno de los flags siguientes para indicarle a Git cómo eliminar los archivos que ya no necesitamos en la última versión del proyecto.

>Los argumentos usados para este comando son:
>__--cached:__ elimina un archivo del "staging area" o "memoria ram", este procedimiento se usa en caso de un error de un archivo que no sea necesario. El archivo sigue existiendo en físico (disco duro) en la carpeta del proyecto. Deja de hacer seguimiento (trackear) al historial de cambios de estos archivos, por lo que quedan en estado sin seguimiento (untracked).
>
>__--force:__ elimina todos los archivos del proyecto tanto de la carpeta de git y del disco duro. Git siempre guarda todo, por lo que podemos acceder al registro de la existencia de los archivos, de modo que se pueda recuperar los si es necesario (pero debemos usar comandos más avanzados).
>
>__-r:__ permite la eliminación recursiva cuando se proporciona un nombre de directorio principal.

__* git checkout:__
    Este comando es usado para viajar en el tiempo, para ver versiones anteriores del proyecto (ver commit antiguos: mirar, pasear y volver); también se realiza los cambios entre ramas (branch), con este comando se pueden copiar todos los cambios, algunos cambios, archivos, otros.
    Este comando tambien acepta y usa un parámetro de referecia (ref), donde se puede mover a un commit usando la referencia (ref) sin realizar cambios (solo ver la información).

__* git reset:__
    Este comando permite volver a una version anterior del proyecto (al pasado), sin posibilidad de regresar a la información actual, ya que la historia anterior se borra y se crea una nueva (sobreescribe) historia.
    Tambien es utilizado para deshacer las cosas, cuando se ejecuta este comando trae la posición (head / index) antes de que se presentará un problema en el código usando la referencia (ref).

>Los argumentos usados para este comando son:
>__--soft:__ borra el historial y/o registro en el "directorio de git", pero mantiene los archivos que están en el "staging area", el cambio se realiza solo en el "directorio de trabajo".
>
>__--mixed:__ quita todos los cambios en el "staging area" y los lleva al "directorio de trabajo", no toca ningun otro archivo para cambios en el "directorio de trabajo". Limpia el "staging area"
>
>__--hard:__ borra toda la información ubicada en el "staging area" y del "directorio de trabajo", sin poder volver atrás, es el comando mas utilizado. Elimina todos los cambios y vuelve alineados con "HEAD".
>
>__--HEAD:__ permite sacar los archivo del listado que se ubica en el "staging area", y asi esos archivo sean incluidos en el proximo commit.  Esto impide que los últimos cambios en estos archivos se envíen al último commit
>
>__Nota:__ este comando es una mala practica, solo se recomienda su uso como un ultimo recurso, es decir, en caso de emergencia. La fuente de las referencias son el: Head / Hash.

__* git reflog:__
    Es un método más rápido para mostrar commit y/o conseguir commit que se han perdido o borrado. Git suele guardar un silencioso registro de donde está HEAD en cada momento en el repositorio local. Cada vez que confirmas cambios (commit) o cambias de rama el registro de reflog es actualizado. Este comando es muy usado en casos donde se necesite reescribir la historia.
    Además, muestra el listado del registro de referencia (reflogs), por lo que git realiza un seguimiento de las actualizaciones en el extremo de las ramas, tambien permite revisar la información de donde se trabajo en el pasado.

__* git merge:__
    Es usado para unir y/o fusionar ramas; cuando se unen las ramas hay que tener en cuenta que se pueden presentar conflictos. Un merge es un commit. Para ejecutar este comando hay que estar ubicado en la rama de interés (main) de que se quiere el cambio, como control de versiones.
    Este comando tambien acepta y usa un parámetro de referecia (ref), donde se usa para hacer una fusión de un commit especifico usando el ref.

__* git clone:__
    Comando para realiza una copia del proyecto tanto en el "directorio de trabajo" como crear la BD de todos los cambios en el "repositorio local", por puerto https o ssh, lo importante es destacar que para el copiado del proyecto local debe de estar ubicado en la carpeta "site".

__* git fetch:__
    Este comando descarga el contenido remoto sin modificar el estado del repositorio local, es decir, realiza una copia de los archivos del "servidor de repositorio remoto" a un "servidor local"

__* git pull:__
    Descarga el contenido remoto y tratará inmediatamente de cambiar el estado del repositorio local para reflejar ese contenido, es decir, extrae la información del proyecto remoto almacenado en la nube al equipo local (directorio de trabajo y bd de repositorio local) del desarrollador, es decir.
    Este comando se encarga de hacer un "git fetch" y un "git merge" junto, esto puede provocar en ciertas ocasiones un conflicto de informacion en el repositorio local.

__* git push:__
    Envía la información del proyecto local a un repositorio remoto en la nube.

__* git branch:__
    Este comando se encarga de crear y lista/muestra las Ramas del proyecto, se identifica con un * cual es la que se esta utilizando. La nueva rama debe ser creada desde las rama principal. Las ramas son formas de hacer cambios en un proyecto sin afectar con esos cambios a la rama principal.

>Los argumentos usados para este comando son:
>__-r:__ se muestran todas las ramas remotas, las que están ubicadas en el servidor (github).
>
>__-a:__ se muestran todas las ramas tanto locales como remotas.
>
>__-D:__ se encarga de borrar la(s) rama(s).
>
>__-m:__ se encarga de realizar el cambio del nombre de la rama, o de mover la misma.

__* git remote:__
    Este comando maneja un conjunto de repositorios rastreados.

>Los argumentos usados para este comando son:
>__-v:__ muestra en detalle el nombre y url del proyecto en la nube.

__* git rebase:__
    Es una forma de mover la totalidad de una rama a otro punto del del árbol, alterando la historia del commits. Este comando solo se debera utilizar en un "repositorio local"; porque si el rebase se hace en el repositorio remoto (muy mala practica), entonces puede crear muchos problemas cuando otros desarrolladores intentan sacar los últimos cambios de código del repositorio remoto.

__* git stash:__
    Este comando permite almacenar temporalmente los cambios que se hayan realizados en el codigo, estos cambios (pruebas) no necesitan estar guardados en una rama en especifico o hacer un commit para su registro.
    Al almacenar los cambios con el comando STASH resulta práctico si hay que cambiar de contexto (de una modificación parcial) y se requiere trabajar en otra parte del codigo.

__* git clean:__
    Se utiliza para eliminar archivos no deseados de tu directorio de trabajo. Ejemplos de estos archivos pueden ser:

+ Archivos resultados de una compilación
+ Archivos duplicados (imágenes, documentos, codigo)
+ Archivos *.log
+ entre otros.

>Los argumentos usados para este comando son:
>__--dry-run:__ significa borrado en seco, estos argumentos indica y simula los archivos a borrar.
>
>__-f:__ borra solo los archivos de manera forzado, que no tienen seguimiento en git.
>
>__-f -d:__ borra los archivos y carpetas de manera forzada, que no tienen seguimiento en git.

__* git cherry-pick:__
    Se utiliza para tomar el cambio introducido en un único commit en git y tratar de volver a ingresarlo como un nuevo commit en la rama principal donde se esta trabajando actualmente, es decir, el commando ejecuta commit con cambios específicos de una rama a otra rama, en lugar de fusionar la rama que contiene todos los cambios.

>El argumento usado para este comando son:
>__--abort:__ detiene una operación de ejecución de commit.
>
>__Nota:__
>1. Este comando es una mala practica ya que se esta reconstruyendo la historia del proyecto, por lo tanto se debera usar con mucho cuidado.

__* git grep:__
    Es un comando que permite buscar en los archivos del repositorio local utilizando expresiones regulares, tambien indica la ubicación de los mismos. En resumen este comando se usa para buscar en los archivos del proyecto.

>Los argumentos usados para este comando son:
>__-n [palabra]:__ imprime los números de línea donde nos indica donde Git a encontrado coincidencias, es decir, muestra la línea de ubicación en el codigo.
>
>__-c [palabra / código]:__ este comando hace que git resuma el resultado de búsqueda mostrando cuantas veces se repite la palabra (encontrada) y en que archivo esta ubicada la información. Tambien se usa para buscar la información de cuantas veces se utiliza un atributo (codigo) HTML.

__* git blame:__
    Este comando toma nota de las líneas de cualquier archivo y con cual commit fue el ultimo en introducir un cambio en cada línea del archivo y específica que persona fue autor de ese commit, es decir, muestra quien realizo la programación de una parte del proyecto línea por línea.

>Los argumentos usados para este comando son:
>__-c [nombre del archivo]:__ este argumento se encarga de mostrar un poco mejor (indentado) la información solicitada.
>
>__-L (linea_inicio),(linea_fin) [nombre del archivo]:__ este comando usa los rangos de línea (números enteros) para mostrar por pantalla que analista del proyecto realizo un trabajo especifico.
>
>__-L (linea_inicio),(linea_fin) -c [nombre del archivo]:__ este argumento aplica los dos conceptos arriba desarrollados.

### :key: PROCEDIMIENTOS

---

__* Inicio de un Repositorio Local:__

    git init

    Ej: git init ↵
        Initialized empty Git repository in D:/xampp/htdocs/site/git_comandos/.git/

__* Información de uso y/o ayuda de un comando:__

    git [Comando] --help

    Ej: git add --help ↵

__* Muestra la Configuración de las Variables y sus valores:__

    git config --list o git config -l

__* Muestra la Ubicación donde están almacenadas las variables:__

    git config --list --show-origin

__* Configuración de los Usuarios Globales - También Aplica solo para cambio/actualización del E-Mail:__

    git config --global user.email "tu@email.com"
    Ej: config --global user.email "team@platzi.com" ↵

    git config --global user.name "Tu Nombre"
    Ej: git config --global user.name "Freddy Vega" ↵

__* Configuración de los Alias Globales:__

    git config --global alias.[nombre del alias] "[escribir el comando]"

    Ej: git config --global alias.stats "shortlog --sn --all --no-merge" ↵
        git stats ↵ (Ejecuta el Alias)

__* Ejecución de un commit:__

    git commit -m "dejar el mensaje"

__* Ejecución añadir un archivo al staging y hacer de un commit:__

    git commit -am "dejar el mensaje"

__* Remendar / Enmendar el ultimo commit:__

    git add [Nombre del Archivo a ser añadido al "Staying Area"]
    git commit --amend

    Ej: git add css/estilos.css ↵

        git commit --amend ↵

__* Cambio del mensaje del ultimo commit:__

    git commit --amend -m "escribir el mensaje nuevo" ↵

__* Cambio del mensaje del ultimo commit:__

    git commit --amend --no-edit ↵

__* Muestra archivos sin seguimiento:__

    git status -s

__* Muestra los detalles / cambios de un Archivo:__

    git show [nombre_archivo]

    Ej: git show historia.txt ↵

__* Mostrar los detalles / cambios de un Commit:__

    git show [id_commit]

    Ej: git show 26f3331 ↵

__* Comparar dos Commit:__

    git diff [id_commit_A] [id_commit_B]

    Ej:
    git diff db23bc0182ff9e2b61efa49402b2f532b958001d 3ac1e45963461f02c44b96d4bbdf087e0e5b848d ↵

__* Detalle de un Archivo:__

    git log [nombre_archivo]

    Ej: git log historia.txt ↵

__* Detalle resumindo de los cambios de un Commit:__

    git log --stat

__* Listado gráfico de Commits:__

    git log --graph --oneline

__* Resumen de commit por pantalla:__

    git log --oneline

__* Muestra todos los detalles de los commit:__

    git log --all

__* Muestra todos los detalles de los commit en forma gráfica:__

    git log --all --graph

__* Muestra en forma Resumida y Gráfica la historia de un proyecto desde sus inicios:__

    git log --all --graph --decorate --oneline

__* Guardar información de un log en txt:__

    git log > [nombre_archivo]

    Ej: git log > log.txt ↵

__* Muestra la información con más detalles de un Commit:__

    git log -g

__* Detalle de un Archivo:__

    git log [SHA o HASH]

    Ej: git log 7752b22 ↵

__* Detalle mas especifico de los cambios de un Commit:__

    git reflog

__* Numero limitado de Commit:__

    git lot -#

    Ej: git lot -2 ↵

__* Buscar información en la historia de los commits:__

    git log -S [palabra]

    Ej: git log -S "cabecera" ↵
        Este comando busca cuantas veces se uso la palabra "cabecera"

__* Muestra los commits realizado por los miembros del equipo:__

    git shortlog

__* Muestra ciertos commits realizado por los miembros del equipo:__

    git shortlog -sn

__* Muestra un listado de todos commits realizado y eliminados:__

    git shortlog -sn --all

__* Muestra un listado de todos commits realizado, eliminado los merge:__

    git shortlog -sn --all --no-merge

__* Cambiar el Nombre de un Archivo:__

    git mv file_from file_to

    Ej: git mv README.md README ↵

__* Eliminar un archivo del "Staging Area":__

    git rm --cached [nombre_archivo]

    Ej: git rm --cached historia.txt ↵

__* Cambiando de Version (histórico/actual) del Proyecto:__

    - Version Histórica:
        git checkout [id_commit] [nombre_archivo]

        Ej:  git checkout c84152d README.md ↵

    - Version Actual:
        git checkout [nombre_rama] [nombre_archivo]

        Ej:  git checkout main README.md ↵

__* Cambiando de Rama:__

    git checkout [nombre_rama]

    Ej: git checkout main ↵

__* Cambiando de Commit - Sin realizar cambios:__

    git checkout [hash]

    Ej: git checkout eff544f ↵

__* Pasos para volver a una version anterior del proyecto [SOFT]:__

    git reset [tag_commit] --soft  o  git reset --soft [commit_sha]

    Ej: git reset 26f333115c6724daae9cad02516718680d0e51a1 --soft ↵

        o

        git reset --soft 9cb545f ↵

__* Pasos para volver a una version anterior del proyecto [HEAD]:__

    git reset --HEAD@{#}

    Ej: git reset HEAD@{4} ↵
        (Al ejecutar este comando es como hacer un reset --soft)

__* Pasos para volver a una version anterior del proyecto [HARD]:__

    git reset [tag_commit] --hard  o git reset --hard [commit_sha]

    Ej: git reset 26f333115c6724daae9cad02516718680d0e51a1 --hard ↵

        o

        git reset --hard 9cb545f ↵

__* Borrar un archivo del STAGING AREA:__

    git reset HEAD [hombre_archivo]

    Ej: git reset HEAD hyperblog_project.code-workspace ↵
    (Este comando saca un archivo del staging area, el archivo quedara unstage)

__* Creación de Ramas:__

    git branch [nombre_rama]

    Ej: git branch header ↵

__* Cambio del Nombre de una Rama:__

    git branch -m [nombre_rama_antiguo] [nombre_rama_actual]

__* Borrando una Rama:__

    git branch -D [nombre_rama]

    Ej: git branch -D cabecera ↵

__* Listado e Historia de las Ramas:__

    git show-branch ↵

__* Listado e Historia de las Ramas mas Detallada:__

    git show-branch --all ↵

__* Hacer un merge: unir/fusionar dos ramas:__
    Para ejecutar este comando, se debe estar en master (main), y desde master (main) hacer un merge con cabecera.

    git merge [nombre_rama] "mensaje"

    Ej: git checkout master "mensaje" ↵

        git merge cabecera "Unión de ramas" ↵

__* Hacer un merge: de un commit (ref) especifico:__
    Para ejecutar este comando, se debera aplicar en la rama que se quiere fusionar el commit, antes de aplicarlo lo estudio mas a profundidad.

    git merge ref[SHA o HASH]

    Ej: git merge eff544f ↵

__* Hacer un rebase: reorganiza los cambios de la historia (commits):__

    git rebase [nombre_rama]

    Ej:
    1. Se debe ejecutar primero en la rama que se quiere fusionar (experimento)
        git checkout experimento ↵
        git rebase main ↵

    2. Luego se debe ejecutar en la rama principal (main)
        git checkout main ↵
        git rebase experimento ↵

__* Hacer un stash: almacenar los cambios en memoria de manera temporal:__

    git stash

    Ej: git stash ↵

    Saved working directory and index state WIP on main: 7c444e0  Respaldo numero 9 del proyecto en la noche - 03062024

__* Listar los cambios temporales (stash): puede haber uno o varios stash:__

    git stash list

    Ej: git stash list ↵

        stash@{0}: On main: primer mensaje
        stash@{1}: WIP on main: b96805e experimento # 2
        stash@{2}: WIP on main: b96805e experimento # 2

__* Hacer un [Stash POP]:__
    Recupera y Publica los cambios guardados en el ultimo stash, luego elimina el elemento despues que aparece.

    git stash pop (para un stash) o git stash pop stash@{ (num_stash) } (para varios stash)

    Ej: git stash pop ↵

__* Hacer un [Stash APPLY]:__

    git stash apply (para un stash) o git stash apply stash@{ (num_stash) } (para varios stash)

    Nota: Retorna los cambios de un stash especifico (de una lista), no elimina el stash, es como un vistazo al mismo.

__* Asignar un mensaje al stash:__

    git stash save "se escribe el mensaje a asignar"

    Ej: git stash save "primer mensaje" ↵

        $ git stash save "primer mensaje"
        Saved working directory and index state On main: primer mensaje

__* Eliminación de un stash:__

    git stash drop (para un stash) o git stash drop stash@{ (num_stash) } (para varios stash)

    Ej: git stash drop ↵

        $ git stash drop
        Dropped refs/stash@{0} (01dd4fc4e4c0623d9c607ea7768976d2de6d51e3)

__* Eliminación de todos los stash:__

    git stash clear (para varios stash)

    Ej: git stash clear ↵

__* Crear una rama usando el comando stash:__

    git stash branch [nombre_de_la_rama]

    Ej: git stash branch english-version ↵

__* Revisa e Identifica los archivos no tienen seguimiento en Git:__

    git clean --dry-run

    Ej:
        git clean --dry-run ↵
        Would remove historia - copia (2).txt
        Would remove historia - copia (3).txt
        Would remove historia - copia (4).txt
        Would remove historia - copia.txt

__* Elimina solo los archivos no tienen seguimiento en Git:__

    git clean -f

    Ej:
        git clean -f ↵
        Removing blogpost - copia (2).html
        Removing blogpost - copia.html
        Removing historia - copia (2).txt
        Removing historia - copia (3).txt
        Removing historia - copia (4).txt
        Removing historia - copia (5).txt
        Removing historia - copia (6).txt
        Removing historia - copia (7).txt
        Removing historia - copia.txt

 __* Elimina los archivos y carpeta no tienen seguimiento en Git:__

    git clean -f -d

    Ej:
        git clean -f -d ↵
        Removing css - copia/

__* Ejecutar el comando: cherry-pick:__

    git cherry-pick

    Ej:
        git log --oneline ↵   < Se ubica el commitsha

        git cherry-pick dca2a24 ↵

__* Procedimiento para detener la ejecucion del comando: cherry-pick:__

    git cherry-pick -- abort

    Ej: git cherry-pick -- abort ↵

__* Busqueda de Archivos, usando el comando: grep:__

    git grep [palabra]

    Ej: git grep color ↵

__* Busqueda de Archivos e Indica su ubicación, usando el comando: grep:__

    git grep -n [palabra]

    Ej: git grep -n platzi ↵

__* Busqueda de Archivos con Resumen Data, usando el comando: grep:__

    git grep -c [palabra / codigo]

    Ej:
        1. Palabra
        git grep -c platzi ↵

        2. Codigo
        git grep -c "<p>" ↵

__* Ejecutar el comando: blame:__

    git blame [nombre del archivo]

    Ej: git blame blogpost.html ↵

__* Muestra la información indentada:__

    git blame -c [nombre del archivo]

    Ej: git blame -c blogpost.html ↵

__* Muestra la información por rangos de busqueda numéricos:__

    git blame -L <linea_inicio>,<linea_fin> [nombre del archivo]

    Ej: git blame -L 10,50 blogpost.html ↵

__* Muestra la información por rangos de busqueda numéricos e indentado:__

    git blame -L <linea_inicio>,<linea_fin> -c [nombre del archivo]

    Ej: git blame -L 35,53 -c css/estilos.css ↵

__* Como crear un Tag:__

    Para llevar un control de versiones del proyecto finalizado o con mejoras, el procedimiento es:
    1- se copia el has de un commit, Ej: c84152d
    2- crear el tag, comando git tag -a [nombre_version] -m "mensaje" [numero_tag]

    Ej: git tag -a v0.1 -m "mejora del proyecto al cambiar la rama" c84152d ↵

__* Listado de Tags:__

    git tag

__* Muestra a que commit esta conectado un Tag:__

    git show-ref --tags

__* Eliminar un Tag (Local):__

    git tag -d [nombre_tag]

    Ej: git tag -d dormido ↵

__* Como clonar un Repositorio:__

    git clone [nombre_ruta_URL] [HTTPS/SSH]

    El proyecto deberá estar almacenado en la carpeta SITE, mara mi caso en particular.

    Ej:
        1. HTTPS: git clone https://github.com/freddier/hyperblog.git ↵

        2. SSH: git clone git@github.com:puchenkv/hyperblog.git ↵

### :orange_book: ACRÓNIMOS EN GIT

+ Config:

        -l (list)

+ Branch:

        -a (all)
        -r (remote)
        -u (upstream)
        -d (delete)
        -m (move)

+ Blame:

        -c (?)
        -L (Line)

+ Commit (confirmaciones):

        -m (msg) o --message

+ Clean:

        -f (force)
        -d (directories)

+ Grep (Globally Search for Regular Expression and Print Out, herramienta de linux):

        -n (--line-number)
        -c (--count)

+ Log:

        -S (string)

+ RM:

        -r (recursive)

+ Remote:

        -v (verbose)

+ Status:

        -s (short)

+ Tag:

        -a (add)
        -d (delete)

+ SHA: Secure Hash Algorithm
+ Wip: work in progress

### :bulb:TIPS EN GIT

__* Ventana de Comando: Git Bash:__
    Cuando después de ejecutar los comandos `git config --list` o `git log + [Nombre_Archivo]` y al final de la ventana muestre la palabra "END" o los ":" se deberá presionar la letra __q__ que significa "__Quit__" para salir de la consulta.

__* VIM:__
Es un editor de texto (de código abierto, libre y multiplataforma) basado en la línea de comando.

## :star:NOTAS DE [GITHUB]:star:

### :key:PROCEDIMIENTOS

__* GitHub (Definición):__
    Software que se usa para colaborar con otros programadores, usa una interfaz web, almacenar y publicar proyectos, historial de cambios y manejo de versiones. Es la red social del codigo.

__* Crear un nuevo repositorio:__
    Establece la conexión con el proyecto, solo debe ejecutarse una sola vez.

    git remote add [repositorio_remoto] [ruta: https o ssh]

    Ej:
        1. SSH
        git remote add origin git@github.com:puchenkv/tutorial_git_github.git ↵

        2. HTTP
        git remote add https://github.com/freddier/hyperblog.git ↵

__* Lista de repositorios online rastreados:__

    git remote

    Ej: git remote ↵
        origin

__* Lista Detallada de repositorios online rastreados:__

    git remote -v

    Ej: git remote -v ↵
        origin  git@github.com:puchenkv/tutorial_git_github.git (fetch)
        origin  git@github.com:puchenkv/tutorial_git_github.git (push)

__* Cambiar la URL de conexión:__

    git remote set-url [repositorio_remoto] [URL]

    Ej: git remote set-url origin git@github.com:puchenkv/tutorial_git_github.git ↵

__* Procedimiento para actualizar el proyecto de la nube a la bd local de control de versiones:__

    git pull [repositorio_remoto] [repositorio_local]

    Ej: git pull origin main ↵

__* Integración de Ramas (merge) tanto local como el servidor:__
    Este comando se ejecuta cuando hay documentos en la nube que no se encuentran en local, es decir, cuando git te muestra el siguiente error: "fatal: refusing to merge unrelated histories".

    git pull [repositorio_remoto] [repositorio_local] --allow-unrelated-histories

    Ej: git pull origin main --allow-unrelated-histories ↵

__* Subir contenido al repositorio en la nube:__

    git push -u [repositorio_remoto] [repositorio_local]

    Ej: git push -u origin main ↵

    Nota: la rama local se vincula con la rama remota automáticamente.... -u: upstream (flag)

__* Como Hacer un Tag a la Nube (github):__
    Para tener un histórico de control de versiones.

    git tag [Titulo_colocar_de_la_version] -m "mensaje"

    Ej: git tag version1.0 -m "mensaje version 1.0" ↵

__* Subir un Tag a la Nube (github):__

    git push [repositorio_remoto] [comando_git]

    Ej: git push origin --tags ↵

__* Eliminar un Tag de la nube:__

    git push [repositorio_remoto] :refs/tags/[nombre_tag]

    Ej: git push origin :refs/tags/dormido ↵

### :key: CONFIGURACIONES

==__LLAVES SSH - CONFIGURACIÓN LOCAL EN EL EQUIPO__==

+ PROCEDIMIENTO PARA CREAR LA LLAVE:

        ssh-keygen -t rsa -b 4096 -C "correo del analista"

+ PROCEDIMIENTO PARA REVISAR QUE EL SERVIDOR SSH ESTE ENCENDIDO:

        eval $(ssh-agent -s) ↵

+ PROCEDIMIENTO PARA AGREGAR LA LLAVE AL SERVIDOR LOCAL:

        ssh-add ~/.ssh/id_rsa ↵ (2 enter)

==__PROCEDIMIENTO DE REVISION DE LA CONFIGURACIÓN DE GIT EN EL EQUIPO LOCAL__==

    git config -l ↵

==__LLAVES SSH - CONFIGURACIÓN EN LA NUBE (GITHUB)__==

    git remote set-url origin url-ssh-del-repositorio-en-github

==__COMO CREAR UN ALIAS (SE GENERAN LOCALMENTE):__==

    alias [nombre_alias]=[formato_codigo]

    Ej: alias arbolito=git log --all --graph --decorate --oneline ↵

### :star:TRADUCCIONES DE [PALABRAS]:star:

1. brach: rama.
2. blame: culpa y/o responsable.
3. merge: unir, fusionar.
4. stage: escena.
5. staging: puesta en escena.
6. unstage: fuera del escenario.
7. upstream: subiendo o subir.
8. tracked: rastreado o seguimiento.
9. tag: etiqueta
10. untracked: sin rastreo o seguimiento.
