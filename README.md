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

The next step is to tune the parameters of k-NN to increase the prediction accuracy, take the number of k-NN neighbors for example.
![readme_plot6](https://user-images.githubusercontent.com/64850893/86266446-3c088780-bb93-11ea-82e8-2eaec34fc3b0.jpg)

In conclusion, the optimal prediction accuracy of the credit score "grade" by k-NN is 86.7%, when the scaling method is Min-Max, the test size is 0.1, the weight
is "distance", the number of neighbors is 15, the type of distance is manhattan and PCA_N=9 (original dataset).

# Model 2 Decision Tree
To discover if there is any room for improvement of the prediction accuracy, another model, the Decision Tree is implemented. It is noteworthy that the Decision Tree is invariant to the scaling of the data, so preprocessing steps like Min-Max scaling are not necessary. In addition, implementing Decision Tree on the raw dataset takes only few seconds, therefore, there is no need to conduct PCA.

Similarly, I tuned the parameters of Decision Tree to increase the prediction accuracy, take the maximum depth for example.
![readme_plot7](https://user-images.githubusercontent.com/64850893/86267279-77578600-bb94-11ea-8797-97e7c0ce9cdb.jpg)

One of the advantages of the Decision Tree model is that it is easy to interpret and visualize. For this loan dataset, the prediction accuracy achieves 95.8% when the max depth is 15. The visualization of a decision tree with 15 layers of nodes is a little bit messy. To clearly demonstrate how each node is split by a specific feature, I visualized the process of a decision mdoel when max depth is 4.
![readme_plot8](https://user-images.githubusercontent.com/64850893/86267758-33b14c00-bb95-11ea-8d0f-b8718f644f3a.jpg)

