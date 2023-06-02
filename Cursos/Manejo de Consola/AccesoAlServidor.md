# Acceder al servidor 
Para usar el servidor, se debe establecer una conexión usando el protocolo SSH (Secure SHell) al servidor que desee conectarse. Esta conexión varía según el sistema operativo desde el que se realizará la conexión.

## Sistema operativo Windows
Existen software clientes para Windows que permiten iniciar conexión remota (SSH) y acceder a ambientes Unix desde tu computador. Entre las más conocidas se encuentra
PuTTY,que puede descargarse del sitio oficial del software http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html. También existe el software cliente de ssh 
MobaXterm, que puede descargarse del sitio https://mobaxterm.mobatek.net/download.html, y finalmente, el cliente de transferencia de archivos FileZilla, que puede 
descargarse del sitio oficial https://filezilla-project.org/download.php?type=server.

En este tutorial utilizaremos MobaXterm, siguiendo las indicaciones dadas a continuación para el ingreso al servidor:
* Una vez abierto MobaXterm, en el menú presione el botón **Session** (1) y seleccione el botón **SSH** (2). A continuación, en la campo de **Remote host** ingrese la dirección IP del servidor (3). Seleccione la casilla de **Specify username** (4) e ingrese el usuario correspondiente(5). Asegúrese de que el puerto sea 22. Presione OK.

![Intrucciones para acceder a la consola](https://github.com/PaulaSiauchoU/BIOTECGEN/blob/main/Cursos/Manejo%20de%20Consola/MobaXterm1.PNG)

* Ingrese la contraseña que corresponde al usuario. Aunque no aparecen caracteres cuando se está escribiendo, en realidad se está escribiendo la contraseña. Luego presione la tecla Enter. Ahora hemos accedido al servidor y estamos en nuestro directorio home del ambiente Unix.

![Imagen de la consola una vez entramos con nuestras credenciales](https://github.com/PaulaSiauchoU/BIOTECGEN/blob/main/Cursos/Manejo%20de%20Consola/MobaXterm2.PNG)

## Sistema operativo Linux

MacOS y en Linux cuentan con todo lo necesario para comenzar. Usted puede usar SSH desde la terminal, sin necesidad de un software especial. Todo lo que necesita para ingresar al servidor es el software de conexión SSH y el nombre del usuario. Teclee el comando `ssh usuario@servidor` y presione la tecla “Enter”. `usuario` corresponde al valor en el campo **Specify username** de MobaXterm y `servidor` a la dirección IP a la que se quiere conectar. Enseguida, le pedirá la contraseña. Aunque no aparecen caracteres cuando la escribe, en realidad se está escribiendo su contraseña.

*ssh* – es la abreviación de Secure Shell. Es el nombre de un programa y un protocolo que permite el acceso y la ejecución de comandos en un ordenador remoto. El programa permite que los datos transiten de forma cifrada, ofreciendo así una mayor seguridad.

Para salir de un ordenador remoto, desconectando la conexión, utilize el comando exit. Por ejemplo: 

```bash
p.siaucho@servidor:~$ exit
```
**NOTA.** Algunas características importantes para tener en cuenta de la línea de comando de Linux, son:

* El sistema Linux distingue letras mayúsculas y minúsculas. Si el comando a ser ejecutado es, por ejemplo, `pwd`, los comandos `Pwd`, `PWd`, `PWD`, `PwD`, `pWD`, `pWd` y `pwD` no funcionarán.

* Todo comando en Linux debe ser seguido de la digitación de la tecla “Enter”.

* La línea donde escribes el comando varía con el tipo de intérprete de comandos del sistema (bash, csh, etc) y configuración del shell. En general, bash presenta el nombre del usuario, el nombre del servidor y el nombre del directorio corriente y, finalmente, un signo de dólar ($). Por ejemplo, `p.siaucho@server proyecto $`. Significa que el usuario *p.siaucho* está con la sesión iniciada en el servidor *server* y está en el directorio *proyecto*.
