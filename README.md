# Image_Classification

## Table of contents
- README.md --> Project motivation | Goals | Methodology | Results | Conclussions | Limitations | Future Work | Contributions | Tools
- Report_AML_XReverte --> The project itself
- Notebook_XReverte_AML.ipynb --> Sample code used for the project

## Motivation
In an **increasingly visual and digitalized world**, images have become a powerful form of communication and expression. The development of Deep Learning techniques for image classification acquires particular relevance as it allows us to unravel the secrets and visual richness contained in large datasets.

The use of **transfer learning** techniques allows us to capitalize on the previous knowledge of pretrained models and adapt them to our specific dataset through fine-tuning, providing an effective solution with limited resources.

The choice of Google Colab as a development framework gives us access to **scalable computational resources**, allowing us to tackle Deep Learning projects without the need for expensive infrastructure. On the other hand, the fastai library offers an intuitive and powerful interface for implementing **Deep Learning** models, significantly facilitating the development and experimentation process.

Through this project, we aim to **explore different pretrained models** such as VGG19, Resnet34, DenseNet121, and EfficientNet_b0, with the goal of comparing their performance and determining the most suitable for our image classification task. Additionally, we plan to implement an ensemble approach** that combines the predictions of multiple models to improve the accuracy and robustness of the final system.

Despite resource limitations, such as GPU usage restrictions in Google Colab, we are committed to overcoming technical challenges and **maximizing the performance** of our models. Through this project, we hope to contribute to the advancement of the computer vision field and provide practical and efficient solutions for image classification in various contexts and applications.

