# Inspector Weeds Generalization Dataset

This directory contains the **generalization dataset** used to evaluate the Inspector Weeds DeepLabV3+ model on images from a different source than the main training dataset.

## Dataset

- **Images:** 30
- **Purpose:** Generalization testing
- **Task:** Semantic segmentation
- **Model evaluated:** DeepLabV3+
- **Data source:** Different from the primary Inspector Weeds training dataset

## Evaluation

The generalization dataset was used to compare the performance of the different DeepLabV3+ model pipelines developed during the project.

- the main project dataset; and
- the separate generalization dataset.

This provided additional evidence that the selected model was able to maintain its performance on images outside the original training data.

## Structure

The generalization images are stored in this directory together with any corresponding annotation files used for evaluation.

```text
generalization/
├── image_01.jpg
├── image_01_mask.png
├── image_02.jpg
├── image_02_mask.png
└── ...
```

The exact filenames may vary depending on the original dataset source.

## Notes

This dataset was used only for **generalization testing** and was not used to train the final model.

Keeping this dataset separate from the training data helps provide a more realistic indication of how the model may perform on unseen plantation imagery.

## Source and Licence

The images in this dataset originate from a separate source from the main Inspector Weeds dataset.

Please refer to the original image source for the applicable licence and attribution requirements.