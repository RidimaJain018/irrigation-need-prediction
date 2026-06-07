Irrigation Need Prediction
A multi-class classification project that predicts crop irrigation need — Low, Medium, or High — based on agricultural and environmental features. Built for a Kaggle-style tabular competition using LightGBM with systematic feature engineering.

Problem Statement
Given crop, soil, region, and weather-related features, predict the level of irrigation a crop requires. This is a 3-class classification task with real-world relevance for smart, water-efficient farming.
Target: Irrigation_Need → Low | Medium | High

Repository Structure
irrigation-need-prediction/
│
├── irrigation.ipynb       
└── README.md

Dataset
The dataset is sourced from a Kaggle Playground Series competition and is not included in this repo due to competition terms.
To run this notebook:

Download train.csv and test.csv from the competition page on Kaggle.
Place both files in the root directory alongside the notebook.


Approach
1. Feature Engineering

Soil × feature crosses — Soil_Type crossed with Crop_Type, Crop_Growth_Stage, Season, Irrigation_Type, and Region
Stage-Irrigation cross — Crop_Growth_Stage + Irrigation_Type as a combined feature
14 pairwise categorical interactions — across crop, season, region, water source, and irrigation type
Binary encoding — Mulching_Used (Yes/No → 1/0)

2. Encoding Strategy

Target Encoding on all interaction and cross features — captures mean target signal without cardinality explosion
One-Hot Encoding on base categorical columns (Soil_Type, Season, Region, Irrigation_Type, Water_Source, Crop_Growth_Stage)

3. Models
ModelNotesLogistic RegressionBaseline with class_weight='balanced'LightGBMFinal model — n_estimators=1000, learning_rate=0.05, num_leaves=31

Tech Stack
Python · Pandas · NumPy · Scikit-learn · LightGBM · category_encoders

How to Run

Download the dataset from Kaggle and place train.csv and test.csv in the root directory.
Install dependencies:

bashpip install pandas numpy scikit-learn lightgbm category_encoders

Run irrigation.ipynb end-to-end — submission.csv will be generated.

Ridima Jain
