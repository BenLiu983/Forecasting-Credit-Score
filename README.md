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
Before applying k-NN to the original loan dataset, I scaled the dataset by 3 statistical methods, Min-Max Scaling, Standard Scaling and Robust Scaling.
![readme_plot4](https://user-images.githubusercontent.com/64850893/86265486-d2d44480-bb91-11ea-90b3-b1e101034852.jpg)

It is ideal to utilize the raw dataset for all parts of analysis, however, since this is a 880,000 * 9 dataset, the computation cost is heavy. In fact, it takes about
20 minutes to compute the results in Table 3. To explore how the parameters of k-NN affects its prediction accuracy efficiently, modification is necessary. Therefore, PCA will be utilized to decrease the number of features in the dataset.
![readme_plot5](https://user-images.githubusercontent.com/64850893/86265936-79204a00-bb92-11ea-97c4-00cb86023f74.jpg)
According to the above graph, Choosing N=5 as PCA components makes most sense, since it increases the efficiency by around 150 times at the cost of about 2% of prediction accuracy, compared to the case when N=9.

