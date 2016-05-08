In order to maximize the use of available data, k-fold cross validation may be used. It splits the data set into k groups. Multiple (k)
training and testing was perform using a different group each time. The average of these trainings is used.

In sklearn.cross_validation, a KFold class is avalaible to generate the indeces needed to perform k-fold cross validation. It can
also shuffle the data first to remove any bias. The output of k-fold is an array. Each row is a combination of two arrays: train set
index and test set index.
