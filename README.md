# LesionSegmentation_X_Epilepsy

This project aims to develop and evaluate advanced deep learning models for automated lesion segmentation across the full spectrum of epilepsy. By leveraging diverse architectures and multimodal MRI data, the goal is to enhance segmentation accuracy and robustness. Ultimately, this work seeks to improve clinical presurgical evaluation to support better outcomes in epilepsy surgery.

---

## Supervisors

**Automated Lesion Segmentation for Pre-Surgical Evaluation in Epilepsy**
*Sep 2025 – Present*

Under the supervision of:

* **Dr. Aya Fawzy Khalaf**
  Associate Research Scientist at Yale University in the Blumenfeld Lab.
  [Yale Profile](https://medicine.yale.edu/profile/aya-khalaf/)

* **Eng. Mahmoud Salman**
  MESc Biomedical Engineering student at Western University.
  [LinkedIn Profile](https://linkedin.com/in/mahmoud1yaser)

* **Dr. Tamer Basha**
  Associate Professor at Cairo University and Postdoctoral Fellow at Harvard Medical School.
  [LinkedIn Profile](https://www.linkedin.com/in/tamer-basha-b81812ab/)

---

## Project Status: In Development

This repository is currently under active development. Core modules, preprocessing workflows, and model training pipelines are still being built and tested.
Key components—including data harmonization, multi-sequence training strategies, and evaluation metrics—are subject to change as the project evolves.

Planned updates include:

* End-to-end nnUNet training for T1, FLAIR, and joint inputs
* Comparative benchmarking across architectures
* Integration of clinical metadata
* Full documentation and reproducible workflows

Expect rapid iteration and incomplete workflows until the first stable release.

---

## Project Structure

```
LesionSegmentation_X_Epilepsy/
├── README.md
├── .gitignore
├── requirements.txt
└── src/
    └── notebooks/
        ├── data_setup/
        │   └── bids_to_centric.ipynb
        │
        ├── SynthSeg/
        │   └── launch_synthSeg.ipynb
        │
        └── nnUNet_training/
            ├── FLAIR/
            │   ├── preprocessing/
            │   ├── models/
            │   └── notes.txt
            │
            ├── T1/
            │   ├── preprocessing/
            │   ├── models/
            │   └── notes.txt
            │
            └── T1_FLAIR/
                ├── preprocessing/
                ├── models/
                └── notes.txt
```