![cifarML](https://github.com/XReverte/Image_Classification/assets/100844285/ed3a7de5-8ebf-4f35-ab2b-681b56e7e72b)
*Image generated by Microsoft Bing (2023). graphic_art [1.0]*

## Goals
The main objective of the image classification project using Deep Learning techniques is to develop systems capable of automatically identifying and categorizing images with precision and efficiency. We focus on the **CIFAR-10 dataset**, which contains 60,000 color images of size 32x32, distributed across 10 classes such as airplane, automobile, bird, cat, deer, dog, frog, horse, ship, and truck. This dataset represents an interesting challenge due to its diversity and complexity.

The data is divided into three sets: **40,000 images for training**, **10,000 for validation**, and **10,000 for unlabeled testing**, balanced in terms of the number of images per class. To evaluate the performance of our models, we will use metrics obtained by comparing the training set with the validation set. Once the best model is selected, we will evaluate its performance on the unlabeled testing set.

Given the complexity of the task, we choose to leverage pretrained models. While designing a model from scratch could offer a more tailored architecture for the specific case study, this option does not compensate for the lack of training data, following the principle of "**The Unreasonable Effectiveness of Data**" *by Peter Norvig*, which emphasizes the importance of data over algorithms in complex problems.

![cifar-10](https://github.com/XReverte/Image_Classification/assets/100844285/d16bd3a4-f40a-45c1-843e-885282117ddd)
*CIFAR-10 datset example*

## Methodology
For data preparation, we utilized the "fastai" library, employing the "**DataBlock**" to define the necessary steps. This includes specifying the types of input data and prediction targets, as well as applying transformations and splitting the data into training and validation sets.

The "**DataLoader**" was used to load the data in batches and apply transformations during model training and validation. Taking the "DataBlock" as input, we defined the batch size and applied the specified transformations for data augmentation. We aimed for a balance between data accuracy and regularization to prevent overfitting through the appropriate combination of transformations in the dataloader and datablock.

Once this balance was achieved, we selected a pretrained model and explored different **combinations of hyperparameters** to find the most suitable one. Hyperparameters such as learning rate, freeze epochs, weight decay, dropout, and batch size were considered.

The choice of learning rate was based on initial recommendations and graphs obtained with "learn.lr_find()", which was further adjusted manually. As for the batch size, it was determined based on available RAM memory. We limited the number of epochs to 3 due to time constraints on GPU usage.

After finding the best parameter combination for the selected model, we **combined the training and validation** sets into a single folder to train with a larger amount of data and obtain better predictions on the unlabeled test set.

Finally, we performed an **ensemble** of the results from nine pretrained models, combining predictions according to each model's performance and weighting them based on their accuracy. Our selection criterion included at least one model from each of the four available pretrained architectures, as well as all those whose accuracy exceeded the threshold of 0.95. This approach resulted in the selection of one VGG19 model, two ResNet34 models, three DenseNet models, and three EfficientNet models to form part of the final ensemble.

## Results and conclusions
After applying the described methodology, we have achieved **promising results** in the task of image classification using Deep Learning techniques. When evaluating the performance of our models on the test set, we observed notably high accuracy, demonstrating the effectiveness of our approach in the automatic identification and categorization of images.

Furthermore, by performing an ensemble of the results from various pretrained models, we were able to further improve the **precision and robustness** of the final system. This strategy allowed us to combine the strengths of each individual model and mitigate potential weaknesses, resulting in a more solid and reliable overall outcome.

This project has demonstrated the viability and e**ffectiveness of utilizing Deep Learning techniques** for image classification, providing practical and efficient solutions for a variety of applications in the field of computer vision. The results obtained could represent a significant step towards the development of intelligent systems capable of understanding and processing visual information in a manner similar to humans.

The conclusion of the project was reflected in an **outstanding accuracy rate of 94.72%** in image classification, earning me a grade of 9.45/10, highlighting my proficiency in applying cutting-edge Deep Learning methodologies to tackle practical challenges in image recognition.

![captura_epochs1](https://github.com/XReverte/Image_Classification/assets/100844285/f237eb48-970d-490b-a66e-a56d75a7f6a8)

*Training results before Progressive Resizing (EfficientNet). bach_size=64 | dropout=0.005 | epochs=10 | learning_rate=0.005 | weight_decay= 0.0 | freeze_epochs=3*


![Captura_epochs2](https://github.com/XReverte/Image_Classification/assets/100844285/a9243c83-d081-4744-b2d2-6ccf27f1e9a3)

*Training Rresults after Progressive Resizing (EfficientNet). bach_size=256 | image_size=256 | dropout=0.005 | epochs=20 | learning_rate=0.01 | weight_decay= 0.0 | freeze_epochs=1 | cbs=callbacks*


![Captura_ConfMatrix](https://github.com/XReverte/Image_Classification/assets/100844285/692be5a5-dc8b-4183-af78-ba1238bdfebf)

*Confusion Matrix (EfficientNet)*


![Captura_loss](https://github.com/XReverte/Image_Classification/assets/100844285/0a232803-77c0-4b39-afe6-a542d14f4da4)

*Maximum Error Images (EfficientNet)*

## Limitations
Despite achieving promising results, it is important to acknowledge that our approach also presents areas for improvement and potential limitations. For example, we could explore **additional regularization techniques** to further reduce the risk of overfitting and enhance the model's ability to generalize to unseen data.

The CIFAR-10 dataset, while widely used and diverse, contains **low-resolution images** (32x32), which may limit the generalization ability of our models to situations with higher quality or resolution images.

Due to **computational resource** constraints such as processing time and available memory, we were unable to explore all possible combinations of models and hyperparameters, which could have affected the final performance of our system.

Although we carefully selected pretrained models for our ensemble, some models may have been more suitable than others for the task of image classification on the CIFAR-10 dataset. A **more exhaustive exploration** of different pretrained model architectures could have further improved our results.

Additionally, the interpretation of results may be limited by the inherent complexity of Deep Learning models and the **lack of transparency** in their internal decision-making processes, making it challenging to understand how and why the model arrives at certain conclusions.

## Contributions
Our work has provided practical and efficient solutions for **automatic image classification**, which may have potential applications in a variety of fields.

By ensemble of multiple pretrained models, we have **improved the accuracy and robustness** of the final system, demonstrating the utility of this strategy for enhancing the performance of image classification models.

Furthermore, we have **shared the code** and resources used in this project, enabling other researchers and professionals to reproduce our results and build upon our work. This transparency and accessibility foster collaboration and the advancement of knowledge in the field of image classification using Deep Learning techniques.

## Tools
- Technologies: Python | Google Colab | *CIFAR-10 dataset
- Libraries: numpy | pandas | matplotlib | sklearn | fastai | Google Colab | random | os | torchvision
- Machine Learning Models: VGG19 | ResNet34 | DenseNet121 | EfficientNet_b0
