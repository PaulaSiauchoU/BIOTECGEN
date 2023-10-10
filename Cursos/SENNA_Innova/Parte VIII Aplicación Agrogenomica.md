# Aplicación - agrogenómica 
La agrogenómica es un campo interdisciplinario que combina la genómica y la agricultura para estudiar los genomas de plantas y animales utilizados en la agricultura. Su objetivo principal es comprender mejor los aspectos genéticos y moleculares relacionados con la producción agrícola y ganadera, con el fin de mejorar la productividad, la resistencia a enfermedades, la calidad y otros rasgos deseables en cultivos y animales de cría.

La agrogenómica involucra técnicas de secuenciación de ADN y análisis genómico para identificar genes responsables de características importantes en las especies agrícolas y ganaderas. Estos rasgos pueden incluir la resistencia a enfermedades, la tolerancia a estrés ambiental, la calidad nutricional, el rendimiento de cultivos, la eficiencia en el uso de recursos como el agua y los nutrientes, y otros atributos que son relevantes para la producción sostenible de alimentos y productos agrícolas.

Por otro lado, el ADN es como un "libro de instrucciones" en el cuerpo de los seres vivos. Es un conjunto de cuatro letras (nucleótidos) que contiene la información para construir y dirigir todas las partes de un organismo, como si fuera un plan para hacer y mantener un ser vivo.

El genotipado se refiere al proceso de determinar la composición genética de un individuo o una muestra biológica. En términos más simples, es el análisis de las variantes genéticas presentes en el ADN de cualquier organismo. Estas variantes pueden incluir cambios en nucleótidos individuales (llamados SNP, por sus siglas en inglés, o polimorfismos de un solo nucleótido). El genotipado se realiza típicamente utilizando tecnologías de secuenciación de ADN donde se determina de forma precisa el orden de los nucleótidos en una región de ADN, los datos generados son utilizados en investigaciones genéticas, estudios de asociación genética para identificar relaciones entre variantes genéticas y enfermedades, estudios de ascendencia para rastrear la herencia ancestral, y muchas otras aplicaciones en la genética y la medicina.
## Datos genotípicos
Como mencionamos brevemente en la introducción los datos genotipicos se pueden obtener mediante tecnologías de secuenciación, en datos, la salida de este proceso se representa en un archivo fastq, que se ve así: 

> @SRR001666.1 071112_SLXA-EAS1_s_7:5:1:817:345 length=36
> GGGTGATGGCCGCTGCCGATGGCGTCAAATCCCACC
> +SRR001666.1 071112_SLXA-EAS1_s_7:5:1:817:345 length=36 IIIIIIIIIIIIIIIIIIIIIIIIIIIIII9IG9IC

En este formato se almacena la secuencia obtenida junto con otras metricas de calidad. Pero para identificar variantes y mutaciones se tiene que mapear contra una referencia. Es como armar un rompecabezas de secuencias utilizando la imagen de referencia que viene en la caja del rompecabezas. 
Luego, detectamos las diferencias de cada una de las letras, en el ejemplo que trabajaremos hoy solo tendremos en cuenta una posición de todo el genoma, pero un archivo con todas las variantes se conoce como VCF (Variant calling format o formato de llamado de variantes) y se ve así: 

