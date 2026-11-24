# DeepLabV3+ Model Training

This directory contains the DeepLabV3+ semantic segmentation training pipelines developed for **Inspector Weeds**.

The objective of the model is to segment palm-oil plantation imagery into three classes:

- Background
- Ground Weeds
- Palm Oil Tree Trunk

The segmentation output is later used by the Inspector Weeds platform to calculate weed coverage and support weed-treatment planning.

## Files

### `01_deeplabv3plus_baseline.ipynb`

Establishes the baseline DeepLabV3+ model using the original annotated dataset without additional data augmentation.

The pipeline includes:

- loading image and PNG-mask pairs;
- Roboflow class mapping;
- image preprocessing;
- DeepLabV3+ model configuration;
- model training and validation;
- class-level segmentation metrics; and
- model checkpointing.

The model uses a **ResNet-50 encoder with ImageNet pretrained weights**.

The baseline provides a reference point for comparing the later data-centric experiments.

### `02_deeplabv3plus_data_centric.ipynb`

Extends the baseline training pipeline to evaluate DeepLabV3+ using additional prepared training data.

The notebook supports the combination of:

- prepared real training data;
- Pix2PixHD-generated synthetic images; and
- augmented synthetic images.

These datasets are combined into a single training dataset before DeepLabV3+ training.

This experiment was used to assess whether increasing the quantity and diversity of training samples improved segmentation performance.

## Training Pipeline

```text
Prepared Training Dataset
          ↓
Dataset Loading
          ↓
DeepLabV3+
ResNet-50 Encoder
          ↓
Training + Validation
          ↓
Model Evaluation
          ↓
Best Model Checkpoint
```

## Evaluation

Model performance is evaluated using segmentation metrics including:

- Intersection over Union (IoU);
- Mean Intersection over Union (mIoU);
- Precision; and
- Recall.

Particular attention was given to the **Ground Weeds** class because weed segmentation is the primary task required by the Inspector Weeds decision-support system.

## Model Selection

Multiple data-centric approaches were evaluated during development, including conventional augmentation and synthetic-data-based training.

The final model used by the Inspector Weeds application was selected based on its performance on both the project dataset and a separate generalization dataset containing images from a different source.

The selected pipeline was the **DeepLabV3+ model trained using 10× augmented real training data**, which demonstrated the strongest overall generalization performance among the evaluated approaches.