# Capstone Project - Shopping Coupon Recommendation using Ensemble Models
In this captsone project, a customer ecommerce shooping transaction data from Kaggle is used to evaluate data and compare the performance of recommendation models using Surprise library. 

## Business Objectives
The application is built based on the CRISP-DM framework and Ensemble Modeling concepts. The following are the business objective of this application,
1. Identify the performance/accuracy score of recommendation Models
2. Identify the factors that affect the recommendation of coupons to user based on a user purchase history
3. Summarize and provide future recommendations

## Data
The dataset comes from the Kaggle data repository (https://www.kaggle.com/code/danofer/ecommerce-store-predict-purchases-data-prep/data?select=2019-Oct.csv). The data contains consumer user behavior data for a one month (October 2019) from a large multi-category online store. The dataset contains 26560620 entires with a total of 9 columns.
Each row in the file represents an user event. All events are related to products and users. There are different types of events.
- event_time: Time when event happened at (in UTC). Converted to 'Shopping_time'
- event_type: Typical funnel: view => cart => purchase
  - view - a user viewed a product
  - cart - a user added a product to shopping cart
  - purchase - a user purchased a product
- product_id: ID of a product (dropped)
- category_id: Product's category ID (dropped)
- category_code: multi-hierarchical name of Product's category
- brand: Downcased string of brand name
- price: Float price of a product. Present
- user_id: Permanent user ID (dropped)
- user_session: Temporary user's session ID. Same for each user's session. Is changed every time user come back to online store from a long pause (dropped)
- Coupon: Whether user used a coupon or not. Synthetically generated column

Since the dataset is large, used **Stratification** to sample the data for this analysis. EDA funtions like null checks, data massaging methods were performed to plot data charts using Seaborna and Plotly to understand the data visually and in detail. Price and Shopping Time features exhibited a higher correlation.

## Feature Importance/ Selection
Used RandomForestRegressor() on 'price' as target feature for this analysis. Between 'coupon' and 'event_type' classifier columns, 'coupon' is selected.

![image](https://user-images.githubusercontent.com/102641103/189555390-181bf8a1-cf98-469a-a677-b3a749a6e622.png)

## Recommendation Models Used
In the intial analysis, association rules and SURPRISE models were used and identified they are not suitable for the given dataset. Since, classifiers work better I am leveraging Ensemble Models for this application.

The following Ensemble Models along with GridSearchCV() were used in this application,
1. LogisticRegression() - for baseline prediction
2. Boosting Classifiers
  - 2.1 AdaBoostClassifier()
  - 2.2 GradientBoostingClassifier()
  - 2.3 XGBClassifier()
  - 2.4 HistGradientBoostingClassifier()
3. Bagging Classifiers
  - 3.1 DecisionTreeClassifier()
  - 3.2 ExtraTreeClassifier()
4. VotingClassifier
  - 4.1 HardVoting
  - 4.2 SoftVoting
5. StackingClassifier

## Conclusion
Bagging Classifiers using DecisionTreeClassifier() and ExtraTreeClassifier() with or without GridSearchCV() performed well than other models used in the analysis. Between these models, when other metrics like fit_time, FN, FT were taken into consideration, DecisionTreeClassifier() perfromed better than ExtraTreeClassifer(). 

## Explainer Dashboard
Used the ClassifierExplainer() to quickly building interactive dashboards for analyzing and explaining the predictions and workings of the seelcted bagging DecisionTreeClassifier() model with GridSearchCV(). A high-level summmary of some important metrics,
#### Feature Importance
![image](https://user-images.githubusercontent.com/102641103/189556571-252ae61b-98a9-483d-8294-64c175b3c1cc.png)
#### Confusion Matrix
![image](https://user-images.githubusercontent.com/102641103/189557675-61d44b06-637b-4023-905e-30fbaada57c5.png)
#### Perfomance Metrics
![image](https://user-images.githubusercontent.com/102641103/189556719-21fcb481-cc67-47c6-a11a-037cb27ff2e8.png)

For more details on the explainer dashboard reports are availabel in the 'Explainer Dashboard' (https://github.com/vinithajeeva/ai-ml-capstone-project/tree/main/Explainer%20Dashboard) folder of this GitHub Repository.

## Future Recommendations
1. The ensemble models can be applied to ‘event_type’ to understand whether the model accuracy improves
2. Adding more data around user profile like age, sex, education, job etc. will further improve the targeting of coupons to users
3. Adding Merchant Catalog or Coupon information will further enhance the recommendation of coupons to the users as well as improves revenue generation for the merchants

## Content
* /Explainer Dashboard --------------------------------------------- | Folder contains the explainer dashboard files of Bagging DecisionTreeClassifer() |
* /data                --------------------------------------------- | Folder contains the stratified shopping data |
* /notebook            --------------------------------------------- | Folder contains the EDA, Modeling and Explainer Dashboard notebooks |
* Shopping Coupon Recommendation using Ensemble Models - Read Out -- | Sumamry and Final Readout file of the Capstone Project Analysis |
* README.md            --------------------------------------------- | this readme file |

## Requirements
1. This project is implemented with Python 3.7.13
2. The final assignment is implemented in Google Colab and can be executed in any python notebook apps
3. The required packages and libraries with their versions are listed in the individual notebook files
