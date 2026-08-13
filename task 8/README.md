# Task 8: House Price Prediction (Regression Model)

## Why I picked this one

I wanted my third task to actually involve building a model, not just exploring data, so I went with the Advanced level ML task. Predicting house prices felt like a good pick it's intuitive (more space, better location, newer house generally higher price), which makes it easier to sanity check whether the model's actually learning something sensible or just fitting noise.

## The data

- `house_data.csv` 500 rows
- Columns: Area_sqft, Bedrooms, Bathrooms, House_Age_years, Location_Score, Garage, Price

Six features to predict one target (Price). No missing values, so I could spend most of my time on the modeling side rather than cleanup.

## What I did

Started by looking at how each feature correlated with Price a quick correlation heatmap made it pretty obvious early on that `Area_sqft` and `Location_Score` were going to matter a lot more than something like `Bedrooms` on its own.

Split the data 80/20 into train and test sets, then trained two models so I could actually compare approaches instead of just trusting one:

- **Linear Regression** as a baseline simple, interpretable, good starting point.
- **Random Forest Regressor** to see if a more flexible, non-linear model could pick up on anything the linear model was missing.

Evaluated both using RMSE and R², and also pulled feature importances out of the Random Forest to double check my assumptions from the correlation heatmap.

Finally, I wrapped the trained model in a small `predict_price()` function so it's easy to feed in a new set of features and get a price estimate back figured that's the more "usable" version of the project rather than leaving the model sitting inside the notebook.

## Results

| Model              | RMSE      | R² Score |
|---------------------|-----------|----------|
| Linear Regression    | ~25,334   | 0.903    |
| Random Forest         | ~27,747   | 0.884    |

Honestly the result kind of surprised me at first I expected Random Forest to win by default since it's the "fancier" model. But it turns out the relationship between these features and price is pretty close to linear, so the simpler model actually edged it out. Good reminder that more complex isn't automatically better it depends on the underlying data.

`Area_sqft` and `Location_Score` came out as the two strongest predictors in both models, which lined up with what the correlation heatmap suggested early on.

Visuals included: `correlation_heatmap.png`, `eda_relationships.png`, `feature_importance.png`, `predicted_vs_actual.png`. Full workflow is in `House_Price_Prediction.ipynb`.

## Running it yourself

Open `House_Price_Prediction.ipynb` in Jupyter, VS Code, or Colab and run top to bottom `house_data.csv` needs to be in the same folder.

## What's next

If I were to take this further, the natural next step would be wrapping `predict_price()` in a small Streamlit app a simple form for the 6 inputs, and it spits out an estimated price. Would make it something a non-technical person could actually use.

---
*Task 8 (Advanced Level) — Synent Technologies Data Science Internship*