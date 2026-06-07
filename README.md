# Leaf Classification using ResNet-34

## Overview

This project implements an end-to-end leaf species classification system using deep learning and transfer learning techniques.

The project is based on the Kaggle **Classify Leaves** competition and follows the deep learning workflow introduced in *Dive into Deep Learning (D2L)* by Li Mu.

The goal is to automatically classify leaf images into one of **176 tree species** using a convolutional neural network.

---

## Competition Information

**Competition Link**

https://www.kaggle.com/c/classify-leaves

### Competition Result

| Metric        | Score   |
| ------------- | ------- |
| Public Score  | 0.92590 |
| Private Score | 0.93045 |

The final model achieved over **93% classification accuracy** on the private leaderboard.

---

## Dataset

The dataset contains leaf images collected from various tree species.

### Dataset Statistics

* Training Images: 18,353
* Test Images: 8,800
* Categories: 176 tree species

Each sample consists of:

* Leaf image
* Species label

---

## Project Pipeline

### 1. Data Preparation

The original dataset is loaded from Kaggle and processed using Pandas.

A label encoding system is created to convert species names into numerical labels for neural network training.

Example:

```text
acer_rubrum → 10
ginkgo_biloba → 66
quercus_alba → 136
```

Both forward and reverse mappings are maintained for prediction decoding.

---

### 2. Custom Dataset Construction

A custom PyTorch Dataset class was implemented to:

* Load image paths dynamically
* Read labels from CSV files
* Support train / validation / test modes
* Automatically perform image transformations

This design improves code modularity and scalability.

---

### 3. Data Augmentation

To improve model generalization, several preprocessing techniques are applied:

* Resize (224 × 224)
* Random Horizontal Flip
* Tensor Conversion

Data augmentation helps reduce overfitting and improves robustness to image variations.

---

### 4. Model Architecture

The project adopts a transfer learning strategy using **ResNet-34**.

Advantages of ResNet include:

* Deep feature extraction capability
* Residual connections for stable training
* Strong performance on image classification tasks

The final fully connected layer is modified to output probabilities for 176 species.

---

### 5. Model Training

Training configuration:

| Parameter     | Value            |
| ------------- | ---------------- |
| Framework     | PyTorch          |
| Backbone      | ResNet-34        |
| Batch Size    | 32               |
| Image Size    | 224 × 224        |
| Loss Function | CrossEntropyLoss |
| Optimizer     | Adam             |

The dataset is automatically split into:

* Training Set (80%)
* Validation Set (20%)

---

### 6. Prediction and Submission

After training, the model predicts labels for all test images.

The predicted class indices are converted back to species names and exported as:

```text
submission.csv
```

The submission file is then uploaded to Kaggle for evaluation.

---

## Technologies Used

* Python
* PyTorch
* TorchVision
* Pandas
* NumPy
* Matplotlib
* PIL

---

## Project Highlights

* Built a complete image classification pipeline using PyTorch.
* Implemented a custom Dataset and DataLoader.
* Applied transfer learning with ResNet-34.
* Utilized data augmentation to improve generalization.
* Achieved a Private Score of **0.93045** on Kaggle.
* Gained hands-on experience with computer vision model development and evaluation.

---

## Learning Outcomes

Through this project, I developed practical experience in:

* Computer Vision
* Convolutional Neural Networks (CNNs)
* Transfer Learning
* Data Augmentation
* PyTorch Model Development
* Kaggle Competition Workflow
* Deep Learning Model Training and Evaluation

---

## References

[1] Li Mu et al.

Dive into Deep Learning (D2L)

https://d2l.ai/

[2] PyTorch Documentation

https://pytorch.org/

[3] Kaggle Classify Leaves Competition

https://www.kaggle.com/c/classify-leaves
