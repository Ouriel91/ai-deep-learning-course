# 🏗️ Building Defect Detection using YOLOv8

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Ouriel91/mbdd2025-building-defect-detection/blob/main/project_2_MBDD2025_Building_Defect_Detection.ipynb)

[![GitHub Repository](https://img.shields.io/badge/GitHub-Repository-181717?logo=github)](https://github.com/Ouriel91/mbdd2025-building-defect-detection)

[![Personal AI Portfolio](https://img.shields.io/badge/Personal-AI%20Portfolio-blue?logo=github)](https://github.com/Ouriel91/ai-deep-learning-course/tree/main/project_02_mbdd2025)

A complete end-to-end Computer Vision project for **multi-class building defect detection** using **YOLOv8**, **Transfer Learning**, and **Fine-Tuning** on the **MBDD2025** UAV dataset.

This repository presents a complete machine learning workflow for UAV-based building defect detection, from raw dataset validation and preprocessing to model training, evaluation, and controlled experimentation.

This project is based on the **MBDD2025** dataset introduced by **Q. Zha et al., _A dataset of building surface defects collected by UAVs for machine learning-based detection_ (Scientific Data, 2025)**.

📄 **Reference Paper:** https://www.nature.com/articles/s41597-025-06318-5

📦 **Dataset:** https://www.kaggle.com/datasets/mennamahmoudd/mbdd2025-building-defects

Rather than simply training a pretrained detector, this project develops a complete and reproducible object detection pipeline from raw annotations to final evaluation.

The work includes:

- Automatic dataset validation and integrity checking
- Exploratory Data Analysis (EDA) of more than **14,000 UAV images** and **57,000 annotated defects**
- Pascal VOC to YOLO annotation conversion
- Automated Train / Validation / Test split generation
- Transfer Learning and end-to-end Fine-Tuning of **YOLOv8n**
- Quantitative evaluation using Precision, Recall, mAP50 and mAP50-95
- Qualitative prediction visualization and comprehensive error analysis
- Comparison with the official MBDD2025 benchmark
- A controlled experiment evaluating the effect of increasing the input image resolution (640 → 960) while keeping all other training parameters unchanged

The controlled experiment demonstrated consistent improvements in **Recall**, **mAP50**, **mAP50-95**, and the **Crack** class AP50-95, while introducing the expected increase in inference time. This provides a practical analysis of the trade-off between detection accuracy and computational efficiency.

---

# 👥 Team Members

- **Ouriel**
- **Ilya**
- **Sagi**

---

# 📌 Project Highlights

✅ Complete end-to-end object detection pipeline

✅ Comprehensive dataset validation and preprocessing

✅ Exploratory Data Analysis (EDA)

✅ Transfer Learning using pretrained YOLOv8n

✅ End-to-end Fine-Tuning for 100 epochs

✅ Formal evaluation using Precision, Recall, mAP50 and mAP50-95

✅ Error analysis with qualitative predictions

✅ Controlled experiment on input image resolution

✅ Comparison with the official MBDD2025 paper

✅ Fully reproducible Google Colab workflow

---

# 🎯 Project Objectives

The objective of this project is to automatically detect visible surface defects in buildings from UAV imagery.

For every detected defect, the model predicts:

- Defect class
- Bounding box location
- Detection confidence

The project follows a complete machine learning workflow:

- Dataset preparation
- Data validation
- Exploratory analysis
- Transfer learning
- Fine-tuning
- Evaluation
- Error analysis
- Controlled experimentation

---

# 📊 Dataset

### Dataset

**MBDD2025 – Building Surface Defect Detection Dataset**

The dataset contains UAV images annotated using Pascal VOC XML format.

### Statistics

- **14,471** UAV images
- **57,613** annotated defects
- **5 defect classes**

| Class |
|--------|
| Crack |
| Leakage |
| Abscission |
| Corrosion |
| Bulge |

The dataset was automatically converted to YOLO format after extensive validation.

---

# 🔍 Exploratory Data Analysis

Before training, a complete EDA pipeline was performed.

The analysis includes:

- Dataset inventory
- XML validation
- Missing annotation detection
- Class distribution
- Objects per image
- Bounding-box statistics
- Bounding-box spatial distribution
- Multi-class co-occurrence analysis
- Dataset quality verification

These analyses were used to verify dataset consistency before training.

---

# 🛠️ Dataset Preparation

The notebook automatically performs:

- Pascal VOC parsing
- Annotation validation
- Metadata generation
- Image-level metadata
- Object-level metadata
- Train / Validation / Test split
- YOLO label generation
- Dataset integrity checks
- Automatic dataset configuration (`dataset.yaml`)

The final split follows approximately:

| Split | Ratio |
|--------|------:|
| Train | 70% |
| Validation | 20% |
| Test | 10% |

---

# 🧠 Model

The project uses:

**YOLOv8n**

with pretrained weights:

```text
yolov8n.pt
```

Transfer Learning is performed by initializing the network from pretrained COCO weights and fine-tuning the complete model on the MBDD2025 dataset.

No layers were manually frozen; the entire network was optimized during training.

---

# ⚙️ Training Configuration

| Parameter | Value |
|------------|-------|
| Model | YOLOv8n |
| Epochs | 100 |
| Optimizer | Auto |
| Batch Size | 16 |
| Initial Image Size | 640×640 |
| Experiment | 960×960 |
| Random Seed | 42 |

Training includes the default Ultralytics augmentation pipeline.

---

# 📈 Results

The baseline model achieved strong detection performance across all defect classes.

Evaluation metrics include:

- Precision
- Recall
- mAP50
- mAP50-95
- Per-class AP
- Confusion Matrix
- Inference Time

The notebook also presents qualitative prediction examples together with detailed error analysis.

The controlled experiment showed that increasing the input image resolution from **640×640** to **960×960** consistently improved Recall, mAP50, mAP50-95, and the AP50-95 of the Crack class, while introducing the expected increase in inference time.

---

# 🧪 Controlled Experiment

A controlled experiment was conducted to evaluate whether increasing the input image resolution improves defect detection performance.

### Experiment

Only a single parameter was modified:

```text
Image Size

640 × 640

↓

960 × 960
```

All other training parameters remained unchanged.

### Results

The higher-resolution model demonstrated:

- Higher Recall
- Higher mAP50
- Higher mAP50-95
- Improved Crack AP50-95
- Better localization quality in qualitative examples

The improvement was achieved at the expected cost of slower inference speed.

This experiment demonstrates the trade-off between detection accuracy and computational efficiency.

---

# 📑 Comparison with the Reference Paper

The project reproduces the official MBDD2025 object detection workflow while extending it through an additional controlled experiment.

Rather than modifying the model architecture, this work isolates the effect of input image resolution and quantitatively evaluates its influence on detection quality and inference speed.

The resulting analysis complements the original benchmark by providing additional insights into the relationship between spatial resolution and defect localization performance.

---

# 📂 Repository Structure

```text
.
├── project_2_MBDD2025_Building_Defect_Detection.ipynb   # Complete end-to-end project notebook
└── README.md                                            # Project documentation
```

> **Note:** Training checkpoints, experiment outputs, and pretrained weights are **not included** in this repository in order to keep it lightweight. During execution, the notebook automatically creates the required project directories in Google Drive, downloads the dataset, trains the model, and generates all checkpoints, logs, metrics, and figures.

> **Pretrained checkpoints:** The notebook is fully reproducible and can be executed from scratch. However, if you would like to reproduce the reported results without retraining, the trained model checkpoints used in this project are available upon request.

> **Need the trained checkpoints?** Feel free to contact me through GitHub if you would like access to the trained models used in this project or have any questions regarding the implementation.

---


# 🚀 Getting Started

## 1. Clone the repository

```bash
git clone https://github.com/Ouriel91/mbdd2025-building-defect-detection.git
```

---

## 2. Open the notebook

Open

```text
project_2_MBDD2025_Building_Defect_Detection.ipynb
```

using **Google Colab** link inside the notebook (with text Open in Colab).

---

## 3. Mount Google Drive

The notebook automatically creates the required project folders if they do not already exist.

Previously trained experiment folders are automatically reused when available.

If the pretrained checkpoints are available, the notebook can resume from the saved models, allowing you to reproduce the reported results without repeating the full training process.

---

## 4. Run the notebook

Execute the notebook from top to bottom.

The notebook automatically:

- downloads the dataset
- validates annotations
- prepares YOLO labels
- creates metadata
- trains the model
- evaluates the results
- generates figures and metrics

No manual preprocessing is required.

---

# 📦 Dependencies

The notebook installs any missing Python packages automatically.

Main libraries include:

- Python
- PyTorch
- Ultralytics
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Seaborn
- KaggleHub

---

# ⭐ Key Achievements

- End-to-end object detection workflow
- Robust dataset validation
- Automated preprocessing pipeline
- Transfer Learning with YOLOv8n
- Fine-Tuning on UAV imagery
- Comprehensive error analysis
- Controlled experimental design
- Comparison with published benchmarks
- Fully reproducible Google Colab implementation

---

# 🔮 Future Work

Potential future improvements include:

- Evaluation of larger YOLO architectures
- Vision Transformer based detectors
- Test-time augmentation
- Hyperparameter optimization
- Deployment using Gradio or Streamlit
- Building-level defect aggregation and reporting

---

### Reference Paper

Q. Zha et al.

**A dataset of building surface defects collected by UAVs for machine learning-based detection**

Scientific Data, 2025.

Link: https://www.nature.com/articles/s41597-025-06318-5

---

# 📚 References

### Dataset

MBDD2025 Building Defects Dataset

Link: https://www.kaggle.com/datasets/mennamahmoudd/mbdd2025-building-defects

---


# 🙏 Acknowledgments

This project was completed as part of the **Applied Computer Vision** course.

Special thanks to the creators of the **MBDD2025** dataset and to the **Ultralytics YOLO** development team for making state-of-the-art object detection tools publicly available.