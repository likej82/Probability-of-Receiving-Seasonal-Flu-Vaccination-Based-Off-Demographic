# Probability of Receiving Seasonal Flu Vaccination Based Off Demographic
![Alt text](https://raw.githubusercontent.com/likej82/vaccination_models/Gina/images/H1N1.webp)
## Overview:
As the world struggles to vaccinate the global population against COVID-19, an understanding of how people’s backgrounds, opinions, and health behaviors are related to their personal vaccination patterns can provide guidance for future public health efforts. The 2009 H1N1 pandemic caused between 43 million and 89 million cases of H1N1 between April 2009 and April 10, 2010. There were also between 195,000 and 403,000 H1N1-related hospitalizations during that time.
## Business Problem:
As a large pharmaceutical company, that wants to increase the likihood of someone recieving a vaccine, knowing the demographic of people who are less likely recieve a vaccine, could have some insight on who to "target".
## Data Understanding:
Our dataset is from a National 2009 H1N1 Flu Survey. 
The survey was sponsored by the CDC and the National Center for Immunization and Respiratory Diseases (NCIRD). The NHFS was conducted from October 2009 to June 2010. It was a state-based random-digit-dialed survey of over 29,000 households each month. The survey was about the swine flu, also known as the H1N1 flu. 

The dataset also has some limitations such as: 

<u><b>Missing Values:</b></u>

12,274 missing values out of 26,707, in the "health_insurance" column as well as 13,330 missing values out of 26,707 in the "employment_industry" column and 13,470 missing values from the "employment_occupation" column. 


<u><b>Coded Columns:</u></b>

The columns "hhs_geo_region", "employment_industry" and "employment_occupation" were coded and we were unable to decipher them. 

<u><b>High Coerrelation:</u></b>

From common knowledge we were able to see that the columns "health_insurance", "doctor_recc_h1n1" and "doctor_recc_seasonal" has a high correlation, considering if you don't have health insurance, you more than likely do not have a primary doctor, so having a doctor reccomondation would be impacted by health insurance. As well as the columns "education" and "income_poverty" are impacted by each other. So taking caution in choosing columns based off this knowledge.

<u><b>Bias:</u></b>

The column "race" is heavily skewed. Knowing America is 75% "white" (https://www.census.gov/quickfacts/fact/table/US/PST045222) and our data showing that 80.4% of people catergorized themselves as "white" shows us heavy bias and from that we are unable to get a clear idea of probability from different races and vaccination rates.

<u><b>Outdated:</u></b>

This survey is from 2009, while in the year 2023, we know that the Corona Virus had a huge impact on the perception of vaccines as well as behaviors like large gatherings and wearing masks, so some of these can't be translated to present day.
## Data Cleaning:

Started by joining data sets and dropping 28 irrelevant columns and dropping the rows with missing values since it was less than 10% of null. Renamed columns for easier understanding. Seperated our data into a train test split and created a Dummy Classifier for a baseline model. Which had an accuracy score of 53%. Created a Logistic Regression model with all features that had an accuracy score of 75%. If we can create a model within both of those accuracy percentages, we can claim a succesful model. Creating a decision tree to show the top features that are most important to the "vaccine" column. From that removed the features that consited of opinions because its not a "targetable demographic". After the second decision tree model we see that top features that are most important to the "vaccine" column is "age", "education" and "gender". With those top features we run a second Logist Regression model and have an accuracy score of 63.40%. Now to run the final test on the X_test. We preformed a final Logistic Regression model and find our accuracy score is 63.31%. We also plotted a violin graph and split the class "0" and "1" to show the accuracy score as well. "0" being 74% and "1" being 52%. The combined average score of both equals 63.31%. Which is confirmation of our final model accuracy.
Then gathering the average probability of each feature we can see which demographics are less likely to receive the seasonal vaccine.

## Visual Analysis: ##

- Our first Dummy Model shows that the probability of one getting the seasonal vaccine is more likely "0" (not getting vaccine)

![](https://github.com/likej82/vaccination_models/blob/Gina/images/Dummy.png?raw=true)

- As well as our CV model having an accuracy score of 53%

![](https://github.com/likej82/vaccination_models/blob/Gina/images/Dummy_model.png?raw=true)



- Including all the features into a Confusion Matrix
![](https://github.com/likej82/vaccination_models/blob/Gina/images/LogRegAllFet.png?raw=true)


- Plotting our ROC curve to see the potential between the two
![](https://github.com/likej82/vaccination_models/blob/Gina/images/ROC.png?raw=true)

- On to our first Decision Tree with box plots, we can see the most relevant features.

![](https://github.com/likej82/vaccination_models/blob/Gina/images/AllFetImport.png?raw=true)

![](https://github.com/likej82/vaccination_models/blob/Gina/images/DTAll.png?raw=true)

- Next we take use the "targetable demographics" based on domain knowledge
![](https://github.com/likej82/vaccination_models/blob/Gina/images/Demo.png?raw=true)

![](https://github.com/likej82/vaccination_models/blob/Gina/images/DTDemoj.png?raw=true)

- Our final Confusion Matrix based off our top 3 demographics has an accuracy score of 63%
![Alt text](https://github.com/likej82/vaccination_models/blob/Gina/images/LogRegConMa.png?raw=true)

- Our final Violin Plot shows the "vaccine" classes "0" & "1" accuracy scores of almost 74% and 52%
![](https://github.com/likej82/vaccination_models/blob/Gina/images/ViolinProb.png?raw=true)


## Findings: ##
From our final analysis we can see the demographic to best "target" is:
- Age: 18 - 34 Years

- Education: Less than a High School Dipolma

- Gender: Male

## Recommendations: ##
For a company that is looking to incease vaccination rates we recommend focusing on:

- Younger people (18 - 34). They are 40% less likely to be vaccinated.
- Early stages of education. People with less than a High School Diploma are 11% less likely to be vaccinated.
- Men more than women. Men are 8% less likely to be vaccinated.
## Future Insights: ##
- How has COVID changed seasonal flu behavior?
- Why do certain groups get vaccinated less?
- Perform a more comprehensive survey

## For more information: ##
Please view our full analysis in our [Jupyter Notebook](https://github.com/likej82/vaccination_models/blob/Gina/Master.Notebook.ipynb) as well as our [Presentation](https://github.com/likej82/vaccination_models/blob/main/presentation/Seasonal%20Flu%20Vaccination%20Project%20Presentation.pdf)

Contacts
Gina Guerin - Gina.b.guerin@gmail.com

Wes Smolen - Wjsmolen@gmail.com

Namsoo Lee - Likej1218@gmail.com

## Repository Structure ##

You are in the README.md. The 'Master.Notebook.ipynb' contains the jupyter notebook that explains our data science steps for you to replicate! Our 'Presentation.pdf' contains our google slides presentation that sums up important information for our audience. In 'data' you will be able to see the dataset we worked with. Likewise, 'Images' will contain images used in this 'README.md' generated from code and as well as from the web.


```bash

├── Data                             <- Data file used in this project
├── Images                           <- Images and Graphs used in this project obtained from external and internal source
├── .gitignore                       <- Contains list of files to be ignored from GitHub
├── Presentation.pdf                 <- Slide Presentation of the project
├── README.md                        <- Contains README file to be reviewed
└── Master.Notebook.ipynb                   <- Jupyter notebook of the project containing codes and analysis


```
