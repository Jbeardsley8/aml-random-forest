# 💵 AML Random Forest Classifier

This project applies a Random Forest classifier to detect potential money laundering activity using transactional data. It includes full feature engineering, pipeline building, hyperparameter tuning, and model evaluation.

## Dataset

This project uses the **Anti-Money Laundering Simulated Dataset** 

The dataset simulates realistic financial transactions with labeled money laundering activity. It includes attributes such as account IDs, transaction amounts, currency types, and timestamps.

---

## Class Imbalance

Money laundering is rare in the real world, and the dataset reflects this imbalance — fraudulent transactions make up only a small percentage (less than 1%) of the total.

To address this:
- The model uses `class_weight='balanced'` in the Random Forest to give more importance to minority class (laundering).
- Threshold tuning was performed to improve **precision** and **recall** rather than relying on default 0.5 cutoffs.

## Project Structure

- `random_forest_attempt2.ipynb` — Main analysis notebook
- `pipeline_cache/` — *[ignored]* Used temporarily during model fitting
- `HI-Small_Trans.csv` — *[ignored]* Original transactional dataset (not uploaded)

## Key Features

- Feature engineering (account frequency, daily activity)
- Preprocessing pipeline using `ColumnTransformer` and `Pipeline`
- Hyperparameter tuning via `GridSearchCV`
- Threshold optimization using F1-score, precision, and recall
- Feature importance visualization
- Model evaluation using classification reports and confusion matrix

## Note

Large files are intentionally excluded from version control via `.gitignore`.

## Tools & Libraries

- Python
- Scikit-learn
- imbalanced-learn
- Pandas, NumPy, Matplotlib

## Model Performance

Performance was evaluated using stratified cross-validation and F1-score as the primary metric. See notebook for full results and visualizations.

## Post-Model Recommendations

After scoring transactions with the optimized model and threshold:

- Transactions predicted as laundering (label = 1) are flagged for review.
- These flagged transactions are ranked by predicted probability.
- The top-ranked transactions are exported to `flagged_transactions.csv`.
- While sampling techniques had minimal impact on model performance—potentially due to the model’s internal handling of imbalance, the nature of the dataset, or possible limitations in my undrestanding or implementation.

This allows investigators or compliance teams to manually review the most suspicious activities first, improving investigation efficiency.

You can adjust the threshold based on operational resources or regulatory risk tolerance.


*Developed by [@Jbeardsley8](https://github.com/Jbeardsley8)*
