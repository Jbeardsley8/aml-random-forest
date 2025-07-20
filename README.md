# 💸 AML Random Forest Classifier

This project applies a Random Forest classifier to detect potential money laundering activity using transactional data. It includes full feature engineering, pipeline building, hyperparameter tuning, and model evaluation.

## Project Structure

- `random_forest_attempt2.ipynb` — Main analysis notebook
- `pipeline_cache/` — *[ignored]* Used temporarily during model fitting
- `HI-Small_Trans.csv` — *[ignored]* Original transactional dataset (not uploaded)

## Key Features

- Custom feature engineering (account frequency, daily activity)
- Preprocessing pipeline using `ColumnTransformer` and `Pipeline`
- Hyperparameter tuning via `GridSearchCV`
- Threshold optimization using F1-score, precision, and recall
- Feature importance visualization
- Model evaluation using classification reports and confusion matrix

## Note

Large files are intentionally excluded from version control via `.gitignore`.

## 🛠 Tools & Libraries

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

This allows investigators or compliance teams to manually review the most suspicious activities first, improving investigation efficiency.

You can adjust the threshold based on operational resources or regulatory risk tolerance.


*Developed by [@Jbeardsley8](https://github.com/Jbeardsley8)*
