# nnU-Net for FCD Lesion Segmentation

This repository contains a complete pipeline for Focal Cortical Dysplasia (FCD) lesion segmentation using nnU-Net. It is designed to handle class imbalance through custom oversampling and is organized for easy local or cloud execution.

## 📂 Project Structure

```
nnU-net/
├── notebooks/                         # Executable Jupyter Notebooks
│   ├── 00_Data_Preprocessing.ipynb
│   ├── 01_Train_Oversampling.ipynb
│   ├── 02_Continue_Training.ipynb
│   └── 03_Inference.ipynb
│
├── src/                               # Source Code & Config
│   ├── config.py                      # Central configuration
│   ├── splits_final.json              # Fixed cross-validation splits
│   └── custom_nnunet/                 # Custom logic (Trainer, DataLoader)
│
└── data/                              # Data Directory (Expected Input)
    ├── bonn_fcd_fixed/                # Raw MRI data
    └── participants-data/             # Excel metadata
```

## 🚀 Setup Instructions

### 1. Data Preparation

You must place your data in the `data/` folder as follows:

1. **Raw Images**: Place your dataset folder (e.g., `bonn_fcd_fixed`) inside `nnU-net/data/`.
2. **Metadata**: Place your `participants.xlsx` inside `nnU-net/data/participants-data/`.

*Note: If your data is located elsewhere, you can modify `DATA_ROOT` in `src/config.py`, but keeping the default structure is recommended.*

### 2. Configuration (`src/config.py`)

All global parameters are managed in `src/config.py`. You should edit this file to match your experiment needs.

**Key Parameters to Edit:**

* **`TRAINING_TIME_MINUTES`**: Maximum duration for training (default: 11h 45m). Useful for time-limited environments like Kaggle.
* **`OVERSAMPLE_FACTOR`**: How much more frequently rare subjects should be sampled (default: `3.0`).
* **`RARE_SUBJECTS`**: A list of string IDs (e.g., `'sub-00001'`) that represent the minority class/rare cases to oversample.

## 🏃‍♂️ How to Run

The pipeline is divided into sequential notebooks located in the `notebooks/` folder.

### Step 1: Data Preprocessing

Open and run **`notebooks/00_Data_Preprocessing.ipynb`**.

* **What it does:** Converts your Excel/MRI data into the format required by nnU-Net (`dataset.json`, organized images) and saves it to `data/nnUNet_raw`.
* **Output:** `data/nnUNet_raw/Dataset002_BonnFCD_FLAIR`

### Step 2: Training

Open and run **`notebooks/01_Train_Oversampling.ipynb`**.

* **What it does:** Starts the training process using the custom `nnUNetTrainerOversampling`.
* **Important:** You can change the `FOLD` variable in the notebook to train different Cross-Validation folds (0-4).
* **Output:** Checkpoints are saved to `data/nnUNet_results`.

### Step 3: Continue Training (Optional)

If training was interrupted or you want to add more epochs, run **`notebooks/02_Continue_Training.ipynb`**.

* **What it does:** Automatically finds the last checkpoint and resumes training.

### Step 4: Inference

Open and run **`notebooks/03_Inference.ipynb`**.

* **What it does:** Uses the trained model to predict segmentation masks for test images.
* **Metrics:** Calculates Dice, IoU, and other metrics to evaluate performance.

## 🛠 Customization

* **Splits**: The 5-fold cross-validation splits are fixed in `src/splits_final.json`. Edit this file to change which subjects are in which fold.
* **Model Logic**: To modify the trainer or data loading logic, edit the Python files in `src/custom_nnunet/`.
