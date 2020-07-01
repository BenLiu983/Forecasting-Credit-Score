# Forcasting Credit Score of Loan Applicants in an Irish Bank

# Introduction
What major factors does the management team of a bank consider when they decide to grant a loan? This question is preoccupying the minds of loan applicants around the world. Understanding this, I initiate to discover several factors which may play an important role in how a bank calculates the credit score of loan applicants, utilizing a mix of statistical analysis, visualization and machine learning models.

This project is based on a dataset that contains information about 1 million potential borrowers of a specific bank, which is a peer to peer lending bank based in Ireland. The complete dataset is from Lending Club, and it has been changed from Kaggle. The goal of this report is to predict the credit score of loan applicants with high accuracy, as well as drive business insights. 

# Methodology
First of all, I conducted exploratory data analysis and generated visualization. Then k-NN and Decision Tree were applied on the dataset to predict the credit score of loan applicants.

# Data
After feature selection, the target dataset contains nearly 1 million records and 10 major features, including 5 numeric features and 5 categorical features.
![readme_plot1](https://user-images.githubusercontent.com/64850893/86263267-fb0e7400-bb8e-11ea-94f4-0085db804bce.jpg)

# Exploratory Data Analysis (EDA)
I conducted descriptive analysis about these features respectively, by their statistical values or distribution plots. Then I further explored the correlation between the features.
![readme_plot2](https://user-images.githubusercontent.com/64850893/86263934-d8c92600-bb8f-11ea-90d7-1f41d2781c5d.jpg)

# PCA 
Before fitting the dataset with some machine learning models, it is necessary to analyze the relationship between "grade" and other 9 independent features. The objective is to summarize 9 features to 2 features, so that they can be shown in a 2 dimension intuitive graph. Therefore, principal component analysis (PCA) is utilized.
![readme_plot3](https://user-images.githubusercontent.com/64850893/86264357-660c7a80-bb90-11ea-8025-128464be5ceb.jpg)
According to above plot, although there are overlaps, it is noteworthy that the color is becoming lighter from the left to the right in the plot. Therefore, it is feasible to classify the dataset with typical classification models.
 
 # Model 1  k-NN
Before applying k-NN to the original loan dataset, I scaled the dataset by 3 statistical methods, Min-Max Scaling, Standard Scaling and Robust Scaling.
![readme_plot4](https://user-images.githubusercontent.com/64850893/86265486-d2d44480-bb91-11ea-90b3-b1e101034852.jpg)
By the above results, the Min-Max scaling will be applied in the following cases.

It is ideal to utilize the raw dataset for all parts of analysis, however, since this is a 880,000 * 9 dataset, the computation cost is heavy. In fact, it takes about
20 minutes to compute the results in the last table. To explore how the parameters of k-NN affects its prediction accuracy efficiently, modification is necessary. Therefore, PCA will be utilized to decrease the number of dimensions in the dataset.
![readme_plot5](https://user-images.githubusercontent.com/64850893/86265936-79204a00-bb92-11ea-97c4-00cb86023f74.jpg)
According to the above graph, Choosing N=5 as PCA components makes most sense, since it increases the efficiency by around 150 times at the cost of about 2% of prediction accuracy, compared to the case when N=9.

The next step is to tune the parameters of k-NN to increase the prediction accuracy, take the number of k-NN neighbors for example.
![readme_plot6](https://user-images.githubusercontent.com/64850893/86266446-3c088780-bb93-11ea-82e8-2eaec34fc3b0.jpg)

After multiple experiments by changing different parameters, it can be concluded that the optimal prediction accuracy of the credit score "grade" by k-NN is 86.7%, when the scaling method is Min-Max, the test size is 0.1, the weight is "distance", the number of neighbors is 15, the type of distance is manhattan and PCA_N=9 (original dataset).

# Model 2 Decision Tree
To discover if there is any room for improvement of the prediction accuracy, the Decision Tree model is implemented. It is noteworthy that the Decision Tree is invariant to the scaling of the data, so preprocessing steps like Min-Max scaling are not necessary. In addition, implementing Decision Tree on the raw dataset takes only few seconds, therefore, there is no need to conduct PCA.

Similarly, I tuned the parameters of Decision Tree to increase the prediction accuracy, take the maximum depth for example.
![readme_plot7](https://user-images.githubusercontent.com/64850893/86267279-77578600-bb94-11ea-8797-97e7c0ce9cdb.jpg)

One of the advantages of the Decision Tree model is that it is easy to interpret and visualize. For this loan dataset, the prediction accuracy achieves 95.8% when the max depth is 15. The visualization of a decision tree with 15 layers of nodes is a little bit messy. To clearly demonstrate how each node is split by a specific feature, I visualized the process of a decision mdoel when max depth is 4.
![readme_plot8](https://user-images.githubusercontent.com/64850893/86267758-33b14c00-bb95-11ea-8d0f-b8718f644f3a.jpg)

It is noteworthy that in the optimal Decision Tree model for this loan dataset, the "interest rate" takes up a considerable percentage of importance among all 9 features, based on the following table.
![readme_plot9](https://user-images.githubusercontent.com/64850893/86268012-8e4aa800-bb95-11ea-82c5-a77f699f4611.jpg)

After multiple experiments by changing different parameters of the Decision Tree model, it can be concluded that the optimal prediction accuracy of the credit score "grade" is 95.7, when the max depth is 15 and others are set as default values.

# Conclusion
The prediction accuracy of the optimal k-NN model achieves 85.8%. It is not influenced by correlation of different features, taking test data as a cumulative features in a
way of a distance. However, a disadvantage of k-NN model is that, it is somewhat difficult to interpret the relationship between the response feature and the independent
features. Therefore, the Decision Tree algorithm is utilized, and the relevant optimal prediction accuracy increases to 95.7%. But it is noteworthy that the feature "interest rate" has a considerable influence on the response feature "grade". If the feature "interest rate" is removed, the performance of the Decision Tree model drops dramatically. Therefore, there is a trade-off in applying these 2 models in this loan dataset, where the k-NN model is more robust and the Decision Tree model is easier to interpret.

# Future work
In the future investigation, I will attempt to study how the feature "loan condition" (good or bad) is influenced by other features. Additionally, more machine learning models with different parameters would be experimented.
