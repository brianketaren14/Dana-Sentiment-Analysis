# Dana Sentiment Analysis Project

## Project Overview

This project focuses on classifying sentiments of user reviews from Google Play Store for **Dana**, one of Indonesia's leading digital wallets. The application can be used for saving money, transferring funds, and paying bills. By analyzing user sentiments, we can understand customer satisfaction and identify areas for improvement.

---

## Dataset

- **Source**: Google Play Store (Dana Application - ID: `id.dana`)
- **Total Reviews**: 10,000 user reviews
- **Language**: Indonesian
- **Sentiment Classes**: 3 categories
  - **Positive**: Satisfied users expressing praise
  - **Neutral**: Balanced opinions or factual statements
  - **Negative**: Dissatisfied users expressing complaints

---

## Text Preprocessing Pipeline

The project implements a comprehensive text preprocessing pipeline with the following steps:

### 1. **Text Cleaning** (`cleaningText`)
- Removes mentions (@username) and hashtags
- Eliminates links and special characters
- Removes numbers and non-alphanumeric characters
- Replaces newlines with spaces
- Strips excess punctuation and whitespace

### 2. **Case Folding** (`casefoldingText`)
- Converts all characters to lowercase
- Ensures consistency (e.g., "Good" and "good" treated equally)

### 3. **Tokenization** (`tokenizingText`)
- Splits text into individual tokens (words)
- Prepares text for word-level processing

### 4. **Stopword Filtering** (`filteringText`)
- Removes Indonesian and English stopwords
- Filters custom stopwords: "iya", "yaa", "gak", etc.
- Retains only meaningful words contributing to sentiment

### 5. **Stemming** (`stemmingText`)
- Uses Sastrawi Indonesian stemmer
- Reduces words to root form (e.g., "berlari" → "lari")
- Normalizes word variations

### 6. **Sentence Reconstruction** (`toSentence`)
- Joins processed tokens back into readable text
- Provides clean, processed reviews for model input

---

## Model Evaluation

The model is evaluated using multiple metrics:

### Performance Metrics
- **Accuracy**: 84%

### Classification Report
```
           precision    recall  f1-score   support

    negative       0.85      0.79      0.82       363
     neutral       0.66      0.76      0.71       513
    positive       0.93      0.88      0.90      1124

    accuracy                           0.84      2000
   macro avg       0.81      0.81      0.81      2000
weighted avg       0.84      0.84      0.84      2000  

```

### Confusion Matrix
<img width="650" height="547" alt="image" src="https://github.com/user-attachments/assets/65b03f7f-975e-4074-bcfc-43d682bf98c2" />


## Key Findings & Insights

- Successfully classified 10,000 Dana app reviews into three sentiment categories
- Preprocessing pipeline effectively handles Indonesian language nuances
- LSTM architecture captures sentiment patterns in review sequences
- Model demonstrates strong performance in distinguishing positive, neutral, and negative reviews
- Identifies common complaints and praise points from user feedback
