# CIFAR-10 Image Classification with Deep Learning

This project was developed for the Deep Learning course at the University of Milano-Bicocca.

The objective was to build and compare multiple convolutional neural network architectures for CIFAR-10 image classification, progressively moving from a shallow CNN baseline to deeper and residual architectures, and finally to transfer learning.

The project was implemented in Python using TensorFlow and Keras.

---

## Project Overview

CIFAR-10 is a standard computer vision benchmark composed of 60,000 RGB images of size 32×32, equally distributed across 10 classes.

The project investigates five main questions:

1. Can a custom CNN classify CIFAR-10 effectively?
2. Does targeted hyperparameter tuning improve model performance?
3. Does data augmentation reduce overfitting?
4. Which classes are most often confused?
5. Does transfer learning outperform custom CNN architectures?

A total of 15 model configurations were trained and compared using the same train, validation and test split.

---

## Dataset

The CIFAR-10 dataset contains:

- 60,000 RGB images;
- 10 balanced classes;
- 32×32 pixels per image;
- 45,000 training images;
- 5,000 validation images;
- 10,000 test images.

The original dataset is not included in this repository.

Preprocessing and Data Augmentation
Pixel values are rescaled and normalized inside the model pipeline so that the same preprocessing is applied during both training and inference.
Two augmentation regimes were explored.
Standard augmentation
- random horizontal flip
- small translation
- small contrast variation
Stronger augmentation
- random horizontal flip
- wider translation
- random zoom
- stronger contrast variation
Standard augmentation substantially improved the shallow CNN and reduced overfitting, while stronger augmentation often reduced accuracy because CIFAR-10 images are only 32×32 pixels.
Models
Four architecture families were explored.
1. Shallow CNN
A simple baseline architecture with two convolutional blocks and a dense classification head.
- Baseline test accuracy: 72.8%
- With standard augmentation: 79.7%
2. Deep CNN
A deeper custom CNN with eight convolutional layers, Batch Normalization, Global Average Pooling and Dropout.
Several configurations were tested, including:
- different learning rates
- gradient clipping
- L2 regularization
- alternative dense heads
Best Deep CNN test accuracy: 91.2%
3. Residual CNN
A custom residual architecture using skip connections to improve gradient flow and optimization.
Different learning-rate, clipping and augmentation configurations were evaluated.
Best Residual CNN test accuracy: 91.6%
This was the best-performing model in the project.
4. Transfer Learning
ImageNet-pretrained architectures were also evaluated:
- MobileNetV2
- ResNet50
Experiments included frozen backbones, stronger augmentation and fine-tuning.
Best transfer-learning result:
- MobileNetV2 + augmentation + fine-tuning: 90.0%
The best custom Residual CNN therefore slightly outperformed the transfer-learning approaches.
Results
Model	Test Accuracy
Shallow CNN	72.8%
Shallow CNN + Augmentation	79.7%
Best Deep CNN	91.2%
Best Residual CNN	91.6%
Best Transfer Learning	90.0%


The Residual CNN achieved the strongest overall performance with:
- 91.6% test accuracy
- 0.420 test loss
- approximately 2.78M parameters
Error Analysis
The best model was also evaluated through per-class metrics and a confusion matrix.
The most frequent errors occurred between visually similar classes, especially:
- cat ↔ dog
- deer ↔ horse
- automobile ↔ truck
- airplane ↔ ship
Many misclassified examples were also characterized by low resolution, occlusion, unusual poses or poor contrast.
Main Findings
The experiments showed that:
- even a simple CNN can learn useful representations on CIFAR-10
- standard data augmentation strongly reduces overfitting
- deeper architectures provide a major improvement over the shallow baseline
- targeted hyperparameter changes improve stability, but do not always improve accuracy
- overly aggressive augmentation can remove useful visual details from very small images
- residual connections produced the best overall custom architecture
- transfer learning was competitive, but did not outperform the best custom Residual CNN
Technologies
- Python
- TensorFlow
- Keras
- NumPy
- Matplotlib
- scikit-learn
- MobileNetV2
- ResNet50
Repository Structure
cifar10-image-classification/
├── notebooks/
│   └── cifar10_classification.ipynb
│
├── docs/
│   └── CIFAR10_Presentation_final.pdf
│
├── .gitignore
└── README.md

Presentation
The complete project presentation, including architecture comparisons, training curves, confusion matrices and qualitative error analysis, is available here:
[Read the project presentation](docs/CIFAR10_Presentation_final.pdf)
Team
Lorenzo Gulizia
Filippo Avon
University of Milano-Bicocca
Academic Year 2024/2025

Questo GitHub lo legge correttamente come Markdown.

The notebook expects the extracted CIFAR-10 Python batches in:

```text
data/cifar-10-batches-py/
