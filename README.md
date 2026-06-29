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

### Dataset Features

| Column | Description |
|--------|-------------|
| `reviewId` | Unique identifier for each review |
| `userName` | Name of the reviewer |
| `userImage` | Profile image URL of the reviewer |
| `content` | The review text content |
| `score` | Star rating (1-5) given by user |
| `thumbsUpCount` | Number of helpful votes |
| `reviewCreatedVersion` | App version when review was posted |
| `at` | Timestamp of the review |
| `replyContent` | Developer's reply to the review (if available) |
| `repliedAt` | Timestamp of developer's reply |
| `appVersion` | Current app version |

---

## Project Objectives

1. **Sentiment Classification**: Classify user reviews into positive, neutral, and negative sentiments
2. **Text Understanding**: Extract meaningful patterns from Indonesian language reviews
3. **Model Performance**: Achieve high accuracy in sentiment prediction
4. **Deployment**: Provide a trained model for real-time sentiment analysis

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

## Model Architecture

### LSTM Neural Network

The project uses a **Long Short-Term Memory (LSTM)** deep learning model suitable for sequence analysis:

```
Input Layer
    ↓
Embedding Layer (word embeddings)
    ↓
LSTM Layer (128 units) [captures sequential patterns]
    ↓
Dropout Layer (0.5) [regularization to prevent overfitting]
    ↓
Dense Layer (64 units, ReLU activation)
    ↓
Dropout Layer (0.5)
    ↓
Output Dense Layer (3 units, Softmax) [sentiment classification]
```

### Key Components

- **Embedding Layer**: Converts text tokens to dense vectors
- **LSTM Units**: Captures long-term dependencies in text sequences
- **Dropout Regularization**: Prevents overfitting with L2 regularization
- **Softmax Output**: Produces probability distribution across 3 sentiment classes

---

## Technologies & Libraries

### Core Dependencies

| Library | Purpose |
|---------|---------|
| `TensorFlow/Keras` | Deep learning framework for model building |
| `NLTK` | Natural Language Toolkit for text processing |
| `Sastrawi` | Indonesian stemmer for text normalization |
| `Scikit-learn` | Machine learning utilities (preprocessing, metrics) |
| `Pandas` | Data manipulation and analysis |
| `NumPy` | Numerical computing |
| `Matplotlib/Seaborn` | Data visualization |
| `google-play-scraper` | Scraping reviews from Google Play Store |

For a complete list, see [requirements.txt](requirements.txt)

---

## Model Evaluation

The model is evaluated using multiple metrics:

### Performance Metrics
- **Accuracy**: 85%

### Classification Report
```
              precision    recall  f1-score  
    Positive       0.89      0.76      0.82      
     Neutral       0.65      0.78      0.71      
    Negative       0.94      0.91      0.91      

```

### Confusion Matrix
<img width="529" height="413" alt="image" src="https://github.com/user-attachments/assets/db9d11a5-adb2-4117-bcfd-043610569e82" />

## Key Findings & Insights

- Successfully classified 10,000 Dana app reviews into three sentiment categories
- Preprocessing pipeline effectively handles Indonesian language nuances
- LSTM architecture captures sentiment patterns in review sequences
- Model demonstrates strong performance in distinguishing positive, neutral, and negative reviews
- Identifies common complaints and praise points from user feedback
