<div align="center">

<h1>🛒 Amazon Product Recommendation System</h1>

<p><em>Building intelligent product recommendations using collaborative filtering and matrix factorization on 7.8M Amazon Electronics ratings</em></p>

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![scikit-surprise](https://img.shields.io/badge/Surprise-FF6B6B?style=for-the-badge&logo=scipy&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)

[![Dataset](https://img.shields.io/badge/📊_Dataset-Download_on_Kaggle-4CAF50?style=flat-square&logo=kaggle)](https://www.kaggle.com/datasets/vibivij/amazon-electronics-rating-datasetrecommendation)
[![Notebook](https://img.shields.io/badge/📓_Notebook-Open_in_Jupyter-F37626?style=flat-square)](Recommendation_Systems_Learner_Notebook_Low_Code_updated.ipynb)
[![Presentation](https://img.shields.io/badge/📑_Presentation-View_Slides-2196F3?style=flat-square)](SydneeSampsonBlackwell-Amazon%20Product%20Recommendation%20System%20Presentation%203.1.26.pptx.pdf)

</div>

---

## 📌 Overview

> **Role:** Data Science Manager at Amazon  
> **Goal:** Build a recommendation engine that suggests products to customers based on their past ratings of other products — no product metadata, no review text, just signals from user behavior.

E-commerce giants like Amazon, Walmart, and Etsy spend millions on personalized recommendation systems. This project implements and compares three distinct recommendation approaches on Amazon's Electronics dataset, from simple popularity-based ranking to advanced matrix factorization.

---

## 📂 Project Assets

| Asset | Description |
|---|---|
| [📓 Learner Notebook](Recommendation_Systems_Learner_Notebook_Low_Code_updated.ipynb) | Full end-to-end analysis and model implementation |
| [📊 Electronics Ratings Dataset](https://www.kaggle.com/datasets/vibivij/amazon-electronics-rating-datasetrecommendation) | 7.8M user-product ratings hosted on Kaggle (no headers — see schema below) |
| [📑 Project Presentation](SydneeSampsonBlackwell-Amazon%20Product%20Recommendation%20System%20Presentation%203.1.26.pptx.pdf) | Summary slides with findings and recommendations |

---

## 🗄️ Dataset

**File:** `ratings_Electronics.csv` — 304 MB, 7,824,482 rows, no header row

| Column | Description |
|---|---|
| `userId` | Unique identifier for each customer |
| `productId` | Unique identifier for each product |
| `Rating` | Product rating (1.0 – 5.0) |
| `timestamp` | Unix timestamp of the rating *(not used in modeling)* |

> **Note:** The dataset was filtered down to ~65,000 observations of users with sufficient interaction history before modeling.

---

## 🧠 Models Implemented

### 〔1〕 Rank-Based Recommendation System

> *Popularity wins — recommend what everyone loves.*

A baseline model that ranks products by average rating, filtered by a minimum number of interactions. Two variants:
- Top 5 products with **≥ 50** user interactions
- Top 5 products with **≥ 100** user interactions

No personalization — same recommendations for every user. Useful as a cold-start solution for new users.

---

### 〔2〕 Collaborative Filtering (User-User & Item-Item)

> *"Users like you also bought..." — powered by KNN.*

Uses the **Surprise** library with `KNNBasic` to build similarity-based models:

- **User-User:** Finds users with similar rating histories and recommends products they liked
- **Item-Item:** Finds products that tend to be rated similarly and cross-recommends

Both models were hyperparameter-tuned via `GridSearchCV`, and evaluated using **Precision@k**, **Recall@k**, and **F1@k**.

---

### 〔3〕 Matrix Factorization (SVD)

> *Decompose the ratings matrix to uncover hidden preference patterns.*

Implements **Singular Value Decomposition (SVD)** via the Surprise library to factorize the sparse user-product ratings matrix into latent factors. Hyperparameters tuned with `GridSearchCV` to minimize RMSE.

---

## 📊 Evaluation

Models are compared on:
- **RMSE** (Root Mean Square Error) — how close predicted ratings are to actual
- **Precision@k / Recall@k / F1@k** — relevance of the top-k recommendations

---

## 🚀 Getting Started

This notebook was built for **Google Colab** due to the `surprise` library's installation requirements.

```bash
# 1. Clone the repo
git clone https://github.com/your-username/amazon-product-recommendation-system.git

# 2. Open the notebook in Google Colab
# Upload Recommendation_Systems_Learner_Notebook_Low_Code_updated.ipynb
# Upload ratings_Electronics.csv to your Google Drive

# 3. Run cells sequentially from top to bottom
```

> ⚠️ Run cells in order — the notebook installs specific numpy/surprise versions at the top that must be applied before the rest of the code runs.

---

## 🛠️ Tech Stack

- **Python** — core language
- **Pandas / NumPy** — data manipulation
- **Matplotlib / Seaborn** — exploratory visualization
- **scikit-surprise** — collaborative filtering & SVD models
- **Google Colab** — execution environment

---

<div align="center">

**Sydnee Sampson Blackwell** · Amazon Product Recommendation System · 2026

</div>
