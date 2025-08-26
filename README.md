# Marketing Analysis Using Python: A Data Analytics Project

## Brief Description about this Project
The goal of this project is to analyze which customer features (like demographics and past interactions) most influence whether a customer buys a product after seeing an ad.

## Data Description
The dataset that used in this project is collected from kaggle - [https://www.kaggle.com/datasets/loveall/clicks-conversion-tracking](https://www.kaggle.com/datasets/loveall/clicks-conversion-tracking)

Below are the descriptions of the variables.

1. ad_id: an unique ID for each ad.
2. xyz_campaign_id: an ID associated with each ad campaign of XYZ company.
3. fb_campaign_id: an ID associated with how Facebook tracks each campaign.
4. age: age of the person to whom the ad is shown.
5. gender: gender of the person to whim the add is shown
6. interest: a code specifying the category to which the person’s interest belongs (interests are as mentioned in the person’s Facebook public profile).
7. Impressions: the number of times the ad was shown.
8. Clicks: number of clicks on for that ad.
9. Spent: Amount paid by company xyz to Facebook, to show that ad.
10. Total conversion: Total number of people who enquired about the product after seeing the ad.
11. Approved conversion: Total number of people who bought the product after seeing the ad.

## Scope of The Project
1. Data preparation
   - The `age` column is recoded into four age intervals: '30–34' as 1, '35–39' as 2, '40–44' as 3, and '45–49' as 4.
   - `Approved_Conversion` is recoded into a binary column (`Accepted_Conversion`), where 0 = no conversion and 1 = at least one conversion.
2. Exploratory data analysis (EDA)
   - Using correlation test to see how the `interest`, `Impressions`, `Clicks` , and `Spent` columns correlated with `Approved_Conversion`.
   - Using bar plot to see how `age`, `gender`, and `Total conversion` related to  `Approved_Conversion` for  each campaign (`ad_id`, `xyz_campaign_id`, and `fb_campaign_id`).
3. Model training

Uses RandomForestClassifier (and possibly other models).

Splits into X_train, X_test, y_train, y_test.

Evaluates using ROC AUC (a good metric for imbalanced classification like marketing conversion).

Performance stability check

Retrains on the full training data and checks how performance changes, to ensure the model generalizes.

Model interpretation

Uses SHAP values or feature importance to see which features most influence conversion.
