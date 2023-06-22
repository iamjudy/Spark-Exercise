# Spark-Exercise

Exercises for the course: [Spark and Python for Big Data with PySpark](https://www.udemy.com/course/spark-and-python-for-big-data-with-pyspark/)

Using **[Databricks](https://community.cloud.databricks.com/?o=2484294035440853#)** to set up the environment. Other options:
- Local VirtualBox 
- AWS EC2 PySpark 
- AWS EMR Cluster


## Machine Learning with Spark MLlib
### Key Concepts
#### VectorAssembler
VectorAssembler is a transformer in Spark MLlib that combines a given list of columns into a single vector column. It's commonly used in the preprocessing stage of machine learning workflows.

In [our code](https://github.com/iamjudy/Spark-Exercise/blob/main/Linear%20Regression/Linear_Regression_Consulting_Project.ipynb), inputCols specifies the columns to combine ('Age', 'Tonnage', 'passengers', 'length', 'cabins', 'passenger_density', 'cruise_cat'), and outputCol is the name of the new combined column ('features').

#### LibSVM Data Format
The `.format('libsvm')` method in Apache Spark is used to specify the format of the data to be read or written. LibSVM is a popular, sparse data format for machine learning applications. Each row corresponds to a labeled point with its features listed as an index-value pair. For example, a data line might be:

> 0 128:51 129:159 130:253 ...

This signifies that this point's label is 0, the feature indexed at 128 has the value 51, the feature at 129 has the value 159, and so forth.

#### Tree Method Classifiers
- Intuition Behind Splits
  **Entropy** and **Information Gain** are the Mathematical Methods of choosing the best split.
  
- Random Forests
  To improve performance, we can use many trees with a random sample of features chosen as the split.
  - A new random sample of features is chosen for every single tree at every single split.
  - Works for both classification and regression tasks!
  - Suppose there is **one very strong feature** in the data set. Most of the trees will use that feature as the top split, resulting in an ensemble of similar trees that are **highly correlated**.
  - Averaging highly correlated quantities does not significantly reduce variance, however, by randomly leaving out candidate features from each split, Random Forests *"decorrelate"* the trees, such that the averaging process can reduce the variance of the resulting model.
 
- Gradient Boosted Trees
  -  A loss function to be optimized
  -  A weak learner to make predictions
  -  An additive model to add weak learners to minimize the loss function
 
  -  The workflow of gradient boosting, in a simplified and concise manner, is as follows:
     > 1. **Initialize**: Train an initial decision tree model and make predictions.
     > 2. **Compute Errors**: Calculate the errors made by this model, which are the differences between the predicted and actual values.
     > 3. **Train More Models**: Train another model that attempts to correct the errors made by the previous model.
     > 4. **Iterate**: Repeat this process for a specified number of iterations, each time trying to correct the residuals (errors) from the previous model's predictions.
     > 5. **Combine**: Aggregate the predictions from all models, often a simple sum of the individual predictions, to get the final prediction.

- Having a `.featureImportances` attribute available, we can check which features (x) affect outcome (y) the most.

- So, 3 steps to implement it in Spark:
  1. Train a weak model **m** using data samples drawn according to some weight distribution.
  2. Increase the weight of samples that are misclassified by model m, and decrease the weight of samples that are classified correctly by model **m**.
  3. Train the next weak model using samples drawn according to the updated weight distribution.
 
  In this way, the algorithm always trains models using data samples that are "difficult" to learn in previous rounds, which results in an ensemble of models that are good at learning different "parts" of training data.


#### K-means Clustering
- **Elbow method** to choose the "K" value at which the SSE decreases abruptly.
  First of all, compute the sum of squared error (SSE) for some values of k (for example 2, 4, 6, 8, etc.).
  The SSE is defined as the sum of the squared distance between each member of the cluster and its centroid.

  ![hi](https://imgtr.ee/images/2023/06/22/mnTs7.png)
  




