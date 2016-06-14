1. It's naive because each feature is treated to be independent
1. Skeleton code using sklearn
```python
from sklearn import GaussianNB

# get data sets
# Construct a classifier
clf = GaussianNB()
# Train
clf.fit(X, y)
# Predict
clf.predict(X)
# Score
clf.score(X, y)
```
1. Metrics
* common ones such as confusion matrix, accuracy, and f1 score and etc.
* A more sophisticated measure to compare the prediction across the board called calibrate plot.
  - Get the predicted probability or log probablility of all samples.
  - Partition of the sample into groups with similar posititive probabilities and calculate the actual positive probability.
    The std of actual probability can also be calculated.
  - Compare the predicted probability with actual probability.
