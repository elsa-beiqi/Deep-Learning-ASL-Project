## Project Overview
This project focuses on classifying American Sign Language (ASL) images into 29 classes (A-Z, SPACE, DELETE, NOTHING) using Convolutional Neural Networks (CNNs) and Transfer Learning approaches (VGG16, ResNet50, InceptionV3). The dataset consists of 200x200 images representing each class, which were preprocessed by resizing to 100x100 pixels, scaling pixel values between 0 and 1, and one-hot encoding the labels.

### CNN
An initial CNN architecture with 4 convolutional layers was tested, each paired with a pooling layer. Filters increased from 16 to 128, using a kernel size of 7x7 and a pooling size of 2x2. After flattening, 3 dense layers were added, with neurons set to 128, 64, and 29 (the number of classes). The model used ReLU activations, softmax for the output, and was trained with a batch size of 256 over 100 epochs, reaching a validation accuracy of 96.66%.
To improve performance, the CNN model was restructured with 6 convolutional and pooling layers, starting with 8 filters and doubling them up to 256. Batch size was reduced to 128, and further tuning of the learning rate led to a peak validation accuracy of 99.87%. Additional experiments with increased batch size (256) and a decreased learning rate (0.00001) yielded similar results, confirming the architecture’s effectiveness.

### Transfer Learning
Three transfer learning models—ResNet50, InceptionV3, and VGG16—were fine-tuned for ASL classification:
1. ResNet50: The initial model made the last 5 layers trainable and added dense layers with 1024, 512, 256, and 29 neurons. With a batch size of 128, this model achieved 94.57% validation accuracy after tuning.
2. InceptionV3: Two models were tested, one with all layers frozen and the other with the last 5 layers trainable. Both models used ReLU activations, 128 batch size, and were trained for up to 100 epochs. The frozen model achieved 97.98% validation accuracy, while the partially trainable model reached 96.1%.
3. VGG16: This model was optimized by varying the number of frozen layers and dense layers. The best results came from freezing all layers, adding 5 dense layers with neurons set to 1024, 512, 256, 128, and 29. Validation accuracy peaked at 99.47% with a batch size of 256 and learning rate of 0.0001. Further tuning led to an optimized model with 99.95% validation accuracy and 99.93% test accuracy on Kaggle, using all training data and the best checkpointed weights.

### Conclusion
The final VGG16 model with fully frozen layers and added dense layers achieved the highest performance, with 99.95% validation accuracy and strong leaderboard results on Kaggle. The CNN model also performed competitively, demonstrating that both custom architectures and transfer learning approaches can be highly effective for ASL classification tasks.
