# Credit-card-fraud-detection-using-Shap-for-feature-selection
This project explores the use of SHAP (SHapley Additive exPlanations) for feature selection in credit card fraud detection and analyzes the impact on model performance, particularly focusing on precision and recall.

Description:

The project investigates the effectiveness of SHAP in identifying the most influential features for credit card fraud classification. Here's the workflow:

SHAP Feature Selection: SHAP values are calculated to understand the contribution of each feature to the model's predictions.
Feature Analysis: Features with consistently low SHAP values (potentially indicating low importance) are identified, with a specific focus on the V27 feature.
Model Training & Evaluation (with and without V27): Eight different machine learning models are trained and evaluated:
Each model is trained once using the full feature set
Another model is trained for each type excluding the V27 feature identified by SHAP analysis
Performance Comparison: The impact of dropping V27 on model performance is analyzed across various metrics (Accuracy, Precision, Recall, F1-Score, ROC AUC) for all eight models, with a particular focus on precision and recall for KNN, Random Forest, Decision Tree, and Logistic Regression.

Results:

The analysis revealed that dropping the V27 feature based on SHAP insights led to a significant improvement in precision (0.0016) for the KNN model, while maintaining recall. However, the impact on other models varied:

Logistic Regression (dropped V27) showed negligible changes in most metrics, suggesting V27 might not be a significant feature for this model.
Other models exhibited trade-offs:
Random Forest (dropped V27) showed a slight improvement in precision and a more significant improvement in recall.
Decision Tree (dropped V27) showed improvements in both precision and recall.

In-Depth Analysis of Feature Selection Impact on KNN, Random Forest, Decision Tree, and Logistic Regression:

KNN: During feature selection, we observed a significant improvement in precision (from 0.9167 to 0.9429) for the KNN model after dropping V27, with minimal change in recall. This 3% increase suggests that V27 might have introduced noise or redundancy for the KNN model. Eliminating this potentially misleading feature allowed the KNN model to better identify true positives (fraudulent transactions) while avoiding false positives (legitimate transactions flagged as fraud).

Random Forest: The initial precision of Random Forest was already high (0.9762). Dropping V27 resulted in a marginal increase in precision but a more significant improvement in recall (from 0.7455 to 0.8000). This suggests that V27 might have hampered Random Forest's ability to identify some genuine fraudulent transactions (false negatives). Removing V27 likely allowed the Random Forest model to better capture the underlying patterns for fraud detection, leading to a better balance between identifying true positives and minimizing false negatives.

Decision Tree: Similar to Random Forest, Decision Tree also showed improvement in both precision and recall after removing V27. This indicates that V27 might have negatively impacted the model's decision-making process for classifying transactions. By eliminating this potentially confusing feature, the Decision Tree model could differentiate between fraudulent and legitimate transactions more effectively.

Logistic Regression: Interestingly, Logistic Regression's performance remained relatively unchanged with and without V27. This suggests that V27 might not have been a significant factor for this model. Logistic Regression might have relied more heavily on other features for classification, rendering V27 less influential in its decision-making process.

Key Takeaways:

SHAP can be a valuable tool for identifying potentially irrelevant features in a dataset for credit card fraud detection.
Dropping features with low SHAP values can lead to improvements in specific performance metrics (particularly precision in this case) for certain models, but the impact can vary.
It's crucial to analyze the impact on both precision and recall to understand the trade-off between identifying true positives and minimizing false negatives.
The decision of whether or not to drop a feature should be based on a comprehensive understanding of the trade-offs and the specific requirements of the fraud detection system.
Future Work:

Explore cost-sensitive learning techniques to explicitly account for the trade-off between precision and recall based on real-world costs associated with misclassifications.
Investigate the specific characteristics of the V27 feature to understand why its importance varies across different models.
Analyze the impact of SHAP-guided feature selection on a wider range of machine learning algorithms.
