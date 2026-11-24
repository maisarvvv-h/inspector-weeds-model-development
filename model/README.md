# Inspector Weeds – Model Development

This repository contains the model development work for the **Inspector Weeds** capstone project, including data preparation, augmentation, experimentation, training, and evaluation of the DeepLabV3+ semantic segmentation model.

## Repository Contents

```text
model-development/
├── data-preparation/
│   ├── 01_generate_augmentations.ipynb
│   └── 02_generate_synthetic_data.ipynb
│
├── training/
│   ├── 01_deeplabv3plus_baseline.ipynb
│   └── 02_deeplabv3plus_data_centric.ipynb
│
└── README.md
```

## Trained Model

The final trained model is **not stored in this repository**.

The model used by the Inspector Weeds website is located in the website repository:

**[Inspector Weeds Website](https://github.com/maisarvvv-h/inspector-weeds-website)**

Model file:

```text
model/best_deeplabv3plus.pt
```

The model is stored using **Git LFS** due to its file size.

## Model Output

The DeepLabV3+ model performs semantic segmentation using three classes:

- Background
- Ground Weeds
- Palm Oil Tree Trunk

The segmentation outputs are later used by the website to calculate weed coverage, classify weed severity, and support dashboard and treatment-planning features.

## Related Repository

The full web application, inference pipeline, trained model, dashboard, and treatment-planning features are available here:

**[Inspector Weeds Website Repository](https://github.com/maisarvvv-h/inspector-weeds-website)**