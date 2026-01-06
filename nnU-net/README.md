# nnU-Net for FCD Lesion Segmentation

This directory contains the implementation of the nnU-Net framework for Focal Cortical Dysplasia (FCD) lesion segmentation, organized into three sequential Jupyter notebooks. These notebooks serve as a complete pipeline from training to interference.

## Notebooks

The notebooks are numbered to indicate the execution order:

### [01_Train_Oversampling.ipynb](./01_Train_Oversampling.ipynb)

**Purpose:** Main training pipeline.

* Implements a custom `nnUNetTrainer` to handle class imbalance.
* Applies **oversampling** for rare subjects (non-cortical thickening).
* Configures doubled data augmentation parameters (rotation, scaling, intensity).
* Enforces fixed 5-fold cross-validation splits.

### [02_Continue_Training.ipynb](./02_Continue_Training.ipynb)

**Purpose:** Resuming training from a checkout.

* Used when training is interrupted or needs to continue for more epochs.
* Restores the trainer state and continues from the last saved checkpoint.

### [03_Inference.ipynb](./03_Inference.ipynb)

**Purpose:** Inference and evaluation.

* Loads the trained model checkpoint.
* Reconstructs the necessary nnU-Net folder structure for inference.
* Runs predictions on test images.
* Evaluates performance using Dice, IoU, Precision, Recall, and HD95 metrics.
* Visualizes segmentation results against ground truth.

## Key Features

* **Custom Trainer:** `nnUNetTrainerOversampling` designed for unbalanced datasets.
* **Oversampling:** Targeted sampling of rare FCD subtypes.
* **Kaggle/Colab Compatibility:** Scripts include environment setup and path configuration for cloud environments.
