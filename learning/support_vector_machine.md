* Compared with Logistic regression, the cost function is linearized (See SupportVectorMachine.png in ~/MachineLearning).
  * Large margin classifier: it will try to separate the two classes as much as possible. Mathematically, it tries to maximize 
  the average distance between the data points to the decision boundary multiplied by the length of the normal of the decision boundary. 
  If the average distance is big, the norm of the normal doesn't need to be big, leading to small error from regularization term. 
  Otherwise, the norm of the normal has to be big, leading to big error from regularization term. Here, the regularization term plays 
  a more fundamental role.
  * SVM is convex mathematically.
* For complex boundary, nonlinear function is needed to convert feature vector x to z. 
  * Use landmark points and kernel for optimization: z = theta0+theta1*f1+theta2*f2+... and f1=gaussian(distance between x1 and landmark 1) 
  and so on. Optimization will find theta vector. Gaussian kernel is also called rbf kernel in sklearn.svm, and gamma in SVC constructor 
  is 1/sigma.
  * The use of kernels change the original nonseparable features (x, say, 3 features) to more nonlinear separable 
  features (f1, f2, f3, ..., say 100 landmark points).
  * Other choice of kernel. They basically measure the similarity between sample points and landmark points. 
  They should satisfy Mercer's theorem to ensure the proper working of SVM numerical tricks.
    * Linear kernel: no kernel used. For small data set. This is similar to Logistic.
    * Polynomial kernels: inner product of x vector and landmark vector, raised to 2nd, 3rd, and ... power.
    * String kernel, chi-square kernel, ...
* A naive choice of landmark points: choose the training points themselves as landmark points. __It might have interesting use in the 
interpretation of [Regularization](regularization.md)__
* Landmark point idea works well with SVM (Linearized cost function). It also works with other algorithm mathematically, 
  but not as efficient computationally as in SVM.
* The variance in Gaussian kernel is a parameter chosen by the user. Smaller variance in Gaussian -> higher requirement to fit 
  the sample points -> potential of overfitting (higher variance in fitting result). Easy to remember the conclusion.
* Large set, too many feature: not very good for svm.
