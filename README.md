# DenseASPP Semantic Segmentation Project

This repository contains the implementation developed for a **Computer Vision project during the third semester of the Master's in Data Science at the University of Padova**.

The project was developed as a **group assignment**, focusing on understanding and improving a semantic segmentation architecture based on **Dense Atrous Spatial Pyramid Pooling (DenseASPP)**.

## Project Overview

Semantic segmentation is a computer vision task where a class label is assigned to **every pixel in an image**. It is widely used in applications such as autonomous driving, medical imaging, and scene understanding.

In this project, we reproduced and experimented with the **DenseASPP architecture**, which uses **atrous (dilated) convolutions** to capture multi-scale contextual information while preserving spatial resolution. 

The main goal was to understand how architectural modifications affect segmentation performance and computational efficiency.

## Dataset

The experiments were conducted using the **Cityscapes dataset**, a benchmark dataset for urban scene understanding. 

The dataset contains high-resolution street images with pixel-level annotations.
For this project:

* Total images used: **3,475**
* Training set: **2,380**
* Validation set: **595**
* Test set: **500**

Images were resized using random crops and augmented with techniques such as flipping and color adjustments.

## Implemented Architectures

Three different architectures were implemented and compared:

### 1. Vanilla DenseASPP

Baseline model composed of:

* DenseNet121 backbone (pretrained)
* DenseASPP block with atrous convolutions
* Final classification head

### 2. DenseASPP + CBAM

The baseline architecture was extended with a **Convolutional Block Attention Module (CBAM)** to refine feature maps using channel and spatial attention.

### 3. DenseASPP + CBAM + Encoder–Decoder

The most complex version adds an **encoder–decoder structure** with skip connections to combine:

* low-level spatial features
* high-level semantic features

This aims to improve boundary precision in segmentation results.

## Training Setup

Main training details:

* Loss: **Sparse Categorical Cross Entropy**
* Optimizer: **Adam**
* Evaluation metric: **Mean Intersection over Union (mIoU)**
* Learning rate schedule: **Polynomial decay**
* Data augmentation: brightness, contrast, saturation, horizontal flips

## Results

The experiments compared the three architectures using **mIoU** as the evaluation metric.

Key observations:

* The **baseline DenseASPP** performed consistently well.
* Adding **CBAM alone did not improve performance**.
* The **encoder–decoder variant showed small improvements**, especially when backbone layers were partially unfrozen.

These experiments helped highlight the trade-off between **model complexity, training stability, and segmentation performance**.

## Authors

This project was developed as a **group assignment** by:

* Marina Lima Braga
* Diana Cristina Andrade Damian
* Diego Alonso Brule Galleguillos

Master's in Data Science
**University of Padova**

