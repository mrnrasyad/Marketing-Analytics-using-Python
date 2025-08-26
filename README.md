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
5. gender: gender of the person to whom the add is shown
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
   - A correlation test is conducted to examine the relationships between `interest`, `Impressions`, `Clicks`, and `Spent` with `Approved_Conversion`.
   - Bar plots are used to analyze the relationships of `age`, `gender`, and `Total conversion` with `Approved_Conversion` across campaigns (`ad_id`, `xyz_campaign_id`, and `fb_campaign_id`).
3. Model training
   - A new `df` is created to prevent data leakage. The data is split into training (60%), validation (20%), and testing (20%) sets, with the same feature engineering applied to each.
   - The base model uses Logistic Regression and Random Forest, evaluated with ROC AUC.
4. Performance stability check
   - Retrains on the full training data and checks how performance changes, to ensure the model generalizes.
5. Model interpretation
   - Uses SHAP values or feature importance to see which features most influence conversion.
  
## Results
#### `interest`, `Impressions`, `Clicks`, and `Spent` Vs. `Approved_Conversion`
The correlation analysis shows that `interest` has almost no effect on conversions (0.058), while `Impressions` have a strong positive correlation (0.684), making visibility the strongest driver of approved conversions. `Clicks` (0.560) and `Spent` (0.593) both show moderate positive correlations, indicating that higher engagement and ad spend contribute to conversions, though their impact is weaker than impressions.

#### `Approved_Conversions` Vs. `Age` per `Campaign`
Campaign 1178 achieves the highest average conversions and significantly outperforms the others, particularly in the 30–34 age group, which emerges as the most responsive segment overall. Campaigns 1178 and 936 both peak within this younger segment, while Campaign 916 performs best in the 40–44 group. These results suggest that future resources should prioritize the structure of Campaign 1178, with a strategic focus on targeting audiences aged 30–34.

<p align="center">
  <img src=image/1.png />
</p>

#### `Approved_Conversions` Vs. `Gender` per Campaign
Campaign 1178 achieves the highest approved conversions across both genders, peaking among female customers with an average of 1.42. Campaigns 916 and 936 perform similarly with averages below 0.5, showing that campaign choice, not gender, is the dominant factor. Overall, Campaign 1178 is nearly three times more effective than the others.

<p align="center">
  <img src=image/2.png />
</p>

#### `Total_Conversions` Vs. `Approved_Conversion` per Campaign
Campaign 1178 dominates in both total and approved conversions, driving the majority of business impact. Campaign 916 shows high approval efficiency but suffers from very low volume, while Campaign 936 sits in between with moderate conversions but relatively low efficiency.

<p align="center">
  <img src=image/3.png />
</p>

#### Top 10 Features

The Logistic Regression model achieved an ROC AUC of **0.668**, while the Random Forest model obtained **0.629**, indicating weaker performance. However, a performance stability check using `RandomForestClassifier` produced an improved ROC AUC of **0.727**. This SHAP summary plot shows the top features that influence whether a customer buys after seeing an ad.

<p align="center">
  <img src=image/4.png />
</p>

Other than `Total_Conversions`, engagement metrics like `Impressions`, `interest`, and `Spent` have the biggest impact, while demographics (such as gender and age) play a smaller role. In short, customer actions matter more than who they are. These results are in line with the correlation analysis conducted earlier.

## Conclusions 
This project demonstrates that **campaign design and customer engagement metrics are far more influential than demographics in driving conversions**. Campaign 1178 consistently delivers the highest impact, especially among the **30–34 age group**, making it the most valuable audience segment to target. Gender does not significantly affect outcomes, as performance is determined primarily by the campaign itself. Correlation and feature-importance analyses confirm that `Total_Conversions`, `Impressions`, and `interest`. are key predictors, while demographics (such as gender and age) play a smaller role.

From a modeling perspective, Logistic Regression achieved a baseline ROC AUC of 0.668, while Random Forest improved to 0.727, showing that machine learning can enhance predictive performance with proper stability checks. Overall, the findings suggest that future marketing strategies should prioritize Campaign 1178’s structure, optimize for visibility and engagement, and allocate resources toward the younger 30–34 segment to maximize returns.

