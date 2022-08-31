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


```
mkdir carpeta
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

```
# agregar los cambios de un archivo al staged
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


# se agrega el origen remoto de tu repositorio de GitHub
git remote add origin https://github.com/usuario/repositorio.git
# la primera vez que vinculamos el repositorio remoto con el local
git push -u origin master
# para las subsecuentes actualizaciones, sino cambias de rama
git push


#para descargar los cambios del repositorio remoto al local
git pull
```