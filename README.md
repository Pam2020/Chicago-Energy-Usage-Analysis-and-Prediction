# DATA602 Final Project: Chicago Energy Usage Classification problem

A machine learning project using the Chicago energy consumption data retrieved from the Chicago data portal. This is implemented as a part of DATA 602 course on introduction to machine learning. 

## Data Description

The data comprises the energy usage in households, businesses, and industries in Chicago in the year 2010. The dataset consists of electricity and gas used for the months, characteristics of the distribution of usage over these months, and data related to building and occupancy characteristics. 
The dataset has 67051 instances and 73 attributes. 

The data can be found in the "Data" folder in this repository. 

## Problem Statement

Typically, energy usage depends on a lot of factors including the size of the building, occupany, and utility. In our data, we have some of these characterstics along with the energy consumption recorded. The building type variable categorizes the building as residential, commercial and industrial. In this study, I will try to predict the building type based on the energy consumption statistics and the building characterstics given in the data. This would be a multi-class classification problem. 

## Exploratory Data Analysis Findings

As a part of EDA, preliminary data processing is done where the duplicate columns are dropped and data types are corrected. Columns that give similar information and those that are higly correlated are also dropped as they would not be very helpful for modeling. This process brings down the number of columns to 44. However, the original dataset with 73 columns will also be used in the modeling along with dimensionality reduction techinques and compared to the model performance using the reduced dataset.

We also infer that the target variable distribution is higly imbalanced. This fact would be helpful in modeling and model evaluation phases. It is also observed that there are a lot of outliers in the total energy and gas consumed. These outliers will be handled before the modeling is done based on further study. 

#### Some key observations include: 
1. The energy and gas used are maximum in commercial buildings. However, the distribution has more deviation for the commercial buildings. There are more number of outliers for energy usage in commercial buildings. 
2. Community area has a strong influence on the energy consumed. This is expected as each community will have a specific type of buildings grouped i.e if a community has residential buildings, it is unlikely that there would be a commericial or industrial building in that community. Therefore, community area is an important feature to predict building type. 
3. Building age seems to be maximum for residential buildings. However, the distribution is more spread out for commercial buildings. Most of the industrial buildings are fairly new. This could be a reasonable parameter for classification. 
4. Contradictory to our intuition, the average building size for residential and commercial buildings show similar distribution. The building sizes for industrial buildings seem to be lesser than residential and commercial ones. 

## Next steps

The following will be done before the modeling phase:
1. The outliers in different columns observed during the EDA will be handled. 
2. Majority of the data is numerical and are widely ranged. Therefore, the data needs to be standardized when building pipelines. 
3. Missing values will be handled with pipelines. 










