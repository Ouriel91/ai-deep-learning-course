# Project 02 – MBDD2025 Building Defect Detection

## Project Overview

This project focuses on detecting visible building surface defects from UAV images using deep learning and transfer learning.

The dataset used is MBDD2025, which contains UAV images annotated for five defect classes:

- Crack
- Leakage
- Abscission
- Corrosion
- Bulge

The main task is multi-class object detection.

For each image, the model should predict:

- defect class
- bounding box location
- confidence score

## Dataset

Dataset: MBDD2025 – Building Defects

Source:
https://www.kaggle.com/datasets/mennamahmoudd/mbdd2025-building-defects

The dataset contains approximately:

- 14,471 UAV images
- 57,613 annotated defect instances
- Pascal VOC XML annotations
- YOLO-format labels

The dataset includes repeated and overlapping UAV frames, which may require special attention when defining train, validation, and test splits.

## Current Progress

Completed:

- Dataset loading through KaggleHub
- Dataset structure validation
- Image/XML pairing validation
- Pascal VOC parsing
- Object-level metadata generation
- Image-level metadata generation
- Annotation validation
- Ground-truth visualization
- Initial exploratory data analysis

Current notebook:

`01_MBDD2025_EDA.ipynb`

## Initial EDA Findings

The initial analysis identified several important dataset characteristics:

- Significant class imbalance between defect categories
- Large variation in the number of objects per image
- Many relatively small defect annotations
- Variation in bounding-box size and shape across classes
- Spatial concentration of annotations toward the center of images
- Many multi-object images, but fewer multi-class images
- A small number of bounding boxes requiring further validation

## Planned Next Steps

1. Investigate UAV frame continuity and possible sequence structure.
2. Define a robust train/validation/test split.
3. Build a pretrained object-detection baseline.
4. Apply transfer learning and fine-tuning.
5. Experiment with training parameters.
6. Evaluate performance using detection metrics such as Precision, Recall, and mAP.
7. Compare results with published MBDD2025 benchmarks.
8. Explore an application layer for building-inspection screening.

## Project Direction

The core scientific task is defect detection and localization.

A possible application layer may later aggregate detected defects and flag images or structures for further professional inspection.

This application layer will be treated separately from the ground-truth object-detection task.

## References

MBDD2025 Dataset Paper:

Q. Zha et al.,
"A dataset of building surface defects collected by UAVs for machine learning-based detection",
Scientific Data, 2025.

Dataset:
https://www.kaggle.com/datasets/mennamahmoudd/mbdd2025-building-defects