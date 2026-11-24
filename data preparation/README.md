# Data Preparation

This directory contains the data-preparation pipelines used during the development of **Inspector Weeds**.

Two approaches were explored to increase the diversity of the training data:

1. conventional image augmentation; and
2. synthetic image generation using Pix2PixHD.

The prepared datasets were later used in the DeepLabV3+ model experiments contained in the `training/` directory.

## Files

### `01_generate_augmentations.ipynb`

Generates augmented versions of the original annotated training images using **Albumentations**.

The same transformation is applied to both the plantation image and its corresponding semantic segmentation mask so that the annotations remain aligned.

The current pipeline generates:

- **10 augmented versions per original training image**
- corresponding augmented PNG segmentation masks

These augmented samples were created to increase variation in the training data and evaluate whether additional data diversity improves DeepLabV3+ performance and generalization.

### `02_generate_synthetic_data.ipynb`

Uses **Pix2PixHD** to generate synthetic palm-oil plantation imagery from the annotated training data.

The notebook includes:

- preparation of image pairs for Pix2PixHD;
- Pix2PixHD model training;
- synthetic image generation; and
- evaluation of generated images using FID.

The generated synthetic images were used as an additional source of training data in the later data-centric DeepLabV3+ experiments.

## Data Preparation Workflow

```text
Original Annotated Dataset
          │
          ├── Image Augmentation
          │       └── Augmented Images + Masks
          │
          └── Pix2PixHD
                  └── Synthetic Images + Masks
                          │
                          └── Optional Augmentation
```

The generated datasets are treated as intermediate training data and are separate from the original annotated dataset.

## Purpose

These pipelines were developed to investigate whether expanding the available training data could improve the segmentation model's ability to identify ground weeds under different plantation conditions.

The original training dataset remains unchanged. Augmented and synthetic datasets are generated separately for experimentation.