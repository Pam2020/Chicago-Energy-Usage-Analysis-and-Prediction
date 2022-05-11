# DATA602 Final Project: Chicago Energy Usage Classification problem

A machine learning project using the Chicago energy consumption data retrieved from the Chicago data portal. This is implemented as a part of DATA 602 course on introduction to machine learning. 

## Data Description

The data comprises the energy usage in households, businesses, and industries in Chicago in the year 2010. The dataset consists of electricity and gas used for the months, characteristics of the distribution of usage over these months, and data related to building and occupancy characteristics. 
The dataset has 67051 instances and 73 attributes. 

The data can be found in the "Data" folder in this repository. 

## Problem Statement

Typically, energy usage depends on a lot of factors including the size of the building, occupany, and utility. In our data, we have some of these characterstics along with the energy consumption recorded. The building type variable categorizes the building as residential, commercial and industrial. In this study, I will try to predict the building type based on the energy consumption statistics and the building characterstics given in the data. As the data for industrial buildings is very less (less than 0.1%) compared to the other two classes, I will be merging the Commercial and Industrial classes to form a single class named 'Non-Residential'.

## Exploratory Data Analysis Findings

As a part of EDA, preliminary data processing is done where the duplicate columns are dropped and data types are corrected. Columns that give similar information and those that are higly correlated are also dropped as they would not be very helpful for modeling. This process brings down the number of columns to 44. However, the original dataset with 73 columns will also be used in the modeling along with dimensionality reduction techinques and compared to the model performance using the reduced dataset.

We also infer that the target variable distribution is higly imbalanced. This fact would be helpful in modeling and model evaluation phases. It is also observed that there are a lot of outliers in the total energy and gas consumed. These outliers will be handled before the modeling is done based on further study. 

#### Some key observations include: 
1. The energy and gas used are maximum in commercial buildings. However, the distribution has more deviation for the commercial buildings. There are more number of outliers for energy usage in commercial buildings. 
2. Community area has a strong influence on the energy consumed. This is expected as each community will have a specific type of buildings grouped i.e if a community has residential buildings, it is unlikely that there would be a commericial or industrial building in that community. Therefore, community area is an important feature to predict building type. 
3. Building age seems to be maximum for residential buildings. However, the distribution is more spread out for commercial buildings. Most of the industrial buildings are fairly new. This could be a reasonable parameter for classification. 
4. Contradictory to our intuition, the average building size for residential and commercial buildings show similar distribution. The building sizes for industrial buildings seem to be lesser than residential and commercial ones. 

## Feature Processing

Features in the dataset are processed before the modeling phase. My dataset has a majority of numerical features that have a lot of outliers. Firstly, I handle the outliers by capping them using the 97% value. This reduces the range of the numerical values facilitating better modeling. Secondly, some of the columns that are highly correlated are dopping to reduce the feature set to 23. This helps achieve managable run times. 

I also combine the 'Industrial' and 'Commercial' classes in the target varible to form a new class named 'Non-Residential'. This reduces my problem to a binary classification problem. 

## Modeling

I have chosen a few classifers to solve this classification problem and compared their evaluation scores to find the best model for this problem. I use the GridSearchCV to perform cross-validation and hyperparameter tuning. The model parameters that optimize the precision macro score are chosen to be the best parameters for the classifier. The different classifiers explored are:

1. **Logistic Regression**: I start with this model as this is the simplest classifier model for binary classification. I have built logistic regression models with and without using PCA as a pre-processing step. Contrary to my expectation, including PCA takes longer time to run. This makes sense as my data is large and performing a GridSearch on large dataset can be computationally expensive. 
2. **Decision Tree**: The simplest model for classifiaction is the Decision tree. I again build decision trees with and without using PCA as a pre-processign step. 
3. **Random Forest**: Random forests are more complex but can give better results as they average the scores for different decision trees. However, this can also be computationally expensive. 
4. **Stochastic Gradient Descent Classifier**: As I notice longer runtimes for my dataset, I decide to include the SGDClassifier with loss as 'hinge'. This is more efficient than Support vector machine model for my dataset. 

These models are evaluated based on the F1 score, precision, recall and roc auc scores. The code for modeling can be found in the 'Chicago_Energy_Modeling.ipynb' notebook. 

## Results

Based on my analysis, the Random forest model gives the best scores. However, this model takes nearly 10 minutes to run. The next best model is the Logistic regression model. Logistic regression model with and without PCA perform similarly. Therefore, I conclude that Logistic regression is a good enough model when working with limited computational capability. 

![Results](https://github.com/Pam2020/DATA602-FinalProject-ChicagoEnergy/blob/main/Images/Results.PNG)

## Further Explorations

The following are some things that can be done to improve model performance:

1. More nuanced feature engineering to improve the features that are used for modeling. 
2. Pre-processing using KMeans or other methods can be implemented. 
3. Splitting the data into train, validation and test, followed by training and evaluating the models manually can be useful in reducing run times. GridSearch can be computationally expensive for large datasets and might not be an ideal way to go about hyper-parameter tuning.  
4. More nuanced models such as SVM or Neural Networks can be used if the computational capacity exists to run them on large datasets.
5. Ensemble models where different classifiers can work together to make predictions can be used to for better performance.












