<div align="center">

# 🛒 Amazon Product Recommendation System

### Collaborative Filtering · Matrix Factorization · E-Commerce Analytics

*Building intelligent product recommendations using 7.8M Amazon Electronics ratings — from popularity-based baselines to SVD-powered personalization.*

<br>

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![scikit-surprise](https://img.shields.io/badge/Surprise-FF6B6B?style=for-the-badge&logo=scipy&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)

<br>

![Ratings](https://img.shields.io/badge/Ratings-7.8M-blueviolet?style=flat-square)
![Filtered Dataset](https://img.shields.io/badge/Filtered_Dataset-65K_observations-blue?style=flat-square)
![Models](https://img.shields.io/badge/Models_Built-3-orange?style=flat-square)
![Category](https://img.shields.io/badge/Category-Electronics-green?style=flat-square)

<br>

</div>

---

## 📁 Project Assets

| Asset | Description |
|:---|:---|
| 📓 [Analysis Notebook](Recommendation_Systems_Learner_Notebook_Low_Code_updated.ipynb) | Full EDA, collaborative filtering, and SVD model implementation |
| 📊 [Dataset on Kaggle](https://www.kaggle.com/datasets/vibivij/amazon-electronics-rating-datasetrecommendation) | 7.8M user-product Electronics ratings (hosted externally — too large for GitHub) |
| 📑 [Presentation Deck](SydneeSampsonBlackwell-Amazon%20Product%20Recommendation%20System%20Presentation%203.1.26.pptx.pdf) | Summary slides with findings and recommendations |

---

## 🧠 Business Context

Amazon's recommendation system is one of its most powerful competitive advantages — intelligently predicting what customers want before they search for it. This project takes on that challenge directly.

**Goal:** Build a recommendation engine that suggests Electronics products to customers based on their past ratings — using no product metadata, no review text, just behavioral signals from user activity.

- 🎯 Recommend the right product to the right user at the right time
- 📊 Compare multiple recommendation approaches on real-world scale data
- 🔧 Tune and evaluate models using industry-standard metrics

---

## 📊 Dataset

<div align="center">

**7,824,482 ratings · filtered to ~65,000 · no header row · Electronics category**

</div>

| Column | Description |
|:---|:---|
| `userId` | Unique identifier for each customer |
| `productId` | Unique identifier for each product |
| `Rating` | Product rating (1.0 – 5.0) |
| `timestamp` | Unix timestamp *(not used in modeling)* |

> The full dataset (304 MB) is hosted on Kaggle. Download it and place it in the project root before running the notebook. Data was filtered to users with sufficient interaction history before modeling.

---

## ⚙️ Methodology

<div align="center">

```
EDA  →  Filtering  →  Rank-Based Baseline  →  Collaborative Filtering  →  Matrix Factorization  →  Evaluation
```

</div>

| Step | Action |
|:---:|:---|
| 1 | **EDA** — Rating distributions, user/product interaction counts, sparsity analysis |
| 2 | **Filtering** — Subset to users with sufficient ratings history (~65K observations) |
| 3 | **Baseline Model** — Rank-based recommendations using average rating + minimum interaction threshold |
| 4 | **Collaborative Filtering** — KNNBasic user-user and item-item similarity models via Surprise |
| 5 | **Matrix Factorization** — SVD to decompose the sparse ratings matrix into latent factors |
| 6 | **Tuning** — GridSearchCV for hyperparameter optimization across all models |
| 7 | **Evaluation** — RMSE, Precision@k, Recall@k, F1@k |

---

## 🎯 Results: Three Models

### ![#grey](https://img.shields.io/badge/Model_1-Rank--Based_(Popularity)-607D8B?style=flat-square)
> ⭐ No personalization — recommends universally top-rated products above a minimum interaction threshold

Two variants: **top 5 products with ≥ 50 interactions** and **top 5 with ≥ 100 interactions**. Useful as a cold-start solution for new users with no rating history.

<br>

### ![#blue](https://img.shields.io/badge/Model_2-Collaborative_Filtering_(KNN)-1565C0?style=flat-square)
> 👥 "Users like you also bought..." — powered by user-user and item-item KNN similarity

- **User-User:** Finds users with similar rating histories and recommends products they liked
- **Item-Item:** Finds products rated similarly and cross-recommends
- Tuned via GridSearchCV; evaluated with Precision@k, Recall@k, F1@k

<br>

### ![#purple](https://img.shields.io/badge/Model_3-Matrix_Factorization_(SVD)-6A1B9A?style=flat-square)
> 🔢 Decomposes the sparse ratings matrix to uncover hidden preference patterns

SVD factorizes the user-product matrix into latent factors, capturing nuanced taste signals that explicit similarity measures miss. Hyperparameters tuned to minimize RMSE.

---

## 💡 Key Findings

| Finding | Insight |
|:---|:---|
| 📈 Sparsity is extreme | 7.8M ratings across millions of users and products — most user-product pairs are unrated |
| 🔢 SVD handles sparsity best | Matrix factorization outperforms similarity-based approaches on sparse data |
| 🌟 Cold-start gap is real | New users benefit most from rank-based recommendations until sufficient ratings accumulate |
| 🔧 Tuning moves the needle | Optimized models showed meaningful RMSE improvement over out-of-the-box baselines |

---

<div align="center">

*Built with Python · pandas · NumPy · matplotlib · seaborn · scikit-surprise · Google Colab*

</div>
