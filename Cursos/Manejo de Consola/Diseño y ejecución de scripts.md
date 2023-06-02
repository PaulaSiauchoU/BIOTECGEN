# Scripts: creación y ejecución 

Hasta el momento hemos visto formas de dar instrucciones en la terminal mediante comandos, los cuales son enunciados que no necesitan ser interpretados y pueden ser 
ejecutados directamente. Los comandos en Unix, y por lo tanto en la terminal de Linux, se ejecutan después del símbolo `$`.

Además de los comandos, para ejecutar instrucciones se pueden usar scripts, que por su traducción desde el inglés significa "guión". En programación los scripts se 
refieren a secuencias de comandos que están escritas en un lenguaje de programación en particular, por ejemplo Pyhton, Bash o Julia. Por esta razón, al momento de ser 
intepretados necesitan un compilador que los pueda ejecutar. 

## Creación de scripts 

Para crear un script desde la terminal, se debe empezar creando un archivo de texto plano. Una buena práctica es finalizar el nombre del archivo con la extención del 
programa mediante el cual se vaya a interpretar. Por ejemplo, si creamos un script llamado "MiPrimerScript" y el interpretador es Bash, se sugiere llamarlo
"MiPrimerScript.sh"; si es Python, "MiPrimerScript.py"; si es Perl, "MiPrimerScript.pl" o "MiPrimerScript.PL". Debido a que Unix no es un sistema que dependa de las 
extensiones para decidir cómo interpretar los archivos, no es obligatorio incluir la extensión en el nombre del archivo para que este funcione correctamente pero sí es
una buena práctica para ayudar a distinguirlos de otros tipos de archivos y permite versatilidad a la hora usar los mismos en otros sistemas que sí sean dependientes
de extensiones para la ejecución. 

Vamos a crear un script cuyo intérprete es Bash y va a imprimir en pantalla la frase "Hola Mundo". El primer paso es crear el archivo el cual vamos a llamar *Saludo.sh*. 
Vamos a crearlo abriendo directamente un editor de texto, en este caso nano. 
```console
$ nano Saludo.sh
```

Cuando se ejecute el comando aparecerá en pantalla el editor de nano:

![Resultado del comando `ls -l` en la carpeta del archivo Saludo.sh](https://github.com/jidiaz/BTG-CP/blob/main/Cursos/Manejo%20de%20Consola/PermisosArchivos.PNG)
## Esquema de scripts 
Los scripts suelen tener tres componentes principales. 
1. Línea de código que indica cómo debe ser intrerpretado el script. Inicia con una secuencia de carácteres llamada shebang o shabang compuesta por un numeral(#) y un signo de exclamación cerrado (!), y se completa con la ubicación del intrérprete en el equipo. 
2. Comentarios. Estas líneas de código tienen como principal función documentar y explicar más detalles sobre el script. No son instrucciones ejecutables y tienen siempre un carácter especial al inicio de la línea que le dice al intérprete que es un comentario y no una línea a ejecutar. Muchos lenguajes de programación usan el signo numeral (#) para indicar comentarios. Por ejemplo la línea `# Esto es un comentario` indicaría un comentario en un script de Python o Bash.
3. Comandos a ejecutar. Estos se escriben de la misma manera a como se ejecutarían en la terminal

Siguiendo la construcción de el script de ejemplo Saludo.sh, 

```bash
#!/bin/bash
echo "Hola Mundo"
# Este es un script que imprime la frase "Hola Mundo"
```
La primera línea indica el componente número 1 indicado anteriormente. La segunda línea es el comando a ejecutar. Nótese que en este ejemplo solo tenemos un comando pero lo usual es que se tengan varios. Por último, la tercera línea indica un comentario el cual no afecta la ejecución del script. 
Cuando ya se tiene el script listo se debe guardar, en el caso del editor Nano se puede usar las teclas *Crl*+*X* que le dan la instrucción al editor de salir. Como hasta este momento no hemos guardado el documento, Nano nos preguntará si queremos guardar y con qué nombre. Cada editor de texto usa combinaciones de teclas distintas y esta información de puede encontrar en la documentación de cada editor. En el caso de Nano, la podemos entrar en esta página [Overview of nano's shortcuts](https://www.nano-editor.org/dist/latest/cheatsheet.html).

Después de guardar y salir del editor de texto, va a volver a aprecer la terminal. Antes de ejecutar el archivo es importante comprobar si este archivo tiene los permisos necesarios para ser ejecutado. 

## Manejo de permisos. 
En el sistema Unix los archivos y carpeta pueden tener tres tipos de permisos: lectura (**r**), escritura (**w**) y ejecución (**x**). El permiso de lectura permite para los archivos, ver su contenido, y para los directorios, ver el nombre de los archivos contiene. Por otro lado, el permiso de escritura permite crear, modificar, renombrar y eliminar archivos y directorios. Finalmente, cuando un archivo tiene habilitado el permiso **x**, el usuario o grupo puede ejecutarlo. Asimismo, este permiso sobre un directorio permitirá recorrer su árbol para acceder ficheros y subdirectorios, pero no ver los ficheros dentro del directorio (excepto que se le dé el permiso de lectura). 

Antes de poder ejecutar el archivos se debe comprobar si el usuario tiene los permisos necesarios para realizar esta acción. Una opción para realizar esta verificación es listar los archivos en la carpeta con la opción `-l`. Siguiendo con el ejemplo que venimos construyendo, escribimos el comando `$ ls -l` en el directorio donde se encuentra *Saludo.sh*. El resultado que obtiene debe ser parecido al que aparece a continuación. 

[Resultados del comando `ls -l` en la carpeta que contiene a Saludo.sh]

La información que aparece en el recuardo en morado indica los permisos que tienen los archivos en la carpeta. De esta manera, el usuario tiene permisos de lectura y edición (rw), el grupo de lectura y edición(rw), y el resto, solo de lectura(r). En este caso para ejecutar el archivo vamos a habilitar también el permiso de ejecución para el usuario. Para eso, se utiliza el comando `chmod` con la siguiente sintaxis

```console 
$chmod [OPTIONS] MODE FILE...
```
Donde `MODE` será un número de 3 cifras en donde cada una indicará los permisos para la persona dueña del archivo, para el grupo y para el resto de los usuarios correspondientemente. `FILE` se refiere al nombre del archivo con su ubicación especificada si así lo requiriese. `[OPTIONS]` es opcional, para más información ver la documentación del comando en este link [Chmod Command in Linux (File Permissions)](https://linuxize.com/post/chmod-command-in-linux/). 

Cada cifra del parámetro `MODE` se le da un valor de 4 si se quiere ortorgar permiso de lectura, 2 si se quiere otorgar permiso de lectura y 1 si es permiso de ejecución. En caso de querer asignar más de un permiso los valores se suman. Para mayor información sobre el funcionamiento de estos valores ver el siguiente video. 
[video explicación Chmod]

Teniendo en cuenta lo anterior, al aplicarlo a nuestro ejemplo, 
```console
$chmod 755 Saludo.sh
```
Este comando le da permisos de lectura, edición y ejecución a la persona dueña del archivo; lectura y edición al resto de los usuarios. 
Una vez cambiados los permisos podremos ejecutar el archivo
```console
$bash Saludo.sh
```
