Hey Git!!

This repository contains my solution to the Spaceship Titanic Kaggle challenge. The notebook covers comprehensive Exploratory Data Analysis (EDA), robust feature engineering, and machine learning modeling.

Key Details:

Model: XGBoost Classifier
Validation Strategy: Stratified K-Fold Cross-Validation (5 folds)
Mean Accuracy Score: 0.80313

Feature Engineering Overview:
The following transformations were applied to the dataset:

1. Group Extraction: Derived a Group feature by extracting the prefix from the PassengerId (e.g., 1234_02 → 1234) to capture possible group-based travel patterns.
2. Cabin Decomposition: Split the Cabin feature into three parts: Deck, Num, and Side, which were then used as independent features.

Spending Aggregates:
1. Filled missing values in all spending columns (RoomService, FoodCourt, ShoppingMall, Spa, VRDeck) with 0.
2. Created TotalSpend and TotalSpend_log as the sum and log-transformed total expenditures.
3. Created a binary feature SpendZero to flag passengers who didn’t spend anything.

Categorical Encoding:
1. Applied one-hot encoding to categorical features: HomePlanet, Destination, Deck, Side, Group

Missing Value Handling:
1. HomePlanet and Destination: filled with most frequent values (Earth, TRAPPIST-1e)
2. CryoSleep and VIP: filled with False and converted to binary (0 or 1)
3. Age and Num: filled with the median
4. Deck and Side: filled with default values (F, S)
5. Dropped Columns: Removed Name and Cabin as they were either redundant or sparsely informative after feature extraction

Summary:
After thorough data preprocessing and feature engineering, I trained an XGBoost model with carefully tuned hyperparameters. The model was evaluated using Stratified K-Fold Cross-Validation to ensure robustness and reduce variance due to class imbalance. It achieved a strong average validation accuracy of 0.80313. All steps, from preprocessing to modeling, are included for full reproducibility.
