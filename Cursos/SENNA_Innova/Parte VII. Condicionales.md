## Condicionales y operadores lógicos

Los **condicionales** son una parte fundamental de la programación y desempeñan un papel clave en el control del flujo de un programa. Permiten que un programa tome decisiones en función de condiciones específicas. Pueden evaluar expresiones o variables y ejecutar diferentes bloques de código según el resultado de la evaluación. Esto permite que un programa responda de manera dinámica a diferentes situaciones y realice acciones específicas en función de las condiciones establecidas.

Los condicionales permiten que un programa realice comparaciones, verifique igualdades o desigualdades, y tome decisiones basadas en esa información.
La estructura **if-else-elif** es una forma de construir condicionales en Python que permite evaluar múltiples condiciones y ejecutar diferentes bloques de código en función de esas condiciones. A continuación, se describe cada parte de esta estructura:

1. if: La cláusula "if" es la primera parte de la estructura y se utiliza para evaluar una condición. Si la condición se evalúa como verdadera (True), se ejecuta el bloque de código indentado que le sigue. Si la condición es falsa (False), se omitirá ese bloque de código y se pasará a la siguiente parte de la estructura.

2. elif (opcional): La cláusula "elif" es una abreviatura de "else if" y se utiliza para evaluar una condición adicional después de la cláusula "if". Puedes tener tantas cláusulas "elif" como necesites. Cada cláusula "elif" se evaluará solo si las condiciones anteriores a ella son falsas. Si se encuentra una cláusula "elif" cuya condición se evalúa como verdadera, se ejecutará el bloque de código correspondiente a esa cláusula y se omitirán las siguientes partes de la estructura.

3. else (opcional): La cláusula "else" es la última parte de la estructura y se utiliza para definir un bloque de código que se ejecutará si todas las condiciones anteriores son falsas. Es decir, si ninguna de las condiciones en las cláusulas "if" y "elif" se evalúa como verdadera, se ejecutará el bloque de código del "else". Puedes tener solo una cláusula "else" en la estructura if-else-elif.

Aquí tienes un ejemplo que ilustra la estructura if-else-elif en Python:

```python
BTG = 5

if BTG < 0:
    print("BTG es negativo")
elif BTG == 0:
    print("BTG es cero")
else:
    print("BTG es positivo")
```
![image](https://github.com/jidiaz/BTG-CP/assets/137444188/87b08fbc-33aa-4a2d-b193-611832422daf)

En este ejemplo, se evalúan diferentes condiciones utilizando la estructura if-elif-else. Si el valor de "BTG" es menor que 0, se imprime "BTG es negativo". Si no se cumple la primera condición, se verifica si "BTG" es igual a 0. Si es así, se imprime "BTG es cero". Si ninguna de las condiciones anteriores es verdadera, se ejecuta el bloque de código del "else" y se imprime "BTG es positivo".

Recuerda que la indentación es fundamental en Python, asegúrate de indentar correctamente el código dentro de cada cláusula para que se ejecute de manera adecuada.

# Operadores lógicos
Los operadores lógicos son herramientas utilizadas en programación para combinar y evaluar condiciones lógicas. Permiten realizar comparaciones entre valores o expresiones y producir un resultado basado en la lógica booleana.

1. Operador lógico AND (and):
El operador and devuelve True si todas las condiciones evaluadas son True, y False si alguna de las condiciones es False. En otras palabras, el resultado es True solo si todas las condiciones son verdaderas.

2. Operador lógico OR (or):
El operador or devuelve True si al menos una de las condiciones evaluadas es True, y False si todas las condiciones son False. En otras palabras, el resultado es True si alguna de las condiciones es verdadera.

3. Operador lógico NOT (not):
El operador not es un operador unario que invierte el valor de una condición. Si la condición es True, el resultado será False, y si la condición es False, el resultado será True.

Supongamos que estamos desarrollando un programa para determinar el riesgo de una enfermedad genética hereditaria basado en ciertas variantes genéticas. Utilizaremos tres variables booleanas para representar la presencia o ausencia de estas variantes:

```python
variante1 = True
variante2 = False
variante3 = True

# Operador lógico AND
if variante1 and variante2:
    print("Riesgo alto")
else:
    print("Riesgo bajo")

# Operador lógico OR
if variante1 or variante2:
    print("Riesgo moderado")
else:
    print("Riesgo bajo")

# Operador lógico NOT
if not variante3:
    print("Riesgo bajo")
else:
    print("Riesgo moderado")
```
Se utilizan los operadores lógicos and, or y not para evaluar las condiciones y determinar el riesgo de la enfermedad genética en función de la presencia o ausencia de las variantes.

Cada bloque condicional evalúa las condiciones utilizando los operadores lógicos correspondientes. Dependiendo de los resultados de las evaluaciones, se imprimirá un mensaje que indique el nivel de riesgo de la enfermedad ("Riesgo alto", "Riesgo moderado" o "Riesgo bajo").
