* Model error from train set, cross validation set and test set
  * error from train set should all be very small for every models (for example, different orders of polynomials) in consideration.
  * Evaluate error from cross validation set and choose the best model. The error from cross validation set is still from a 
  "train set" because the order of the polynomial is essentially a fitting parameter.
  * Evaluate error from test set. This is the "true" error of the model.
* Underfitting (high bias) or overfitting (high variance)?
  Calculating training error and cross validation error can help detect whether it's underfitting or overfitting.

|Training error|cross validation or test error|reason|reason|Possible solution|
|----|----|----|----|----|
|High|High|underfitting|too much regularization||
|Low|High|Overfitting|too little regularization|More training data point|

* As shown in the table above, degree of regularization can also be related to overfitting and underfitting. 
* As an aside, minimizing cross validation error is helpful to find the proper [Regularization](regularization) or model.
* It would seem that overfitting could be remedied by more data. Since people tend to put in more feature (just-in-case mind set), 
it is important for some people to gain access to data. Conceptually, it makes more sense to work on the model and choose a reasonable
number of features to begin with. One of the useful test is to ask if a _human_ expert can do a good prediction with given feature set. 
If yes, then the set is probably complete. If not, then it is probably incomplete.
* Training curve.
Plot training or cross-validation error as a function of training data set size. It helps to determine whether it's underfitting or
overfitting.
* If it turns out some features have an extremely high coefficients, it may be a "signature" and should be removed.
