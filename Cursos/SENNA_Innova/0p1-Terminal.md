# La terminal

La terminal (también conocida como línea de comandos, consola o shell) es una interfaz de texto que permite a los desarrolladores interactuar con una computadora o sistema operativo a través de comandos de texto en lugar de una interfaz gráfica de usuario (GUI). La terminal es una herramienta esencial en programación y tiene varias funciones y usos importantes:

- Ejecución de programas y comandos: Puedes ejecutar programas, scripts y comandos directamente desde la terminal. Esto es útil para compilar y ejecutar código, iniciar aplicaciones, y realizar diversas tareas de administración del sistema.

- Automatización de tareas: Puedes crear scripts de shell o scripts de automatización que ejecuten una serie de comandos en secuencia. Esto es útil para realizar tareas repetitivas o complejas de manera eficiente.

- Navegación de archivos y directorios: Puedes moverte a través de directorios, crear, copiar, eliminar y gestionar archivos y carpetas utilizando comandos como `cd`, `ls`, `mkdir`, `cp`, `rm`, entre otros.

- Gestión de versiones: Las herramientas de control de versiones como Git se utilizan a menudo desde la terminal para gestionar repositorios de código, realizar confirmaciones (commits), fusionar ramas (branches), entre otras acciones.

`- Depuración y diagnóstico: Puedes utilizar comandos para analizar registros del sistema (logs), realizar pruebas de conectividad de red (ping, traceroute), verificar el uso de recursos del sistema y solucionar problemas.

- Administración de paquetes: En sistemas basados en Unix/Linux, como Ubuntu o CentOS, puedes utilizar la terminal para instalar, actualizar y gestionar paquetes de software utilizando comandos como apt, yum, pip, o conda, dependiendo de la distribución y el tipo de paquetes.

- Configuración y personalización del sistema: Puedes editar archivos de configuración, cambiar la apariencia del sistema y personalizar tu entorno de trabajo desde la terminal.

- Acceso remoto: La terminal también se utiliza para conectarse a servidores remotos mediante SSH (Secure Shell) y realizar tareas de administración en esos servidores.

- Desarrollo web y servidores: Los desarrolladores web a menudo utilizan la terminal para ejecutar servidores locales, administrar bases de datos y automatizar flujos de trabajo en el desarrollo de aplicaciones web.


La terminal se puede utilizar en tu propio equipo (computadora local) sin necesidad de un servidor. La terminal es una herramienta estándar que se encuentra disponible en la mayoría de los sistemas operativos, incluyendo Windows, macOS y sistemas basados en Unix/Linux. La terminal de Unix, en comparación con las terminales de otros sistemas operativos, tiene varias ventajas que la hacen especialmente poderosa y atractiva para desarrolladores, administradores de sistemas y usuarios avanzados. Además, la mayoría de software que se utilizan en bioinformática, y por lo tanto, en agrogenómica se encuetran disponibles para ejecutar en Linux. Por esta razón, en estas guías nos vamos a enfocar en el manejo de terminal en el sistema operativo de Linux. 

## Conexión a la terminal en un entorno local.

### Sistema operativo Windows  
Para conectarse a la terminal de Linux desde un sistema operativo de Window se pueden utilizar varias herramientas. Nos vamos a enfocar en un software de Terminal Remota, MobaXTerm, esta aplicación permite establecer conexiones SSH a servidores Linux y trabajar en ellos de forma remota. Proporcionan una interfaz de terminal similar a la que encontrarías en Linux. 
MobaXTerm se puede descargar de manera gratuita de la página (https://mobaxterm.mobatek.net/download.html). 

Una vez se instale en el computador, al abrir el programa se verá una interfaz parecida a la ade la siguiente imagen. 
![MobaLocal1](https://github.com/jidiaz/BTG-CP/assets/12628984/f1066732-59c8-4493-880f-d73948d52ac4)
A continuación se debe escoger la opción 'Start Local Terminal' o su equivalente en español. A continuación se abrirá una ventana como la que se presenta a continuación. 

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/f9810d1a-2175-42e3-9b8a-8a1746fd34ef)



![Imagen de la consola una vez entramos con nuestras credenciales](https://github.com/jidiaz/BTG-CP/blob/main/Cursos/Anal%C3%ADtica%20de%20datos%20agrogen%C3%B3micos-SENA/MobaXterm2.PNG)

### Sistema operativo Linux

MacOS y en Linux cuentan con todo lo necesario para comenzar. Usted puede usar SSH desde la terminal, sin necesidad de un software especial. Todo lo que necesita para ingresar al servidor es el software de conexión SSH y el nombre del usuario. Teclee el comando `ssh usuario@servidor` y presione la tecla “Enter”. `usuario` corresponde al valor en el campo **Specify username** de MobaXterm y `servidor` a la dirección IP a la que se quiere conectar. Enseguida, le pedirá la contraseña. Aunque no aparecen caracteres cuando la escribe, en realidad se está escribiendo su contraseña.

*ssh* – es la abreviación de Secure Shell. Es el nombre de un programa y un protocolo que permite el acceso y la ejecución de comandos en un ordenador remoto. El programa permite que los datos transiten de forma cifrada, ofreciendo así una mayor seguridad.

Para salir de un ordenador remoto, desconectando la conexión, utilize el comando exit. Por ejemplo: 

```bash
p.siaucho@cb-data:~$ exit
```
**NOTA.** Algunas características importantes para tener en cuenta de la línea de comando de Linux, son:

* El sistema Linux distingue letras mayúsculas y minúsculas. Si el comando a ser ejecutado es, por ejemplo, `pwd`, los comandos `Pwd`, `PWd`, `PWD`, `PwD`, `pWD`, `pWd` y `pwD` no funcionarán.

* Todo comando en Linux debe ser seguido de la digitación de la tecla “Enter”.

* La línea donde escribes el comando varía con el tipo de intérprete de comandos del sistema (bash, csh, etc) y configuración del shell. En general, bash presenta el nombre del usuario, el nombre del servidor y el nombre del directorio corriente y, finalmente, un signo de dólar ($). Por ejemplo, `p.siaucho@server proyecto $`. Significa que el usuario *p.siaucho* está con la sesión iniciada en el servidor *server* y está en el directorio *proyecto*.
