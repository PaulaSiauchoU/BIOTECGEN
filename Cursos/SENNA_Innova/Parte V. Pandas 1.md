# Pandas 
Es una biblioteca de código abierto para Python que proporciona estructuras de datos y herramientas de análisis de datos de alto rendimiento. Fue desarrollada con el objetivo de facilitar el manejo y análisis de datos tabulares y en serie, lo que la convierte en una herramienta fundamental en el ámbito del análisis de datos y la ciencia de datos. 

Pandas ofrece las estructuras de datos Series y DataFrame, que son extremadamente flexibles y eficientes para el análisis y manipulación de datos. Estas estructuras permiten trabajar con datos tabulares y en serie de forma intuitiva, lo que facilita el manejo de datos complejos. Además, proporciona una amplia gama de funciones y métodos para la manipulación y limpieza de datos. Puedes realizar operaciones como selección, filtrado, agregación, transformación y fusión de datos de manera sencilla y eficiente. También ofrece herramientas para manejar valores faltantes y eliminar duplicados, lo que simplifica el proceso de preparación de datos.

Pandas se integra sin problemas con otras bibliotecas populares de Python para el análisis de datos, como NumPy, Matplotlib y scikit-learn. Esto te permite realizar operaciones avanzadas de análisis estadístico, visualizaciones y aplicar algoritmos de aprendizaje maquina de manera eficiente y sin problemas.
Utiliza estructuras de datos optimizadas y algoritmos vectorizados que aprovechan las capacidades de procesamiento en paralelo de las CPU modernas. Esto resulta en un rendimiento superior en comparación con otras bibliotecas de manipulación de datos.

Pandas ofrece funciones integradas para importar y exportar datos desde y hacia una amplia variedad de formatos, como CSV, Excel, bases de datos SQL, entre otros. Esto simplifica el proceso de carga y guardado de datos, permitiendo una fácil integración con diferentes fuentes de datos.

**Instalación de Pandas y configuración del entorno de desarrollo:**


Pandas se debe instalar si se utiliza de forma local en un computador, al trabajar en google colab solo es neceario importar la librería utilizando 
 ```
 import pandas as pd
 ```
## Carga de documentos
**Carga y guardado de datos:** 

Para cargar y guardar datos desde y hacia diferentes fuentes, como archivos CSV, Excel, bases de datos SQL y formatos JSON. 
Para esto se utilizan funciones como`read_csv()`, `read_excel()`, `to_csv()`, `to_excel()`, entre otras. 
Una de las formas más sencillas de acceder a los documentos es cargarlos a google drive y conectar google colab con drive utilizando la siguiente línea de código: 
``` python
  from google.colab import drive
drive.mount('/content/drive')
%cd /content/drive/MyDrive/
```

Luego se crea un dataframe con el siguiente código
```
df = pd.read_csv("Origen.csv")
```

![image](https://github.com/jidiaz/BTG-CP/assets/137444188/fa88cd2f-e9f7-4c7e-9da9-f3e1593fa5ae)


## Series y dataframes en Pandas
Otra de las formas de tener datos es creandolos directamente en pandas, existen series y data frames. La Serie es una estructura de datos unidimensional en Pandas que puede contener diferentes tipos de datos, como enteros (int), floats, cadenas de texto (Strings), etc. Es similar a una columna en una hoja de cálculo o una matriz unidimensional en Python.

- **Creación de una Serie:** Para crear una Serie, puedes utilizar la función `pd.Series()` y pasar una lista, una matriz NumPy o un diccionario como argumento. Por ejemplo:

  ```python
  import pandas as pd

  data = [10, 20, 30, 40, 50]
  serie = pd.Series(data)
  print(serie)
  ```

  Esto creará una Serie con los valores `[10, 20, 30, 40, 50]`.

- **Indexación y acceso a elementos de una Serie:**

Puedes acceder a elementos individuales de una Serie utilizando su índice. Por ejemplo:

  ```python
  print(serie[0])  # Acceder al primer elemento
  print(serie[2:4])  # Acceder a un rango de elementos
  ```

- **Métodos y operaciones comunes en Series:**

Pandas ofrece una amplia gama de métodos y operaciones para manipular y analizar Series. Algunos ejemplos comunes son:

  - `head()` y `tail()`: Muestra los primeros o últimos elementos de una Serie.
  - `describe()`: Calcula estadísticas descriptivas, como media, mediana, desviación estándar, etc.
  - `max()`, `min()`, `mean()`, `sum()`: Calcula el valor máximo, mínimo, media y suma de una Serie.
  - `sort_values()`: Ordena los valores de la Serie en orden ascendente o descendente.

  ![image](https://github.com/jidiaz/BTG-CP/assets/137444188/12ecd9a1-9aaa-4f40-91fa-cde61201e77b)


- **DataFrame en Pandas**

El DataFrame es una estructura de datos bidimensional en Pandas que organiza los datos en filas y columnas, similar a una tabla de Excel o una base de datos relacional.

- **Creación de un DataFrame a partir de diferentes fuentes de datos:**
Puedes crear un DataFrame utilizando diferentes fuentes de datos, como listas, diccionarios, matrices NumPy, archivos CSV, Excel, bases de datos, etc. Por ejemplo:

  ```python
  import pandas as pd

  data = {'Nombre': ['Juan Rodríguez', 'María Castro', 'Luis Fuentes'], 'Edad': [25, 30, 35]}
  df = pd.DataFrame(data)
  print(df)
  ```
Esto creará un DataFrame con dos columnas, "Nombre" y "Edad", y tres filas con los valores correspondientes.

- **Manipulación de filas y columnas:** Puedes agregar, eliminar y modificar filas y columnas en un DataFrame. Algunas operaciones comunes son:

  - `df.columns`: Accede a las columnas del DataFrame.
  - `df['Columna']`: Accede a una columna específica.
  - `df['Nueva Columna'] = valores`: Agrega una nueva columna al DataFrame.
  - `df.drop('Columna', axis=1)`: Elimina una columna del DataFrame.

- **Filtrado y selección de datos en un DataFrame:**
 
Puedes filtrar y seleccionar datos en un DataFrame utilizando condiciones lógicas. Algunas operaciones comunes son:

  - `df[df['Columna'] > valor]`: Filtra las filas que cumplen con una condición específica.
 
![image](https://github.com/jidiaz/BTG-CP/assets/137444188/676058b4-6da3-4a9c-a546-fa585e21fd21)



