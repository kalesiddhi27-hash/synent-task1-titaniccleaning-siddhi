# Task 1: Data Cleaning & Preprocessing (Titanic Dataset)

## What this is about

For my Synent Technologies data science internship, I picked this task to practice something I think is honestly the most underrated skill in data science — cleaning up messy data. Everyone loves jumping straight to models, but if your data's a mess going in, nothing after that really matters.

I worked with a Titanic-style passenger dataset that was deliberately messy missing ages, missing fares, some duplicate rows, and inconsistent text in the `Sex` column (extra spaces, mixed casing, that kind of thing). My goal was to get it into a clean, reliable state that could actually be used for analysis or modeling later.

## About the data

- `titanic_raw.csv` — 412 rows, 11 columns
- Columns: PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Fare, Cabin, Embarked
- Problems I found: missing values scattered across Age, Fare, Embarked, and Cabin, 12 exact duplicate rows, and messy formatting in the Sex column

## How I approached it

First thing I did was just look — checked the shape, data types, and ran `.isnull().sum()` to see where the gaps actually were before touching anything.

From there:

- **Age and Fare** had missing values, so I filled those in with the median. Mean felt riskier here since both can get skewed by outliers.
- **Embarked** only had a couple of missing entries, so I just used the mode (most common port).
- **Cabin** was mostly empty like, over 70% missing so instead of dropping it entirely (which felt wasteful) I turned it into a simple `has_cabin` flag. Whether someone had a recorded cabin at all seemed like it could still be informative.
- Dropped the 12 duplicate rows I found.
- Cleaned up the `Sex` column there were entries like " male", "Female", "female " floating around, so I standardized casing and stripped whitespace, then converted it to a proper category type.
- Renamed all the columns to consistent snake_case since the originals were a mix of styles.
- Exported everything to `titanic_cleaned.csv`.

## What I ended up with

Went from 412 messy rows down to **400 clean rows across 12 columns**, with zero missing values left. Full process is documented step-by-step in `Data_Cleaning_Titanic.ipynb`.

## Running it yourself

Just open `Data_Cleaning_Titanic.ipynb` in Jupyter, VS Code, or Colab and run the cells in order `titanic_raw.csv` needs to be sitting in the same folder for it to work.

---
*Task 1 of 3 — Synent Technologies Data Science Internship*