# Expresiones regulares

Una de las herramientas más utilizadas en el sistema Unix es la aplicación de expresiones regulares para coincidir, localizar y manejar patrones de caracteres sobre los archivos. Si bien el uso de expresiones regulares está muy generalizado en Linux, también se puede usar en lenguajes de programación como Perl, C ++, Python y Java. 
Uno de los comandos más conocidos para aplicar expresiones regulares es `grep`, palabra que significa "búsqueda global de expresiones regulares e impresion de las líneas coincidentes" (**G**lobal search for **R**egular **E**xpression and **P**rint matching lines). Sin embargo, las expresiones regulares se puede usar en comandos como `sed`, `tr`y `vi`. La sintaxis para `grep` es la siguiente: 
```
grep [opciones] patrón [documento(s)]
```
*patrón* se refiere a la expresión regular que el comando va a buscar sobre el documento seleccionado.

En la tabla 1 se encuentra un resumen de los carácteres más usados en la construcción de expresiones regulares

|Caracter | ¿Qué hace? | Ejemplo | Tipos de resultados a esperar |
| :-: | :-: | :-: | :-: |
| ^ | Coincidir lo que esté al principio de la línea | ^abc | abc, abcdef.., abc123 |
| $	| Coincidir lo que esté al final de la línea	|abc$|	my:abc, 123abc, theabc|
|.|Coincidir con cualquier caracter|	a.c |	abc, asg, a2c|
|\||	operador **O**| abc\|xyz	|abc **o** xyz|
|(...)|	Capturar todo lo que coincida con el contenido entre paréntesis	|(a)b(c)|	Captura 'a' y 'c'|
|[...]|	Coincidir con algún caracter especificado dentro de los paréntesis cuadrados|[abc]|a,b, or c|
|[^...]|Coincidir con cualquier caracter no contenido en los brackets|[^abc]|xyz, 123, 1de|
|[a-z]|	Coincidir con cualquier caracter que esté en rango especificado entre 'a' y 'z| [b-z]|bc, mind, xyz|
|{x}|Coincidir 'x' número de veces con el patron que se especifica|(abc){2}|abcabc|
|{x,}|Coincidir 'x' o más número de veces con el patron que se especifica|(abc){2,}|abcabc, abcabcabc|
|{x,y}|Coincidir entre 'x' y 'y' número de veces con el patron especificado |(a){2,4}|	aa, aaa, aaaaa|
|* |Coincidir cualquier caracter o grupo de carácteres que estén en vez de '* ' |ab\*c|	abc, abbcc, abcdc|
|+	|Coincidir el caracter que está antes del '+' una o más veces| a+c|	ac, aac, aaac|
|?| Coincidir con el caracter antes del '?' cero o una vez.|ab?c|ac, abc|
|\ | Saltar el caracter o crear una secuencia de escape después de la barra inclinada '\'|a\sc|	a c|

Sobre uno de los poemas emblemáticos del habla hispana, "Amor empieza por desasociego" escrito por Sor Juana Inés de la Cruz, vamos a ejemplificar lo anterior. 

>Amor empieza por desasosiego,
>
>solicitud, ardores y desvelos;
>
>crece con riesgos, lances y recelos;
>
>susténtase de llantos y de ruego.
>
>Doctrínanle tibiezas y despego,
>
>conserva el ser entre engañosos velos,
>
>hasta que con agravios o con celos
>
>apaga con sus lágrimas su fuego.
>
>
>Su principio, su medio y fin es éste:
>
>¿pues por qué, Alcino, sientes el desvío
>
>de Celia, que otro tiempo bien te quiso?
>
>
>¿Qué razón hay de que dolor te cueste?
>
>Pues no te engañó amor, Alcino mío,
>
>sino que llegó el término preciso.

Si iniciamos haciendo la siguiente búsqueda: 
```console
grep amor SorJuana.txt
```

Obtendremos el resultado de la imagen 


![grep ejemplo 1](https://github.com/PaulaSiauchoU/BIOTECGEN/blob/main/Cursos/Manejo%20de%20Consola/Regex1.PNG)

La salida del comando muestra la línea en el archivo donde se entontró el patrón a buscar. Es importante recordar que Linux es sensible a las mayúsculas a menos que se le indique lo contrario. Por eso, si usamos el comando

```console
grep Amor SorJuana.txt
```
vamos a obtener un resultado diferente: 

![grep ejemplo 2](https://github.com/PaulaSiauchoU/BIOTECGEN/blob/main/Cursos/Manejo%20de%20Consola/Regex2.PNG)

Ahora vamos a buscar todas las pabras que terminen en 's',

```
grep s\  SorJuana.txt
````
Nótese que los caracteres no solo incluyen las letras de la 'a' a la 'z' sino también cualquier caracter como espacio. En este caso se debe anteponer la barra inclinada `\` para indicar que el espacio después debe ser interpretado como un caracter y no como un cambio de parámetro. Después de aplicar el comando anterior el resultado sería el siguiente:
![grep ejemplo 3](https://github.com/PaulaSiauchoU/BIOTECGEN/blob/main/Cursos/Manejo%20de%20Consola/Regex3.PNG)

Linux solo reconoció aquellas palabras que después de la 's' final tenían un espacio. Si quisiéramos incluir además aquellas que están seguidas de una coma `,` el comando podría ser el siguiente: 

```console
grep "s\ \|s," SorJuana.txt
```
En este caso se puso la expresión regular entre comillas para que el operador "O" pudiera ser interpretado correctamente. El resultado de se ve en la siquiente imagen

![ejemplo grep 4](https://github.com/PaulaSiauchoU/BIOTECGEN/blob/main/Cursos/Manejo%20de%20Consola/Regex4.PNG)

Como hemos visto en los ejemplos anteriores, por defecto ´grep´ imprime en pantalla las líneas donde se encuentra el patrón de caracteres que coincide. Sin embargo, ¿qué se hace en el caso necesitemos contar el número de coincidencias? En ese caso le tenemos que pedir al comando que cuente el número de ocurrencias. Para eso redirigimos la salida de `grep` como entrada de `wc` con la opción `-l`:

```console
grep -o "s\ \|s," SorJuana.txt | wc -l
```
la salida de este comando es 

![ejemplo grep 5](https://github.com/PaulaSiauchoU/BIOTECGEN/blob/main/Cursos/Manejo%20de%20Consola/Regex5.PNG)

Si hacemos el conteo manual del ejemplo 4, vemos que el número de palabras terminadas en 's' coincide con 15. 


**Aquí puedes encontrar más material sobre expresiones regulares:**
https://phoenixnap.com/kb/grep-command-linux-unix-examples
https://francisconi.org/linux/expresiones-regulares#:~:text=Una%20expresi%C3%B3n%20regular%20en%20Linux,caracteres%20u%20operaciones%20de%20sustituciones.

