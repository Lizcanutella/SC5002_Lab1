# SC5002 Lab Assignment, Part 2: Linear vs Ridge Regression

Experiment for Artificial Intelligence Fundamentals & Applications (SC5002, NTU). The jupyter notebook in this repo compares Linear Regression against Ridge Regression on the California Housing dataset, with three different regularisation strengths using 5-fold cross-validation.

`SC5002_Part2.ipynb`: Colab notebook (with outputs)

## How to run the notebook

1. Open `SC5002_Part2.ipynb` in [Google Colab](https://colab.research.google.com/) (File -> Upload notebook, or open from GitHub).
2. Click on 'Runtime' -> 'Run all'. 

## Method

- **Data:** California Housing randomly sampled to 1,000 rows.
- **Target:** `MedHouseVal`, the median house value in units of $100,000.
- **Features (8):** `MedInc`, `HouseAge`, `AveRooms`, `AveBedrms`, `Population`, `AveOccup`, `Latitude`, `Longitude`.
- **Preprocessing:** `StandardScaler`, then 80/20 train/test split.
- **Evaluation:** mean R^2 over 5-fold cross-validation on training set (800 rows).
- **Models:** `LinearRegression`, and `Ridge`.

## Results and findings

| Model | Mean 5-Fold CV R^2 |
|---|---|
| Linear Regression | 0.6457 |
| Ridge (alpha = 0.1) | 0.6457 |
| Ridge (alpha = 10) | 0.6443 |
| Ridge (alpha = 1000) | 0.3574 |

- **Low alpha (0.1, 10):** performance is the same as linear regression. With 8 features and 800 samples the model is not overfitting, so penalty has little to correct.
- **High alpha (1000):** R^2 drops to 0.357. Penalty shrinks the coefficients to zero, which causes underfitting.
- **Bias–variance trade-off:** regularisation helps when overfitting is the problem. Here the best models would thus be at low alpha.
- **Cross-validation** averages over 5 folds, which gives a stable estimate, rather than a single train/test split.

## Limitations found

- `StandardScaler` is fit on the full data before the train/test split which causes some data leakage.
- In the template, the 20% test split is created but it's not actually used for final evaluation. All the reported values are from the training set's cross-validation scores.

## AI usage

Generative AI (Claude, Anthropic) was used as a learning and checking tool, as required by the assignment's "Learn with AI" tasks. Full prompt logs are found in the submitted PDF report.
