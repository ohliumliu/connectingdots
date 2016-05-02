* Logistic regression is used for classification.
* In the case of two outcomes, logistic regression is a fitting procedure using a sigmoid function h = 1/(1+e^(-z)), 
where z is a function of feature vector x. The key of this function is h(-inf)=0, h(0)=0.5 and h(inf)=1. The model prediction 
from the regression is thus outcome = 1 when z(x)>0 and outcome = 0 when z(x)<0.
* Expression of z(x)
  * z could be a linear function of x. For example, z = a + bx_1 + cx_2. In this case, the decision boundary in (x_1, x_2) space is a line.
  * z could be a nonlinear function of x. For example, z = a + bx_1^2 + cx_2^2. In this case, the decision boundary in (x_1, x_2) space is 
  an elliptical.
  * It is possible that the model cannot be cast in terms of a single variable z.
* The cost function is not square sum, because the it would have a lot of local minima. A better choice is to choose a log function. 
  It turns out it's possible to find such a function so that the cost function is convex. Furthermore, it's actually the prediction of 
  maximum likelyhood.
* If there are multiple choices of n different outcomes, use one-vs-all method. The problem becomes n separate 0/1 classification. 
  When making prediction, choose the choice that maximize the hypothesis function (i.e., probability). Alternatively, 
  it can become n*(n-1)/2 one-vs-one problem, as used in some sklearn libraries.

