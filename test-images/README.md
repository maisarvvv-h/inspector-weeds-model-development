Website Test Images

This directory contains the images used to test the end-to-end Inspector Weeds web application.

These images are separate from the training and validation data used during DeepLabV3+ model development.

Purpose

The test images were used to evaluate whether the trained segmentation model could be successfully integrated into the Inspector Weeds application and produce the information required by the decision-support workflow.

The images were uploaded through the application and processed through the complete system:

Image Upload
      ↓
DeepLabV3+ Inference
      ↓
Semantic Segmentation
      ↓
Weed Coverage Calculation
      ↓
Severity Classification
      ↓
Dashboard
      ↓
Treatment Planning

These images are intended primarily for application testing and demonstration, rather than formal model-performance evaluation.

Formal generalization testing was conducted separately using the project's generalization dataset.

File Naming Convention

Test images follow a standardized naming convention representing the plantation zone and individual tree.

For example:

A24.jpg

represents:

A — Zone A

24 — Tree/Image 24 within the simulated plantation dataset

Additional examples include:

A01.jpg
A15.jpg
B04.jpg
B12.jpg

The Inspector Weeds application reads the zone identifier from the uploaded filename and uses it to associate the analysis result with the appropriate plantation zone.

Role in the Application

For each uploaded image, the system uses the trained DeepLabV3+ model to identify:

background;

ground weeds; and

palm oil tree trunk.

The segmentation output is then converted into operational information including:

weed coverage percentage;

severity classification;

plantation zone;

treatment requirement; and

estimated treatment OPEX.

Results from multiple test images are aggregated within the Dashboard and Treatment Planning components of the application.

Important Distinction

These images should not be confused with the generalization dataset.

The two datasets serve different purposes:

Website Test Images
Used to test the functionality and end-to-end integration of the Inspector Weeds application.

Generalization Dataset
A separate 30-image dataset from a different source used to evaluate the model's ability to generalize to previously unseen image conditions.

Notes

The zone and tree identifiers used in the filenames form part of the project's simulated plantation-management workflow.

They allow individual image-level predictions to be aggregated into zone-level information for dashboard visualization and treatment planning.