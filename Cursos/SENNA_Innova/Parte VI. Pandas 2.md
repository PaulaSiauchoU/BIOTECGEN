**Nota:** En esta guía vas a encontrar varios ejemplos para poner en práctica los temas vistos. Te animamos a que los reproduzcas por tu cuenta para afianzar tus conocimientos. 

En la parte 1 de Pandas vimos las funcionalidades más usadas de esta librería. En esta sección vamos a ahondar en consulta de datos combinando las funciones ya vistas. También podrás encontrar creación de subsets, agrupación de datos, gráficas y otras características útiles de Pandas. 

## Consulta de datos

En guía de Pandas parte 1 vimos ejemplos para consultar elementos individuales usando su índice, sin embargo no ahondamos en el funcionamiento de los índices. Estos etiquetan los datos y ayudan a identificarlos usando indicadores conocidos importantes para el análisis y visualización de los mismos. Asímismo, permiten un alineamiento automático y explícito de los datos al mismo tiempo que permiten crear subconjuntos de datos de manera intuitiva. 
La opción por defecto de Pandas es asignar los índices a cada fila empezando desde el 0. Por ejemplo, al importar el siguiente [dataset](https://www.datos.gov.co/api/views/7h9i-7gun/rows.csv?accessType=DOWNLOAD) como Dataframe y mostrando las 5 primeras fila, obtenemos el siguiente resultado: 

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/dd927eef-e5fe-4bf1-8f8a-ea540efb7b5e)

Al lado izquierdo de los valores de la columna "Código Registro Plantación" hay un número que corresponde a $0$ para la primera fila, a $1$ para la segunda y así sucesivamente. Estos valores corresponden a los índices los cuales asignó Pandas automáticamente al crear el Dataframe. De esta manera podemos acceder a un conjunto de filas usando los índices usando el comando `plantaciones.loc[[0,1,2],:]`

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/0fb59302-3b00-49e5-8ca3-f7a4c983730c)

Como se puede observar en el ejemplo, al escoger estas filas se conserva la indexación.  

Por otro lado, de la primera parte se mencionó cómo hacer filtros usando condicionales y cómo con esta nomenclatura podemos acceder a distintas columnas. Filtrando la columna "Municipio" para el dataset del ejemplo anterior, obtenemos el siguiente resultado:

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/013b78fc-3cf1-45d3-9dec-acdb5fdaa812)


Al usar el mismo comando que aplicamos para mostrar las tres primera líneas, `plantaciones.loc[[0,1,2],:]`, obtenemos el siguiente resultado: 

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/2fcfa04c-c496-4e13-b7ec-3b8afcb64a97)

Nótese que Python nos indica que no encontró la fila con índice 0. Esta columna se eliminó con el filtro, y con ella, su índice. De hecho, si se observa el resultado del dataset se pueden ver que ya no tenemos índices consecutivos. 

# Indexación 

Como ya mencionamos en la sección anteriorla indexación en Pandas es esencial para un manejo eficiente y efectivo de los datos tabulares. Facilita el acceso, la manipulación y el análisis de datos, y es una de las características clave que hacen que Pandas sea una biblioteca poderosa y popular para la manipulación de datos en Python. Estas son algunas ventajas de la indexación en Pandas. 

- **Acceso a datos eficiente**: Los índices en Pandas permiten un acceso eficiente a los datos. En lugar de recorrer todo el DataFrame para buscar un valor específico, Pandas puede utilizar el índice para ubicar rápidamente la fila o columna deseada. Esto es especialmente beneficioso en DataFrames grandes, donde la búsqueda sin un índice puede ser costosa en términos de tiempo de ejecución.

- **Etiquetado de datos**: Los índices permiten etiquetar filas y columnas en un DataFrame. Esto facilita la identificación y selección de datos específicos utilizando etiquetas en lugar de índices numéricos, lo que hace que el código sea más legible y menos propenso a errores.

- **Operaciones de alineación**: Los índices son esenciales para realizar operaciones de alineación de datos. Pandas se encarga automáticamente de alinear los datos en función de los índices, lo que significa que puedes realizar operaciones aritméticas y lógicas entre DataFrames con diferentes estructuras, y Pandas se encargará de alinear los datos correctamente.

