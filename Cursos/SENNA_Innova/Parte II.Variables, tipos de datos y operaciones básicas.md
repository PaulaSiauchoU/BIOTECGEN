## Variables, tipos de datos y operaciones básicas
### Variables
Una **variable** es un contenedor que se utiliza para almacenar y manipular datos en un computador. Es una etiqueta o nombre simbólico que se asigna a un valor específico en la memoria del computador. Estos valores pueden ser números, cadenas de texto, booleanos u otros tipos de datos.
La importancia de las variables en la programación radica en su capacidad para almacenar información y acceder a ella posteriormente. Esto permite la manipulación de datos de forma dinámica y facilita la creación de algoritmos más flexibles y reutilizables.
### Tipos de datos
Los **tipos de datos** se refieren a las categorías o clasificaciones de los valores que pueden ser almacenados y manipulados en un programa. Python es un lenguaje de programación de tipado (en este enlace puedes encontrar mas información sobre el tipado: https://dev.to/leolas95/tipado-estatico-y-dinamico-tipado-fuerte-y-debil-133n) dinámico, lo que significa que no es necesario declarar explícitamente el tipo de una variable, ya que el tipo se infiere automáticamente según el valor asignado.

En cuanto a los tipos de datos asociados con números existen 3 tipos. 
  - **int**: Representa números enteros sin punto decimal, por ejemplo: 5, -10, 0.
  - **float**: Representa números de punto flotante con parte decimal, por ejemplo: 3.14, -2.5, 0.0.
  - **complex**: Representa números complejos, que consisten en una parte real y una parte imaginaria, por ejemplo: $3 + 2j$, $-1.5 - 4j$
    En este enlace encuentras mas información sobre los números complejos: https://ellibrodepython.com/numeros-complejos

Para crear una variable se utiliza el operador "=", por ejemplo para crear la variable btg, utilizaríamos: 
``
 btg = 12
``
``
biotecnologia = 12
genetica = -0.1
biotecgen = biotecnologia + genetica
print (biotecgen)
``
En este ejemplo, biotecnología puede definirse como un float o un int, genetica a un float, biotecgen al ser una suma que requiere decimales debe ser un float. 

Para las cadenas de texto (Strings), se representa la secuencia de caracteres encerrados entre comillas simples ('') o comillas dobles (""). Por ejemplo: 'Hola', "Mundo", "¡Hola, Mundo!".
``
btg = "Biotecnología y genetica SAS"
``
Los **booleanos**, son un tipo de dato fundamental en programación que puede tener uno de dos valores: verdadero (true) o falso (false). Deriva su nombre del matemático y lógico británico George Boole, quien desarrolló el álgebra booleana, que es la base de la lógica binaria utilizada en los computadores. En la mayoría de los lenguajes de programación, incluyendo python, el tipo de datos booleano se representa internamente como un bit, donde 0 generalmente representa falso y 1 representa verdadero. Los booleanos se utilizan ampliamente en programación para realizar evaluaciones condicionales y tomar decisiones basadas en el resultado de esas evaluaciones.

Por ejemplo, en un programa podrías tener una variable booleana llamada "esMayorDeEdad" que tenga el valor verdadero si una persona tiene más de 18 años, o falso si tiene 18 años o menos. Luego, puedes utilizar esta variable en una estructura de control condicional, como un if-else que explicaremos en las siguientes partes de este curso, para ejecutar diferentes bloques de código en función del valor de la variable booleana.

Las **listas, tuplas y diccionarios** son estructuras de datos utilizadas en programación para organizar y almacenar colecciones de elementos relacionados. Cada una tiene sus propias características y se utilizan en diferentes situaciones según las necesidades del programa.

Una **lista** es una colección ordenada y mutable de elementos. Puede contener elementos de diferentes tipos, como números, cadenas de texto, booleanos, entre otros. Se define utilizando corchetes `[ ]` y los elementos se separan por comas. La principal característica de las listas es que se puede modificar su contenido, como agregar elementos, eliminar elementos existentes o cambiarlos. Por ejemplo:
   
   ```python
   mi_lista = [1, 2, "Hola", True]
   ```
Una **tupla** es similar a una lista, pero es inmutable, lo que significa que no se puede modificar después de su creación. Se define utilizando paréntesis `( )` y los elementos se separan por comas. A diferencia de las listas, no se pueden agregar, eliminar o modificar elementos una vez que se crea una tupla. Las tuplas son útiles cuando se necesita almacenar datos que no deben cambiar, como las coordenadas de un punto en un plano. Por ejemplo:
   
   ```python
   mi_tupla = (3, 4, "Hola")
   ```
Un **diccionario** es una colección de pares clave-valor, donde cada valor se accede a través de una clave única. Se define utilizando llaves `{ }` y los pares clave-valor se separan por comas. Los diccionarios son útiles cuando se necesita acceder a los elementos de manera eficiente utilizando una clave personalizada en lugar de un índice numérico. Por ejemplo:
   
   ```python
   mi_diccionario = {"nombre": "Juan", "edad": 25, "ciudad": "Madrid"}
   ```
   
   En este ejemplo, "nombre", "edad" y "ciudad" son las claves, y "Juan", 25 y "Madrid" son los valores correspondientes.

![image](https://github.com/jidiaz/BTG-CP/assets/137444188/801258a7-a056-4fcc-b139-8991a411b078)

Como se observa en la imagen también es posible hacer comentarios de texto dentro de casillas de código utilizando el caracter #, en este ejemplo, se creó una lista de genes y se utilizó la función len() para conocer la longitud de la lista. En las siguientes partes de este curso aprenderemos más sobre funciones. 

### Operaciones
También podemos hacer operaciones con las variables que creamos. En programación, los operadores son símbolos especiales que se utilizan para realizar **operaciones** en datos y variables. Los operadores permiten combinar, comparar o manipular valores según las reglas definidas en el lenguaje de programación. A continuación, se presentan algunos de los operadores más comunes en Python:

1. Operadores aritméticos:
   - Suma (+): se utiliza para sumar dos valores.
   - Resta (-): se utiliza para restar un valor de otro.
   - Multiplicación (*): se utiliza para multiplicar dos valores.
   - División (/): se utiliza para dividir un valor por otro.
   - Módulo (%): devuelve el resto de la división entera entre dos valores.
   - Potencia (**): se utiliza para elevar un valor a una potencia.
   - División entera (//): devuelve la parte entera del cociente de una división.

2. Operadores de asignación:
   - Asignación (=): se utiliza para asignar un valor a una variable.
   - Asignación con operación aritmética (+=, -=, *=, /=, %=, //=, **=): se utilizan para realizar una operación aritmética y asignar el resultado a la variable.

3. Operadores de comparación:
   - Igualdad (==): verifica si dos valores son iguales.
   - Desigualdad (!=): verifica si dos valores son diferentes.
   - Mayor que (>): verifica si el valor de la izquierda es mayor que el de la derecha.
   - Menor que (<): verifica si el valor de la izquierda es menor que el de la derecha.
   - Mayor o igual que (>=): verifica si el valor de la izquierda es mayor o igual que el de la derecha.
   - Menor o igual que (<=): verifica si el valor de la izquierda es menor o igual que el de la derecha.

4. Operadores lógicos:
   - AND (y lógico): devuelve True si ambas expresiones son verdaderas.
   - OR (o lógico): devuelve True si al menos una de las expresiones es verdadera.
   - NOT (no lógico): invierte el valor de la expresión.

5. Operadores de pertenencia:
   - in: verifica si un valor está presente en una secuencia.
   - not in: verifica si un valor no está presente en una secuencia.

6. Operadores de identidad:
   - is: verifica si dos variables se refieren al mismo objeto.
   - is not: verifica si dos variables no se refieren al mismo objeto.

Estos son solo algunos de los operadores más comunes en Python. Dependiendo del lenguaje de programación, pueden haber más operadores específicos. Los operadores te permiten realizar diferentes acciones en tus programas y son fundamentales para realizar comparaciones, cálculos y manipulación de datos.


