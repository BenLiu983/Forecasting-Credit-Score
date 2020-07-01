# Forcasting Credit Score of Loan Applicants in an Irish Bank

# Introduction
What major factors does the management team of a bank consider when they decide to grant a loan? Do they prefer to accept the loan application from clients with high income? These questions are preoccupying the minds of loan applicants around the world. Understanding this, I initiate to discover several factors which may play an important role in how a bank calculates the credit score of loan applicants, utilizing a mix of statistical analysis, visualization and machine learning models.

This project is based on a dataset that contains information about 1 million potential borrowers of a specific bank, which is a peer to peer lending bank based in Ireland. The complete dataset is from Lending Club, and it has been changed from Kaggle. The goal of this report is to extract business insights from the analysis of this large loan dataset. I am sharing this work to people who are interest in bank loans, to help them get a better understanding about the factors that may influence the credit score of a loan applicant.

# Methodology
First of all, I conducted exploratory data analysis and generated visualization. Then k-NN and Decision Tree are applied on the dataset to predict the credit score of loan applicants.

# Data
After feature selection, the target dataset contains nearly 1 million records and 10 major features, including 5 numeric features and 5 categorical features.
![readme_plot1](https://user-images.githubusercontent.com/64850893/86263267-fb0e7400-bb8e-11ea-94f4-0085db804bce.jpg)

# Exploratory Data Analysis (EDA)
I conducted descriptive analysis about these features respectively, by their statistical values or distribution plots. Then I further explored the correlation between the features 
![readme_plot2](https://user-images.githubusercontent.com/64850893/86263934-d8c92600-bb8f-11ea-90d7-1f41d2781c5d.jpg)

# PCA 
Before fitting the dataset with some machine learning models, it is necessary to analyze the relationship with "grade" and other 9 independent features. However, in addition to ’grade’, there are still 9 other features. The goal is tosummarize 9 features to 2 features, so that they can be shown in a 2 dimension intuitive graph. Therefore, principal component analysis (PCA) is utilized.
![readme_plot3](https://user-images.githubusercontent.com/64850893/86264357-660c7a80-bb90-11ea-8025-128464be5ceb.jpg)
 According to above plot, although there are overlaps, it is noteworthy that the color is becoming lighter from the left to the right in the plot. Therefore, it is feasible to classify the dataset with typical classification models.
 
 # Model 1  k-NN
 
