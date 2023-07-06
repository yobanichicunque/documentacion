# Terminal de comandos

Conocer la ruta del directorio actual, pwd (significa: imprimir ruta del directorio actual) y devuelve la ruta de donde se esta ejcutando ese comando en este momento.

```py
pwd
```

---

whoami (significa: quien soy?). Muestra el nombre del usuario actual.

```py
whoami
```

---

help (significa: ayuda). Muestra la documentacion de cómo utilizar los comandos de la terminal de git bash. Por ejemplo help pwd te mostraria las diferentes formas de utilizar dicho comando.

Variantes de help.

```py
help pwd
pwd --help
pwd  -h
```

---

Para concer la version de un programa.

```py
git --version
node --version
python --version
```

---

Ver el historial de comando de busqueda.

```py
Flecha Arriba
Flecha Abajo
```

---

Limpia la terminal de comandos.

```py
clear
```

---

Lista el contenido visible del directorio actual(listar el contenido del directorio).

```py
ls 
```

Lista detalles de las carpetas y archivos contenidas en un directorio. Por ejemplo, muestra la fecha de creacion, el tipo de archivo, los permisos en sistema operativo y mas.

```py
ls -l
```
Lista todos los archivos. Es decir, archivos ocultos y visibles(-a significa todo es decir all).

```py
ls -a
```

List todos los archivos con todos los detalles de cada archivo

```py
ls -la
```

---

cd Fotos (change directori). Sirve para cambiar de directorio. Es decir cd mas nombre de la carpeta a la que queremos movernos, en este caso a la carpeta Fotos.

```py
cd Fotos
```

Cuando el nombre de  tus archivos o carpetas tengan espacios en blanco y quiera acceder a ellos simplemente escribir el nombre entre comillas dobles.

```py
cd "Archivos de programas"
```

Utilizar tabulador para autocompletar los nombres de las carpetas o archivos. En este caso esoty en el Desktop donde hay una carpeta con el nombre Fotos, por lo tando la terminar detecta que hay una carpeta o archivo que inicia con la letra F, y al presionar tabulador me autocompleta el nombre de dicha carpeta, de esta manera no tego que escribir manualmente todo el nombre.

```py
cd F, mas tecla Tabulador
```

cd y arrastrar la ruta de la carpeta con el mouse. Autocompleta la ruta a la cual te quieres cambiar.

```py
cd arrastrar ruta carpeta
```

Para regresar a user yobani-tec.

```py
cd ~
```

Representa el directorio actual. Es decir, al ejecutar el comando no llevaria al directorio o ruta actual. Por ejemlo si estamos en Desktop y ejecutamos el comando, pues nos dejaria en Desktop que en este caso es el directorio actual.

```py
cd .
```

Para movernos un dierectorio anterior o un nivel superior.

```py
cd ../
```

Para movernos a la raiz del disco duro. La raiz para este caso el la carpeta donde esta instalado git bash.

```py
cd /
```

Para cambiar al disco local d. O cd /c para cambiar al c.

```py
cd /d 
```

Para regresar dos carpeta o dos niveles antes.

```py
cd ../..
```

Para volver a la carpeta donde estaba.

```py
cd -
```

---

Sirve para crear cualquier tipo de archivo con cualquier tipo de extension, por ejemplo .exe, .doc, .pdf etc.

```py
touch hola-mundo.txt
```

Para crear un archivo y agregarle contenido a dicho archivo.

```py
echo "Hola soy yobani" >  hola.txt
```

Para ejecutar un archivo y mostrar su contenido.

```py
cat hola.txt
```

Para crear una nueva carpeta(directorio).

```py
mkdir nueva carpeta 
```

---

Permite elimanr carpetas vacias, es decir, sin contenido.

```py
rmdir nueva carpeta
```
Permite elimnar archivo, perno no carpetas.

```py
rm hola.txt
```

Permite elimnar una carpeta con contenido.

```PY
rm -r nueva carpeta
```

Permite eliminar carpetas y archivos forzando cualquier proceso es decir eliminar de manera recursiva(con todo el conetido dentro) y forzada(mata dos los procesos relacionado a esa carpeta u archivo. Es el comando recomendado para eliminar cualquier direc torio). Comando recomendado para eliminar carpetas con contenido.

```PY
rm -rf nueva carpeta
```

---

Para mover el archivo a otra carpeta. Nombre del archivo que queremos mover y luego el nombre del directorio.

```py
mv hola.txt Fotos/
```

Para mover el archivo a otra carpeta y con un nuevo nombre.

```py
mv hola.txt Fotos/nota.txt
```

Para mover el archivo un nivel mas arriba.

```py
mv hola.txt ../
```

Para mover el archivo dos niveles mas arriba.

```py
mv hola.txt ../..
```

Para renombrar un el nombre de un archivo. En este caso se dice mueve el archivo hola.txt a la mis carpeta, pero con el nombre prueba.txt.

```py
mv hola.txt prueba.txt
```

---

Para copiar un archivo y pegarlo un nivel arriba.

```py
cp hola.txt ../
```

Para copiar un archivo y pegarlo un nivel arriba y con un nuevo nombre.

```py
cp hola.txt ../prueba.txt
```

Copiar una carpeta con todo su contenido, al mismo tiempo crear una carpeta llamada carpetados y pegar todo el contenido en dicha carpeta.

```py
cp -r carpeta carpetados
```

---

Para buscar archivos dentro de una carpeta.

```py
find hola.txt
```

Buscar todos los archivos que empiecen con j.

```py
find *j
```

---

Para listar los procesos activos de la computadora. Es similar al administrador de tareas.

```py
ps
```

Ejecutar en la terminarl de PowerShell ya que al ser la terminal nativa de windows tiene acceso a todos los procesos que se estan ejecutando en la computadora.Este comando permite terminar un proceso en segundo plano, para ello se pone el el comando kill y el ID del proceso  a terminar. Ejemplo kill 7412 y Enter.

```py
kill 7412 
```

---

Abrir editor nano.

```py
nano
```

Abrir editor vim.

```py
vim
```

Abrir editor visual studio code.

```py
code
```

Abrir editor visual studio code en el direcotrio actual.

```py
code .
```

Abrir un proyecto con visual escribiendo la ruta de la carpeta de tu proyecto.

```py
code /c/xampp/htdocs/Projects/1-CRUD_DJANGO
```

---

Permite listar tdodos los alias de los comados que hayas creado.

```py
alias
```

Permite crear alias ha ciertas instrucciones. En este caso estamos diciendo que hi es igual a crear un nuevo archivo con la extension txt, y con el nombre hola Por lo tanto siempre que querramos crear un archivo txt con dicho nombre, simplemete escribimos el comando hi y Enter.

```py
alias hi="touch hola.txt"
```

Permite elimnar un alias. para ello es necesario especificar el nombre del alias.

```py
unalias hi
```

---

**Fin del curso...**

**¡Felicitaciones por llegar hata aquí!**

---
