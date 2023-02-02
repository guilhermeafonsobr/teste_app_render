# Rossmann stores - 6 weeks sales forecast

**Disclaimer:** this project was inspired by the "Rossmann Store Sales" challenge published on kaggle (https://www.kaggle.com/c/rossmann-store-sales). It is a fictitious project but with all the steps of a real project.

## Business scenario
The sales director of the Rossmann stores wants to estimate the sales forecast for the next 6 weeks on its different units spread across Europe.

## Solution methodology
The resolution of the challenge was carried out following the CRISP (CRoss-Industry Standard Process for data mining) methodology, which is a cyclical approach that streamlines the delivery of value.

## Data collection and understanding
The first step was to collect (from kaggle) and understand the data; soon after, the cleaning of the database and treatment of missing values took place.
There are 1017209 sales records for 1115 different stores, containing different attributes such as: "date", "store_type", "customers", "assortment", "school_holiday", "open", "promo2", "sales", among others. The explanation of each of the attributes is available on the notebook.
To complete the data understanding step, features that will not be available at the time of the forecast were removed, such as the number of customers, which will only be known on the day of sales and, therefore, it would be impractical to train the model with such variable.

## Exploratory data analysis guided by a mind map of hypotheses
The next step was to perform exploratory data analysis (EDA). But right before that, a mind map of hypotheses was made in order to guide the EDA, to generate insights and to understand a little more about the database and the most important attributes.

With the feature diagram above, several hypotheses were generated; the ones that were judged to be most relevant were selected (listed below) and then the EDA actually started.

1. Stores with a larger assortment should sell more
2. Stores with closer competitors should sell less
3. Stores with longer-standing competitors should sell more
4. Stores where products cost less for longer (active promotions) should sell more
5. Stores with more promotion days should sell more
6. Stores with more extended promotions should sell more
7. Stores open during Christmas holiday should sell more
8. Stores should sell more over the years
9. Stores should sell more in the second half of the year
10. Stores should sell more after the 10th day of each month
11. Stores should sell less on weekends
12. Stores should sell less during school holidays
13. Stores that open on Sundays should sell more

The discussion of each hypothesis to validate or refute it is found in the notebook.

| Model Name |  MAE CV | MAPE CV | RMSE CV |
|--- |--- |--- |--- |
| Linear Regression| 2082.46 +/- 295.78 | 30.26 +/- 1.66 | 2950.11 +/- 468.88 |
| Lasso Regression | 2116.65 +/- 341.58 | 29.2  +/- 1.18 | 3056.56 +/- 504.44 |
| Random Forest Regressor | 837.7   +/- 219.23 | 11.61 +/- 2.32 | 1256.59 +/- 320.26 |
| XGBoost Regressor | 767.43 +/- 187.22 | 0.115397 +/- 0.221 | 1103.412218 +/- 278.36|

My final choice of model was XGBoost.

In this case, the model will be hosted on a free cloud (Heroku), where we have a space limitation. If I choose random forest, the final model would be 1GB. Meanwhile, with XGBoost, the model became much smaller.

The metric problems can be solved in "Hyperparameter fine tuning" step.

Look the metrics after a better choice of parameters to train the model:

| Model Name |  MAE CV | MAPE CV | RMSE CV |
|--- |--- |--- |--- |
| XGBoost Regressor | 767.43 | 0.115397 | 1103.412218 |

## Business Results

Finally, with the model trained, it's time to translate model performance into business performance. Considering the MAE obtained in the forecast for each store, during the test period, the best and worst sales scenarios for each store were projected.

Below, the expected business performance of the first 5 stores:

| store	| predictions |	MAE |	MAPE	| worst_scenario | best_scenario |
| 1	| 169305.70	| 308.78	| 0.07 |	157881.01	| 180730.40 |
| 2	| 182122.09	| 395.43	| 0.08 |	167491.11	| 196753.09 |
| 3	| 258817.89	| 538.91	| 0.08 |	238878.23	| 278757.55 |
| 4	| 338596.25	| 944.09	| 0.09 |	303664.96	| 373527.54 |
| 5	| 174173.37	| 388.33	| 0.09 |	159805.20	| 188541.55 |

Overall, the model performed well.
But it is always possible to improve it; following the CRISP methodology, if a new round is needed, it may be considered to train stores individually or even a smaller group of them, for example. Another possibility is to explore other machine learning models.
However, the deadline for delivery of forecasts and the performance of the model already in production must be taken into account. Something very heavy or time-consuming is also impractical, even if it performs exceptionally well.
It is a trade-off that must be closely aligned with the company's management.
Further details on business performance are available on the notebook.

## Sneak peak from Telegram Bot

## Lessons Learned
* Metrics are important, but they are not everything;
* Make more graphics, make better graphics;
* Keep your code clean;
* Plan and re-plan your work;

## Next cycle
* Better plots;
* More tests in ML algoritms;
* Build a pipeline to retrain model.
