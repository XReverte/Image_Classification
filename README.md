# Image_Classification

## Table of contents
- README.md --> Project motivation | Goals | Methodology | Results | Conclussions | Limitations | Future Work | Contributions | Tools
- Report_AML_XReverte --> The project itself
- Notebook_XReverte_AML.ipynb --> Sample code used for the project

## Motivation
En un mundo cada vez más visual y digitalizado, las imágenes se han convertido en un poderosa forma de comunicación y expresión. El desarrollo de técnicas de Deep Learning para la clasificación de imágenes adquiere una relevancia particular, ya que nos permite desentrañar los secretos y la riqueza visual contenida en grandes conjuntos de datos.

El uso de técnicas de transfer learning nos permite capitalizar el conocimiento previo de modelos preentrenados y adaptarlos a nuestro conjunto de datos específico a través de fine-tuning, lo que nos brinda una solución eficaz con recursos limitados.

La elección de Google Colab como framework de desarrollo nos proporciona acceso a recursos computacionales escalables, lo que nos permite abordar proyectos de Deep Learning sin la necesidad de una infraestructura costosa. La biblioteca fastai, por otro lado, ofrece una interfaz intuitiva y potente para la implementación de modelos de Deep Learning, facilitando considerablemente el proceso de desarrollo y experimentación.

A través de este proyecto, buscamos explorar diferentes modelos preentrenados, como VGG19, Resnet34, DenseNet121 y EfficientNet_b0, con el objetivo de comparar su rendimiento y determinar el más adecuado para nuestra tarea de clasificación de imágenes. Además, nos proponemos implementar un enfoque de ensamble que combine las predicciones de varios modelos para mejorar la precisión y robustez del sistema final.

A pesar de las limitaciones de recursos, como las restricciones de uso de la GPU en Google Colab, estamos comprometidos a superar los desafíos técnicos y maximizar el rendimiento de nuestros modelos. A través de este proyecto, esperamos contribuir al avance del campo de la visión por computadora y brindar soluciones prácticas y eficientes para la clasificación de imágenes en diversos contextos y aplicaciones.

## Goals
El objetivo principal del proyecto de clasificación de imágenes mediante técnicas de Deep Learning es desarrollar sistemas capaces de identificar y categorizar automáticamente imágenes con precisión y eficiencia. Nos centramos en el dataset CIFAR-10, que contiene 60,000 imágenes en color de tamaño 32x32, distribuidas en 10 clases, como avión, automóvil, pájaro, gato, ciervo, perro, rana, caballo, barco y camión, lo que representa un desafío interesante debido a su diversidad y complejidad.

Los datos se dividen en tres conjuntos: 40,000 imágenes para entrenamiento, 10,000 para validación y 10,000 para pruebas sin etiquetar, equilibrados en cuanto al número de imágenes por clase. Para evaluar el rendimiento de nuestros modelos, utilizaremos métricas obtenidas mediante la comparación del conjunto de entrenamiento con el conjunto de validación. Una vez seleccionado el mejor modelo, evaluaremos su rendimiento en el conjunto de pruebas sin etiquetar.

Dada la complejidad de la tarea, se optará por aprovechar modelos previamente entrenados. Si bien diseñar un modelo desde cero podría ofrecer una arquitectura más adecuada para el caso de estudio específico, esta opción no compensa la falta de datos de entrenamiento, siguiendo el principio de "The Unreasonable Effectiveness of Data" de Peter Norvig, que enfatiza la importancia de los datos sobre los algoritmos en problemas complejos.

## Methodology
Para la preparación de los datos, utilizamos la biblioteca "fastai", empleando el "DataBlock" para definir los pasos necesarios. Esto incluye la especificación de los tipos de datos de entrada y los objetivos de predicción, así como la aplicación de transformaciones y la división de datos en los conjuntos de entrenamiento y validación.

El "DataLoader" se utiliza para cargar los datos en batches y aplicar transformaciones durante el entrenamiento y validación del modelo. Se recibe el "DataBlock" como entrada, se define el tamaño del batch y se aplican las transformaciones indicadas para data augmentation. Se busca un equilibrio entre la precisión y la regularización de los datos para evitar el overfitting mediante la combinación adecuada de transformaciones en el dataloader y el datablock.

Una vez encontrado este equilibrio, seleccionamos un modelo preentrenado y exploramos diferentes combinaciones de hiperparámetros para encontrar la más adecuada. Consideramos parámetros como el learning rate, freeze epochs, weight decay, dropout y batch size.

La elección del learning rate se basa en recomendaciones iniciales y gráficos obtenidos con "learn.lr_find()", ajustándolo posteriormente de forma manual. En cuanto al batch size, se determina en función de la memoria RAM disponible. Limitamos el número de epochs a 3 debido a restricciones temporales de uso de la GPU.

