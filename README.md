# Neural Network Charity Analysis
## Overview of the analysis
Alphabet Soup is a non-profit philanthropic organization which has raised and donated over $10b in the past twenty years. Alphabet Soup analyzes the impact of each donation and vets potential recipients to ensure that the foundation's money is used effectively, and is interested in using machine learning to assist in the vetting process. The purpose of this analysis was to use machine learning and neural networks to develop a binary classifier capable of predicting whether applicants will be successful if funded by Alphabet Soup.

To complete this assessment, the following steps were performed:
- Preprocess the data for a neural network model
- Compile, train, and evaluate the model
- Optimize the model

## Results 
From Alphabet Soup’s business team, a CSV was provided which contains more than 34,000 organizations that have received funding from Alphabet Soup over the years. The dataset includes the following metadata about each organization:
- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

The goal of the machine learning process was to accurately predict whether an organization would be successful in their humanitarian endeavors when funded by Alphabet Soup. As such, the target variable for the model is the "IS_SUCCESSFUL" data. EIN and the name of each donation recipient organization are not relevant to the analysis and were therefore removed during preprocessing. The remaining variables - "APPLICATION_TYPE", "AFFILIATION", "CLASSIFICATION", "USE_CASE", "ORGANIZATION", "STATUS", "INCOME_AMT", "SPECIAL_CONSIDERATIONS", and "ASK_AMT" were considered as features for the model. 


| Attempt         | Loss          | Accuracy |
| -------------   | ------------- | -------- |
| Original - Train| 53.5%         | 74.1% |
| Original - Test | 55.7%         | 72.8% |
| #1 - Train      | 54.0%         | 74.0%   |
| #1 - Test       | 56.0%         | 72.5%  |
| #2 - Train      | 53.7%         | 72.5%  |
| #2 - Test       | 55.8%         | 72.5%  |
| #3 - Train      | 53.9%         | 74.0%  |
| #3 - Test       | 55.8%         | 72.7%  |
| #4 - Train      | 53.4%         | 74.2%  |
| #4 - Test       | 60.2%         | 72.5%  |

Using bulleted lists and images to support your answers, address the following questions.
Data Preprocessing
What variable(s) are considered the target(s) for your model?
What variable(s) are considered to be the features for your model?
What variable(s) are neither targets nor features, and should be removed from the input data?
Compiling, Training, and Evaluating the Model
How many neurons, layers, and activation functions did you select for your neural network model, and why?
Were you able to achieve the target model performance?
What steps did you take to try and increase model performance?

## Summary 
Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and explain your recommendation.
