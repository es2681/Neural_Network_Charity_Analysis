# Neural Network Charity Analysis
## Overview of the analysis
Alphabet Soup is a non-profit philanthropic organization which has raised and donated over $10b in the past twenty years. Alphabet Soup analyzes the impact of each donation and vets potential recipients to ensure that the foundation's money is used effectively, and is interested in using machine learning to assist in the vetting process. The purpose of this analysis was to use machine learning and neural networks to develop a binary classifier capable of predicting whether applicants will be successful if funded by Alphabet Soup.

To complete this assessment, the following steps were performed:
- Preprocessing the data for a neural network model
- Compiling, training, and evaluating the model
- Optimizing the model

## Results 
From Alphabet Soup’s business team, a CSV file was provided which contains data on more than 34,000 organizations that have received funding from Alphabet Soup over the years. The dataset includes the following metadata about each organization:
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

#### Preprocessing the Data
The goal of the machine learning process was to accurately predict whether an organization would be successful in their humanitarian endeavors when funded by Alphabet Soup. As such, the target variable for the model is the "IS_SUCCESSFUL" data. EIN and the name of each donation recipient organization are not relevant to the analysis and were therefore removed during preprocessing. The remaining variables - "APPLICATION_TYPE", "AFFILIATION", "CLASSIFICATION", "USE_CASE", "ORGANIZATION", "STATUS", "INCOME_AMT", "SPECIAL_CONSIDERATIONS", and "ASK_AMT" were considered as attritube features for the model. 

Of the categorical attribute features, there were two attributes that included a wide variety of datapoints - there were 17 different types of applications submitted to Alphabet Soup and 71 different classifications for the various donation recipients. As such, data was binned together for the "APPLICATION_TYPE" and "CLASSIFICATION" variables to condense the number of variables. Application types with less than 500 submissions to Alphabet Soup were binned together in an "other" category which reduced the total number of application types from 17 to 9. Classification types with less than 1000 organizations identified as such were binned together in an "other" category which reduced the total number of classification types from 71 to 6. Binning these two variable categories makes the data easier to manage for the model. 

#### Compiling, Training, and Evaluating the Model
After binning was completed and categorical variables were transformed using OneHotEncoder, the data had 43 columns of attribute features. A general rule of thumb is to multiply the number of attributes by 2 or 3 to determine the number of neurons to use in hidden layers. As such, 80 neurons were used in the first hidden layer of the neural network. A second layer was also included in the model with 30 neurons. A relu activation function was used for each of the two hidden layers, while a sigmoid activation function was used for the final output layer. With these parameters, the training data had a loss rate of 53.5% and an accuracy of 74.1%, while the testing data had a loss rate of 55.7% and an accuracy of 72.8%.

Ideally, Alphabet Soup is looking for a model that has an accuracy rate of at least 75%. In an attempt to improve the prediction capabilities of the model, various features were tweaked as described below:
- **Attempt #1: Reducing the number of bins** - As described above, during preprocessing of the original model, the number of application types were binned together so that the 17 types were reduced to 9. I binned the data further by combining application types with less than 1000 submissions into a single "other" category. This dropped the number of application types further to only 6. This number of application type bins will remain the same for all other attemps.  
- **Attempt #2:Using different activation functions for the hidden layers** - In the original model, the relu activation function was used for the hidden layers. In this attempt, I changed the activation function to tanh.
- **Attempt #3: Adding an additional hidden layer** - The first model used two hidden layers. In this attempt, I added a third hidden layer with 10 neurons. 
- **Attempt #4: Adding additional epochs** - The original model (as well as all other attempts), evaluated the training data over 100 epochs. In this attempt, I increased the number of epochs to 500. 

Below is a summary of the loss and accuracy percentages for the training and testing data in each attempt. 

**Summary**
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

## Summary 
None of the four attempts were able to increase the accuracy to at least 75%. Further, none of the attempts were able to successfully make any significant improvements to the loss rate or accuracy of the original model. The loss rate increased significantly in the fourth attempt in which the number of epochs was increased from 100 to 500. Going forward, I think I would try to reduce the number of attribute features in the model. It's possible that many of the attributes included do not have a significant impact on the success of a donation and create extra noise for the model. I would also like to increase the number of neurons in the first hidden layer. Best practices indicate that the number of neurons should be able double or triple the number of attributes in the model. We  had 43 attributes and roughy doubled that number to come up with 80 neurons in the first hidden layer. I would like to triple the number of attibutes and see if 120 neurons in the first hidden layer makes an impact on the accuracy. 