> ##fileformat=VCFv4.0
> ##fileDate=20110705
> ##reference=1000GenomesPilot-NCBI37
> ##phasing=partial
> ##INFO=<ID=NS,Number=1,Type=Integer,Description="Number of Samples With Data">
> ##INFO=<ID=DP,Number=1,Type=Integer,Description="Total Depth">
> ##INFO=<ID=AF,Number=.,Type=Float,Description="Allele Frequency">
> ##INFO=<ID=AA,Number=1,Type=String,Description="Ancestral Allele">
> ##INFO=<ID=DB,Number=0,Type=Flag,Description="dbSNP membership, build 129">
> ##INFO=<ID=H2,Number=0,Type=Flag,Description="HapMap2 membership">
> ##FILTER=<ID=q10,Description="Quality below 10">
> ##FILTER=<ID=s50,Description="Less than 50% of samples have data">
> ##FORMAT=<ID=GQ,Number=1,Type=Integer,Description="Genotype Quality">
> ##FORMAT=<ID=GT,Number=1,Type=String,Description="Genotype">
> ##FORMAT=<ID=DP,Number=1,Type=Integer,Description="Read Depth">
> ##FORMAT=<ID=HQ,Number=2,Type=Integer,Description="Haplotype Quality">
> #CHROM POS    ID        REF  ALT     QUAL FILTER INFO                              FORMAT      Sample1        Sample2        Sample3 2      4370   rs6057
> G    A       29   .      NS=2;DP=13;AF=0.5;DB;H2           GT:GQ:DP:HQ
> 0|0:48:1:52,51 1|0:48:8:51,51 1/1:43:5:.,. 2      7330   .         T  
> A       3    q10    NS=5;DP=12;AF=0.017               GT:GQ:DP:HQ
> 0|0:46:3:58,50 0|1:3:5:65,3   0/0:41:3 2      110696 rs6055    A   
> G,T     67   PASS   NS=2;DP=10;AF=0.333,0.667;AA=T;DB GT:GQ:DP:HQ
> 1|2:21:6:23,27 2|1:2:0:18,2   2/2:35:4 2      130237 .         T    . 
> 47   .      NS=2;DP=16;AA=T                   GT:GQ:DP:HQ
> 0|0:54:7:56,60 0|0:48:4:56,51 0/0:61:2 2      134567 microsat1 GTCT
> G,GTACT 50   PASS   NS=2;DP=9;AA=G                    GT:GQ:DP   
> 0/1:35:4       0/2:17:2       1/1:40:3

## ¡Ahora vamos a Python a analizar los datos!
En esta sección utilizaremos las herramientas de python que hemos aprendido en secciones anteriores, junto con nuevas herramientas, para analizar el impacto de las variantes en el gen BG1 en el tamaño de un cultivo de mazorca. El estudio se realizó con el proposito de determinar el impacto de un genotipo sobre diferentes características de la planta. El set de datos fue realizado basado en la información de esta publicación científica:  [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7589417/](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7589417/).

En esta simulación se analizaron 100 plantas a las que se les midió:

 1. El área de las hojas en milimetros cuadrados
 2. El peso seco de la planta en gramos 
 3. La altura de las plantas en centimetros
 4. El tamaño de la tusa de la mazorca en centimetros
 5. El peso de mazorca en gramos 
 6. Tamaño del grano en milimetros 
 7. Genotipo en una posición específica del genoma

El primer paso será descargar los datos y crear un archivo en colab como lo vimos en la primera sección del curso, si tienes dudas sobre este proceso ve a la primera guía. 
### Pandas 
Ahora importaremos pandas usando el código 

    import pandas as pd
Conectaremos colab con drive

    from google.colab import drive
    drive.mount('/content/drive')
Entraremos a la carpeta donde se encuentra nuestro archivo, si es la carpeta principal puedes usar este código, si creaste una carpeta diferente recuerda ajustalo del código ejemplo 

    %cd /content/drive/MyDrive/

 Ahora cargaremos la matriz con el nombre de variable 'df' usando pandas
 

    df = pd.read_csv("Python_DatosAgrogenomicos.csv")
Vamos a ver el encabezado para asegurarnos de que las columnas que esperamos se encuentren allí 

    df.head()
