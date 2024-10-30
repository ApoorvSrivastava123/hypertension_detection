# Hypertension Detection Using Time-Series Image Modalities and Convolutional Neural Networks

This project presents a novel approach for detecting hypertension using time-series transformations of ballistocardiogram (BCG) signals and deep learning models. The proposed method uses convolutional neural networks (CNNs), specifically a custom model called **Hpt-Net**, to classify hypertension with high accuracy.

## Table of Contents
- [Overview](#overview)
- [Methodology](#methodology)
- [Data Source](#data-source)
- [Model Architecture](#model-architecture)
- [Results](#results)
- [Usage](#usage)
- [Future Work](#future-work)
- [Contributing](#contributing)
- [License](#license)

## Overview
Hypertension, commonly known as high blood pressure, is a major health concern worldwide. Traditional blood pressure monitoring techniques are often labor-intensive and inconvenient for long-term use. This project leverages BCG signals—a non-invasive measure of cardiac activity—to detect hypertension automatically. The custom model, Hpt-Net, demonstrates enhanced accuracy by transforming BCG signals into time-series images.

## Methodology
The process of detecting hypertension in this project involves several steps:
1. **Data Acquisition**: BCG data is collected and segmented.
2. **Image Transformation**: The BCG signals are converted into images using three time-series transformation techniques:
   - **Gramian Angular Field (GAF)**
   - **Recurrence Plot (RP)**
   - **Markov Transition Field (MTF)**
3. **Composed Image Creation**: The three images are combined to form a "composed image" representing different aspects of the BCG data.
4. **Classification**: The composed images are processed through Hpt-Net, a custom CNN model, as well as other CNN models like ResNet50 and AlexNet for comparison.

## Data Source
The dataset comprises BCG signals of 67 normal individuals and 61 hypertensive individuals, sampled at 100 Hz. Each signal was divided into 30-second segments, resulting in over 132,000 BCG segments for analysis.[https://figshare.com/articles/dataset/Unobtrusive_Mattress-based_Identification_of_Hypertension_by_Integrating_Classification_and_Association_Rule_Mining/7594433]

## Model Architecture
Hpt-Net is a custom CNN architecture designed for efficient and accurate hypertension classification:
- **Input Layer**: Accepts composed BCG images.
- **Convolutional Layers**: Three convolutional layers with ReLU activation extract discriminative features.
- **Pooling Layers**: Three pooling layers reduce dimensionality.
- **Fully Connected Layers**: Integrates extracted features for final classification.
- **Output Layer**: A sigmoid layer for binary classification (hypertension or normal).

## Results
Hpt-Net achieved a classification accuracy of **98.3%** with composed images, outperforming other CNN architectures:
| Model      | Accuracy | Precision | Recall | F1 Score |
|------------|----------|-----------|--------|----------|
| ResNet50   | 87.5%    | 89%       | 85%    | 87%      |
| AlexNet    | 95.8%    | 100%      | 97%    | 98%      |
| **Hpt-Net** | **98.3%** | **100%**  | **97%** | **98%**  |
