# Fundamentos de Git y GitHub

### Temas

- [Pasos previos](#pasos-previos)
- [Configuracion inicial](#configuración-inicial)
- [Flujo básico](#flujo-básico)
- [De master a main](#de-master-a-main)
- [Ayuda](#ayuda)
- [Ignorar archivos](#ignorar-archivos)
- [Clonar repositorios](#clonar-repositorios)
- [Ramas](#ramas)
- [Fusiones](#fusiones)
- [Cambios](#cambios)
- [Registro del historial](#registro-del-historial)
- [Reseteo del historial](#reseteo-del-historial)
- [Resetear un repositorio](#resetear-un-repositorio)


---

## Pasos previos

Antes d einiciar este curso de Fundamentos de Git Y GitHub es necesario tener instalado Git en tu PC y tener una cuenta de GitHub.

```py
#Programas necesarios para este curso
Visual Studio Code
Git
GitHub
```
[🔼 Regresar](#temas)

## Configuración inicial

### Configurando Git por primera vez

```py
git --version
git config --global user.name "Yobani Chicunque"
git config --global use.email yobanichicunque@gmail.com
git config --global user.ui true
git config --list
# asignando visual studio code como editor de configuracion de git
git config --global core.editor "code --wait"
git config --global -e
# para estandarizar los saltos de linea en windows
git config --global core.autocrlf true
# para estandarizar los saltos de linea en linux/mac
git config --global core.autocrlf input
# ver todas las opciones de la configuracion en la terminal
git config -h
# ver todas las opciones de la configuracin en el navegador
git help config

```

### Inicializar Git en un directorio local

```py
mkdir carpeta
cd carpeta
touch README.md
touch .gitignore
git init
code .
```

[🔼 Regresar](#temas)

---

## Flujo básico

Estados

- Modified
- Staged
- Commited
- Remote


```py
# Agregar los cambios de un archivo al staged
git add archivo/directorio
# agregar todos los cambios de todos los archivos al staged
git add .


# los cambios son compromotidos en el repositorio
# debes escribir el mensaje del cambio
# cuando se abra el archivo de configuracion
# al terminar guarda y cierra el archivo
# para que los cambios tengan efecto
git commit
# es un shortcut del comando anterior
# escribes y afirmas el mensaje del cambion en un solo paso
git commit -m "mensaje descriptivo del cambio"


# se agrega el origen remoto de tu repositorio en GitHub
git remote add origin https://github.com/usuario/repositorio.git
# la primera vez que vinculamos el repositorio remoto con el local
git push -u origin master
# para las subsecuentes actualizaciones, sino cambias de rama
git push


# para descargar los cambios del ropositorio remoto al local
git pull
```

[🔼 Regresar](#temas)

---

## De master a main

### Para repositorios nuevos

```py
git init
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
```

### Para repositorios existentes

```py
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
```

### Para reemplazar la rama master por main en GitHub

```py
# Paso 1
# Crea la rama local main y pásale el historial de la rama master
git branch -m master main


# Paso 2
# Haz un push de la nueva rama local main en el repositorio de GitHub
git push  -u origin main

# Paso  3
# Cambia el HEAD actual a la rama main 
git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
```

**Paso 4**

Cambia la rama default de master a main de Git
Hub.

Para hacerlo siguie las instrucciones de este enlace.

```py
# Paso 5
# Elimina la rama master del repositorio remoto
git push origin --delete master
```

Para reemplazar la rama master por main en Git

```py
git config --global init.defaultBranch main
```

[🔼 Regresar](#temas)

---

## Ayuda

```py
# ayuda en la terminal
git comando -h
# ayuda en el navegador
git help comando
```

## Ignorar archivos

```py
# esto es un comentario
archivo.txt
carpeta
/archivo_desde_raiz.ext
# ignorar todos los archivos que terminen en .log
*.log
# excepto production.log
!production.log
# ignorar todos los archivos terminados en .txt dentro de la carpeta doc
# pero no es sus subcarpetas
doc/*.txt
# ignorar todos los archivos terminados en .txt dentro de la carpeta doc
# y tambien en sus subcarpetas
doc/**/*.txt
```

[🔼 Regresar](#temas)

---

## Clonar repositorios

```py
git clone https://github.com/usuario/repositorio.git
```

[🔼 Regresar](#temas)

---

## Ramas

```py
# crear ramas
git branch nombre-rama

# cambiar de rama
git checkout  nombre-rama

# crear una rama y cambiar a ella
git checkout -b rama

# eliminar rama
git branch -d nombre-rama

# crear rama rama remota
# De esta manaera se crea la rama remota en github y se suben los cambias efectuados en ella
git push -u origin nombre-rama

# eliminar ramas remotas
git push origin --delete nombre-rama

# eliminar rama(forzado)
git branch -D nombre-rama

# listar todas las ramas del repositorio
git branch

# listar ramas no fusionadas a la rama actual
git branch --no-marged

# listar ramas fusionadas a la rama actual
git branch --marged

# rebasar ramas
git checkout rama-secundaria
git rebase rama-principal
```


[🔼 Regresar](#temas)

---

## Fusiones


```py
# nos cambiamos a la rama principal que quedara de la fusion
git checkout rama-principal

#ejecutamos el comando merge con la rama secundaria a ejecutar
git merge rama secundaria
```

[🔼 Regresar](#temas)

---

## Cambios

Puedes agregar modificaciones al último cambio. Y lo recomendable es hacer estos cambios antes de hacer un push. De lo contrario ya no se puedria efectuar o modificar un cambios sobre el ultimo commit.

```py
# sin editar el mensaje del ultimo commit
git commit --amend --no-edit


# editando el mensaje del ultimo commit
git commit --amend -m "Nuevo mensaje para el ultimo commit"

# eliminar el ultimo commit
git reset --hard HEAD~1
```

Podemos desplazarnos en el historial del repositorio hacia atras o adelante en cambios o ramas, sin afectar el repositorio como tal.

```py
# cambiar a una rama
git checkout nombre-rama

# cambiar a un commit en particular
git checkout id-commit
```

## Registro del historial

```py
git log

#Muestra en una sola linea por cambio
git log one line

# guarda el log en la ruta y archivo que especifiquemos
git log > commits.log

# muestra el historioal con el formato que indicamos
git log --pretty=format:"%h - %an, %ar : %s"

# cambiamos la n por cualquie numero entero y mostrará los n cambios recientes
git log -n

# muestra los cambios realizados despues de la fecha especificada
git log --after="2019-07-07 00:00:00"

# muestra los cmbios realizados antes de la fecha especificada
git log --before="2019-07-08 00:00:00"

# muestra los cambios realizado en el rango de fecha especificado
git log --after="2019-07-07 00:00:00" --before="2019-07-08 00:00:00"

# muestra una grafia del historioal de cambios, rama y fusiones
git log --oneline --graph --all

# guarda la grafica del historioal de cambios en un archivo de texto plano
git log --oneline --graph --all > graph.log

# muestra todo el registro de acciones del log
# incluyendo intersecciones, camibios, eliminaciones  y fusiones, etc.
git reflog

# diferencias entre el work directoy  y el staging area
git diff

```

## Reseteo del historial

```py
#nos muestra el listado de archivos nuevos (untracked), borrados o editados
git status

# borra HEAD
git reset --soft

# borra HEAD y Staging
git reset --mixed

# borra todo: HEAD, Staging y Working Directory
git reset --hard

# deshace todos los cambios después del commit indicado, preservando los cambios localmente
git reset id-commit

# desecha todo el historial y regresa al commit especificado
git reset --hard id-commit
```

## Resetear un repositorio

```py
cd carpeta-repositorio
mv .git/config ~/saved_git_config
rm -rf .git
git init
git branch -M main
git add .
git commit -m "Commit inicial"
mv ~/saved_git_config .git/config
git push --force origin main
```

voy en el minuto 3:22 en el tema resetoe de un repositorio

[🔼 Regresar](#temas)

---



