# Manejo básico de directorios

Un directorio es un conjunto de archivos. Todos los directorios de un sistema UNIX parten de un directorio principal llamado “raíz”, que se representa como “/”. 
El directorio raíz es la base para todo el árbol de directorios y allí es donde están contenidos todos los directorios del sistema.

Cuando un usuario accede a una sesión, Linux lo ubica en su directorio de trabajo personal (/home/nombre-usuario). Allí tienes la libertad absoluta para hacer lo que
requieras con tus archivos y directorios. Sin embargo, no podrás acceder y manipular el directorio de otro usuario, ya que Linux tiene un sistema de permisos que concede o restringe libertades sobre los directorios y ficheros.

**NOTA**: es importante destacar que todos los nombres de archivos y comandos son “case-sensitive” (distinguen entre mayúsculas y minúsculas).

Una vez ingresamos con nuestro usuario y contraseña, es importante reconocer nuestra ubicación en el sistema para la generación de archivos o movernos a lo largo de 
nuestra actividad. Para saber dónde estamos ubicados en el sistema, ejecutamos el comando `pwd`:

```console
p.siaucho@cb-data:~$ pwd
```

Cuya salida sería:

```console
/hpcfs/home/p.siaucho directorioactual
```

## Crear directorios
El orden de nuestros archivos depende de la metodología de organización deseada por el usuario. Por ello, crear y manipular directorios es importante. Para crear un 
directorio se utiliza el comando `mkdir` seguido por el nombre del directorio que deseamos crear.

```console
p.siaucho@cb-data:~$ mkdir prueba
```

Donde *prueba* es el nombre del directorio que queremos crear.

## Cambiar de directorio
Para movernos por la estructura de directorios utilizamos el comando `cd`, abreviación de “cambio de directorio”.

Como ya vimos, al entrar al sistema comenzamos en el directorio “~”, que hace referencia a nuestro home. Si queremos cambiarnos al directorio prueba, debemos usar 
el comando `cd`:

```console
p.siaucho@cb-data:~$ cd prueba
p.siaucho@cb-data:~/prueba$
``` 

Como podemos ver, la consola cambia para mostrar el directorio actual de trabajo, ahora ya estamos en el directorio prueba. Para volver al directorio que lo contiene,
usamos el comando `cd ..`:
```console
p.siaucho@cb-data:~/prueba$ cd ..
p.siaucho@cb-data:~$
```
Nota el espacio entre “cd” y “..”. Cada directorio tiene una entrada de nombre “..” la cual se refiere al directorio que contiene al directorio actual. De igual forma,
existe en cada directorio la entrada “.” la cual se refiere al directorio mismo en el que nos encontramos, así que el siguiente comando nos deja donde estamos:

```console
p.siaucho@cb-data:~/prueba$ cd .
```
Para más información de comandos básicos en Linux, puedes revisar los tutoriales recomendados al final del documento en material de apoyo.

# Manejo básico de archivos
## Crear y editar archivos
Para crear un archivo vacío rápidamente, podemos ejecutar el comando `cat`, `touch` o utilizar un editor de texto, como “nano”, “vi” o “vim” para crear y editar un archivo.

```console 
p.siaucho@cb-data:~/prueba$ cat > archivo1.txt
```
```console
p.siaucho@cb-data:~/prueba$ touch archivo1.txt
```
Cualquiera de los comandos anteriores crea un archivo vacío llamado *archivo1.txt*

```console
p.siaucho@cb-data:~/prueba$ nano archivo1.txt
```
```console
p.siaucho@cb-data:~/prueba$ vim archivo1.txt
```
```console
p.siaucho@cb-data:~/prueba$ vi archivo1.txt
```
Cualquiera de los comandos anteriores crea un archivo llamado archivo1.txt y lo abre con un editor para manipular su contenido.


## Listar contenido
Para ver el contenido de un directorio utilizamos el comando `ls`

```console
p.siaucho@cb-data:~/prueba$ ls
```
El sistema informa la presencia del archivo archivo1.txt creado. Vamos a usar el comando cat ahora para ver el contenido del archivo recién creado:

```console
p.siaucho@cb-data:~/prueba$ cat archivo1.txt
```
Si el archivo tiene algún contenido, este se presentará en pantalla. Por ejemplo:
```console
Mi primer archivo
```
Para ver un listado más detallado, podemos usar el comando ls -l:

p.siaucho@cb-data:~/prueba$ ls -l
Salida:
 **video salida**
 
# Copia archivos y directorios
Existen diversas formas de copiar archivos usando la terminal de Unix, en este tutorial vamos a ver dos formas básicas para copiar archivos, `cp` y `scp`. El uso y los argumentos necesarios dependerán si se quieren copiar los archivos en un mismo equipo o a través de una red externa. 

## Copia interna de archivos y directorios
Cuando queremos copiar archivos de una ubicación a otra dentro del mismo equipo usamos el comando `cp`. En este caso se deben usar los parámetros
* **archivo a copiar**: si está en la carpeta donde se encuentra ubicado, solo el nombre. De lo contrario deberá especificar la ruta correspondiente.
* **nombre directorio de destino:** ruta donde queremos copiar el archivo.

Ejemplo
```console
$ cp archivo1.txt /hpcfs/home/p.siaucho/Documents
```
En el ejemplo anterior el comando indica que se copie el archivo llamado "archivo1.txt" desde la carpeta en la que nos encontramos (por esta razón únicamente se pone el nombre del archivo) a otra carpeta que se llamada "Documentos". Como nos encontramos fuera de la carpeta "Documentos" se debe especificar la ruta de la misma. 

## Copia remota de archivos y directorios
"
Para copiar archivos remotamente, es decir, transferir los archivos de tu computador al clúster, y viceversa, debes utilizar el comando `scp` (secure copy). Para ejecutar la función scp es importante tener claros los siguientes parámetros:

**Usuario:** el nombre de usuario en el servidor. **Host:** dominio del servidor remoto. Archivo origen: ruta del archivo que queremos copiar. **Directorio destino:** ruta donde queremos copiar el archivo.

Para copiar archivos del clúster a tu computador, ejecuta el siguiente comando desde tu computador:
```console
$ scp usuario@host:Archivo_origen  directorio_destino
```
Ejemplo:

```console
$ scp p.siaucho@direccionIP:~/prueba/archivo1.txt  .
```
Para copiar archivos de tu computador al clúster, ejecuta el siguiente comando desde tu computador:

```console
$ scp archivo_origen usuario@host:directorio_destino
```
Ejemplo:
```console
$ scp archivo.txt p.siaucho@direccionIP:~/prueba/
```
**NOTA:** Este comando únicamente funciona sobre un solo archivo por lo que si se quiere aplicar a carpetas enteras se debe hacer un proceso reiterativo. El comando `scp` permite esta función, para hacerlo hay que agregar el argumento *-r* que indica recursivo.

Por ejemplo:
```console
$ scp -r directorio_origen usuario@host:directorio_destino
```

