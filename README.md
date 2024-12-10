# COF Database project
Data and context can be found on this paper: [https://pubs.acs.org/doi/epdf/10.1021/acs.chemmater.8b01425?ref=article_openPDF](https://pubs.acs.org/doi/10.1021/acs.chemmater.8b01425)


#### -- Project Status: [On-hold]


## Project Intro/ Objective
This project attempts to find insights and predict methane uptake capacity of covalent organic frameworks via a regression model.


## Project Description


First, I wanted to visualise the data to understand the trends and outliers. This includes:
- a report of min, max and all categorical variables
- boxplots of continuous values
- histograms of discrete values 


Then, the data was visualised using a <code>sns.relplot()</code> to show the relationship of predictors to the response (y = AbsMU_high_P_[molec/unit_cell])
and color-coded by bond types. 


The data was then organised into X and y and using a random forest to find feature importance based on mean decrease of purity. This was done to reduce the dimensionality from <i>p</i>=1116. A threshold of 0.001 was used to chose important features, with supercell volume being the most important.


Many algorithms were assessed for selection. Algorithms (from <code>sklearn</code>) were trialed using default parameters with RepeatedKFold cross-validation (<code>n_splits</code> = 5, <code>n_repeats</code> = 10) include:
- Linear Regression
- Decision Tree
- ensemble methods:
  -   Random Forest
  -   AdaBoost
  -   Bagging
  -   GradientBoosting
  -   XGBoost <-- using the XGBoost library
- SVR
- KNeighbors


Evalution of each algorithm includes:
- metrics: Averages, train and validation scores printed
  - mean_absolute_error
  - mean_square_error
  - root_mean_square_error
- Plots
  - Learning Curves (scoring = RMSE)
  - Regression Predictions of simulated data and predicted data


Random Forest had the best performance so was this algorithm was selected. Hyperparameter tuning using Optuna evaluated on held-out test set.


To make predictions, a property algorithm was developed using tools from scikit-learn and xgboost.


### Objective
- Curate large dataset
- Trained ML algorithm to predict target property
- Select optimal algorithm for material representation
- Validate algorithm
- Developed an assessment protocol informed by construction of model


