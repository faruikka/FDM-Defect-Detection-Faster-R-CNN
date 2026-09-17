# FDM 3D-Printed Defect Detection Using Faster R-CNN

## Overview

This project investigates image-based deep learning for detecting and localizing defects in FDM 3D-printed PLA specimens.

The current prototype uses **Faster R-CNN with a ResNet-50 FPN V2 backbone**, pretrained on COCO and fine-tuned for four defect classes.

## Defect Classes

- Cracking
- Layer shifting
- Stringing
- Warping

## Current Prototype

The notebook:

- Loads Pascal VOC XML annotations
- Merges four per-class Roboflow exports
- Applies light training augmentation
- Fine-tunes Faster R-CNN using PyTorch/Torchvision
- Uses a train/validation/test split
- Saves the best checkpoint based on validation loss
- Reports mAP, Precision, Recall, F1-score, and a confusion matrix
- Supports inference on new images
- Can generate Pascal VOC XML annotations for an unlabeled batch

## Preliminary Results

The current experimental run produced:

| Metric | Result |
|---|---:|
| mAP@0.5 | 98.17% |
| mAP@0.75 | 66.47% |
| mAP@0.5:0.95 | 61.93% |

These are **preliminary prototype results**, not final thesis results. The dataset split, duplicate images, annotation quality, class balance, and evaluation procedure should be verified before using these values as final research results.

## Training Curves

### Training Loss

![Training Loss](results/training_loss.png)

### Validation Loss

![Validation Loss](results/validation_loss.png)

## Dataset

The current prototype uses a Pascal VOC-annotated dataset exported from Roboflow. The dataset itself is not included in this repository by default.

Before redistributing any dataset images or annotations, check the original dataset's license and usage conditions.

## Running the Notebook

The notebook is designed for **Google Colab**.

1. Open the notebook in Google Colab.
2. Upload the required dataset archives or mount Google Drive.
3. Update the dataset paths and class names if necessary.
4. Run the cells in order.
5. Review the dataset audit before training.
6. Train and evaluate the model.

## Files

```text
FDM-Defect-Detection-FasterRCNN/
├── FDM_Defect_Detection_FasterRCNN.ipynb
├── README.md
├── requirements.txt
└── results/
    ├── training_loss.png
    └── validation_loss.png
```

## Future Work

- Build a larger dataset from FDM/PLA specimens
- Add genuinely defect-free specimens
- Verify split independence and avoid data leakage
- Improve annotation quality and class balance
- Evaluate on independently collected specimens
- Tune the model and training procedure
- Compare Faster R-CNN with other object detectors

## Research Status

**Work in progress — undergraduate thesis project.**