Y deberíamos ver la siguiente tabla: 
![df_head](https://github.com/jidiaz/BTG-CP/assets/137444188/58f5b6f8-12ab-48ed-8086-47f1b66680d4)


#### Estadísticas 
Utilizaremos la función describe() para obtener estadísticas de los datos como el conteo (count), promedio (mean), desviación estandar (std), el valor mínimo de una categoría (min), el valor máximo (max), entre otros. 

    df.describe()
Para obtener el nombre de las columnas podemos usar el comando 

    df.columns()
Ahora, realizaremos un diagrama de caja y bigotes para identificar outliers (valores extremos), en este ejemplo lo estamos haciendo con la columna 'Tamaño del grano (mm)', pero puedes hacerlo con todas las columnas que contiene la matriz, asegurate de que el texto sea exactamente igual, puedes hacerlo copiando y pegando del resultado del anterior método (df.columns())

    plt.figure(figsize=(8,  6))
    
    boxplot = df.boxplot(column='Tamaño del grano (mm)')
    
    plt.title("Diagramas de Caja")
    
    plt.ylabel("Valores")
    
    plt.xticks(rotation=45)
    
    plt.show()
El resultado de este código será la siguiente gráfica: 

![DiagramaDeCajaYBigotes](https://github.com/jidiaz/BTG-CP/assets/137444188/1cc2a239-ca16-4287-bb1d-d139e4f37868)

 
#### Filtrado de datos 
Un "outlier" (en español, valor atípico o valor excepcional) es un punto de datos que se aleja significativamente de la mayoría de los otros puntos de datos en un conjunto. En otras palabras, es un valor que está muy por encima o por debajo de la norma en un conjunto de datos y que puede influir en el análisis estadístico y sesgar los resultados si no se maneja adecuadamente.

Los outliers pueden surgir por diversas razones, como errores de medición, errores de entrada de datos, eventos inusuales o excepcionales en el entorno de recopilación de datos, o simplemente porque representan valores extremos legítimos en el conjunto de datos.
En este caso el valor outlier es el que tiene la medición en 40 que por alguna razón, probablemente errores en la medición se aleja mucho de los demás. Al ser solo un punto de dato que es exactamente podemos elegir todos los valores diferentes a 40, en otros casos pueden aplicarse otras reglas como < (menor que), > (mayor que), entre otros.

Para eliminar el outlier podemos aplicar un filtro que conserve solo los valores diferentes de 40, pero puedes utilizar otros de los operadores que vimos en las secciones anteriores. 

    df = df[df['Tamaño del grano (mm)'] != 40]
Ahora volvemos a visualizar el diagrama, usando el mismo código.
 ### Detección de duplicados
Los datos duplicados pueden distorsionar la precisión y la integridad de tus análisis. Si cuentas dos veces la misma observación, podría dar lugar a resultados inexactos y decisiones incorrectas. Al eliminar duplicados, aseguras que tus resultados sean representativos y reflejen la verdadera naturaleza de los datos. Evitas que ciertas observaciones influyan de manera desproporcionada en tus análisis.
Para detectar los duplicados podemos utilizar la siguiente función: 

    df[df.duplicated()]
En caso de que se hayan encontrado duplicados se pueden eliminar usando

    df.drop_duplicates()
### Otras transformaciones
  
Normalizar y estandarizar son dos técnicas comunes en el procesamiento de datos, especialmente en el ámbito de la minería de datos, el aprendizaje automático y la estadística. Ambas técnicas se utilizan para preprocesar y transformar los datos antes de aplicar modelos o análisis estadísticos. Aunque frecuentemente se utilizan de manera intercambiable, tienen significados ligeramente diferentes.

**Normalización:** La normalización se refiere al proceso de ajustar los valores de una variable para que estén en un rango específico. El objetivo principal de la normalización es escalar los datos para que todas las variables tengan la misma influencia en el análisis, evitando así que una variable domine sobre las demás debido a su escala original. Una de las formas de normalizar es: 

    X_normalized = (X - X_min) / (X_max - X_min)
**Estandarización:** La estandarización es un proceso similar, pero con un enfoque ligeramente diferente. En lugar de ajustar los valores en un rango específico, la estandarización se centra en transformar los valores de manera que tengan una media de 0 y una desviación estándar de 1. Esto es útil para algoritmos y análisis estadísticos que asumen una distribución normal de los datos.
En este caso no realizaremos estos procesos considerando que las estadísticas que revisamos con la función df.describe()
En algunos casos, como por ejemplo, al implementar aprendizaje de máquina es importante tener todas las características codificadas en números (floats o int) para poder hacer estadísticas y que los algoritmos funcionen correctamente. En este caso transformaremos la columna 'genotipo en el BG1 – posicion 1024' asignando 0 al alelo 'A' y 1 al alelo 'T'. Utilizaremos el siguiente código: 

    genotipoNumerico = {'A':  0,  'T':  1}
    
    df['genotipo en el BG1 – posicion 1024'] = df['genotipo en el BG1 – posicion 1024'].replace(genotipoNumerico)
    
    df.head()
Esto nos imprimirá la matriz corregida con la codificación nueva 

## Correlación 

La correlación es una medida estadística que describe la relación entre dos variables. Indica la dirección (positiva o negativa) y la fuerza de la relación entre estas variables. En el análisis de datos, la correlación es importante por varias razones:

- Identificar relaciones: La correlación ayuda a identificar si existe una relación entre dos variables. Puede indicar si las variables tienden a aumentar juntas (correlación positiva), disminuir juntas (correlación negativa) o no tener una relación aparente (correlación cercana a cero).

- Predicción: La correlación puede ayudar a predecir el valor de una variable basándose en la otra variable. Si dos variables están altamente correlacionadas, es posible utilizar una para predecir la otra con mayor precisión.

- Selección de características: En problemas de aprendizaje automático y minería de datos, la correlación se utiliza para seleccionar las características más relevantes o importantes para un modelo. Variables altamente correlacionadas pueden no agregar mucha información adicional, por lo que se pueden eliminar para simplificar el modelo.

- Ayuda en la validación de hipótesis: La correlación se utiliza para validar hipótesis en estudios científicos y de investigación. Si se espera que dos variables estén relacionadas, se puede usar la correlación para confirmar o refutar esta hipótesis.

- Anomalías y detección de errores: La falta de correlación entre variables que se esperaría que estén relacionadas puede indicar errores en los datos o la presencia de anomalías.


La correlación se representa a menudo en forma de gráficos, como diagramas de dispersión o mapas de calor, lo que permite visualizar la relación entre las variables. Esto ayuda a comprender mejor los datos y a comunicar los resultados de manera efectiva.


Pandas ofrece una variedad de funciones para calcular y analizar correlaciones entre variables en un DataFrame. Dos de las principales funciones para calcular correlaciones en Pandas son corr() y corrcoef(). 
Para poder obtener una correlación con todas las variantes de nuestro dataset debemos transformar los datos para que Python los pueda interpretar correctamente. En este caso, se asignará el valor $1$ a todas las Timinas (T en nuestro dataset) y un valor de $0$ a todas las Adeninas (A). Para eso, usamos el siguiente código. 

```
genotipoNumerico = {'A': 0, 'T': 1}
df['genotipo en el BG1 – posicion 1024'] = df['genotipo en el BG1 – posicion 1024'].replace(genotipoNumerico)
```
Hay muchas formas de obtener un mapa de correlación, en este caso vamos a usar la librería `seaborn`. 

```
import seaborn as sns
sns.heatmap(df.corr(method='spearman'))
```
Como salida del código anterior obtenemos los siguiente:

![image](https://github.com/jidiaz/BTG-CP/assets/12628984/7fa02bbb-7cd8-4a71-8265-2183078f86bb)

En este mapa de calor tenemos todas las variables implicadas en el dataset en cada uno de los ejes. Cada color indica un nivel distinto de correlaciones entre pares de variables según la leyenda de la figura. En este caso no tenemos correlaciones negativas entre las variables por lo que el valor mínimo de la escala llega a 0. Sin embargo es posible una correlación negativa, y en ese caso, las variables tendrían relaciones de proporcionalidad inversa. Nótese que que la variable genotipo en el BG1 tiene una alta correlación con las demás variables (valores cercanos a 1) lo que indica que esta posición **puede** ser un determinante genético de características como el tamaño del grano o el área de la hoja. 
En este caso usamos correlación de Spearman, principalmente porque no evaluamos normalidad, condición necesaria para otras correlaciones como la de Pearson. Es importante siempre revisar las condiciones de cada una de los tipos de correlaciones para poder aplicarlo correctamente. 

Es importante tener en cuenta que la correlación no implica causalidad. Solo porque dos variables estén correlacionadas no significa que una cause la otra. Puede haber factores ocultos o terceras variables que influyan en ambas.

## PCA
PCA (Principal Component Analysis, por sus siglas en inglés) es una técnica de análisis multivariado que se utiliza para reducir la dimensionalidad de un conjunto de datos. Su objetivo principal es encontrar un nuevo conjunto de ejes, llamados componentes principales, en los que los datos proyectados tengan la máxima varianza. Esto permite reducir la complejidad de los datos mientras se mantiene la mayor parte de la información.

Los componentes principales son combinaciones lineales de las variables originales que son ortogonales entre sí y están ordenados por la cantidad de varianza que capturan.

Una de las principales utilidades del PCA es poder visualizar los datos en 2 o 3 dimensiones. Uno de los impactos de hacer esta transformación es perder la infomación particular entre variables, por lo tanto, con datos de PCA no es recomendable determinar la correlación entre variables. 

Para realizar un PCA empezaremos cargando las siguientes librerias: 

    import numpy as np
    from sklearn.decomposition import PCA
    import matplotlib.pyplot as plt

La biblioteca 'sklearn.decomposition' proporciona herramientas para reducir dimensiones en una matriz de datos y nos ayudará a obtener los datos del PCA. 'Numpy' es necesaria para ejecutar las operaciones matematicas que sklearn necesita realizar y 'matplotlib.pyplot' es una librería que nos permitirá graficar los resultados. 

Para poder calcular un PCA, todas las variables deben ser de tipo numerico (int o float), en nuestro ejemplo, en la matriz tenemos los genotipos codificados en A y T, para solucionarlo podemos eliminar esta columna o codificarlo. Se suele evitar eliminar datos, piensen que cada dato que tienen costó tiempo y dinero, entonces optaremos por códificarlo. 

Para codificar estos datos asignaremos un valor a 'A' y uno a 'T', en el ejemplo usamos 0 y 1, respectivamente. 

    genotipoNumerico = {'A': 0, 'T': 1}
    df['genotipo en el BG1 – posicion 1024'] = df['genotipo en el BG1 – posicion 1024'].replace(genotipoNumerico)
    df.head()

Para reducir la dimensionalidad utilizaremos el siguiente código: 

    pca = PCA(n_components=2)
    X_pca = pca.fit_transform(df)
    std_dev = np.sqrt(pca.explained_variance_)
    explained_variance_ratio = pca.explained_variance_ratio_

y ahora visualizaremos los resultados con el siguiente código: 

    plt.figure(figsize=(8,  6))
    plt.scatter(X_pca[:,  0], X_pca[:,  1], alpha=0.7)
    plt.xlabel("Componente Principal 1 ({}% de varianza)".format(int(explained_variance_ratio[0] * 100)))
    plt.ylabel("Componente Principal 2 ({}% de varianza)".format(int(explained_variance_ratio[1] * 100)))
    plt.title("Datos transformados por PCA\nDesviaciones Estándar: [{:.2f}, {:.2f}]".format(std_dev[0], std_dev[1]))
    plt.grid(True)
    plt.show()


