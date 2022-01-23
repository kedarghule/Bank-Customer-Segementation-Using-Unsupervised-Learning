# Bank-Customer-Segementation-Using-Unsupervised-Learning

## Problem Statement

The problem statement is to develop a customer segmentation, i.e. to identify different groups of customers with similar spending behaviour, to define a marketing strategy for the bank. By understanding customers, companies can launch targeted marketing campaigns that are tailored to the specific needs of the customer.

## Dataset

The dataset used for this project can be found at this [link](https://www.kaggle.com/arjunbhasin2013/ccdata).

## Data Cleaning Process

- The dataset has 1 missing value for CREDIT_LIMIT and 313 missing values for MINIMUM_PAYMENTS.
- We perform imputation by replacing the missing values in CREDIT_LIMIT with the median value and replacing the missing values in MINIMUM_PAYMENTS with the mean value.

## Data Preprocessing

- **Handling Skewness**: We observe that our data is pretty skewed. Skewness is a measure of symmetry. To be exact, it is a measure of lack of symmetry. This means that the larger the number is the more your data lack symmetry (not normal, that is). We use the **square root method** to reduce the skewness in the data. The square root method is typically used when your data is moderately skewed. Now using the square root (e.g., sqrt(x)) is  a transformation that has a moderate effect on distribution shape.
- **Scaling**: Data is scaled using `StandardScaler()`.

## Diminensionality Reduction

In this problem, there are many factors on the basis of which the final clustering will be done. These factors are basically attributes or features. The higher the number of features, the harder it is to work with them. Many of these features are correlated, and are hence redundant. This is why we will be performing dimensionality reduction on the selected features.

For this we use **Principal Component Analysis**. PCA is an unsupervised machine learning algorithm that performs dimensionality reduction while attempting to keep the original information unchanged. PCA works by trying to find a new set of features called components. These components are composites of the uncorrelated given input features.

## Clustering

- We use the **K-Means Clustering algorithm** to find the clusters for the group of customers. K-Means Clustering is an unsupervised machine learning algorithm that works by grouping some data points together in an unsupervised fashion. The algorithm groups observations with similar attribute values together by measuring the Euclidean distance between points. Here 'K' is the number of clusters.
- We need to determine the optimal value of 'K' first. For this we use the elbow method. The elbow method is a heuristic method of interpretation and validation of consistency within cluster analysis designed to help find the appropriate number of clusters in a dataset. If the line chart looks like an arm, then the "elbow" on the arm is the value of k 
that is the best. **We find that our optimal K value is 6.** The result for it is shown below.

![Screenshot (5)](https://user-images.githubusercontent.com/41315903/150700616-ea935011-3e47-40dd-9580-189f0c251bed.png)

## Inference

Since this is an unsupervised clustering. We do not have a tagged feature to evaluate or score our model. The purpose is to study the patterns in the clusters formed and determine the nature of the clusters' patterns.
![K-Means Cluster](https://user-images.githubusercontent.com/41315903/150701243-89099d5e-ad7e-41cb-bdb9-12beb857cb91.png)

The following is the distribution of our clusters:
![Distribution of Cluster](https://user-images.githubusercontent.com/41315903/150701794-45f8997d-9bba-4afe-973e-94e7891d8a1e.png)

## Customer Profiling
Inference from the clusters
Cluster 0: Smallest Spenders and Lowest Credit Limit - this is the group with the lowest credit limit but they don't appear to buy much. Unfortunately this appears to be the largest group of customers.

Cluster 1: Medium Spenders with third highest Payments - the second highest Purchases group (after the Big Spenders).

Cluster 2: Big Spenders with large Payments - they make expensive purchases and have a credit limit that is between average and high. This is only a small group of customers.

Cluster 3: Cash Advances with Small Payments - this group likes taking cash advances, but make only small payments.

Cluster 4: Small Spenders and Low Credit Limit - they have the smallest Balances after the Smallest Spenders, their Credit Limit is in the bottom 3 groups

Cluster 5: Cash Advances with large Payments but Highest Credit Limit and Frugal - this group takes the most cash advances. They make large payments, but this appears to be a small group of customers. this group doesn't make a lot of purchases. It looks like the 3rd largest group of customers.
