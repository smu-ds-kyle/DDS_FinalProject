# DDS_FinalProject

# DDS Midterm Case Study - Fall 2024
Hi and welcome!  This repository serves as my midterm submission for Doing Data Science in the MSDS program at SMU.  

## Overview

The premise of this assignment was to simulate a client engagement project from start to finish.  Specifically, this project is for Frito-Lay, who wishes to predict employee attrition using their business data and has engaged us to help solve this problem. 

The final presentation to the client is in the **Presentation.pptx** power point file.  The recorded session can be found [here](https://smu.zoom.us/rec/share/84QO3jf6taja-BAaZxDFqx0sNgPAW7fcUZk2qzYmJAM4m-FKpNhgslIBUONUQK_d.irZiBCHSDQCA8Q2-?startTime=1730266751000).

Passcode: Np@4H!VX

## Requirements

The "client" has a few requirements for this project. 

 - 2 Models
	 - Naive Bayes or
	 - KNN
 - Metrics
	 - 60% specificity
	 - 60% sensitivity
 - Language
	 - R

## Files

The main file in the library is:  **MidTerm_EDA_Modeling.RMD**.  In it, you will find most of the final code used for the project.  It will be lengthly, as it reflects part of my iterative learning process.  I would try something out one day, let the code run for hours, only to come back and realize there was a better way after doing more research.  I thought it more helpful to keep the code iterations than to simply show the end product, at least in a school project setting.  The code is not necessarily "in order" neither would one expect to just run it all as is.  There may be some minor changes need if trying to run it for yourself, such as changing CSV file names where appropriate. 

The **Case Study Files** folder contains the project files as given in class. 

The **Feature Extraction Results** folder contains CSV files generated from varying feature extraction methods I wanted to try for the project.  This was *not* a requirement for the project, but was a rabbit hole I went down in pursuit of the best model.  In total, I tested over 65,000 different models.  The models in this folder represent the potential "best of the best" that I ran deeper analysis on.  The two best models are in **winners.csv.**

## Results

When all was said and done, I settled on two Naive Bayes models, with the following tuning params.  For table formatting, I will define the features/predictors outside the table:

 - Model #1 
	 - Age,JobInvolvement,JobRole,JobSatisfaction,MonthlyIncome_L,OverTime,StockOptionLevel,WorkLifeBalance
 - Model #2
	 - Department,JobInvolvement,JobLevel,OverTime,StockOptionLevel,WorkLifeBalance,YearsWithCurrManager

| Model | Sampling Method | Kernel | Adjust | Laplace |
|-------|-----------------|--------|--------|---------|
| M1    | up              | TRUE   | 3      | 3       |
| M2    | up              | TRUE   | 1      | 5       |

The predicted metrics for these models are show below, having a positive class of "YES" for Attrition:

| Model | Accuracy | Sensitivity | Specificity |
|-------|----------|-------------|-------------|
| M1    | .76      | .83         | .75         |
| M2    | .81      | .77         | .82         |

As can be see above, M2 has the better overall accuracy, but M1 has the better Sensitivity.  Because of this, a company may find M1 more useful in a business setting in which it is specifically looking for employees at high risk of leaving the company.  For the project, it made better sense to use M2 for the predictions as the goal was to get the most right, after meeting the minimum 60% in sensitivity and specificity.  Consequently, M2 was chosen to predict attrition in the competition set.  Those results can be found in **Case1PredictionsEVANS Attrition.csv.**
