THE INVESTIGATION OF PIPPY THE CAT – README (ZIP PACKAGE)

This zip contains the notebooks, exported datasets, and model artifacts used in our project on predicting movie box office sales tiers using metadata and review text.

TEAM CONTRIBUTION OVERVIEW

Jeffrey Abdoelmadjied
Responsible for the initial basis of cleaning in Notebook 1 (early cleaning groundwork).
Fully responsible for Notebook 2: Base modelling and Neural Network (baseline models, MLP design/training, evaluation plots, and exporting the neural network artifacts).

Juliusz Dokrzewski
Responsible for feature engineering and Transformers in Notebook 1.
Took over a large part of the cleaning process after Jeffrey’s initial groundwork.
Worked together with Bart on the explainability that follows the Random Forest section.

Bart Schleidt
Responsible for Notebook 3: Tree-based models and Explainability, with focus on Decision Trees / Random Forest and the explainability workflow.
Worked together with Juliusz on explainability in the later part of Notebook 3.

FILES IN THIS ZIP AND WHAT THEY DO
A) Notebooks (run order)
Notebook_1_Cleaning_EDA_Feature_engineering_group_and_Juliusz.ipynb
Data merge and EDA
Cleaning (basis started by Jeffrey, continued largely by Juliusz)
Feature engineering
Transformers-based text features and topic modelling (Juliusz)

Notebook_2_Base_modelling_and_Neural_network_Jeff.ipynb
Baselines: Dummy, Logistic Regression, KNN, SVM
Neural network (MLP) training and evaluation (learning curves, test metrics)
Exporting scaler + neural network model artifacts (Jeffrey)

Notebook_3_Tree_based_models_and_explainability_bart.ipynb
Tree-based models: Decision Tree and Random Forest
Explainability (Bart, with contributions from Juliusz)
Results and conclusion (answers the business question)

B) Additional files and folders

requirements.txt
Use this file to install the required Python packages.

computed_dataset/
Contains the exported dataset/dataframe after cleaning and feature engineering.
This is the modelling-ready dataset with all engineered features.

artifacts_exported_model/
Contains the exported neural network artifacts:

the trained neural network model

the fitted scaler / preprocessing object
These artifacts allow evaluation/inference without retraining.

HOW TO RUN (IMPORTANT NOTES)

A) Install requirements

Create a new Python environment (recommended).

Install packages using:
pip install -r requirements.txt

B) Recommended execution order

Notebook 1 (data preparation and feature engineering)

Notebook 2 (baseline modelling + neural network)

Notebook 3 (tree-based models + explainability + conclusion)

C) IMPORTANT WARNING ABOUT NOTEBOOK 2 (NEURAL NETWORK)
Do NOT use “Run All” on Notebook 2.

Reason: the neural network will retrain and may produce different results due to training randomness (for example weight initialization and training dynamics). This can cause different metrics and plots.

Recommended approach:

Run Notebook 2 step-by-step, OR

Use the exported artifacts in the folder “artifacts_exported_model/” to reproduce evaluation/inference without retraining.

JEFFREY’S REFLECTION (COLLABORATION)

I really enjoyed working with this team. The collaboration felt strong because everyone was motivated, proactive, and able to explain what they were doing. That made it easy to trust each other’s work and to move quickly without losing quality. I also liked learning from each other. Seeing how the others approached feature engineering and explainability helped me improve how I communicate modelling choices and results.

From my side, I think I performed best when I stayed structured: making sure the baselines were clear, comparisons were fair, and the neural network section was complete and presentation-ready. At the same time, I could have improved by aligning earlier on reproducibility decisions, especially around neural network retraining. I experienced myself that rerunning the full notebook can lead to slightly different outcomes, and I should have documented that earlier and more explicitly during development.

Finally, the “Pippy the Cat” storyline is a small nod to my own cat, and it also fits our audience: our lecturer Riccardo is a big fan of cats. We used it as a light theme to make the project more engaging, without changing the seriousness of the analysis.

(Other team members: please add your reflection below this section.)