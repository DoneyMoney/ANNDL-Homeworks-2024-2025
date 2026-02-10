# Artificial Neural Networks and Deep Learning Projects [2024-2025]

[cite_start]This repository contains the projects developed for the **AN2DL** course at **Politecnico di Milano**[cite: 2, 116]. The work is focused on two main Computer Vision challenges: multi-class image classification and semantic segmentation using advanced Deep Learning architectures.

## 👥 Authors
* [cite_start]**Valeria de Gennaro** [cite: 3, 117]
* [cite_start]**Donato Fiore** [cite: 3, 117]
* [cite_start]**Lorenzo Fonnesu** [cite: 3, 117]
* [cite_start]**Gabriele Lorenzetti** [cite: 3, 117]

---

## 🩸 Homework 1: Blood Cell Classification
**Goal:** Categorize 96x96 RGB images of blood cells into eight distinct classes (Basophil, Eosinophil, Erythroblast, Immature granulocytes, Lymphocyte, Monocyte, Neutrophil, Platelet).

### Technical Overview
* [cite_start]**Dataset Cleaning:** The initial dataset of 13,759 images was cleaned of 1,800 out-of-context images and 8 duplicates to ensure training stability[cite: 9, 24, 40].
* [cite_start]**Model Architecture:** We utilized **ConvNeXtBase** as the primary backbone, which outperformed other tested models like ResNet50 and EfficientNet[cite: 33, 34, 88].
* **Training Strategy:**
    * [cite_start]**Transfer Learning:** Initial training of top layers (GAP, Dense, Dropout) with frozen backbone for 10 epochs[cite: 65].
    * [cite_start]**Fine-Tuning:** Unfreezing layers from the 150th onward using the Adam optimizer with **Cosine Annealing**[cite: 66, 70].
* [cite_start]**Data Augmentation:** An intensive pipeline using `keras_cv` was implemented, including **CutMix**, **Cutout**, and **RandAugment**[cite: 35, 64].



### Results
* [cite_start]**Performance:** The model achieved a final accuracy of **80%** on Codabench, starting from a 20% baseline[cite: 18, 81].

---

## 🪐 Homework 2: Martian Terrain Segmentation
**Goal:** Semantic segmentation of 64x128 grayscale images of the Martian surface into 5 classes: Soil, Bedrock, Sand, Big Rock, and Background.

### Technical Overview
* **Constraint:** As per course rules, all models were **trained from scratch** without relying on any pre-trained weights.
* [cite_start]**Architecture:** A custom **U-Net++** model featuring nested skip connections to improve feature aggregation[cite: 126, 161, 183].
    * [cite_start]**PAN (Path Aggregation Network):** Integrated to better capture local and global contextual information[cite: 179, 189].
    * [cite_start]**SE (Squeeze-and-Excitation):** Modules added to dynamically recalibrate channel-wise feature responses[cite: 167, 179, 195].
* [cite_start]**Loss Functions:** A hybrid loss combining **Focal Loss** and **Dice Loss** was developed to handle the significant class imbalance in the terrain data[cite: 168, 171, 173].



### Results
* [cite_start]**Performance:** The final configuration (U-Net++ + PAN + SE + Augmentation) achieved a Mean IoU (**mIoU**) of **0.63753**[cite: 205, 208].

---

## 🛠 Tech Stack
* **Frameworks:** TensorFlow, Keras.
* [cite_start]**Libraries:** KerasCV (Data Augmentation), NumPy, Matplotlib[cite: 64].
* **Core Techniques:** Transfer Learning, Fine-Tuning, Semantic Segmentation, Multi-scale Feature Fusion.

---

## 📂 Repository Structure
```text
├── Homework 1/
│   ├── AN2DL_HW1_BloodCellClassification.ipynb  # Optimized Notebook
│   └── AN2DL_Homework_1_Report.pdf              # Technical documentation
├── Homework 2/
│   ├── AN2DL_HW2_MarsTerrainSegmentation.ipynb  # Optimized Notebook
│   └── AN2DL_Homework_2_Report.pdf              # Technical documentation
└── README.md
