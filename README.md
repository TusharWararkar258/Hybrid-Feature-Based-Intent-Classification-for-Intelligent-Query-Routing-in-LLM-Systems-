# Hybrid-Feature-Based-Intent-Classification-for-Intelligent-Query-Routing-in-LLM-Systems-
Hybrid Feature-Based Intent Classifier for NPCYF AI CoPilot | LinearSVC + TF-IDF + Sentence Embeddings | 100% Accuracy | IDEAS-TIH, ISI Kolkata
#  Hybrid Feature-Based Intent Classification for Intelligent Query Routing in LLM Systems

> **Internship Project** | IDEAS-TIH, ISI Kolkata |
> **Period:** 21 Jan 2026 – 31 Mar 2026  
> **Guide:** Kunal Gupta, IDEAS-TIH, ISI Kolkata

---

## 📌 Project Overview

An LLM deployed on an agriculture platform (NPCYF AI CoPilot) receives three very different types of questions:

| Intent Class | Example |
|---|---|
| `database_query` | *"What is the average yield of wheat in Punjab?"* |
| `platform_query` | *"How do I reset my password?"* |
| `general_query` | *"What is photosynthesis?"* |

This project builds a **lightweight intent classifier** that reads the user's question first, labels it as one of the 3 categories, and routes it to the correct handler — preventing the LLM from wasting compute on misrouted queries.

---

## ✅ Results

| Metric | Value |
|---|---|
| Overall Accuracy | **100%** |
| Precision | **1.00** |
| Recall | **1.00** |
| F1-Score | **1.00** |
| Misclassifications | **0 out of 300** |

---

## 🧠 Model & Approach

### Classifier
**LinearSVC (C=1.0)** — Support Vector Machine optimised for high-dimensional text classification

### Feature Pipeline — 3 Parallel Streams

```
Input Question
      │
      ├──► TF-IDF + TruncatedSVD     →  300 features
      ├──► Sentence Embeddings        →  384 features  (all-MiniLM-L6-v2)
      └──► Text Statistics            →    5 features  (char count, word count, etc.)
                                           │
                                    ┌──────▼──────┐
                                    │  689 features │
                                    └──────┬──────┘
                                           │
                                      LinearSVC
                                           │
                              ┌────────────▼────────────┐
                              │  database_query /        │
                              │  platform_query /        │
                              │  general_query           │
                              └─────────────────────────┘
```

### Why LinearSVC?
- ✅ Handles 689-dimensional feature vectors efficiently
- ✅ Maximises margin between classes — ideal for linearly separable intents
- ✅ Trains in seconds on thousands of samples
- ✅ Perfect for routing tasks where hard labels (not probabilities) are needed

---

## 📁 Repository Structure

```
📁 Hybrid-Feature-Based-Intent-Classification/
│
├── 📓 model_training.ipynb          ← Complete training pipeline
├── 📓 model_testing.ipynb           ← Evaluation + interactive tester
│
├── 📊 dataset_complete.xlsx         ← Full labelled dataset (3,840 questions)
├── 📊 dataset_test.xlsx             ← Test set (300 questions, 100 per class)
│
├── 📄 internship_report.docx        ← Full technical report
├── 📊 internship_presentation.pptx  ← Project presentation slides
│
└── 📋 README.md                     ← You are here!
```

> ⚠️ **Model File (PKL):** The trained model `intent_classifier_model.pkl` (95MB) exceeds GitHub's 25MB limit.  
> 📥 **Download it here → [Google Drive Link](https://drive.google.com/file/d/1AKXsolmyyqjxkY6KOCIq1tVFVjwmr8gF/view?usp=sharing)**

---

## 📊 Dataset

| Property | Value |
|---|---|
| Total Questions | **3,840** |
| Classes | 3 (database, platform, general) |
| Test Set Size | 300 (100 per class) |
| Format | XLSX |
| Source | Manually curated for NPCYF AI CoPilot |

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/TusharWararkar258/Hybrid-Feature-Based-Intent-Classification-for-Intelligent-Query-Routing-in-LLM-Systems-.git
cd Hybrid-Feature-Based-Intent-Classification-for-Intelligent-Query-Routing-in-LLM-Systems-
```

### 2. Install Dependencies
```bash
pip install scikit-learn sentence-transformers pandas numpy openpyxl
```

### 3. Download the Model
Download `intent_classifier_model.pkl` from the [Google Drive link](https://drive.google.com/file/d/1AKXsolmyyqjxkY6KOCIq1tVFVjwmr8gF/view?usp=sharing) and place it in the project folder.

### 4. Run Training (Optional)
Open and run `model_training.ipynb` in Jupyter Notebook

### 5. Run Testing
Open and run `model_testing.ipynb` — includes interactive tester where you can type any question and get the predicted intent

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.x | Core language |
| scikit-learn | LinearSVC, TF-IDF, Pipeline |
| sentence-transformers | all-MiniLM-L6-v2 embeddings |
| pandas / numpy | Data handling |
| Jupyter Notebook | Development environment |
| pickle | Model serialisation |

---

## 🏛️ About the Organisation

This project was built during an internship at:

**IDEAS-TIH** — Institute of Data Engineering, Analytics and Science Foundation  
Indian Statistical Institute (ISI), Kolkata  


---

## 👨‍💻 Author

**Tushar Wararkar**

---

## 📄 License

This project was developed as part of an internship at IDEAS-TIH, ISI Kolkata. All rights reserved.
