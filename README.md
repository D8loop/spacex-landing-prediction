# 🚀 SpaceX Falcon 9 Landing Prediction

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine_Learning-orange.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626.svg)

## 📌 1. Project Context & Business Objective
The commercial space age is here. Companies are making space travel affordable for everyone. SpaceX has a massive competitive advantage: the cost of launching a Falcon 9 rocket is advertised at $62 million, while other providers cost upwards of $165 million. This massive saving is primarily because SpaceX can reuse the first stage.

**The objective of this project (acting as a Data Scientist for a competing startup, "Space Y") is to train a machine learning model to predict whether the Falcon 9 first stage will successfully land, thereby allowing us to accurately estimate the cost of future launches.**

## 📊 2. Dataset Overview
Data was collected through the public SpaceX API and enriched via web scraping from Wikipedia.
* **Core Features:** Payload mass, orbit type, launch site, flight history, and grid fins status.
* **Target Variable:** `Class` (1 = Successful Landing, 0 = Failure/Crashing).

## 🚀 3. Methodology & Pipeline
The project follows a rigorous end-to-end Data Science pipeline divided into 4 core phases:
1. **Data Collection & Cleaning (`01_...`)**: REST API requests, HTTP handling, and BeautifulSoup web scraping.
2. **Exploratory Data Analysis (`02_...`)**: SQL querying for trend isolation and Data Viz (Matplotlib/Seaborn).
3. **Geospatial Analysis (`03_...`)**: Launch site mapping with Folium and interactive dashboarding with Plotly Dash.
4. **Machine Learning (`04_...`)**: Model training and hyperparameter tuning (Logistic Regression, SVM, Decision Trees, KNN).

## 📈 4. Key Results & Model Selection

Following the latest model evaluation on the test set ($N = 18$), Logistic Regression, SVM, and KNN are tied for the top-performing position, each achieving an identical out-of-sample accuracy of **83.33%**.

| Model | Baseline CV Accuracy | Final Test Accuracy | Status |
|---|---|---|---|
| Logistic Regression | 81.96% | 83.33% | Selected Best Model |
| SVM | 84.82% | 83.33% | Tied (Production Alternative) |
| KNN | 83.39% | 83.33% | Tied |
| Decision Tree | 85.89% | 77.78% | Rejected (Overfitting) |

### Operational Recommendation: Logistic Regression
While three models share the exact same confusion matrix profile (correctly classifying 12/12 landings but missing 3/6 failure edge cases), **Logistic Regression** is selected as the optimal model for deployment based on three core factors:
1. **Robust Generalization**: It shows the tightest alignment between training (81.96%) and testing metrics (83.33%), indicating excellent stability.
2. **Engineering Interpretability**: Unlike the "black-box" nature of SVM or distance-based mechanics of KNN, Logistic Regression provides direct, extractable feature weights. This allows telemetry engineers to audit which physical factors most strongly influence landing risks.
3. **Production Efficiency**: The model requires minimal computational overhead, enabling ultra-fast execution during real-time flight data processing.


```markdown
![Matrice de confusion](/outputs/figures/Confusion_Matrix_lr.png)

## 🗂️ 5. Repository Structure
```text
spacex-landing-prediction/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── 01_data_collection_cleaning.ipynb
│   ├── 02_eda_sql_visualizations.ipynb
│   ├── 03_interactive_maps_dash.ipynb
│   └── 04_machine_learning_prediction.ipynb
├── outputs/
│   └── figures/
├── requirements.txt
└── README.md

