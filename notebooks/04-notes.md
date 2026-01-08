# :love_letter: Notes and conclusions of ``04-evaluation.ipynb``
The best performing model is Random Forest trained on all the features with a cross-fold of K=10.

## Evaluation metrics calculation
Three metrics were used to evaluate the model in this step: accuracy, roc-auc and f1-score.

## ROC curves (best model)
> Plot can be found [here](../media/04-roc_curve_best.png).

The ROC curve shows that the Random Forest model has strong discriminative performance, achieving a ROC-AUC of approximately 0.88 on the test set. The curve lies well above the random guessing baseline, indicating effective separation between patients with an without heart disease.

## Confusion matrix (best model)
> Plot can be found [here](../media/04-confusion_matrix_RandomForest_all_cv10.png).

The confusion matrix shows that the Random Forest model correctly classifies the majority of both healthy patients and patients with heart disease, with relatively few false negatives (11) and false positives (15). In particular, the low number of false negatives indicates that most disease cases are succesfully detected which is the most important metric in case of cardiovascular diseases.

## Precision-recall curves (best model)
> Plot can be found [here](../media/04-precision_recall_curve_best.png).

The precision-recall curve further confirms the robustness of the model, as precision remains high across a wide range of recall values. This suggests that the model is able to identify most positive cases while keeping the number of false positives relatively low, making it well-suited for a medical screening context.

## Classification report

The classification report once again confirms this, with high precision and recall for both classes and an overall accuracy of 0.89. The strong recall for the positive class suggests that the model is well-suited for identifying patients at risk of heart disease while maintaining reliable predictions.
