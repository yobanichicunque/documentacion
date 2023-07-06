# Comandos GitHub

### Temas

1. [Pasos previos](#pasos-previos)
1. [Subir repositiro](#subir-repositorio)
1. [Agreagar y subir cambios](#agregar-y-subir-cambios)
1. [Clonar un repostorio](#clonar-repositorios)
1. [Correr proyecto clonado](#correr-proyecto-clonado)

---

## Pasos previos

Detener el servidor.

```py
Control + c
```

Especificar dependencias mediante un archivo requirements.txt.

```py
pip freeze
pip freeze > requirements.txt
```

Desactivar el entorno virtual.

```
deactivate
```

Exportar la base de datos al proyecto.

Crear un archivo README.md con la documentacion del proyecto.

Crear un archivo .gitignore en la raiz del proyecto.

Guardar todos los cambios del proyecto.

Crear repositorio en GitHub para subir el proyecto.

---

## Subir repositorio

Para repositorio nuevos.

```py
git init
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
```

Para repositorio existentes

```py
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
```

---

## Agregar y subir cambios

```
git add .
git commit -m "Nuevos cambios"
git push
```
---
## Bajar cambios

```
git pull
```

---

## Clonar repositorios

```
git clone https://github.com/usuario/repositorio.git
```

---

## Correr proyecto clonado

Importar la base de datos en un gestor de base de datos.

Crear el entorno virtual y activarlo.

```
python -m venv env
env\scripts\activate
```

Instalar las dependencias del proyecto.

```
pip install -r requirements.txt
```

Correr proyecto Flask.

```
python app.py 
```

Correr proyecto Django.

```
py manage.py runserver 
```

[🔼 Regresar](#temas)

---

**Fin del curso.**

**¡Felicitaciones por llegar hasta aquí!**

---