Una vez encontrada la mejor combinación de parámetros para el modelo seleccionado, combinamos los conjuntos de entrenamiento y validación en una sola carpeta para poder entrenar con una mayor cantidad de datos y obtener mejores predicciones en el conjunto de prueba no etiquetado.

Finalmente, llevamos a cabo un ensamble de los resultados de nueve modelos preentrenados, combinando las predicciones de acuerdo con el rendimiento de cada modelo y ponderándolas según su precisión. Nuestro criterio de selección se basó en incluir al menos un modelo de cada una de las cuatro arquitecturas preentrenadas disponibles, así como todos aquellos cuya precisión superara el umbral del 0.95. Este enfoque resultó en la selección de un modelo VGG19, dos modelos ResNet34, tres modelos DenseNet y tres modelos EfficientNet para formar parte del ensamble final.

## Results and conclusions
Tras aplicar la metodología descrita, hemos obtenido resultados prometedores en la tarea de clasificación de imágenes utilizando técnicas de Deep Learning. Al evaluar el rendimiento de nuestros modelos en el conjunto de pruebas, hemos observado una precisión notablemente alta, lo que demuestra la efectividad de nuestra aproximación en la identificación y categorización automática de imágenes.

Además, al realizar un ensamble de los resultados de varios modelos preentrenados, pudimos mejorar aún más la precisión y robustez del sistema final. Esta estrategia nos permitió combinar las fortalezas de cada modelo individual y mitigar posibles debilidades, obteniendo así un resultado general más sólido y confiable.

En conclusión, este proyecto ha demostrado la viabilidad y efectividad de utilizar técnicas de Deep Learning para la clasificación de imágenes, ofreciendo soluciones prácticas y eficientes para una variedad de aplicaciones en el ámbito de la visión por computadora. Los resultados obtenidos representan un paso significativo hacia el desarrollo de sistemas inteligentes capaces de comprender y procesar información visual de manera similar a los seres humanos.

En conclusión, este proyecto ha demostrado la viabilidad y efectividad de utilizar técnicas de Deep Learning para la clasificación de imágenes, ofreciendo soluciones prácticas y eficientes para una variedad de aplicaciones en el ámbito de la visión por computadora. La conclusión del proyecto se vio reflejada en una destacada tasa de precisión del 94.72% en la clasificación de imágenes, lo que me valió una calificación de 9.45/10, resaltando mi competencia en la aplicación de metodologías de vanguardia en Deep Learning para enfrentar desafíos prácticos en el reconocimiento de imágenes.

## Limitations
A pesar de lograr resultados prometedores, es importante reconocer que nuestro enfoque también presenta áreas de mejora y posibles limitaciones. Por ejemplo, podríamos explorar técnicas adicionales de regularización para reducir aún más el riesgo de sobreajuste y mejorar la capacidad de generalización del modelo a datos no vistos.

El dataset CIFAR-10, aunque ampliamente utilizado y diverso, contiene imágenes de baja resolución (32x32), lo que podría limitar la capacidad de generalización de nuestros modelos a situaciones con imágenes de mayor calidad o resolución.

Debido a las restricciones de recursos computacionales, como el tiempo de procesamiento y la memoria disponible, no pudimos explorar todas las posibles combinaciones de modelos y hiperparámetros, lo que podría haber afectado el rendimiento final de nuestro sistema.

Aunque seleccionamos cuidadosamente los modelos preentrenados para nuestro ensamble, es posible que algunos modelos hayan sido más adecuados que otros para la tarea de clasificación de imágenes en el dataset CIFAR-10. Una exploración más exhaustiva de diferentes arquitecturas de modelos preentrenados podría haber mejorado aún más nuestros resultados.

Además, la interpretación de los resultados podría verse limitada por la complejidad inherente de los modelos de Deep Learning y la falta de transparencia en sus decisiones internas, lo que podría dificultar la comprensión de cómo y por qué el modelo llega a ciertas conclusiones.

## Contributions
Nuestro trabajo ha proporcionado soluciones prácticas y eficientes para la clasificación automática de imágenes, lo que puede tener aplicaciones potenciales en una variedad de campos.

Mediante el ensamble de varios modelos preentrenados, hemos mejorado la precisión y la robustez del sistema final, lo que demuestra la utilidad de esta estrategia para mejorar el rendimiento de los modelos de clasificación de imágenes.

Además, hemos compartido el código y los recursos utilizados en este proyecto, lo que permite a otros investigadores y profesionales reproducir nuestros resultados y construir sobre nuestro trabajo. Esta transparencia y accesibilidad fomenta la colaboración y el avance del conocimiento en el campo de la clasificación de imágenes mediante técnicas de Deep Learning.

## Tools
- Technologies: Python | Google Colab | *CIFAR-10 dataset
- Libraries: numpy | pandas | matplotlib | sklearn | fastai | Google Colab | random | os | torchvision
- Machine Learning Models: VGG19 | ResNet34 | DenseNet121 | EfficientNet_b0
