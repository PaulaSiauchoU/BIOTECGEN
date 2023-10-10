## Funciones en Python:

Las funciones en Python son bloques de código que realizan tareas específicas y se definen mediante la palabra clave def, seguida del nombre de la función y una lista de parámetros entre paréntesis. Estas funciones pueden recibir argumentos (valores) como entrada y pueden devolver un resultado como salida. Las funciones permiten dividir un programa en partes más pequeñas y organizadas, lo que facilita el desarrollo y la reutilización de código. En general, la sintaxis para definir una función:

    def nombre_de_funcion(parametro1, parametro2, ...): 
	    # Cuerpo de la función 
	    # Aquí va el código que realiza la tarea deseada 
	    # Puede haber instrucciones, cálculos, estructuras de control, etc. 
	    return resultado # Opcional: si se desea devolver un valor



Un ejemplo de una función que tiene como objetivo sumar dos números:

    def sumar(a, b): 
    	resultado = a + b 
    	return resultado 

### Funciones integradas (Built-in functions) en Python: 
Python también incluye un conjunto de funciones integradas en el lenguaje que están disponibles para su uso sin necesidad de importar módulos adicionales. Estas funciones son parte del núcleo del lenguaje y se utilizan comúnmente para realizar tareas básicas y operaciones comunes. Algunas de las funciones integradas más utilizadas en Python son: 
	

 - print(): Muestra información en la consola o terminal. Recuerda que puedes ver un ejemplo en la parte I de este curso. 
 -  len(): Devuelve la longitud de una secuencia (cadena, lista, tupla, etc.). 
 - input(): Lee la entrada del usuario desde la consola. 
 - int(), float(), str(), bool(): Convierten valores a enteros, números de punto flotante, cadenas o booleanos, respectivamente. 
 - range(): Genera una secuencia de números. 
 - abs(): Devuelve el valor absoluto de un número. 
 - max(), min(): Devuelve el valor máximo o mínimo de una secuencia. 
 - sum(): Devuelve la suma de los elementos de una secuencia numérica. 
 - round(): Redondea un número al entero más cercano.
