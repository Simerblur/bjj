# Planning for the project

1. **Exploratory data analysis & cleaning**
   - Descriptive statistics and distributions for key variables.
   - Correlation analysis.
   - Handling missing values, outliers, inconsistent categories and duplicates.

2. **Feature engineering**
   - Maybe one hot or other encoding for categorical variables (like genre)
   - Scaling/normalizing numerical features.
   - Creating new features. WATCH OUT FOR LEAKAGE

3. **Dimensionality reduction / feature Selection**
   - Applying a matrix decomposition method (like PCA)
   - Keeping components that explain most variance and/or improve model performance.

4. **Dataset splits**
   - Creating **train**, **validation** and **test** sets
   - WATCH OUT FOR DATA LEAKAGE AGAIN

5. **Modeling and hyperparameter tuning**
   - Baseline model like logistic regression or KNN
   - Random forest (also do gridsearch here)
   - Neural network 

6. **Model evaluation & selection**
   - Evaluating all models on either F1, MSE or another metric
   - Compare the performace and select the best model (ALSO on explainability)

7. **Explainability**
-   SHAP ! Whatever this is but lets use shap

8. **Clusters** BONUS
   - Using a transformer (LIKE BERT)
