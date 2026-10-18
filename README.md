# Digital Insomnia: Screen Habits & Sleep — Linear Regression

## Project Overview

This project explores the relationship between screen habits, lifestyle factors, environmental conditions, and next-day fatigue using Python. The analysis uses exploratory data analysis (EDA), Pearson correlation, hypothesis testing, and seven separate Simple Linear Regression Models (SLRMs).

The goal is to identify which individual predictor has the strongest linear relationship with the `next_day_fatigue_score` target and compare model performance on unseen data.

> **Dataset note:** The dataset is simulated and intended for educational analysis. Results should not be interpreted as evidence of real-world causation or as clinical guidance.

## Dataset

**Source:** [Digital Insomnia: Screen Habits & Sleep — Kaggle](https://www.kaggle.com/datasets/beamhonor0911/digital-insomnia-screen-habits-sleep)

The analysis uses the following variables:

| Variable | Description |
|---|---|
| `age` | Age of the individual, in years |
| `screen_time_before_bed_min` | Screen time before bed, in minutes |
| `screen_brightness_pct` | Screen brightness, as a percentage |
| `caffeine_intake_mg` | Caffeine intake, in milligrams |
| `physical_activity_min` | Physical activity duration, in minutes |
| `room_temperature_f` | Room temperature, in degrees Fahrenheit |
| `ambient_noise_db` | Ambient noise level, in decibels |
| `next_day_fatigue_score` | Numerical target used to analyze and predict next-day fatigue |

The `user_id` field is excluded from modeling because it is an identifier rather than a meaningful predictor. The target score is treated as a numerical measure for this analysis; consult the dataset author's documentation for the exact scale and interpretation.

## Methods

1. **Data inspection and preparation** — review dataset structure, descriptive statistics, and missing values.
2. **Exploratory data analysis** — summarize the variables and visualize their relationships.
3. **Pearson correlation** — measure the direction and strength of each predictor's linear association with the target.
4. **Hypothesis testing** — assess whether each correlation or regression slope is statistically significant.
5. **Train-test split** — use a 70% training set and 30% testing set with `random_state=42`.
6. **Simple Linear Regression** — fit seven separate models, each with one predictor.
7. **Model evaluation** — compare test-set R², Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE).

## Results

The best-performing individual model used `screen_time_before_bed_min`:

| Metric | Result |
|---|---:|
| Training R² | 0.1121 |
| Test R² | 0.1134 |
| MAE | 0.6996 |
| RMSE | 0.8851 |

Screen time before bed ranked first among the seven individual models by test-set performance. Age ranked second, followed by caffeine intake.

Five predictors—screen time before bed, age, caffeine intake, screen brightness, and ambient noise—had statistically significant regression slopes in the training data at the 5% significance level. Physical activity and room temperature were not statistically significant.

Although the screen-time model performed best relative to the other single-predictor models, its test R² indicates that it explains about 11.34% of the variation in the test-set fatigue scores. Its predictive power is therefore limited. Ambient noise was statistically significant but had very little predictive value, illustrating that statistical significance does not necessarily imply strong prediction.

## Tools and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Statsmodels
- Scikit-learn
- Google Colab / Jupyter Notebook

## Repository Contents

Suggested repository structure:

```text
digital-insomnia-linear-regression/
├── README.md
├── digital_insomnia_slrm.ipynb
└── sleep_debt_screen_time.csv  # Include only if redistribution is permitted
```

The notebook contains the code, visualizations, statistical analysis, model comparisons, and conclusions. If the dataset is not redistributed with this repository, download it from the Kaggle source linked above and update the notebook's data-loading path as needed.

## How to Run

1. Download or clone this repository.
2. Obtain the dataset from the [Kaggle dataset page](https://www.kaggle.com/datasets/beamhonor0911/digital-insomnia-screen-habits-sleep), subject to its license and terms.
3. Open `digital_insomnia_slrm.ipynb` in Google Colab or Jupyter Notebook.
4. Ensure the CSV file path in the notebook matches where the dataset is stored.
5. Run the notebook cells in order.

## Limitations

- The dataset is simulated, so patterns may not represent real-world populations.
- Each SLRM uses only one predictor; it does not account for the combined effects of multiple variables.
- Statistical association does not establish causation.
- Model performance is limited, with the best individual model explaining approximately 11.34% of test-set variation.
- Fatigue-score categories and clinical meanings should not be inferred unless defined by the dataset author.

## Future Work

Potential extensions include fitting a Multiple Linear Regression model, checking regression assumptions and multicollinearity, comparing models using cross-validation, and assessing whether combining predictors improves out-of-sample performance.

## Author

**Carl Dennis Manrique**

This project was developed for learning and portfolio purposes as part of my ongoing work in statistics, data analysis, and predictive modeling.
