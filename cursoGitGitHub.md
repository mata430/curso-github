# <ins> <p>CURSO DE GIT Y GITHUB</p></ins>

## Configurando Git por primera vez

```
git --version
git config --global user.name "mata430"
git config --global user.email claudiothon@gmail.com
git config --global user.ui true
git config --list
# (asignando visual studio code como editor de) configuración de git
git config --global core.editor "code --wait"
git config --global -e
# (para estandarizar los saltos de línea en windows)
git config --global core.autocrlf true
# para estandarizar los saltos de línea en linux/mac
git config --global core.autocrlf input
# (ver todas las opciones de la configuración en la terminal)
git config -h
# (ver todas las opciones de la configuración en el navegador)
git help config
```

## Inicializar Git en un directorio local


```mkdir carpeta
cd carpeta
touch README.md
touch .gitignore
git init
code .
```

## Flujo básico

![Fujo baico](https://jonmircha.com/img/blog/git-flow.png)

1. Working Directory: Es el área correspondiente al estado modified y es la carpeta local de tu computadora donde almacenas los archivos de tu proyecto.
2. Staging Area: Es el área correspondiente al estado staged también se le llama index por que es el área donde git indexa y agrega los cambios realizados en los archivos previos a comprometerlos en su registro.
3. Local Repository: Es el área correspondiente al estado committed, donde los cambios ya se han registrado en el repositorio de git también se le llama HEAD por que indica en qué cambio se encuentra el puntero del repositorio.
4. Remote Repository: Es el área correspondiente al estado remote y es el directorio remoto donde almacenamos los archivos del proyecto en alguna plataforma web como GitHub, GitLab, BitBucket. Git denomina origin al repositorio remoto.
Flujo básico de Git

## COMANDOS

```# agregar los cambios de un archivo al staged
git add archivo/directorio
# agregar todos los cambios de todos los archivos al staged
git add .


# los cambios son comprometidos en el repositorio
# debes escribir el mensaje del cambio
# cuando se abra el archivo de configuración
# al terminar guarda y cierra el archivo
# para que los cambios tengan efecto
git commit
# es un shortcut del comando anterior
# escribes y confirmas el mensaje del cambio en un sólo paso
git commit -m "mensaje descriptivo del cambio"

((# cambio de rama
git branch -M main))

#Crear un repositorio en GitHub
# se agrega el origen remoto de tu repositorio de GitHub
git remote add origin https://github.com/usuario/repositorio.git
# la primera vez que vinculamos el repositorio remoto con el local
git push -u origin master (main)
# para las subsecuentes actualizaciones, sino cambias de rama
git push


#para descargar los cambios del repositorio remoto al local
git pull
```

## Cambio de rama master a main

## Para repositorios nuevos

```git init
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
```

## Para repositorios existentes

```git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
```

## Para reemplazar la rama master por main en GitHub

```# Paso 1
# Crea la rama local main y pásale el historial de la rama master
git branch -m master main


# Paso 2
# Haz un push de la nueva rama local main en el repositorio remoto de GitHub
git push -u origin main


# Paso 3
# Cambia el HEAD actual a la rama main
git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
```

## Paso 4

Cambia la rama default de master a main en tu repositorio de GitHub .

Para hacerlo, sigue las instrucciones de este [enlace](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/changing-the-default-branch)

```# Paso 5
# Elimina la rama master del repositorio remoto
git push origin --delete master
```

## Ayuda

```# ayuda en la terminal
git comando -h
# ayuda en el navegador
git help comando
```

## Ignorar archivos

En el archivo .gitignore incluimos todo lo que NO queramos incluir en nuestro repositorio. Lo podemos crear manualmente o con [gitignore.io.](https://www.toptal.com/developers/gitignore)

```# esto es un comentario
archivo.ext
carpeta
/archivo_desde_raiz.ext
# ignorar todos los archivos que terminen en .log
*.log
# excepto production.log
!production.log
# ignorar los archivos terminados en .txt dentro de la carpeta doc,
# pero no en sus subcarpetas
doc/*.txt
# ignorar todos los archivos terminados en .txt dentro de la carpeta doc
# y también en sus subcarpetas
doc/**/*.txt
```

## Clonar repositorios

### Comando  

```
git clone https://github.com/usuario/repositorio.git
```

## Ramas

Una rama nos permite aislar una nueva funcionalidad en nuestro código que después podremos añadir a la versión principal.

```# crear rama
git branch nombre-rama

# cambiar de rama
git checkout nombre-rama

# crear una rama y cambiarte a ella
git checkout -b rama

# eliminar rama
git branch -d nombre-rama

#eliminar rama (forzado no recomendado)
git branch -D nombre-rama

# listar todas las ramas del repositorio
git branch

# lista ramas no fusionadas a la rama actual
git branch --no-merged

# lista ramas fusionadas a la rama actual
git branch --merged

# rebasar ramas
git checkout rama-secundaria
git rebase rama-principal
```

## Fusiones

Une dos ramas. Para hacer una fusión necesitamos:

  1. Situarnos en la rama que se quedará con el contenido fusionado.
  2. Fusionar.

Cuando se fusionan ramas se pueden dar 2 resultados diferentes:

  * Fast-Forward: La fusión se hace automática, no hay conflictos por resolver.

  * Manual Merge: La fusión hay que hacerla manual, para resolver conflictos de duplicación de contenido.

```# nos cambiamos a la rama principal que quedará de la fusión
git checkout rama-principal

# ejecutamos el comando merge con la rama secundaria a fusionar
git merge rama-secundaria
```

## Cambios

Puedes agregar modificaciones al último cambio.

```# sin editar el mensaje del último commit
git commit --amend --no-edit
git add .
git commit --amend --no-edit


# editando el mensaje del último commit
git commit --amend -m "nuevo mensaje para el último commit"

# eliminar el último commit
git reset --hard HEAD~1
```

### Podemos desplazarnos en el historial del repositorio hacia atrás o adelante en cambios o ramas , sin afectar el repositorio como tal.

```# cambiar a una rama
git checkout nombre-rama

# cambiar a un commit en particular
git checkout id-commit
```

