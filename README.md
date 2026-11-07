# Airline_Satisfaction
### Kristen Roggenbauer

## The Problem

In today's world, flying is second-nature for so many people.
* Weekend getaway? Take a quick flight!
* Going across the country for work? Hop on a plane!
* Happy Holidays! Time to fly to see the family!

Millions of people fly each year to many places for many reasons, with a variety of different wants, needs, and goals. However, to an airline, the goal is the same for each passenger:

<center><b>Get the passenger where they need to go safely, and get them there satisfied and happy, ready to book another flight.</b></center>

Getting them there safely? That's the easy part. But ensuring they make it there happy... to do that, we need to understand a whole different issue.

<center><b>What makes a passenger satisfied when on a flight?</b></center>

To do this, one must predict satisfaction, the response variable, using a variety of predictors.

## Finding a Solution

To answer this question, I first explored the data. After exploring the many potential predictors, I used 3 main methods:
1. Logistic Regression
2. Random Forest
3. LightGBM

**1. Logistic Regression**

When performing logistic regression, I removed 3 columns: id (as this was an identifier, not a predictor), satisfaction (as this was the response, not a predictor), and arrival delay in minutes (as this variable had missing values, was strongly correlated to departure delay in minutes, and was not correlated with satisfaction). However, all other columns were used. My first iteration of this model used a 70% training and 30% testing split:

With my logistic regression model, I achieved a ROC AUC score of 0.9216. 

Following this, I used 5-fold Cross Validation with logistic regression, which achieved a ROC AUC score of 0.9214 - slightly lower than the previous score. However, I used Cross Validation for the other models, so I decided to keep this score for comparisons.

**2. Random Forest**

A random forest model creates many decision trees to create an overall model which predicts the satisfaction of flyers. This model again used all variables except satisfaction, id, and arrival delay in minutes. My parameter selection and explanation is shown within the code document. 

With my random forest model, I achieved a ROC AUC score of 0.9568.

This AUC score is much higher than my baseline logistic regression model (~0.035 higher), showing that it does better predict the satisfaction.

**3. LightGBM**

A LightGBM model creates one decision tree vertically, then sequentially creates another to correct the errors from the first. It repeats this process many times to create many decision trees. This model again used all variables except satisfaction, id, and arrival delay in minutes. My parameter selection and explanation is shown within the code document. 

Wth my LightGBM model, I achieved a ROC AUC score of 0.9584

This AUC score is much higher than my baseline (\~.037 higher) and is higher than my random forest model (\~0.0024 higher), showing that it does better predict the satisfaction than both previous attempts. While I continued attempting to tweak this model, discussed further in the code document, this was ultimately the best choice for AUC score, interpretability, and computational speed.

## My Results

I submitted the file to Kaggle using my LightGBM model and achieved a public ROC AUC score of 0.95767. Following the completion of the competition, when more data and true scores were released, my model ultimately received a private ROC AUC score of 0.95897, showing that my model performed slightly better. This result put me at 2966th place out of 3734 submissions. While I wish I had been able to climb the leaderboard a bit more and break the 0.96 barrier, for my first Kaggle competition I am extremely happy with the results and I hope to improve more as I explore more Kaggle competitions in my future. 





