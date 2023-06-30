> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
* Comados terminal Git Bash
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

pwd (significa: imprimir ruta del directorio actual)
Devuelve la ruta de donde se esta ejcutando ese
comando en este momento

whoami (significa: quien soy?)
Muestra el nombre del usuario actual

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
help (significa: ayuda)
Muestra la documentacion de cómo utilizar
los comandos de la terminal de git bash. Por ejemplo
help pwd te mostraria las diferentes formas de utilizar
dicho comando.

Variante de help
help pwd
pwd --help
pwd  -h

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
git --version
node --version
python --version

Para concer la version de un programa
> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Ver el historial de comando de busqueda

Flecha Arriba
Flecha Abajo

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
clear (signifca: limpiar)
Limpia la terminal de comandos

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
ls (listar el contenido del directorio)
Lista el contenido visible del directorio actual.

ls -l
Lista detalles de las carpetas y archivos
contenidas en un directorio. Por ejemplo, muestra
la fecha de creacion, el tipo de archivo, los
permisos en sistema operativo y mas.

ls -a (-a significa todo es decir all)
Lista todos los archivos. Es decir, archivos ocultos
y visibles.

ls -la
List todos los archivos con todos los detalles de cada
archivo

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
cd Fotos (change directori)
Sirve para cambiar de directorio.
Es decir cd mas nombre de la carpeta a la que queremos
movernos, en este caso a la carpeta Fotos

cd "Archivos de programas"
Cuando el nombre de  tus archivos o carpetas tengan espacios
en blanco y quiera acceder a ellos simplemente escribir el nombre
entre comillas dobles.

cd F, mas tecla Tabulador
Utilizar tabulador para autocompletar los nombres de
las carpetas o archivos. En este caso
esoty en el Desktop donde hay una carpeta con el nombre
Fotos, por lo tando la terminar detecta que
hay una carpeta o archivo que inicia con la letra F, y
 al presionar tabulador me autocompleta
el nombre de dicha carpeta, de esta manera no tego que 
escribir manualmente todo el nombre.

cd y arractrar la ruta de la carpeta con el mouse
Autocompleta la ruta a la cual te quieres cambiar

cd ~
Para regresar a user yobani-tec.

cd .
Representa el directorio actual. Es decir, al ejecutar el comando
no llevaria al directorio o ruta actual. Por ejemlo si estamos 
en Desktop y ejecutamos el comando, pues nos dejaria en Desktop
que en este caso es el directorio actual.

cd ../
Para movernos un dierectorio anterior o un nivel superior.

cd /
para movernos a la raiz del disco duro. La raiz para este caso el la carpeta donde esta instalado
git bash.

cd /d 
para cambiar al disco local d. O cd /c para cambiar al c

cd ../..
Para regresar dos carpeta o dos niveles antes.

cd -
Para volvel a la carpeta donde estaba

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
touch hola-mundo.txt
Sirve para crear cualquier tipo de archivo con cualquier tipo de
extension, por ejemplo .exe, .doc, .pdf etc.

echo "Hola soy yobani" >  hola.txt
para crear un archivo y agregarle contenido a dicho archivo

cat hola.txt
Para ejecutar un archivo y mostrar su contenido

mkdir nueva carpeta 
Para crear una nueva carpeta(directorio)

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
rmdir nueva carpeta
Permite elimanr carpetas vacias, es decir, 
sin contenido

rm hola.txt
permite elimnar archivo, perno no carpetas

rm -r nueva carpeta
permite elimnar una carpeta con contenido

rm -rf nueva carpeta
permite eliminar carpetas y archivos forzando cualquier proceso
es decir eliminar de manera recursiva(con todo el conetido dentro)
y forzada(mata dos los procesos relacionado a esa carpeta u
archivo. Es el comando recomendado para eliminar cualquier direc
torio).(comando recomendado para eliminar carpetas con contenido)

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
mv hola.txt Fotos/
para mover el archivo a otra carpeta.
Nombre del archivo que queremos mover y luego el nombre
del directorio.

mv hola.txt Fotos/nota.txt
para mover el archivo a otra carpeta y con un nuevo nombre

mv hola.txt ../
para mover el archivo un nivel mas arriba

mv hola.txt ../..
para mover el archivo dos niveles mas arriba

mv hola.txt prueba.txt
Para renombrar un el nombre de un archivo.
en este caso se dice mueve el archivo hola.txt a la
mis carpeta, pero con el nombre prueba.txt

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
cp hola.txt ../
para copiar un archivo y pegarlo un nivel arriba

cp hola.txt ../prueba.txt
para copiar un archivo y pegarlo un nivel arriba y con un nuevo
 nombre

cp -r carpeta carpetados
copiar una carpeta con todo su contenido, al mismo tiempo
crear una carpeta llamada carpetados y pegar todo el contenido
en dicha carpeta

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
find hola.txt
para buscar archivos dentro de una carpeta

find *j
buscar todos los archivos que empiecen con j

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
ps
Para listar los procesos activos de la computadora.
Es similar al administrador de tareas.

kill 
Ejecutar en la terminarl de PowerShell ya que 
al ser la terminal nativa de windows tiene acceso a
todos los procesos que se estan ejecutando en la 
computadora.Este comando permite terminar un proceso en segundo plano, para ello se pone el el comando kill y el ID del proceso 
a terminar. Ejemplo kill 7412 y Enter

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
nano
abrir editor nano

vim
abrir editor vim

code
abrir editor visual studio code

code .
abrir editor visual studio code. Pero, en este caso
te ubicas en la caperta de tu proyecto y luego 
le ejecutas el comando code .  en este caso el puento 
quiere decir que que visual habra la carpeta o el directorio
actual, que seria la carpeta de tu proyecto.

code /c/xampp/htdocs/Projects/1-CRUD_DJANGO
abrir un proyecto con visual escribiendo la ruta de la
carpeta de tu proyecto

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
alias
permite listar tdodos los alias de los comados que hayas creado

alias hi="touch hola.txt"
Permite crear alias ha ciertas instrucciones.
En este caso estamos diciendo que hi es igual a crear
un nuevo archivo con la extension txt, y con el nombre hola.
Por lo tanto siempre que querramos crear un archivo txt
con dicho nombre, simplemete escribimos el comando hi y Enter.

unalias hi
permite elimnar un alias. para ello es necesario especificar el nombre
del alias.

> - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -