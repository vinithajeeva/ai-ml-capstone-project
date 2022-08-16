# ai-ml-capstone-project - Shopping Coupon Recommendations
In this captsone project, a customer ecommerce shooping transaction data from Kaggle is used to evaluate data and compare the performance of recommendation models using Surprise library. 

## Business Objectives
The application is built based on the CRISP-DM framework. The following are the business objective of this application,
1. Identify the performance/accuracy score of recommendation Models
2. Identify the factors that affect the recommendation of coupons for the brand where a user have most event_type - viewed, in-cart or purchased.
3. Summarize and provide future recommendations

## Data
The dataset comes from the Kaggle data repository (https://www.kaggle.com/code/danofer/ecommerce-store-predict-purchases-data-prep/data?select=2019-Oct.csv). The data contains consumer user behavior data for a one month (October 2019) from a large multi-category online store. The dataset contains 26560620 entires with a total of 9 columns.
Each row in the file represents an user event. All events are related to products and users. There are different types of events.
- event_time: Time when event happened at (in UTC).
- event_type
-- view - a user viewed a product
-- cart - a user added a product to shopping cart
-- purchase - a user purchased a product
Typical funnel: view => cart => purchase
- product_id: ID of a product
- category_id: Product's category ID
- category_code: multi-hierarchical name of Product's category
- brand: Downcased string of brand name
- price: Float price of a product. Present
- user_id: Permanent user ID
- user_session: Temporary user's session ID. Same for each user's session. Is changed every time user come back to online store from a long pause.

EDA funtions like null checks, data massaging methods were performed to plot data charts to understand the data in detail. Price and Shopping Time features exhibited a higher correlation.

## Association Rules - Work In Progress (WIP)
1. PCA - to identify patterns in columns
2. K-Means  to identify patterns in rows

## Recommendation Models Used
The following Recommendation Models from SURPRISE library were used in this application,
1. BaselineOnly() - for baseline prediction
2. KNNBasic() - WIP
3. SVD()
4. NMF() - WIP
5. SlopeOne()
6. CoClustering()

In the initial analysis, **BaselineOnly()** and **SVD()** models performed better than the other models for the given dataset.

After the initial analysis, the *GridSearchCV()* is applied to identify the best hyperparamaters and improved the performance of these Recommendation Models. Among the improved models, **BaselineOnly()** and **SVD()** models outperformed the other improved Recommendation models.

![image](https://user-images.githubusercontent.com/102641103/184792668-047a0a7f-0918-4714-b423-787d07fee661.png)

### Feature Importance of top models - Work In Progress (WIP)
Based on all the model analysis, the following features exhibited the highest feature importance,
1. TBD
2. TBD

## Conclusion - Work In Progress (WIP)
To be concluded

## Content
* Capstone Project Summary and Readout (WIP)   # Sumamry and Final Readout file of the Capstone Project Analysis
* Capstone_Project_EDA.jpynb                   # jupyter notebook with Exploratory Data Analysis (EDA) and Plots
* Capstone_Project_Modeling.jpynb              # jupyter notebook with Recommendation Models Analysis
* README.md                                    # this readme file

## Requirements
1. This project is implemented with Python 3.7.13.
2. The final assignment is implemented in Google Colab and can be executed in any python notebook apps.
3. The required packages and libraries with their versions are listed in the .jpynb files.
