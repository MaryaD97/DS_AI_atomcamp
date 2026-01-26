# Disaster Tweets Classification – NLP Portfolio Project

## Project Overview

This project focuses on building a complete Natural Language Processing (NLP) pipeline to classify tweets as either disaster-related or non-disaster-related. The objective is to understand how raw text data can be transformed into meaningful numerical representations and how different modeling approaches perform on a real-world text classification problem.

The project follows a structured learning-based approach, starting from text preprocessing and feature engineering to traditional machine learning models, word embedding exploration, and a simple deep learning model. The emphasis is on clarity, correctness, and conceptual understanding rather than overly complex architectures.

---

## Dataset Description

The dataset is sourced from the Kaggle competition **“Natural Language Processing with Disaster Tweets”**. It consists of short tweets labeled to indicate whether they describe a real disaster or not.

Each tweet includes:
- An ID
- The tweet text
- Optional keyword and location fields
- A target label (0 = not a disaster, 1 = disaster)

Only the training dataset is used for model development and evaluation, following proper machine learning practices.

Dataset link:  
https://www.kaggle.com/competitions/nlp-getting-started/data

---

## Project Structure

├── data/  
│   ├── train.csv  
│   ├── test.csv  
│   └── sample_submission.csv  
│  
├── notebook/  
│   └── Maryam_Rizwan_nlp.ipynb  
│  
└── README.md  

The notebook contains the complete end-to-end NLP pipeline, including data preprocessing, feature engineering, modeling, evaluation, and analysis.  
The `data` folder holds the original dataset files used in the project.  
All analysis, modeling, and explanations are consolidated in a single, well-documented notebook for clarity and reproducibility.

---

## Methodology

The project is structured into the following main steps:

### 1. Understanding the Problem
The task is framed as a binary text classification problem, with the goal of predicting whether a tweet refers to a real disaster. The informal and noisy nature of social media text makes this a challenging NLP task.

### 2. Text Preprocessing
Text data is cleaned and normalized using steps such as:
- Lowercasing
- Removing punctuation and special characters
- Tokenization
- Stopword removal

These steps reduce noise while preserving meaningful information.

### 3. Feature Engineering
Two traditional text representation techniques are implemented:
- **Bag of Words (BoW)**
- **TF-IDF**

These representations convert text into numerical feature vectors suitable for machine learning models.

### 4. Word Embedding Exploration
To move beyond sparse representations, word embeddings are explored using an embedding layer. Dimensionality reduction (PCA) is applied to visualize embeddings and observe semantic relationships between words. This section focuses on understanding how embeddings capture meaning rather than optimizing performance.

### 5. Model Development
Both traditional and deep learning models are implemented:
- Logistic Regression (BoW and TF-IDF)
- Naive Bayes (BoW and TF-IDF)
- A simple deep learning model using word embeddings

The deep learning model is intentionally kept simple to emphasize the role of embeddings rather than architectural complexity.

### 6. Model Evaluation and Comparison
Models are evaluated using validation accuracy, classification reports, and confusion matrices. A unified comparison table is used to compare all models in a consistent manner.

---

## Results Summary

All models achieve comparable performance, with validation accuracy ranging from approximately 78% to 81%. TF-IDF-based models consistently outperform Bag of Words representations. The deep learning model using word embeddings achieves the highest accuracy, though the improvement over traditional models is modest.

This indicates that feature representation plays a crucial role in text classification and that simpler models can remain competitive on smaller, noisy datasets such as tweets.

---

## Steps to Run the Project

1. Clone the repository:
   ```bash
   git clone <repository-url>
   
2. Navigate to the project directory:
cd disaster-tweets-nlp

3. Ensure the required Python libraries are installed:
   - pandas
   - numpy
   - scikit-learn
   - nltk
   - matplotlib
   - tensorflow

4. Open the notebook:
   - Using Jupyter Notebook or JupyterLab  
   **OR**
   - Upload the notebook to Google Colab

5. Run the notebook cells sequentially from top to bottom to reproduce the results.
