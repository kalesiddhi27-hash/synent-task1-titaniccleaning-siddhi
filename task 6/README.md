# Task 6: Customer Segmentation (Mall Customers)

## Why I picked this one

I wanted to try something with unsupervised learning, and customer segmentation felt like a good real-world use case for it no labels, just raw behavior data, and the goal is to find natural groupings a business could actually act on. Basically: if you ran a mall or retail store, which customers should you be marketing differently to?

## The data

- `mall_customers.csv` 200 rows
- Columns: CustomerID, Gender, Age, Annual Income (k$), Spending Score (1-100)

Pretty small, clean dataset no missing values to deal with here, which let me focus entirely on the clustering itself.

## What I did

Started with some basic EDA looked at how age, income, and spending score were distributed just to get a feel for the customer base before doing anything fancy.

Since K-Means is distance-based, I scaled `Annual Income` and `Spending Score` using `StandardScaler` first otherwise income (which is in the tens of thousands) would completely dominate the distance calculation over spending score (which maxes out at 100).

To figure out how many clusters actually made sense, I ran the **Elbow Method** plotting inertia against different values of k and looking for where the improvement starts to flatten out. That pointed pretty clearly to **k=5**.

From there I applied K-Means with 5 clusters and plotted the results on an income vs spending scatter plot, with the centroids marked. Then I went back and profiled each cluster average age, income, and spending score per group to actually put a story behind the numbers rather than just leaving them as cluster 0, 1, 2, etc.

## What I found

Five pretty distinct customer segments came out of this, and a couple stood out:

- A **high-income, high-spending group** the "premium" customers you'd want to prioritize for loyalty programs or premium product lines.
- A **low-income, high spending group** interesting one, sort of "value seekers" who spend a lot relative to what they earn, maybe more price sensitive but highly engaged.

Everything's saved in `mall_customers_segmented.csv` (original data plus the assigned cluster for each customer), and the visuals distribution plots, the elbow curve, and the final cluster scatter are all in the repo. Full workflow's in `Customer_Segmentation.ipynb`.

## Running it yourself

Open `Customer_Segmentation.ipynb` in Jupyter, VS Code, or Colab and run top to bottom. Just make sure `mall_customers.csv` is in the same folder.

---
*Task 6 of 3 — Synent Technologies Data Science Internship*