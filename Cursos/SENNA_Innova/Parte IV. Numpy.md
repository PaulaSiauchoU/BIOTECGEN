## Bibliotecas de python 

En el contexto de la programación en Python, una biblioteca (también conocida como módulo o paquete) se refiere a un conjunto de funciones, clases y métodos predefinidos que se agrupan juntos para realizar tareas específicas. Estas bibliotecas están escritas en Python o en otros lenguajes y se pueden importar en tus programas para extender las capacidades y funcionalidades de Python.

Las bibliotecas en Python son esenciales para reutilizar código y evitar tener que escribir desde cero funciones y rutinas comunes. Proporcionan implementaciones eficientes y optimizadas de algoritmos y tareas específicas. 

Las bibliotecas pueden tener diferentes propósitos y enfoques. Algunas se centran en tareas científicas, como cálculos numéricos y análisis de datos, mientras que otras se especializan en el desarrollo web, la creación de interfaces gráficas, el aprendizaje de máquina, la manipulación de bases de datos, entre otros.

Un ejemplo de biblioteca es Numpy (Numerical Python) es una biblioteca de programación en Python utilizada para realizar operaciones matemáticas de manera eficiente. Proporciona soporte para matrices (tablas) multidimensionales, así como funciones matemáticas para operaciones en estas matrices.

Algunas de las características clave de NumPy son:

1. **Matrices multidimensionales:** NumPy introduce un nuevo tipo de dato llamado "array" o arreglo, que puede tener cualquier número de dimensiones. Esto permite representar y manipular datos en forma de matrices o tensores de manera eficiente.

2. **Funciones matemáticas:** NumPy proporciona una amplia variedad de funciones matemáticas y operadores para realizar cálculos numéricos, desde operaciones básicas como suma, resta, multiplicación y división hasta funciones trigonométricas, exponenciales y logarítmicas.

3. **Broadcasting:** NumPy permite realizar operaciones entre arreglos de diferentes tamaños y formas de manera automática y eficiente, a través de un mecanismo llamado "broadcasting". Esto facilita la realización de cálculos sobre datos heterogéneos.

4. **Integración con otras bibliotecas:** NumPy es una base para muchas otras bibliotecas científicas y de análisis de datos en Python, pandas (biblioteca para manipulación de datos y análisis), y scikit-learn (biblioteca para aprendizaje de máquina).

En el ejemplo que realizaremos vamos a sumar, restar, multiplicar y dividir. El primer paso es importar la librería, eso lo haremos con el código: 

    import numpy as np
Ahora crearemos un arreglo, un arreglo (también conocido como array) estructura de datos que permite almacenar y organizar múltiples valores del mismo tipo en una sola variable. Los arreglos son particularmente útiles cuando necesitas trabajar con colecciones de datos homogéneos, como una lista de números o caracteres.
En las siguientes partes de este curso aprenderemos más estructuras de datos y como crearlas. Por ahora, crearemos dos arreglos con los nombres arreglo 1 y arreglo 2: 

    # Crear dos arreglos NumPy
    arreglo1 = np.array([1,  2,  3])
    arreglo2 = np.array([4,  5,  6])

Ahora haremos una suma de estos arreglos: 

    suma = arreglo1 + arreglo2
    print (suma)
Con los datos del ejemplo, esto debe imprimir [5 7 9], resultado de la suma de [1+4 , 2+5, 3+6]. 
