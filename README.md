# Medical Visual Question Answering on VQA-RAD Dataset
## 🎓 Course: WOA7015 - Advance Machine Learning (Alternative Assessment)
**Group 16**
* **Ren Xingwang** (Matrix No: 25069113)
* **Zhang Jiarui** (Matrix No: 24231977)

---

### 🏥 Project Executive Summary
This project presents a comprehensive study of Medical Visual Question Answering (Med-VQA) using the VQA-RAD dataset. We systematically evaluated two distinct deep learning architectures to answer the research question: *Can the global context capabilities of Transformers outperform local CNN features in radiology?*

We developed and compared:
1.  **Baseline Model:** A CNN-based architecture using **ResNet-50** for image encoding and **Bi-LSTM** with GloVe embeddings for question encoding.
2.  **Proposed Model:** A **Vision Transformer (ViT)** based architecture utilizing **BERT** embeddings and a specialized **Cross-Modal Attention** module.

Our results demonstrate that the Vision Transformer significantly outperforms the CNN baseline, achieving a new state-of-the-art accuracy for this specific configuration on the VQA-RAD dataset.

### 📂 Repository Contents
This repository contains the complete deliverables for the project:
* `group16_Final_Report.pdf`: The detailed final report covering methodology, error analysis, and clinical implications.
* `Vision_Transformers_Advance_Medical_Reasoning.pdf`: Presentation slides summarizing the project.
* `ViT_vs_CNN_Medical_VQA.ipynb`: The Jupyter Notebook containing the source code, training pipeline, and visualization scripts.

### 📊 Experimental Results
As detailed in Section 3 of the report, the proposed ViT model achieved superior performance across all metrics.

| Metric / Category | CNN Baseline (ResNet-50 + LSTM) | Proposed ViT (ViT + BERT) | Improvement |
| :--- | :--- | :--- | :--- |
| **Overall Accuracy** | **71.2%** | **76.8%** | **+5.6%** |
| **Binary (Yes/No)** | 78.6% | 85.2% | +6.6% |
| **Open-Ended** | 58.3% | 65.4% | +7.1% |
| **Counting** | 54.2% | 61.8% | +7.6% |
| **Weighted F1-Score**| 0.71 | 0.77 | +0.06 |

> **Key Observation:** The ViT model demonstrated faster convergence and better generalization, showing a significant advantage in capturing global context compared to the CNN baseline.

### 🛠️ Methodology & Architecture
#### 1. CNN-Based Baseline
* **Image Encoder:** Pre-trained ResNet-50 extracting a 2048-dim feature vector.
* **Text Encoder:** Bi-directional LSTM with GloVe word embeddings.
* **Fusion:** Concatenation followed by dense layers.

#### 2. Vision Transformer (ViT) Approach
* **Image Encoder:** ViT dividing images into 16x16 patches to capture global dependencies.
* **Text Encoder:** BERT-based tokenizer and encoder for contextual understanding.
* **Fusion:** A 6-layer **Cross-Modal Attention Module** to explicitly align linguistic terms with visual pathologies.

### 🔍 Analysis & Clinical Implications
* **Diagnostic Value:** The ViT model achieved **85.2% accuracy** on binary questions (e.g., "Is there pneumonia?"), reaching a level acceptable for clinical triage support.
* **Interpretability:** Attention visualization confirms that ViT focuses on relevant anatomical regions (e.g., Right Upper Lobe) corresponding to the question, whereas CNN attention is more diffuse.
* **Limitations:** Both models struggle with **Counting questions** (e.g., "How many ribs?"), suggesting a need for explicit object detection modules (like Faster R-CNN) in future work.

### 👥 Member Contributions
* **Zhang Jiarui:** Spearheaded the ViT architecture design, implemented the Patch Embedding and Cross-Modal Attention mechanisms, and developed the data preprocessing pipeline.
* **Ren Xingwang:** Constructed the CNN-LSTM baseline, managed hyperparameter tuning, conducted comprehensive performance evaluation, and generated visualization artifacts (Training dynamics, Confusion Matrices).

### 🚀 Usage
1.  Open `ViT_vs_CNN_Medical_VQA.ipynb` in Google Colab.
2.  Ensure GPU runtime is enabled.
3.  Run the cells to reproduce the training dynamics and evaluation metrics presented in the report.

---
*Based on the Final Report submitted for WOA7015, January 2026.*
