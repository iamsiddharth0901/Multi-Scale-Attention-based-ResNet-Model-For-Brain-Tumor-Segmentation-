# Multi-Scale-Attention-based-ResNet-Model-For-Brain-Tumor-Segmentation-
# Brain Tumor Segmentation using MSA-ResUNet3D

A 3D deep learning approach for brain tumor segmentation from multi-modal MRI scans using a **Multi-Scale Attention ResUNet** architecture.

## Overview

This project performs automated brain tumor segmentation using the BraTS2020 dataset.

The model processes four MRI modalities:

* FLAIR
* T1
* T1ce
* T2

The segmentation identifies three tumor regions:

* Whole Tumor (WT)
* Tumor Core (TC)
* Enhancing Tumor (ET)

## Model Architecture

The proposed **MSA-ResUNet3D** combines:

* 3D Residual Blocks
* Multi-Scale Attention
* Encoder–Decoder architecture
* Skip connections
* Deep supervision
* 3D spatial convolutions

### Pipeline

MRI Volumes
↓
Preprocessing & Normalization
↓
Tumor-Focused Patch Sampling
↓
Data Augmentation
↓
MSA-ResUNet3D
↓
Sliding-Window Inference
↓
Tumor Segmentation

## Training

The training pipeline uses:

* Dice + Cross-Entropy loss
* Adam optimizer
* Learning-rate warmup
* Cosine annealing
* Mixed-precision training
* Gradient accumulation
* Gradient clipping
* Early stopping

## Evaluation

The model is evaluated using:

* Dice Score
* Whole Tumor (WT)
* Tumor Core (TC)
* Enhancing Tumor (ET)
* 95th Percentile Hausdorff Distance (HD95)

## Visual Analysis

The notebook generates:

* MRI modality visualization
* Ground-truth vs prediction comparison
* Error maps
* Predictive uncertainty maps
* Tumor-region breakdown
* Multi-slice segmentation analysis
* Tumor volume statistics
* Training curves

## Dataset

This project uses the **BraTS2020** dataset.

The dataset is not included in this repository. Download the dataset separately and configure the dataset path before running the notebook.

## Repository Structure

```text
brain-tumor-segmentation/
│
├── README.md
├── brain_tumor_segmentation.ipynb
├── requirements.txt
├── .gitignore
│
└── results/
```

## Technologies

Python • PyTorch • NumPy • SciPy • Matplotlib

## 📊 Results

### Validation Performance

The MSA-ResUNet3D model was trained for 25 epochs on the BraTS2020 dataset using an 80/20 train-validation split.

* **Training patients:** 295
* **Validation patients:** 74
* **Model parameters:** 6,984,431
* **Best validation Dice:** **0.6983**
* **Best epoch:** **20**
* **Best validation loss:** **0.2051**

At the best validation epoch:

| Region               |       Dice |
| -------------------- | ---------: |
| Whole Tumor (WT)     |     0.8353 |
| Tumor Core (TC)      |     0.8076 |
| Enhancing Tumor (ET) |     0.7191 |
| **Average**          | **0.6983** |

### Full-Volume Inference

The best checkpoint was evaluated using full-volume sliding-window inference.

| Patient   | WT Dice | TC Dice | ET Dice | Average Dice | WT HD95 | TC HD95 | ET HD95 |
| --------- | ------: | ------: | ------: | -----------: | ------: | ------: | ------: |
| Patient 1 |  0.8445 |  0.8148 |  0.8176 |   **0.8257** |    5.10 |    2.24 |    1.73 |
| Patient 2 |  0.4935 |  0.0087 |  0.0000 |   **0.1674** |   64.83 |   15.78 |       — |
| Patient 3 |  0.8457 |  0.8590 |  0.0000 |   **0.5682** |   57.28 |    3.61 |       — |

`—` indicates that HD95 was not defined for that region in the corresponding sample.

### Qualitative Results

The model's predictions are visualized through:

* Multi-modal MRI inputs (FLAIR, T1, T1ce and T2)
* Ground-truth segmentation
* Predicted tumor segmentation
* Prediction error maps
* Predictive uncertainty maps
* Multi-slice spatial consistency
* Tumor-region breakdown
* Tumor-volume statistics
* Training and validation curves

### Visual Results

#### MRI Modalities & Segmentation

![Publication Panel](results/publication_panel.png)

#### Ground Truth vs Prediction

![Prediction Comparison](results/prediction_comparison.png)

#### Training Performance

![Training Curves](results/training_curves.png)



