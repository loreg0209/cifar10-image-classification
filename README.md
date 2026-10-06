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

The notebook expects the extracted CIFAR-10 Python batches in:

```text
data/cifar-10-batches-py/
