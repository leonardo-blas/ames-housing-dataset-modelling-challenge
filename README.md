# Ames housing dataset challenge

## Problem statement
As part of our data science bootcamp, we were given housing datasets, `train.csv` and `test.csv`, and were asked to develop a model that can accurately predict the `SalePrice` column of the testing set, which was not given. We were asked to optimize the RMSE, meaning to optimize our predictions in terms of dollars.

## Data dictionary
The data dictionary for the Ames housing dataset can be found at https://kaggle.com/competitions/adobe-dsb-34 [1].
From these ~80 columns, our model uses all of them except: `PID`, `Garage Yr Blt`, `MS SubClass`, `Overall Cond`, `BsmtFin SF 2`, `Low Qual Fin SF`, `Bsmt Half Bath`, `3Ssn Porch`, `Pool Area`, `Misc Val`, `Mo Sold`, `Yr Sold`.

## Summary
In this project, we were given `train.csv` and `test.csv` and were asked to predict housing prices based on the housing characteristics givein in `test.csv`. The goal is to develop a model, train it with `train.csv` and make predictions on `test.csv` as close as possible to their true values, which were not given. We measure our effectiveness in RMSE, or how many dollars, in average, our model's predictions will be off by.
<br>
To start this process, we decided on the data to use. We conducted a correlation analysis to determine the columns we wanted and not wanted to train the model on. Then, we dropped the undesired columns, cleaned the ones we chose, and, depending on wether the column had null values and wether it was appropriate, we used a simple or KNN imputer. We also one hot and cardinal encoded our categorical values. Next, we normalized and standardized our data, using a `log1p` function on the numeric and ordinal columns and `StandardScaler()` on all columns. Lastly, we tried several models: Linear, ridge, 2nd degree linear polynomial, and 2nd degree ridge polynomial.
<br>
From our experiments, we learned that our best model is the 2nd degree ridge polynomial model. This model has about 30 thousand coefficients and is challenging to interpret. However, one possible way to interpret it is as an assurance that our initial assumptions on the given data were correct: Some features are more important than other, like overall quality and garage area, and some columns are almost irrelevant, like pool area and year sold.
<br>
All in all, the task was accomplished. We constructed a model that estimates housing prices and has a RMSE score--on `test.csv`--of about $19k, meaning that, in average, its price predictions will be off by about that amount.

## References
[1] J. O, M. Harris, "Ames Iowa Submission". 2024. https://kaggle.com/competitions/adobe-dsb-34
