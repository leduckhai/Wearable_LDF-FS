<div align="center">

# A multimodal dataset and interpretable machine-learning benchmark using Laser Doppler Flowmetry and Fluorescence Spectroscopy

[![Paper](https://img.shields.io/badge/Paper-Communications%20Medicine-1f6feb?style=flat-square)](https://doi.org/10.1038/s43856-026-01766-5)
[![arXiv](https://img.shields.io/badge/arXiv-2502.00973-b31b1b?style=flat-square)](https://arxiv.org/abs/2502.00973)
[![Code](https://img.shields.io/badge/Code-GitHub-181717?style=flat-square\&logo=github)](https://github.com/leduckhai/Wearable_LDF-FS)
[![Data](https://img.shields.io/badge/Data-Publicly%20Available-2ea44f?style=flat-square)](./Data)

**Minh Ngoc Nguyen*** · **Khai Le-Duc*** · **Tan-Hanh Pham*** · Trong Nhan Nguyen · Trang Nguyen · Ba Kien Tran · Viktor Dremin · Sergei Sokolovsky · Edik Rafailov† · Truong-Son Hy†

<sub>* Equal contribution    † Joint supervision</sub>

</div>

---

## Overview

Mental-health conditions are commonly assessed using self-reported questionnaires, while most wearable approaches rely on a limited set of physiological modalities. This work investigates a complementary direction: **non-invasive optical sensing of peripheral microcirculation and tissue metabolism**.

We introduce a multimodal dataset collected with a wearable device that combines:

* **Laser Doppler Flowmetry (LDF)** to measure cutaneous microvascular perfusion;
* **Fluorescence Spectroscopy (FS)** to characterize tissue metabolic activity; and
* demographic, anthropometric, lifestyle, and questionnaire-derived variables.

The repository provides the data and analysis notebooks used to study associations between these signals and stress-related mental-health symptoms. It includes preprocessing, feature extraction, binary and multi-class classification, subject-wise evaluation, and explainability analyses.

> **Key idea:** Wearable optical signals provide complementary physiological information associated with stress-related mental-health states, while interpretable machine learning helps identify the factors driving model predictions.

---

<div align="center">

If this repository supports your research, please **cite the paper** and consider giving the project a ⭐.

</div>

---

## Highlights

|                              |                                                                               |
| ---------------------------- | ----------------------------------------------------------------------------- |
| **Participants**             | 132 adults                                                                    |
| **Age range**                | 18–94 years                                                                   |
| **Geographic coverage**      | 19 countries                                                                  |
| **Sensing modalities**       | Laser Doppler Flowmetry and Fluorescence Spectroscopy                         |
| **Mental-health assessment** | Depression, Anxiety, and Stress Scale — 21 items (DASS-21)                    |
| **Evaluation**               | Patient-disjoint 5-fold cross-validation and leave-one-patient-out validation |
| **Interpretability**         | SHAP-based feature attribution                                                |
| **Availability**             | Public data, preprocessing code, analysis notebooks, and model benchmarks     |

---

## Contributions

### 1. A multimodal wearable dataset for mental-health research

We provide one of the largest systematically characterized datasets combining LDF and FS measurements for mental-health assessment. The cohort spans a broad age range and diverse geographic backgrounds, with physiological measurements linked to standardized DASS-21 assessments.

### 2. A rigorous subject-wise machine-learning benchmark

We evaluate multiple classical and neural learning methods under patient-disjoint protocols. Keeping measurements from the same participant within a single fold reduces subject leakage and provides a more realistic estimate of generalization to unseen individuals.

### 3. Interpretable analysis of physiological and contextual factors

We use SHAP to examine how optical, physiological, and demographic variables influence model outputs. The analysis highlights the complementary roles of microcirculatory dynamics, metabolic fluorescence, heart rate, body-mass index, age, and sex.

---

## Method at a Glance

1. **Data acquisition**
   Repeated fingertip measurements are collected using a non-invasive wearable device equipped with LDF and FS sensors.

2. **Physiological feature extraction**
   Wavelet-based analysis decomposes LDF signals into frequency bands associated with endothelial, neurogenic, myogenic, respiratory, and cardiac activity. FS measurements capture fluorescence-related markers of tissue metabolism.

3. **Mental-health prediction**
   Machine-learning models are trained for binary and multi-class prediction using combinations of wearable, physiological, and demographic features.

4. **Subject-wise validation**
   Patient-disjoint 5-fold cross-validation and leave-one-patient-out evaluation are used to test generalization to unseen participants.

5. **Model interpretation**
   SHAP-based analyses identify the features that most strongly influence predictions at both global and individual levels.

---

## Main Result

For binary stress-related classification using the ten most informative features under patient-disjoint 5-fold cross-validation, **LightGBM** achieved the strongest reported performance:

| Model        |    ROC-AUC |     PR-AUC |
| ------------ | ---------: | ---------: |
| **LightGBM** | **0.7168** | **0.8852** |

These results suggest that multimodal optical sensing contains meaningful signal for stress-related assessment. Performance decreases under stricter subject-independent settings, emphasizing the substantial inter-individual variability of wearable physiological measurements and the importance of leakage-resistant evaluation.

---

## Repository Structure

```text
Wearable_LDF-FS/
├── Data/
│   └── 07-05-2024_TextNorm.xlsx
├── setups/
│   ├── data_preprocessing.ipynb
│   ├── standard_classification.ipynb
│   ├── allfeatures_binary_classification.ipynb
│   ├── allfeatures_multiclass_classification.ipynb
│   ├── sensorfeatures_binary_classification.ipynb
│   ├── sensorfeatures_multiclass_classification.ipynb
│   ├── top10features_binary_classification.ipynb
│   ├── top10features_multiclass_classification.ipynb
│   ├── feature_importance.ipynb
│   ├── shap_standard_classification.ipynb
│   └── additional analysis and neural-model notebooks
└── README.md
```

---

## Getting Started

Clone the repository:

```bash
git clone https://github.com/leduckhai/Wearable_LDF-FS.git
cd Wearable_LDF-FS
```

Launch Jupyter and begin with the preprocessing notebook:

```bash
jupyter lab setups/data_preprocessing.ipynb
```

The analysis notebooks cover:

* data preprocessing and normalization;
* binary and multi-class prediction;
* experiments using all features, sensor-only features, and the top-ranked features;
* patient-disjoint cross-validation;
* feature-importance analysis; and
* SHAP-based model interpretation.

> The repository currently uses notebook-based workflows. For reproducible reruns, we recommend executing preprocessing first and then running the relevant classification and explainability notebooks.

---

## Data

The released dataset contains de-identified wearable physiological measurements and DASS-21-derived assessments, together with selected demographic, anthropometric, lifestyle, and health variables.

The data are intended for research on:

* wearable and multimodal sensing;
* physiological signal analysis;
* mental-health screening;
* interpretable machine learning;
* digital biomarkers; and
* subject-independent clinical prediction.

Please handle the data responsibly and avoid attempts to re-identify participants.

---

## Important Clinical Note

DASS-21 is a validated symptom-severity questionnaire, but it is **not a clinical diagnostic instrument**. Model outputs in this repository should therefore be interpreted as research predictions of questionnaire-associated symptom groups—not as diagnoses or substitutes for evaluation by qualified healthcare professionals.

---

## Paper

**A Wearable Device Dataset for Mental Health Assessment Using Laser Doppler Flowmetry and Fluorescence Spectroscopy Sensors**
*Communications Medicine*, 2026

* Journal article: https://doi.org/10.1038/s43856-026-01766-5
* arXiv: https://arxiv.org/abs/2502.00973

---

## Citation

```bibtex
@article{nguyen2026wearable,
  title   = {A Wearable Device Dataset for Mental Health Assessment Using
             Laser Doppler Flowmetry and Fluorescence Spectroscopy Sensors},
  author  = {Nguyen, Minh Ngoc and Le-Duc, Khai and Pham, Tan-Hanh and
             Nguyen, Trong Nhan and Nguyen, Trang and Tran, Ba Kien and
             Dremin, Viktor and Sokolovsky, Sergei and Rafailov, Edik and
             Hy, Truong-Son},
  journal = {Communications Medicine},
  year    = {2026},
  doi     = {10.1038/s43856-026-01766-5},
  url     = {https://doi.org/10.1038/s43856-026-01766-5}
}
```

---
## Note on the Released Dataset and Reported Results

The version released in this repository is an expanded and updated version of the dataset used in the published paper. It includes additional samples, participants, and refinements to the data-processing pipeline.

As a result, some experimental values obtained from the released dataset may differ slightly from those reported in the paper. These differences do not affect the overall trends, interpretations, or substantive conclusions of the study. The findings obtained from the updated release remain consistent with the analyses presented in the publication.

---

## Contact

For questions about the code or dataset, please contact:

**Khai Le-Duc**
University of Toronto & University Health Network, Canada
Email: [duckhai.le@mail.utoronto.ca](mailto:duckhai.le@mail.utoronto.ca)
GitHub: [@leduckhai](https://github.com/leduckhai)

**Tan-Hanh Pham**
Florida Institute of Technology, USA
GitHub: [@Hanhpt23](https://github.com/Hanhpt23)
Website: [hanhpt23.github.io](https://hanhpt23.github.io)

---