- **Facilita la manipulación de datos**: Los índices hacen que sea más fácil manipular y transformar los datos en un DataFrame. Puedes ordenar, agrupar, filtrar y realizar muchas otras operaciones utilizando índices y etiquetas de columnas.

- **Acceso a datos multidimensionales**: En Pandas, puedes tener DataFrames con índices múltiples (MultiIndex) que permiten organizar y acceder a datos multidimensionales de manera efectiva. Esto es útil en situaciones en las que tienes datos jerárquicos o multidimensionales.

- **Identificación única de filas**: Los índices pueden servir como una identificación única para filas en un DataFrame. Esto es especialmente útil en situaciones en las que deseas garantizar que no haya duplicados en tus datos y cuando trabajas con bases de datos relacionales.

- **Optimización de operaciones**: Pandas está diseñado para aprovechar al máximo los índices al realizar operaciones como concatenación, fusión y agrupación. Utilizar índices adecuadamente puede acelerar significativamente estas operaciones.


En los ejemplos anteriores vimos que al crear un dataframe, Pandas asigna la indexación automáticamente. Sin embargo, se le puede cambiar la indexación a conveniencia. Por ejemplo, 
![image](https://github.com/jidiaz/BTG-CP/assets/12628984/299d509d-cdd6-4b27-afe2-e364d5317bf8)

También se pueden asignar los índices como lo hace Pandas por defecto. Para eso, se usa la función  `.reset_index()`. Volviendo al ejemplo del dataframe de plantaciones_Belen, 

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/435273a4-1807-4a7e-a46b-2bbe51e9ce0e)

Se usó la opción `drop=True` para que eliminara la columna de índices anteriores. 


# Otras funcionalidades útiles en Pandas

**Operaciones matemáticas:** Pandas permite realizar operaciones matemáticas en columnas o filas enteras de un DataFrame.

Ejemplo de suma de sobre la columna 'Área plantación en Ha':

```python
#Operaciones matemáticas
suma = plantaciones_Belen2['Área plantación en Ha'].sum()
suma
```
El resultado para estos comandos es `411.0` lo que indica el área total de plantaciones para el municipio de Belén. 

**Agrupación y agregación:** Puedes agrupar datos en función de una columna y luego aplicar funciones de agregación, como `sum()`, `mean()`, `count()`, etc.

Ejemplo de agregación:

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/72d8f49b-5ef9-4fa2-af6b-af4de80c67da)

El ejemplo muestra una agrupación para el dataframe *plantaciones*. En este caso se puede ver el acumulado de hectáreas plantadas por municipio.  
**Manipulación de valores nulos:** Pandas ofrece métodos para tratar con valores nulos, como `dropna()`, `fillna()`, `isna()`.

Ejemplo de llenar valores nulos con ceros:

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/278442b3-afe2-46b1-aa3f-d2fabf7abd5f)

**Visualización de datos:** Pandas tiene integración con otras bibliotecas de visualización, como Matplotlib y Seaborn, para crear gráficos a partir de los datos. Además, Pandas tiene atributos que permiten hacer visualizaciones de datos sencillas. 

Por ejemplo: 
```
ax = plantaciones['Tipo de plantacion'].hist( color='purple', alpha=0.7, edgecolor='black')
ax.set_xlabel('Tipo de plantación')
ax.set_ylabel('Frecuencia')
ax.set_title('Histograma de tipo de plantación')
```
El resultado del código anterior es



Aquí, bins controla el número de barras en el histograma, color establece el color de las barras, alpha controla la transparencia y edgecolor establece el color del borde de las barras. Con los atributos `set_xlabel` , `set_ylabel` y `set_title` podemos poner las etiquetas de los ejes X, Y y el título correspondientemente. 

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/69b64022-dacc-4a8d-ab26-52b8c3fee074)


Esta opción es útil cuando deseas una forma rápida y sencilla de visualizar un histograma sin necesidad de personalización avanzada.

