# Japanese Vocabulary Ranker Training 🇯🇵📈

This repository contains the training pipeline for a machine learning model designed to predict the **"知っている" (Familiarity Index)** of Japanese words. The model maps vocabulary to a continuous difficulty scale, enabling automated ranking and personalized content selection for language learners.

## 🚀 Overview
The core objective is to quantify how "familiar" a word is to a native speaker. By using the [WLSP-Familiarity (v4.0)](https://github.com/masayu-a/WLSP-familiarity) dataset from the National Institute for Japanese Language and Linguistics (NINJAL), this model learns to estimate word difficulty based on:
1.  **Semantics:** 300D FastText embeddings (pre-trained on Japanese web corpora).
2.  **Structure:** Morphological features like word length, Kanji density, and Hiragana count.

This project is a critical component of the **Anki Word Generator** ecosystem, ensuring that generated flashcards match the user's target JLPT level.

## 🛠️ Tech Stack
* **Framework:** PyTorch (Neural Network Regressor)
* **Embeddings:** FastText (`cc.ja.300.bin`)
* **Data Processing:** Pandas, NumPy, Scikit-learn (MinMax Scaling)
* **Linguistics:** Regular Expressions for Kanji/Kana extraction

## 📊 Key Features & Methodology
* **Log-Normal Transformation:** Applied to the target variable to stabilize training and improve predictions across rare vocabulary.
* **Hybrid Feature Fusion:** Concatenates high-dimensional semantic vectors with structural metadata.
* **Evaluation:** Achieved a **Spearman Rank Correlation of 0.625**, demonstrating strong performance in ranking words by actual perceived difficulty.

<img width="1558" height="744" alt="image" src="https://github.com/user-attachments/assets/8360d208-b45b-4bf6-8da5-183e05b0299a" />

## 📈 Model Performance
The model demonstrates high precision specifically in the **JLPT N3–N2** range, effectively distinguishing between common conversational Japanese and academic terminology.

<img width="579" height="1011" alt="image" src="https://github.com/user-attachments/assets/3b211391-2d08-4cef-a8f7-6dd83469a838" />

## 📝 License
- **Code**: Licensed under the [MIT License](LICENSE).
- **Dataset**: This project uses the **WLSP-Familiarity** dataset by NINJAL, licensed under [CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/deed.ja).
