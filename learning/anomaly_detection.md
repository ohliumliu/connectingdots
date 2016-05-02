* Algorithm
 * Use training set to find the distribution of features. Normally Gaussian. Training set doesn't contain anomalous data.
 * Calculate the probability of observing the cross validation and assign it to be anomalous if it's probability is low.
* Evaluate the performance using test set.
* How to choose the threshold
Because the anomalous data are rare, should use [Metrics for skewed group](metrics_for_skewed_group.md).
* When to use anomaly detection instead of supervised training.
  * small set of anomalous data. 
  * anomalous data are hard to classify. Only knows that it is a rare event, but not sure in what way. 
  This is common if there are many features that could show anomalous value.
* Anomaly detection needs that the features are distribute independently following Gaussian. If not, may need to do 
some transformation of the raw features. For example, fractional power.
* If the anomaly sample has a big probability, may need to find new features to distinguish these cases.
* Use multivariate Gaussian if some features are correlated. Use PCA may suggest new features sets that are independent. 
  For multivariate Gaussian, needs sample number is (much) bigger than the number of parameters.
* Sometimes anomaly also appears as an outlier. The detection algorithm is based on the residual value after fitting.
  * Removing outliers can be done based on residual size.
  * __Fitting should converge if outliers are removed__
