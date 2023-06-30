# Comandos GitHub

### Temas

1. [Pasos previos](#pasos-previos)
1. [](#)
1. [](#)
1. [](#)
1. [](#)

---

>**Nota**
>
>Recuerda agregar una credencial web de GitHub en tu PC, o bien quitar las >credenciales de otro usuario y agregar tus credenciales, de lo contraio no >podras subir tu proyecto a GitHub.

---

## Pasos previos

Detener el servidor.

```
Control + c
```

Especificar dependencias mediante un archivo requirements.txt.

```
pip freeze
pip freeze > requirements.txt
```

Desactivo el entorno virtual.

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

Para repositorio nuevos

```
git init
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
```

Para repositorio existentes

```
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

**¡Felicitaciones por llegar hata aquí!**

---
