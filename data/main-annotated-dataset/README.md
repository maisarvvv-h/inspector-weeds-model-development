# Inspector Weeds Annotated Dataset

This directory contains the image dataset and semantic segmentation annotations used for the **Inspector Weeds** capstone project.

## Dataset

- **Images:** 346
- **Task:** Semantic segmentation
- **Annotation format:** PNG masks
- **Annotation platform:** Roboflow
- **Classes:** Palm tree, ground weeds, and background

The dataset was exported from Roboflow with auto-orientation preprocessing. No augmentation was applied as part of the original Roboflow export.

Additional augmentation was performed separately during DeepLabV3+ model experimentation.

## Structure

The Roboflow semantic segmentation export stores each source image and its corresponding PNG mask in the **same directory**.

The mask uses the same base filename as its source image with `_mask.png` appended.

For example:

```text
data/
├── train/
│   ├── _classes.csv
│   ├── A29_jpg.rf.[id].jpg
│   ├── A29_jpg.rf.[id]_mask.png
│   ├── B48_jpg.rf.[id].jpg
│   ├── B48_jpg.rf.[id]_mask.png
│   └── ...
│
├── valid/
│   ├── _classes.csv
│   ├── [image].jpg
│   ├── [image]_mask.png
│   └── ...
│
└── test/
    ├── _classes.csv
    ├── [image].jpg
    ├── [image]_mask.png
    └── ...
```

A typical image-mask pair therefore looks like:

```text
B48_jpg.rf.ffede9877a3528df1c164d6910cb0a1e.jpg
B48_jpg.rf.ffede9877a3528df1c164d6910cb0a1e_mask.png
```

The `.jpg` file contains the original plantation image, while the corresponding `_mask.png` file contains the semantic segmentation annotation used for model training.

## Visual Examples

Raw PNG segmentation masks are not able to be interpreted when viewed directly because they encode class information as pixel values.

For easier visual interpretation, a small set of colourized masks and overlays may be provided separately in a `samples/` directory.

These visualized examples are for presentation only. Model training uses the original PNG annotation masks.

## Pre-processing

The Roboflow export applied:

- Auto-orientation of image pixel data
- EXIF orientation stripping

No image augmentation was applied during the original Roboflow dataset export.

Additional augmentation was later performed separately during DeepLabV3+ model experimentation.

## Full Dataset

The complete dataset and its semantic segmentation annotations are included in this repository.

The dataset was prepared and exported using **Roboflow**.

## Licence

This dataset is distributed under the **CC BY 4.0** licence.

Dataset source and annotation management: Roboflow.