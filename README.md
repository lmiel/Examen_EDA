# Examen_EDA
link repo: https://github.com/lmiel/Examen_EDA.git <br>
link dataset: https://archive.ics.uci.edu/ml/datasets/Covertype<br>
(no se puede subir pq es un archivo muy grande)<br>

ENUNCIADO

Forest Covertype data (https://archive.ics.uci.edu/ml/datasets/Covertype )es un conjunto de datos cargado en la librería sklearn que permite realizar un ejercicio tipo problemas de clasificación. El objetivo de este dataset es estudiar las variables cartográficas para poder predecir el tipo de cubierta forestal. El tipo real de cubierta forestal para una observación (celda de 30 x 30 metros) se ha determinado a partir de los datos del Servicio Forestal de EE.UU. (USFS).<br>

Los datos están en forma cruda (sin escalar) y contienen columnas binarias (0 o 1) de datos para variables independientes cualitativas (áreas silvestres y tipos de suelo).<br>

Estas áreas de estudio representan bosques con mínimas perturbaciones causadas por el hombre, por lo que los tipos de cubierta forestal existentes son más el resultado de procesos ecológicos, que de prácticas de gestión forestal.<br>



Ejercicio 1<br>

Para conseguir un dataset con una dimensión reducidad, aplica la técnica de Selección de variables basada en árbol de decisión mediante las importancias de cada variable (Decision Trees Importances):<br>

Filtra el tablón para quedarnos solamente con las variables que aglutinan hasta el 95% de la información que se requiere para estimar la variable objetivo.<br>
random_state=100<br>

Ejercicio 2<br>

Después de filtrar el dataset vamos a plantear un problema de clasificación para conseguir un clasificador de la cubierta forestal en basea a las variables cartográficas.:<br>

2.1 Genera una gráfica para visualizar la distribución de las variables del datset en conjunto. Analiza dicha gráfica y explica si hay una necesidad de normalizar los datos.<br>

2.2 Normaliza todas las variables del dataset a una escala estándar. Para ello puedes realizar estas transformaciones:<br>

LLevar las variables de entrada a una escala de 0 a 1<br>
Convertir la variable objetivo en valores numéricos entre 0 y el número de clases menos 1<br>

Ejercicio 3<br>

Después de estandarizar los datos procedemos a crear el primer clasificador:<br>

3.1 Divide el datset en training y en test:<br>

Guarda el 20% de los datos para testeo.<br>
random_state=100<br>
3.2 Entrena un modelo de regresión logística:<br>

Número máximo de iteraciones igual a 1000<br>
random_state=100<br>

3.3 Calcula diferentes métricas para evaluar este modelo y analiza su rendimiendo.<br>

Accuracy<br>
F1-score (average='weighted')<br>
Classification report (zero_division=0)<br>
Confusion matrix<br>

Ejercicio 4<br>

Ahora probamos la creación de otros modelo basados en árboles de decisión:<br>

4.1 Entrena un modelo tipo Decision Tree Classifire y calcula las métricas correspondientes para analizar su rendimiento en comparación con el modelo anterior:<br>

random_state=100<br>
Accuracy<br>
F1-score (average='weighted')<br>
Classification report (zero_division=0)<br>

4.2 Saca la curva de complejidad del modelo Decision Tree (Model Complexity Curve) y crea un nuevo clasificador con el valor óptimo de la profundidad del árbol según esta gráfica. Después saca las métricas correspondiente y analiza el rendimiento del modelo en comparación de los anteriores.<br>

random_state=100<br>
rango de profundidades: de 2 a 30 inclusive<br>

4.3 Saca la gráfica de el Learning Curve para estos modelos, definiendo y aplicando una función que toma el valor del hiperparámetro como su entrada y dibuja la evolución del rendimiento del modelo para el conjunto de training y de test. Explica si este último modelo tiene preferencia o no, comparando con modelos anteriores.<br>

random_state=100<br>
(Sugerencia: No incluya más de 10 puntos en el eje horizontal y empieza la gráfica con un mínimo de 1000 muestras para el modelo)<br>

Ejercicio 5<br>

Ahora probamos la creación de otros modelo basados en bosques aleatorios:<br>

5.1 Entrena un modelo tipo Random Forest Classifire y calcula las métricas correspondientes para analizar su rendimiento en comparación con los modelos anteriores:<br>

random_state=100<br>
5.2 Consulta la profundidad de todos los árboles del bosque creado en el paso anterior y calcula la mediana de este parámetro.<br>

5.3 Saca las curvas de complejidad del modelo Random Forest (Model Complexity Curve) y crea un nuevo clasificador con los valores óptimos analizados dentro de los rangos indicados para cada hiperparámeto. Después crea un modelo con estos parámetros "óptimos" y saca las métricas correspondientes para analizar el rendimiento del modelo en comparación con los anteriores.<br>

random_state=100<br>
define un rango con funciones de numpy para considerar estos números de árboles: [200, 250, 300, 350, 400]<br>
rango de profundidades: de 20 a 40 inclusive en pasos de 2 en 2.<br>
considera estas opciones para max_features : ["auto", "log2", None]<br>
Accuracy<br>
F1-score (average='weighted')<br>
Classification report (zero_division=0)<br>
OOB (out-of-bag score)<br>

5.4 Saca la gráfica del Learning Curve para estos modelos, definiendo y aplicando una función que toma el valor de los hiperparámetros analizados como su entrada y dibuja la evolución del rendimiento del modelo para el conjunto de training y de test. Explica si este último modelo tiene preferencia o no, comparando con modelos anteriores.<br>

random_state=100<br>
(Sugerencia: No incluya más de 10 puntos en el eje horizontal y empieza la gráfica con un mínimo de 1000 muestras para el modelo)<br>

Ejercicio 6<br>

Ahora probamos la creación de otros modelo basados en Gradient Boosting:<br>

18.6.1 Entrena un modelo tipo XGBoost Classifire y calcula las métricas correspondientes para analizar su rendimiento en comparación con los modelos anteriores:<br>

random_state=100<br>

6.2 Consulta el número y la profundidad máxima de los árboles del bosque creado en el paso anterior.<br>

6.3 Saca las curvas de complejidad del modelo XGBClassifier (Model Complexity Curve) y crea un nuevo clasificador con los valores óptimos analizados dentro de los rangos indicados para cada hiperparámeto. Después crea un modelo con estos parámetros "óptimos" y saca las métricas correspondientes para analizar el rendimiento del modelo en comparación con los anteriores.<br>

random_state=100<br>
define un rango con funciones de numpy para considerar estos números de árboles: [100, 200, 300, 400, 500]<br>
rango de profundidades: de 6 a 20 inclusive en pasos de 2 en 2.<br>
valores a considerar para el learning_rate: [0.01, 0.1, 0.3, 0.5]<br>
Accuracy<br>
F1-score (average='weighted')<br>
Classification report (zero_division=0)<br>

6.4 Saca la gráfica del Learning Curve para estos modelos, definiendo y aplicando una función que toma el valor de los hiperparámetros analizados como su entrada y dibuja la evolución del rendimiento del modelo para el conjunto de training y de test. Explica si este último modelo tiene preferencia o no, comparando con modelos anteriores.<br>

random_state=100<br>
(Sugerencia: No incluya más de 10 puntos en el eje horizontal y empieza la gráfica con un mínimo de 1000 muestras para el modelo)<br>

Ejercicio 7<br>

Ahora probamos la creación de otros modelos basados en métodos Bayesianos:<br>

7.1 Entrena un modelo para cada tipo de algoritmos Bayesianos y calcula las métricas correspondientes para analizar sus rendimientos en comparación con los modelos anteriores:<br>

GaussianNB<br>
MultinomialNB<br>
ComplementNB<br>
BernoulliNB<br>
Accuracy<br>
F1-score (average='weighted')<br>
Classification report (zero_division=0)<br>

7.2 Saca la gráfica del Learning Curve para el modelo GaussianNB y explica si este modelo sufre de un posible "Overfitting" o "Underfitting" comparando con modelos anteriores.<br>

random_state=100<br>
(Sugerencia: No incluya más de 10 puntos en el eje horizontal y empieza la gráfica con un mínimo de 1000 muestras para el modelo)<br>

Ejercicio 8<br>

Ahora probamos la creación de otros modelo basados en K vecinos más cercanos:<br>

8.1 Entrena un modelo tipo K-Nearest Neighbors con la configuración por defecto y otros dos modelos con 1 y 100 vecinos más cercanos. Calcula las métricas correspondientes para analizar sus rendimientos en comparación con el modelo anteriores:<br>

random_state=100<br>
Accuracy<br>
F1-score (average='weighted')<br>
Classification report (zero_division=0)<br>

8.2 Saca la gráfica del Learning Curve para estos modelos, definiendo y aplicando una función que toma el valor del hiperparámetro analizado como su entrada y dibuja la evolución del rendimiento del modelo para el conjunto de training y de test. Explica si este último modelo tiene preferencia o no, comparando con modelos anteriores.<br>

(Sugerencia: No incluya más de 5 puntos en el eje horizontal y empieza la gráfica con un mínimo de 1000 muestras para el modelo)<br>

Ejercicio 9<br>

Ahora probamos la creación de otros modelo basados en Redes Neuronales:<br>

9.1 Entrena un modelo tipo MLPClassifier y calcula las métricas correspondientes para analizar su rendimiento en comparación con los modelos anteriores:<br>

random_state=100<br>

9.2 Entrena otro modelo tipo MLPClassifier indicando los siguientes hiperparámetros y calcula las métricas correspondientes para analizar su rendimiento en comparación con los modelos anteriores:<br>

random_state=100<br>
hidden_layer_sizes=(100,200,100)<br>
Número máximo de iteraciones igual a 10000<br>
alpha=1e-5<br>
tol=1e-5<br>
