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

The discussion of each hypothesis to validate or refute it is found in the notebook file.
Below are the summary of the analysis of hypotheses 1, 10 and 13:
