# Semana-3.-Fashion-MNIST
Fashion MNIST model
# Clasificador fashion MNIST con CNN en Keras
# Integrantes:
# Joffre Quinteros
# David Maldonado 
# Esteban Caza
# Luis Campaña
# Bolivar Alvarez


# Descripción:

Este proyecto utiliza Keras para construir y entrenar un modelo de red neuronal convolucional (CNN) para clasificar imágenes del dataset que contiene imágenes en escala de grises. Cada imagen tiene una resolución de 28x28 píxeles. El objetivo es entrenar un modelo que pueda clasificar correctamente estas imágenes en las categorías correspondientes.

# Requisitos:
Para ejecutar este proyecto, necesitarás lo siguiente:

Python 3.x
Keras
NumPy
Matplotlib
scikit-learn
TensorFlow

# Explicación del script:
1. Importación de bibliotecas: Se importan las bibliotecas necesarias, incluyendo matplotlib.pyplot para trazar la matriz de confusión, numpy para operaciones numéricas, keras para definir y entrenar el modelo, y seaborn para mejorar la visualización de la matriz de confusión.
2. Parámetros del modelo y datos: Se definen los parámetros del modelo y los datos, como el número de clases (num_classes) y la forma de entrada (input_shape). Luego, se cargan los datos del conjunto Fashion MNIST y se dividen en conjuntos de entrenamiento y prueba.
3. Preprocesamiento de datos: Las imágenes se escalan al rango [0, 1] y se asegura que tengan la forma correcta para ser procesadas por el modelo
4. Definición del modelo: Se define un modelo secuencial de Keras, que consiste en capas convolucionales, de agrupación y una capa densa final con activación softmax para la clasificación.
5. Compilación y entrenamiento del modelo: Se compila el modelo especificando la función de pérdida, el optimizador y las métricas a utilizar. Luego, se entrena el modelo utilizando el conjunto de entrenamiento, con un tamaño de lote y un número de épocas especificados.
6. Predicciones y matriz de confusión: Se realizan predicciones en el conjunto de prueba y se calcula la matriz de confusión utilizando las etiquetas verdaderas y las predicciones realizadas por el modelo.
7. Visualización de la matriz de confusión: La matriz de confusión se visualiza utilizando un mapa de calor, donde cada celda muestra el recuento de muestras clasificadas en esa categoría. Se muestran las etiquetas reales en el eje y y las etiquetas predichas en el eje x.

# Explicación de las capas:
1. Capa de entrada (Input layer):
Esta capa recibe los datos de entrada con la forma especificada en input_shape, que en este caso es (28, 28, 1), lo que significa que cada imagen de entrada tiene una dimensión de 28x28 píxeles en escala de grises.

2. Capa convolucional (Conv2D):
La primera capa convolucional tiene 32 filtros de tamaño 3x3 y utiliza la función de activación ReLU (Rectified Linear Activation) para introducir no linealidad en la red.
Esta capa realiza la convolución de los filtros sobre la imagen de entrada para extraer características importantes.

3. Capa de agrupación (MaxPooling2D):
Después de cada capa convolucional, se utiliza una capa de agrupación para reducir la dimensionalidad espacial de la salida y, por lo tanto, el número de parámetros de la red.
La capa de agrupación utiliza el método de agrupación máxima (max pooling) con una ventana de tamaño 2x2 para reducir a la mitad la dimensión de la entrada.

4. Capa convolucional (Conv2D):
La segunda capa convolucional tiene 64 filtros de tamaño 3x3 y también utiliza la función de activación ReLU.
Al igual que la primera capa convolucional, esta capa extrae características adicionales de la imagen de entrada.

5. Capa de agrupación (MaxPooling2D):
Otra capa de agrupación se aplica después de la segunda capa convolucional para reducir aún más la dimensionalidad de la salida.

6. Capa de aplanamiento (Flatten):
Esta capa aplanará la salida de la capa anterior en un vector unidimensional. Esto es necesario para conectar la salida de las capas convolucionales a la capa densa final.

7. Capa de dropout (Dropout):
La capa de dropout aplica regularización durante el entrenamiento, lo que ayuda a prevenir el sobreajuste (overfitting) al aleatoriamente dejar fuera algunas unidades durante el proceso de entrenamiento.

8. Capa densa (Dense):
La capa densa final tiene 10 neuronas, una para cada clase en el problema de clasificación.
Utiliza la función de activación softmax, que calcula la probabilidad de que cada entrada pertenezca a cada una de las clases.
En resumen, las capas convolucionales extraen características importantes de las imágenes de entrada, las capas de agrupación reducen la dimensionalidad de la salida, y la capa densa final realiza la clasificación. El dropout ayuda a evitar el sobreajuste y la activación softmax proporciona probabilidades de pertenencia a cada clase.


# Resultados:
El modelo fue entrenado durante 25 épocas, mostrando una mejora constante en la precisión y una disminución en la pérdida tanto en el conjunto de entrenamiento como en el de validación. Se detallará a continuación:

Inicio del Entrenamiento: En la primera época, el modelo alcanzó una precisión de entrenamiento del 75.75% y una precisión de validación del 83.92%.
Final del Entrenamiento: Al final de las 25 épocas, el modelo alcanzó una precisión de entrenamiento del 92.03% y una precisión de validación del 91.73%.

# Evaluación del Modelo:
Después de completar el entrenamiento, el modelo fue evaluado en el conjunto de prueba, obteniendo los siguientes resultados:

Pérdida de Prueba: 0.2557
Precisión de Prueba: 90.73%

# Métricas Detalladas en el Conjunto de Prueba:

Precisión por Clase: [88.18%, 99.69%, 87.63%, 91.13%, 82.73%, 98.89%, 69.94%, 95.70%, 97.60%, 97.28%]
Recuperación por Clase: [81.3%, 98.0%, 84.3%, 91.4%, 89.1%, 97.7%, 73.3%, 97.9%, 97.8%, 96.5%]

Estos valores reflejan cómo el modelo se desempeña en la clasificación de cada clase específica dentro del conjunto de prueba.
