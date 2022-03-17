# Project 2 - Predicting House Sale Prices for Ames, Iowa

### By: Rashidi Norhashim (GA SG-DSI-27)

## Background

Our fictional company, ABC-XYZ Corp., is a long standing giant in the real estate industry. The executives want to create a website that is able to accurately recommend an estimated sale price to budding sellers, given user inputs on the house specifications, as a way to entice sellers to work with the company's many real estate agents.

Acting as the recently recruited Data Scientist, I was tasked to first start of with building a model to accurately predict house sale prices in Ames, Iowa, ABC-XYZ Corp.'s HQ location.

Coming from a Singaporean background, I am aware of another similar company who has a working model that ABC-XYZ Corp. is looking for. A homeowner has to input certain variables such as postal code, property type, floor, unit no., and floor area (as pictured in **Input Variables** below), in order to get an estimate on the sale value (as pictured in **Estimate Sale Valuation** below).

After pitching the idea to the bosses at ABC-XYZ Corp., they are ecstatic and wishes to do the same for their website. However, they have requested to identify and include important localized variables.

Given the Ames Iowa Housing dataset, I will now start to choose those important localized variables and fit into a model to correctly predict future house sale prices.

#### Input Variables
![image](https://user-images.githubusercontent.com/99335911/158867195-c5a8858e-a734-40de-82ba-c03da51b87c8.png)

#### Estimate Sale Valuation
![image](https://user-images.githubusercontent.com/99335911/158867341-30ddc35a-0312-46ef-82f7-6fa37a413c80.png)

(source: 99.co, https://www.99.co/)

## Data Dictionary

Useful Link: http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

## Initial Feature Filtering
***Which to choose??**
![image](https://user-images.githubusercontent.com/99335911/158867752-8f9b1611-c2ee-4e95-af5a-06bdb6ddfb4c.png)

The Ames Housing dataset has 81 columns. Tradeoffs were made in this regard to focus on the task at hand.

Some of the features overdescribes the house specifications. For example, 'garage_cars' and 'garage_area' specifies the same thing, albeit in slightly different ways. 'garage_area', containing continuous numerical values, is picked out of the two.

Another category of features describe a subset of another feature. For example, 'bsmtfin_sf_2','bsmtfin_sf_1', and 'bsmt_unf_sf', are subsets of 'total_bsmt_sf' and as such, 'total_bsmt_sf' is chosen out of all named. Exceptions were made for features that are on an ordinal scale as the weightage of certain specifications of the house might not be equal (i.e. Kitchen Quality might have different weightage when compared to Basement Quality with respect to Overall Quality)

Others that describe the house identification information (like 'id' and 'pid') or those that features describing miscellaneous features (with lesser data points) are not useful in a regression model and will not be chosen.

## Data Cleaning

- Numerical features -> Check for null values
- Ordinal features -> Change to numerical scale
- Categorical features -> Manually Dummify
        - Done in order to determine easily which dummy column was dropped
            - Example: '150' was dropped from 'ms_subclass'

## Exploratory Data Analysis
The following were analysed: 

1) Pairwise collinearity of features analysed and one feature was dropped from feature-pairs with >0.80 correlation.

2) Correlation vs. Target was explored and cutoff threshold was deliberated but not done in favour of Lasso Regression.

## Simple Model

A simple linear regression model was done using features similar to the ones in 99.co.

|99.co|Ames Dataset|Remarks|
|---|---|---|
|Address|Neighborhood|Best indicator of location|
|Property Type|MS Subclass|Best describer of house type|
|Floor Area|Gr Liv Area|Best describer of housing floor area|
         
<u>Scoring for model_99co</u>
Train MSE: 1464088294.1777663
Test MSE: 1152320467.0052726
Cross Val MSE: 1576989381.0013125

## Pre-processing and Feature Engineering
**Lasso Regression**
Lasso Regression was done to eliminate features with low correlation by removing those with zero coefficient post lasso regression.

<u>% Improvement of drop_0 Ridge Regression over the Linear Regression model</u>
Train MSE: -7.9245313139847156%
Test MSE: 7.029361171597387%
Cross Val MSE: 7.044231671102281%

![image](https://user-images.githubusercontent.com/99335911/158869464-efc38f7e-c1be-41ff-8da9-b33435a1ffbe.png)

From here we see that with our Lasso Regression we have improved on our model scores across the board. We can also see that the spread of our residuals are also narrower along the x-axis (y = 0). This means that the base 99co model is not good to predict unseen data as much as our new Lasso model. That being said, the current model is still far from being a finished ready to ship production model.

From the coefficient values, we see that Lasso has identified numerous features (including dummies) as zero (or very close to it). These features are very likely those that had low correlation scores against Sale Price in the first place, compared to others.

However, we do see that there are some coef values which are zero but have a substantial correlation to Sale Price. This is most likely a case of collinearity whereby a stronger collinear feature (like gr_liv_area) is chosen over, for example, lot_frontage.

**Pairwise Collinearity of lot_frontage vs. gr_liv_area:** 0.360696

|Feature|lasso_coef Value|Saleprice Correlation|
|---|---|---|
|lot_frontage|-0.000000|0.328149|
|gr_liv_area|24273.462134|0.698046|


## Model Benchmarks and Tuning
**Linear Regression after dropping Lasso Zero Coefficient Features**
<u>% Improvement of drop_0 Linear Regression over the Lasso model</u>
Train MSE: 7.182530606573792%
Test MSE: -2.6280838571614282%
Cross Val MSE: -0.6400977923164675%

As expected, there is not much improvement over lasso scores because the same number of features were used. Next, we will be exploring regularization to introduce more bias and see if we can improve the scores further.

**Ridge Regression after dropping Lasso Zero Coefficient Features**

<u>% Improvement of drop_0 Ridge Regression over the Linear Regression model</u>
Train MSE: -7.9245313139847156%
Test MSE: 7.029361171597387%
Cross Val MSE: 7.044231671102281%

![image](https://user-images.githubusercontent.com/99335911/158870034-d5cd4d4d-343b-4084-a02c-2f3e817c964a.png)

We see that the Ridge regression model performed worse than the linear regression model in terms of Train MSE but improved in both Test MSE and Cross Val MSE. This means we have effective introduced more bias in order to better predict future unseen data.

## Production Model

Comparing the scores across all models done we see that the Ridge Regression model after dropping Lasso zero coefficient features performed the best and hence this will be the model that we set as the production model.

|Model|Train MSE|Test MSE|Cross Val Score|
|---|---|---|---|
|drop_0_coeff Ridge Regression|702796769|619778333|950438300|
|drop_0_coeff Linear Regression|651192793|666638781|1022462959|
|Lasso Regression|701584300|649567599|1015959823|
|99co Linear Regression|1464088294|1152320467|1576989381|

<u>Production Model Attributes</u>
Train MSE: 673341543.1264241
Cross Val MSE: 833273475.817483
Ridge Regression Alpha: 335.1602650938841
Total Features Used: 73

## Insights

**Production Model Summary**

From fitting our best model on the whole dataset available to us, we see that the cross validation MSE is still far from the Train MSE. This is indicative of an overfit model which is not biased enough to effectively handle unseen data. What else can be explored but was not in this project was to reduce overfitting by the following measures:

1) Eliminating outliers from deep-diving into model predicted residuals.

2) Explore pairwise interactions.

3) Explore different cutoffs to see which will effectively eliminate poorly correlated features (vs. Target) and produce the best model.

**Project Insights**

Although we have identified relevant features for our model through machine learning and feature engineering, at the end of the day we have 73 features in our model and some of the features used in our model are not reasonable real estate knowledge that our day-to-day homeowners might have. If we were to roll out our model as is and requesting that many difficult inputs, people using our platform might find it daunting, which begets the purpose of creating this in the first place.

Thus, it might be more prudent to work with our real estate agents to get an idea of what data or which features are easily known/accessible by our homeowners. Through this, we can have a platform that is not only accurate, but easy to use too. In a way, we want to strike the balance between the simplicity offered by 99co vs our model accuracy and hence, more work can be done to bring this up to be production-ready

## Kaggle Submission Score

Private Score: 24052.28611

Public score: 33203.03021
