# Taller #4
Se presentan los resultados del Taller #4 del curso de Introducción a la Ciencia de Datos.

Los integrantes del grupo son:

#### [![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/daniel-felipe-d%C3%ADaz-caballero-8735ab234/) Daniel Felipe Díaz Caballero

#### [![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/daniel-fabi%C3%A1n-hern%C3%A1ndez-g%C3%B3mez-05a43b221/) Daniel Hernandez Gómez

#### [![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/daniel-vargas-castillo/) Daniel Felipe Vargas Castillo

#### [![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/dflopez/) Daniel Felipe López Rubiano

## Pregunta a Responder
**Es posible clasificar residuos a partir de imagenes mediante la implementación de redes neuronales convolucionales?**

## Motivación

Uno de los más grandes problemas de la sociedad moderna es la acumulación de residuos. Los materiales reciclables no se reciclan correctamente, o nunca llegan a una planta de reciclaje, sino que termina acumulandose en basureros. Si se analiza de cerca, el problema radica fundamentalmente en que las personas no tienen una consciencia de cuidado por el medio ambiente, más precisamente, en la clasificación de los residuos que producen. En la actualidad no es extraño encontrarse una basura clasificada en 3: orgánicos, inorgánicos y reciclables. Sin embargo, a veces es difícil para una persona identificar en dónde debería arrojar su basura, por lo que lo hace en cualquiera de las 3 y sigue con su día. Es así que surge la idea de la clasificación automática de residuos. La persona no debería preocuparse por el lugar correcto en el que debe arrojar su basura, sino que un algorítmo lo clasificaría por él, contribuyendo así a reducir la cantidad de basura que termina en el lugar equivocado.

## Datos Utilizados

Los datos utilizados fueron obtenidos a partir de Kaggle. Se utilizaron 5 datasets diferentes, de dónde se obtuvieron imagenes a clasificar en las siguientes categorías: cartón, vidrio, metal, papel, plastico y orgánico. Estos datasets están disponibles en los siguientes enlaces:

[Dataset 1](https://www.kaggle.com/datasets/roy2004/unsortedwaste): "Unsorted Waste"<br>
[Dataset 2](https://www.kaggle.com/datasets/techsash/waste-classification-data): "Waste Classification Data"<br>
[Dataset 3](https://www.kaggle.com/datasets/hseyinsaidkoca/recyclable-solid-waste-dataset-on-5-background-co): "Recyclable Solid Waste Dataset"<br>
[Dataset 4](https://www.kaggle.com/datasets/ionutandreivaduva/garbage-classification): "Garbage Classification"<br>
[Dataset 5](https://www.kaggle.com/datasets/sanjadrag24/recyclable-waste-images): "Recyclable Waste Images"<br>

A partir de esto, se obtuvo un total de 6059 imagenes, clasificadas de la siguiente manera:

```python
Carboard: 764
Glass: 991
Metal: 1031
Paper: 594
Plastic: 1278
Organic: 1401
```

## Procedimiento

Inicialmente, utilizando la librería TensorFlow, se cargaron los datos y se separaron en dos grupos: entrenamiento y validación. Del total de datos, se utilizaron 5454 para entrenamiento y 605 para validación. Asimismo, se cambió el tamaño de cada imagen a 256x256 previamente a realizar el modelo. Ya teniendo esto, se realizó una red neuronal convolucional, definiendo una función ReLU para la activación y una CrossEntropy como función de costo. Igualmente, se definió un *learning rate* de 0.00125 y un número de épocas de 50.

Así, se obtuvo la siguiente gráfica para el *loss* vs el número de épocas:

<p align="center">
  <img src="https://github.com/dfdiazc/IntroCienciaDatos4/blob/main/results/loss.png?raw=true">
</p>

Y la siguiente para la *precisión* vs el número de épocas:

<p align="center">
  <img src="https://github.com/dfdiazc/IntroCienciaDatos4/blob/main/results/accuracy.png?raw=true">
</p>

Asimismo, se graficó el *loss* vs el *learning rate*:

<p align="center">
  <img src="https://github.com/dfdiazc/IntroCienciaDatos4/blob/main/results/loss_vs_learning_rate.png?raw=true">
</p>

En esta última imagen se puede apreciar como, a partir de aproximadamente un valor de 0.0015 para el *learning rate*, se minimiza la función de costo, esto es, no tiene mayor efecto utilizar una tasa de aprendizaje más álta.

Igualmente, se obtiene la siguiente matríz de confusión:

<p align="center">
  <img src="https://github.com/dfdiazc/IntroCienciaDatos4/blob/main/results/confusion_matrix.png?raw=true">
</p>

Ya teniendo el modelo, se guarda en un archivo .h5 pudiendo así realizar predicciones con imagenes que éste no haya visto antes. Por ejemplo, se pueden clasificar imagenes de la siguiente manera:

<p align="center">
  <img src="https://github.com/dfdiazc/IntroCienciaDatos4/blob/main/results/prediction.jpg?raw=true">
</p>

Se observa que el modelo da una probabilidad de que la imagen pertenezca a una clase dada. Para propósitos prácticos, se asume que la clase con mayor probabilidad es la clase a la que pertenece el objeto.

## Resultados

Se concluye que es posible, mediante la utilización de redes neuronales convolucionales, identificar y clasificar residuos con una buena precisión. Utilizando este modelo, junto a demás herramientas tecnológicas, es posible implementar procesos de automatización de clasificación de residuos.

El modelo obtenido es bastante bueno, como se observa en la matríz de confusión, sin embargo, nada es perfecto. Por este motivo, para mejorar aún más el modelo, es pertinente ampliar el dataset con imagenes variadas, motivando así al algorítmo a aprender a diferenciar una categoría de otra de una mejor manera.
