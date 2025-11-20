# 📰 Fake News Classifier

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML%20Models-orange.svg)
![NLP](https://img.shields.io/badge/NLP-TF--IDF%20%7C%20Text%20Processing-green.svg)
![Project](https://img.shields.io/badge/Project-Fake%20News%20Classifier-purple.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

A clean-tech Machine Learning project for detecting **real vs fake news** using short text headlines.

---

## 🔥 Overview
This project builds a high‑performance ML classifier capable of distinguishing **fake news (0)** from **real news (1)** based solely on short headlines.

The workflow includes:
- Dataset exploration
- Text preprocessing
- Feature engineering (TF‑IDF)
- Model comparison
- Hyperparameter tuning
- Generating predictions for the test dataset

Achieved up to **94% accuracy** using classical ML techniques.

---

## 📦 Dataset
### **Training Data**
- 34,152 headlines
- Labels: `0 = fake`, `1 = real`
- Balanced classes
- Short, political, emotion‑driven text

### **Test Data**
- 9,984 headlines
- Label is always `2` → meaning "unknown"
- Your task: replace `2` with model predictions (`0` or `1`)
- Must preserve:
  - No header
  - Tab separator
  - Column order: `label \t headline`

---

## 🛠 Preprocessing
Applied preprocessing steps:
- Lowercasing
- Tokenization
- Stopword removal
- Punctuation removal
- Optional: Lemmatization
- Vectorization using **TF‑IDF (1–2 grams)**

Why TF‑IDF?
- Works extremely well for short text
- Highlights important word patterns
- Supports n‑grams to capture phrases ("breaking news", "experts say")

---

## 🧱 Feature Engineering
TF‑IDF configuration:
- `ngram_range = (1, 2)`
- `min_df = 2` (remove rare noise tokens)
- `max_df = 0.85` (remove overly frequent words)
- Produces high‑dimensional sparse vectors

---

## 🤖 Models Evaluated
| Model | Notes |
|-------|-------|
| Logistic Regression | Strong baseline, fast training |
| Linear SVC | Best baseline performance |
| Multinomial Naive Bayes | Good for text, slightly worse here |
| Random Forest | Struggles with sparse vectors |

Hyperparameter tuning performed via **RandomizedSearchCV** for Logistic Regression.

---

## 🏆 Model Performance
### **Best overall model:** Linear SVC (baseline)
- Accuracy: **94.69%**

### **Best tuned model:** Logistic Regression
- Accuracy: **94.00%**

Both models generalize well and produce balanced precision/recall.

---

## 📊 Final Predictions
Final workflow:
1. Retrain the best model (Logistic Regression or SVC) on **all training data**.
2. Predict label for each headline in `testing_data.csv`.
3. Replace the original label `2` with `0` or `1`.
4. Save as **testing_predictions.csv** with:
   - No header
   - Tab-separated
   - Columns: `label`, `headline`

---

## 🧪 Confusion Matrix (Tuned Logistic Regression)
```
[[3296  219]
 [ 191 3125]]
```
Accuracy: **94.00%**

Shows strong balance between classes and low misclassification.

---

## 🚀 Future Improvements
- Use Transformer models (BERT, DistilBERT)
- Add sentiment features
- Try topic modeling (LDA)
- Explore ensemble methods
- Apply model explainability (LIME / SHAP)

---

## 📁 Repository Structure
```
📂 FakeNewsClassifier
│── 📁 dataset
│   ├── training_data.csv
│   ├── testing_data.csv
│
│── 📄 fake_news_classifier.ipynb
│── 📄 testing_predictions.csv
│── 📄 README.md
```

---

## 🧠 Key Takeaways
- Classical ML can outperform complex models with strong preprocessing.
- TF‑IDF with n‑grams is extremely effective for headline classification.
- SVC and Logistic Regression remain state‑of‑the‑art for sparse text.
- Proper validation, tuning, and formatting are critical for real submissions.

---

## ✨ Author
Project developed by **Diogo Simões, Javier Garcia and Keberth Rodriguez ** as part of the Ironhack Data Science Bootcamp.


