# e-shop-ml-model
The "E-Shop Clothing EDA, Classification and Regression clickstream dataset" on Kaggle is a dataset that contains clickstream data from an online clothing retailer. The dataset includes information on user clicks, purchases, and other interactions with the retailer's website.

### Dataset 
This dataset is used for various purposes, including:

* Exploratory data analysis (EDA) to gain insights into user behavior on the website.
* Classification tasks such as predicting whether a user will make a purchase based on their clickstream data.
* Regression tasks such as predicting the total revenue generated by the website.

### Framework 
The CRISP-DM method is a structured approach to data analysis and can be applied to analyze the online eshop dataset. Here is a brief outline of how you can use the CRISP-DM method to compare various classifiers:
* Business Understanding: Define the problem trying to solve. In this case, the goal is trying to predict a price based on the given features. And classification model to classify whether the product is affordable or expensive?
* Data Understanding: Load the Portuguese bank marketing dataset into a Pandas DataFrame and explore the data. This includes cleaning the data and handling any missing values.
* Data Preparation: Prepare the data for modeling by splitting the data into training and testing sets and converting categorical variables into numerical data using one-hot encoding.
* Modeling: Train various classifiers using the training data and make predictions on the test data. Evaluate the performance of the models using metrics such as accuracy, precision, recall, and F1-score.
* Evaluation: Compare classifiers' performance to determine which is better suited for the problem at hand.
* Deployment: Use the best-performing classifier to make predictions on new, unseen data and put the model into production.

### Data
The dataset you will use comes from the [Kaggle E-shop Clothing Dataset](https://www.kaggle.com/datasets/adityawisnugrahas/eshop-clothing-dataset).

### EDA Report [eshop-notebook](https://github.com/anujg21/e-shop-ml-model/blob/main/Capstone.ipynb)
* Strong positive correlation between month and session ID (0.97)
* Price and price 2 seems to share negative correlation (-0.74). But why there is negative relation, I'm unsure for now.
* price and page 1 (main category) negative relation.
* The data is relatively balanced throughout the month, with slight clustering towards the start of the month because people tend to have more money to spend at the beginning of the month. Although, we don't know if the customers visiting this website were salaried or self-employed.
* Large concentration of data is noticeable in Poland and other European countries.
    * Countries outside of Europe have also seen E-shopping from this website, but the contribution is more negligible.
* Customers seem to be interested in neutral colors like black, blue, gray, white, and brown.
    * It may be an indication of higher sales of Trousers as, generally speaking, trousers are not fancy colors.
* Placements of pictures matter a lot. Every time we visit the webpage, we look at the image first.
    * An image at the top of the page captures more attention and draws subsequent actions.
* It's possible that the dataset contains images of models in different poses and that the "en face" and "profile" categories are used to help categorize these images.
    * The model's orientation in a clothing photograph can make a difference in how customers perceive the clothing.
    * En-face photos are more in the dataset than profile. Maybe the models photographed in an en-face position allow customers to see the clothing more clearly.
* The website got most visitor from the European countries Poland, Czech Republic and Lithuania.
* Trousers are most purchased product from the website following the blouses, sale and skirts.
    * Trousers are generating more revenue following skirts and blouses.
* Based on our previous analysis, we have identified that the most sold item on the website is Trousers and it has generated a revenue of over 2 million. Out of the total revenue, the Blue color Trousers alone have generated 1.2 million. In addition, Black color Skirts have also performed well and generated an overall value of 540k.
* No missing value. The data seems pretty good.
* The data appears to have a relatively even distribution and there are no outliers present.

### Data Preparation [eshop-notebook](https://github.com/anujg21/e-shop-ml-model/blob/main/Capstone.ipynb)
It comprises of many steps but remember to transform the data using the techiques in hand. 
* Normalization scales the data to be in the range of [0,1]. This is done by subtracting the minimum value of the feature and dividing it by the range of the feature.
* Standardization scales the data to have a mean of 0 and a standard deviation of 1. This is done by subtracting the mean of the feature and dividing it by the standard deviation of the feature.
* Both normalization and standardization are used to bring all the features to the same scale. This is important as KNN, and Logistic Regression models are sensitive to the scale of the features and can lead to incorrect predictions if features are on a different scale.
* Use the StandardScaler class from scikit-learn's preprocessing module to standardize your data. For normalization, you can use the MinMaxScaler class from the same module.
* Label Encoding is a transformation technique in scikit-learn library that is used to convert categorical data into numerical format. It assigns a unique integer value to each category in a categorical feature column. 

### Modeling [eshop-notebook](https://github.com/anujg21/e-shop-ml-model/blob/main/Capstone.ipynb)
Commpare Regression and Classification model. 
Linear Regression, Lasso and Ridge. 
Logistic Classification, KNN and SVC. 

### Conclusion [eshop-notebook](https://github.com/anujg21/e-shop-ml-model/blob/main/Capstone.ipynb)
#### Regression 
* Mean Squared Error (MSE): The average squared difference between the predicted and actual values is 33.55. This value is sensitive to outliers, and a higher value indicates a worse fit.

* Root Mean Squared Error (RMSE): The square root of the MSE is 6.92, which is a more interpretable measure of the model's performance. This means that the predicted values have an average deviation of approximately 6.92 units from the actual values.

* R-squared (R2) Score: This metric ranges from 0 to 1, where 1 indicates a perfect fit. The R2 score of 0.79 indicates that approximately 79% of the variability in the target variable can be explained by the Ridge regression model.

* Mean Absolute Error (MAE): The average absolute difference between the predicted and actual values is 4.38. This value is less sensitive to outliers compared to the MSE.

* Test Score and Train Score: These scores indicate the goodness of fit of the model on the training and test datasets, respectively. The values of 0.79 for both scores suggest that the model is performing relatively well on both the training and test datasets.

* Compared to the Lasso regression model, the Ridge regression model has a lower MSE, RMSE, and MAE, and a higher R2 score, indicating that the model may be more accurate in predicting the target variable. Additionally, the Ridge regression model may be more appropriate if there are many predictor variables that are all important to the model, as it can help with regularization by shrinking the coefficients of all predictors, but not to zero like the Lasso regression.
#### Classification 

* Looking at the metrics, we can see that all three models have high accuracy scores on both the training and test sets, indicating that they perform well on the given data. The precision, recall, and F1-score are also high for all three models, indicating that they have good performance in terms of correctly identifying the positive instances.

* The KNN model has the highest accuracy score on the test set, but it also took the longest time to train compared to the other models. The SVC model has the highest precision score, indicating that it has the lowest rate of false positives. The Logistic Regression model has the lowest precision score, but it has the fastest training time.
