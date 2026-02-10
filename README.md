# Artificial Neural Networks and Deep Learning Projects [2024-2025]

This repository contains the projects developed for the **AN2DL** course at **Politecnico di Milano**. The work is focused on two main Computer Vision challenges: multi-class image classification and semantic segmentation using advanced Deep Learning architectures.

## 👥 Authors
* **Valeria de Gennaro**
* **Donato Fiore**
* **Lorenzo Fonnesu**
* **Gabriele Lorenzetti**

---

## 🩸 Homework 1: Blood Cell Classification
**Goal:** Categorize 96x96 RGB images of blood cells into eight distinct classes (Basophil, Eosinophil, Erythroblast, Immature granulocytes, Lymphocyte, Monocyte, Neutrophil, Platelet).

### Technical Overview
* **Dataset Cleaning:** The initial dataset of 13,759 images was cleaned of 1,800 out-of-context images and 8 duplicates to ensure training stability.
* **Model Architecture:** We utilized **ConvNeXtBase** as the primary backbone, which outperformed other tested models like ResNet50 and EfficientNet.
* **Training Strategy:**
    * **Transfer Learning:** Initial training of top layers (GAP, Dense, Dropout) with frozen backbone for 10 epochs.
    * **Fine-Tuning:** Unfreezing layers from the 150th onward using the Adam optimizer with **Cosine Annealing**.
* **Data Augmentation:** An intensive pipeline using `keras_cv` was implemented, including **CutMix**, **Cutout**, and **RandAugment**.



### Results
* **Performance:** The model achieved a final accuracy of **80%** on Codabench, starting from a 20% baseline.

---

## 🪐 Homework 2: Martian Terrain Segmentation
**Goal:** Semantic segmentation of 64x128 grayscale images of the Martian surface into 5 classes: Soil, Bedrock, Sand, Big Rock, and Background.

### Technical Overview
* **Constraint:** As per course rules, all models were **trained from scratch** without relying on any pre-trained weights.
* **Architecture:** A custom **U-Net++** model featuring nested skip connections to improve feature aggregation.
    * **PAN (Path Aggregation Network):** Integrated to better capture local and global contextual information.
    * **SE (Squeeze-and-Excitation):** Modules added to dynamically recalibrate channel-wise feature responses.
* **Loss Functions:** A hybrid loss combining **Focal Loss** and **Dice Loss** was developed to handle the significant class imbalance in the terrain data.



### Results
* **Performance:** The final configuration achieved a Mean IoU (**mIoU**) of **0.60475** on the competition leaderboard.

---

## 🛠 Tech Stack
* **Frameworks:** TensorFlow, Keras.
* **Libraries:** KerasCV (Data Augmentation), NumPy, Matplotlib.
* **Core Techniques:** Transfer Learning, Fine-Tuning, Semantic Segmentation, Multi-scale Feature Fusion.

---

## 📂 Repository Structure
├── [Homework 1/](./Homework%201/)
│   ├── [AN2DL_HW1_BloodCellClassification.ipynb](./Homework%201/AN2DL_HW1_BloodCellClassification.ipynb)
│   └── [AN2DL_Homework_1_Report.pdf](./Homework%201/AN2DL_Homework_1_Report.pdf)
├── [Homework 2/](./Homework%202/)
│   ├── [AN2DL_HW2_MarsTerrainSegmentation.ipynb](./Homework%202/AN2DL_HW2_MarsTerrainSegmentation.ipynb)
│   └── [AN2DL_Homework_2_Report.pdf](./Homework%202/AN2DL_Homework_2_Report.pdf)
├── [LICENSE](./LICENSE)
└── README.md


* 📂 [**Homework 1**](./Homework%201/): **Blood Cell Classification** (8 classes).
    * 📄 [Training Notebook](./Homework%201/AN2DL_HW1_BloodCellClassification.ipynb): Implementation of **ConvNeXtBase** with transfer learning and fine-tuning.
    * 📕 [Technical Report](./Homework%201/AN2DL_Homework_1_Report.pdf): Analysis of data cleaning (1800+ images removed) and results (80% accuracy).
* 📂 [**Homework 2**](./Homework%202/): **Mars Terrain Segmentation** (5 classes).
    * 📄 [Segmentation Notebook](./Homework%202/AN2DL_HW2_MarsTerrainSegmentation.ipynb): Custom **U-Net++** with **PAN** and **SE blocks** trained from scratch.
    * 📕 [Technical Report](./Homework%202/AN2DL_Homework_2_Report.pdf): Documentation on architecture design and hybrid loss (Focal + Dice).
* ⚖️ [**MIT License**](./LICENSE): Terms of use for this repository.
