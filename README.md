# House price analysis

## Authors

Steve Vu

## Introduction

The project aims at studying and finding the critical factors impacting house prices in Ames, Iowa state before and after the 2007-2008 Financial Crisis. The dataset is here. There are 1465 recorded transactions in 2006-2010, and 79 predictor variables that describe almost every fundamental aspect of residential homes and sale conditions.

While the project confirms the importance of fundamental variables such as living areas, house quality, garage sizes, etc in appraisals of houses, the main research finding is that the critical market factor, time of selling houses, has a light impact on defining transaction prices of properties. As one reasonable reason for the strange phenomenon is the localisation and isolation of the house market in Ames, Iowa state, the project shows me a further research question of studying state-level data and verifying the market trend in Iowa state in 2006-2010.

## Methods

The project goes through four main steps of data visualization, data processing, feature engineering, and modeling. The exploratory data analysis (EDA) is to extract the initial insight of the dataset by systematically grouping graphs together. The data processing step is heavily into transforming categorical and ordinal variables into numeric variables, and coping with missing values as well as outliers. Missing values account for 5.8% of the dataset while there are two outliers being removed.
Before building up a regression model, the feature engineering is critical to standardize predictor variables and log transform the dependent variable in which the density is heavily right skewed. Lastly, I created a linear model with horseshoe prior regularization that is able to shrink the posterior for some regression coefficient more tightly towards 0. The model is as below.

![](https://github.com/SteveVu2212/House-Prices-Analysis/blob/main/Analysis_files/pictures/model.png)

In the model, the prior means that the coefficient <img src="https://render.githubusercontent.com/render/math?math=$\beta_{i}$"> is normally distributed with means of 0 and standard deviation of $\tau\lambda_{i}$. $\tau$ is a common global scale that shrinks all the coefficients $\beta_{i}$ toward zero. $\lambda_{i}$ is a local parameter that allows some of the coefficients $\beta_{i}$ to escape the shrinkage and follows a half-Cauchy of (0,1). $p$ is the number of predictor variables, $p_{0}$ is the expected number of significant predictors, and $n$ is the size of the dataset.

## Results
The posterior distribution and the DAG
