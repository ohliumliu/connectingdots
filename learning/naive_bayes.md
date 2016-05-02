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
