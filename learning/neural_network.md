* Motivation
For example, there is a computer vision problem to classify images based on pixel values. If the image is n x n, 
then there are O(n^2) features in the linear model, and and O(n^4) features in the quadratic model, and so on. 
It is hard to do regression: too much computation, not enough training data set.
* Neural network
  * input: pixel values O(n^2)
  * hidden layer 1 with m1 nodes: each node is from a linear combination of input values and a sigmoid function. 
  The transformation matrix is m1xn^2.
  * hidden layer 2 with m2 nodes: each node is from a linear combination of layer 1 node values and a sigmoid function. 
  The transformation matrix is m2xm1.
  * keep going
  * output layer with a single node: from a linear combination of the layer immediately before and a sigmoid function.
  * the description here doesn't include the constant bias term implicit in each layer.
* It is a "learning mechanism" because hidden layers are calculated from input step by step, and the last step is like 
  [Logistic regression](logistic_regression.md).
* How to calculate cost function and its derivative?
  * Use forward propagation to calculate cost. 
  * Use back propagation to calculate derivative.
  * Check gradient by comparing numerical approximation with back propagation, but numerical approximation is very slow compare. 
  Only do this to confirm back propagation.
  * Use random numbers to initialize parameters.
* For multi-class problem, output layer has multiple nodes corresponding to the probability of different outcomes.
