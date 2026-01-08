# :love_letter: Notes and conclusions of ``03-modeling.ipynb``

## Train-test split
A train-test split of 75:25 was applied to the cleaned dataset and stratify was used to make sure there's an evenly big distribution of heart diseases in the test set as in the train set. The test set (separated in X and y) was saved accordingly inside the `data/splits`-folder.

## Models & hyperparameters grids
### Models
Based on the read papers, Random Forest and XGBoost were the best performing models in most cases. 
The choice to implement those two was solely based on that literature, and no extra models were trained because this isn't the main focus of this project.

### Hyperparameters
A hyperparameter grid was defined per model to finetune the model and select the best performing one.

### Training loop
K-fold cross-validation was implemented with possible values for K equal to 5 and 10. The prepocessor was built based on what the subset was per run. The scoring used is ROC-AUC because this represents a model's ability to distinguish between classes across various thresholds.
All the trained models are saved inside the `models`-folder, together with an overview (saved in `results`) per model about the model name, the ROC-AUC score, the best parameters, used feature subset, best fold value and the model path.
