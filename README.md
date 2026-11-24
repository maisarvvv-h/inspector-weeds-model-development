# Inspector Weeds – Model Development

## Overview
This repository contains the contents used to develop a deep learning model for the Inspector Weeds Capstone Project
The objective was to develop a semantic segmentation model capable of identifying weeds in oil palm plantation images and producing outputs that could later be converted into weed coverage and severity insights within the Inspector Weeds website.

## Data Preparation 
The main annotated dataset is the dataset used to train the model. It is annotated with PNG masks for semantic segmentation. 
The dataset is annotated with three classes:
- background
- ground weeds
- palm tree
The dataset was organized into training, validation, and test sets before model development.

Different data preparation approaches were explored to improve the amount and diversity of training data, including:
- image augmentation
- expanded training datasets
- synthetic data experimentation.

The relevant notebooks and scripts can be found in the data preparation folder.

the generalization dataset is an image dataset from a different source used to test the generalizability of Inspector Weed's final model 

## Model Experiments
The project primarily experimented with DeepLabV3+ using a ResNet50 backbone for semantic segmentation.
the model experimentations was carried out in three main stages: **baseline selection, data-centric experimentation, and generalisation testing**.

### 1. Baseline Experiment

The first experiment was conducted to establish a suitable baseline configuration for the later data-centric experiments.

Different image resolutions and batch sizes were tested using the original annotated dataset with DeepLabV3+. The best-performing baseline used an image resolution of **1024 × 1024 with a batch size of 8**, achieving:

- Recall: **0.82**
- Precision: **0.89**
- IoU: **0.75**

This configuration was then used as the baseline for the subsequent experiments.

### 2. Data-Centric Experiments

The next stage focused on improving model performance through changes to the training data rather than changing the model architecture.

Two main approaches were tested:

- image augmentation; and
- synthetic data generation.

The experiments compared:

- 5× augmentation;
- 10× augmentation;
- synthetic data with 5× augmentation; and
- synthetic data with 10× augmentation.

Among these experiments, **10× augmentation of the original annotated dataset produced the best results**, achieving:

- Recall: **0.96**
- Precision: **0.97**
- IoU: **0.94**

This significantly outperformed both the baseline and the synthetic-data experiments, so the 10× augmentation pipeline was selected for further testing.

### 3. Generalisation Experiments

The next stage evaluated whether the model could perform well on plantation images outside the main training dataset.

During generalisation testing, we found that introducing **downscale augmentation** helped improve the model's ability to generalise to new images. Based on this result, additional augmentation techniques were incorporated into the training pipeline and tested further.

The updated augmentation pipeline maintained strong performance on the main dataset while also improving performance on the generalisation dataset.

The selected final model achieved:

- Recall: **0.96**
- Precision: **0.97**
- IoU: **0.93**

This model was selected as the final model because it performed strongly across both the **data-centric experiments and the generalisation experiments**, rather than only performing well on the original dataset.

The final trained model was subsequently integrated into the Inspector Weeds website for plantation image analysis.

## Final Model

The final trained model is stored in the website repository:

[Inspector Weeds Website](https://github.com/maisarvvv-h/inspector-weeds-website)
`model/best_deeplabv3plus.pt`


## Related Repository

[Inspector Weeds Website](https://github.com/maisarvvv-h/inspector-weeds-website)
