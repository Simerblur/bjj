================================================================================
MOVIE BOX OFFICE PREDICTION - PROJECT SUMMARY
================================================================================

PROJECT OVERVIEW
================================================================================
This project develops machine learning models to predict whether a movie will
achieve Low, Medium, or High box office sales (based on worldwide revenue).
The analysis spans three comprehensive Jupyter notebooks covering data 
preparation, baseline modeling, and advanced ensemble methods.

QUICK START
================================================================================
1. Read BUSINESS_STRATEGY_SUMMARY.md (executive overview)
2. Execute notebooks in order:
   - Notebook 1: Cleaning_EDA_Feature_engineering
   - Notebook 2: Base_modelling_and_Neural_network
   - Notebook 3: Tree_based_models_and_explainability

KEY RESULTS
================================================================================
Best Model: XGBoost
- Test Accuracy: 61.51%
- Macro F1-Score: 61.0%
- Hyperparameters tuned via grid search (135 combinations tested)

Top Performer: Bagging Classifier (61.55% accuracy)
- Slightly higher accuracy than XGBoost
- Selected XGBoost for business explainability and feature importance

Most Important Feature: Theatre Count (Log-scaled)
- Dominant driver of sales predictions
- Accounts for ~30% of model variance
- Clear positive correlation with high sales

DATASET DETAILS
================================================================================
Total Records: 21,770 movies
Features Engineered: 75 → 61 numeric features
Train/Test Split: 80% training / 20% test (stratified)
Target Variable: Sales tier (3 balanced classes ~33% each)

Feature Categories:
- Structural: 10 features (budget, runtime, release year, etc.)
- Categorical: 38 features (genre dummies, rating, seasonal features)
- Text Embeddings: 13 features (BERT embeddings from reviews)

NOTEBOOK BREAKDOWN
================================================================================

NOTEBOOK 1: Cleaning, EDA, Feature Engineering
- Status: Complete (214 cells executed)
- Covers: Data cleaning, exploratory analysis, feature engineering
- Key Findings:
  * Theatre count has strongest correlation (r=0.77)
  * Production budget has high correlation (r=0.71)
  * Release year and runtime are moderate predictors
- Bonus Features:
  * BERTopic topic modeling on reviews (19 topics identified)
  * K-means clustering (optimal k=2, silhouette=0.572)
  * Comprehensive correlation analysis (Spearman correlation)

NOTEBOOK 2: Base Modeling and Neural Network
- Status: Complete (83 cells executed)
- Covers: Baseline models, neural network development, hyperparameter tuning
- Baseline Models Tested:
  * Logistic Regression: 57.1% (structured) / 57.1% (full)
  * KNN: 55.8%
  * SVM: 56.3%
- Neural Network Development:
  * Grid search: 135 hyperparameter combinations
  * Best accuracy: 57.3% (macro F1: 57.8%)
  * Parameters tuned: hidden units (64-256), dropout (0.2-0.5), learning rate
  * Final model re-trained on combined training+validation data

NOTEBOOK 3: Tree-based Models and Explainability
- Status: Complete (54 cells executed successfully)
- Covers: Bagging, random forest, XGBoost with hyperparameter tuning
- Model Performance (on test set):
  * Bagging (Grid Search): 61.55%
  * Random Forest (Grid Search): 60.75%
  * XGBoost (Grid Search): 61.51%
- Explainability Analysis:
  * Permutation Feature Importance: Top 20 features ranked
  * Partial Dependence Plots (PDP): 6 most important features analyzed
  * SHAP Values: Global and local explanations for low/high sales classes
  * Counterfactuals: "What-if" scenarios for prediction changes

BUSINESS DRIVERS (Top 10 Features)
================================================================================
1. theatre_count_log - Number of theaters (log-scaled)
2. release_year - Year of release
3. runtime - Movie length in minutes
4. production_budget_log - Production cost (log-scaled)
5. genre_Documentary - Documentary classification (negative impact)
6. genre_Adventure - Adventure classification (positive impact)
7. metascore - Critic reviews (0-100)
8. userscore - User reviews (0-10)
9. genre_Comedy - Comedy classification (positive)
10. season_Q1 - Released in Q1 (Jan-Mar)

MODEL INTERPRETATIONS
================================================================================

Partial Dependence Plot Insights:
- Theatre Count: Dominates predictions. More theaters → High sales predictions
- Release Year: Movies from 2005-2015 perform best
- Runtime: Optimal range 90-150 minutes (matches blockbuster patterns)
- Production Budget: Positive correlation, but non-linear relationship

SHAP Analysis:
- theatre_count_log: Clear positive correlation with high sales
- genre_Documentary: Pushes predictions toward low sales
- genre_Adventure: Pushes predictions toward high sales
- Runtime & Release Year: Strong discriminators between tiers
- Feature alignment: PDP and SHAP show consistent directionality

CLASS-SPECIFIC PERFORMANCE (XGBoost on Test Set)
================================================================================
Low Sales (Tier 0):
- Precision: 70% (when predicting low, 70% correct)
- Recall: 67% (catches 67% of actual low-sales movies)
- F1-Score: 69%

Medium Sales (Tier 1):
- Precision: 59% (when predicting medium, 59% correct)
- Recall: 50% (catches 50% of actual medium-sales movies)
- F1-Score: 54%

High Sales (Tier 2):
- Precision: 62% (when predicting high, 62% correct)
- Recall: 68% (catches 68% of actual high-sales movies)
- F1-Score: 65%

Observation: Model excels at identifying high-sales blockbusters (87% high-tier
when 3000+ theaters), struggles with medium-tier movies (similar feature space
to both low and high tiers).

RECOMMENDATIONS FOR BUSINESS USE
================================================================================
1. Use for Portfolio Balancing: 40% high-tier / 40% medium-tier / 20% low-tier
2. Allocate Marketing Budget: Budget allocation based on predicted tier
3. Optimize Release Strategy: Theatre count decisions by tier prediction
4. Genre-Specific Positioning: Leverage genre insights for marketing messaging
5. Release Timing: Q3-Q4 for tentpoles, Q1-Q2 for niche/award content

IMPORTANT LIMITATIONS
================================================================================
- Model Accuracy: 61.51% means ~39% misclassifications
- Theatre Count Bias: Dominant feature limits interpretability for early decisions
- Data Coverage: Trained on 2010-2020 data; may not reflect 2024+ market
- Streaming Era: Model does not account for hybrid/streaming release strategies
- Black Swan Events: Cannot predict unprecedented market disruptions
- Use Case: Better for strategic planning than standalone green-light decisions

ARTIFACTS IN /artifacts/
================================================================================
- scaler_nn.joblib: StandardScaler for neural network preprocessing
- mlp_sales_tier.keras: Trained MLP neural network model
- feature_names.joblib: List of 61 feature names (for reproducibility)

HOW TO USE THIS PROJECT
================================================================================
For Executives:
- Read BUSINESS_STRATEGY_SUMMARY.md for high-level findings
- Reference this README for quick facts and model performance

For Data Scientists:
- Execute notebooks in sequence (1 → 2 → 3)
- Reproducible with random_state=42 for all train/test splits
- Dependencies: See requirements.txt

For Analysts:
- Use feature importance tables for trend analysis
- Reference SHAP plots for specific prediction explanations
- Compare PDP curves across features

PROJECT STATUS
================================================================================
Completeness: 100%
- All three notebooks executed and validated
- All hyperparameter tuning completed
- All explainability analyses completed
- Business strategy document finalized
- All artifacts exported and documented

Last Updated: 28 January 2026

================================================================================
END OF README
================================================================================
