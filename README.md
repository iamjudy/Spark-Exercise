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
