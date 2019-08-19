# Trees

Analyzing and Predicting Tree Growth in Roosevelt National Forest in Colorado


# Data

565,892 observations made from 4 (30x30m) areas of the forest. 64 Features recorded including soil type, elevation, distance from water, and many others. The 7 types of trees I am trying to predict based on the information provided by all the other features are:
  1. Lodgepole Pine - 48.76%
  2. Spruce/Fir     - 36.46%
  3. Ponderosa Pine - 6.15%
  4. Krummholz      - 3.53%
  5. Douglis-Fir    - 3%
  6. Aspen          - 1.63%
  7. Cottonwood/
     Willow Populus - 0.47%
     
This data has been processed many times before by many more talented data scientists than myself. The purpose of predicting which trees would grow well would benefit missions of reforestation, and ecosystem maintenance. 

The most important features that I examined from this dataset were elevation, soil types (of which there were 40), the amount of shade recorded at 3 different times per day, the slope of the land, distance from the road, distance from water, and distance from the fire point, as well as the area the tree was growing. 

Elevation was by far the most predictive feature of the entire dataset with a correlation of .70 with tree type. 

# Feature Engineering

I created several derivations of features like squaring the hillshade values, finding the mean of the hillshade value, and finding the logarithm of elevation. These three features specifically had high multicollinearity and were dropped during feature selection. Useful features included the acidity of the soil type, which I derived from researching the quality of the soils listed. I also sorted the soils by the degree of how stony they were labeled in their descriptions, which ranged from very stony, to extremely stony, to bouldery, and even rubbly. I binned elevation and fire point distance, which both proved useful during modeling. 

# Feature Selection

I used the F Test as well as Lasso to evaluate the feature's usefulness. The top 10 features according to the F test were Elevation, Slope, Distance to Road, Areas 1 and 4, Soil Types 10, 38, 39, the category of stoniness of the soil, and the elevation binned. 

The lasso test validated that Areas 1 & 4, Soil Types 10, 38, and 39 and elevation binned had predictive value. 

# Training Models

I did a train-test split of 80/20 for all of my models, and did downsampling since I had plenty of datapoints. My worst performing model was the decision tree, and my best performing model was my baseline XGBoost model, which had an F1 of 0.74 and an accuracy of 0.74. My Random Forest model had an accuracy of 0.75 and an F1 of 0.70. 

