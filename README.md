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


