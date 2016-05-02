* To minimize cost function, there are several choices:
  * Normal function: analytical solution of the minimization problem. Often in matrix format for high dimensions, 
    thus doesn't scale very well. For LinearRegression in sklearn, this is used and called Ordinary Least Square.
  * [Gradient descent](gradient_descent.md): need to choose learning rate, simple.
  * Conjugate gradient, BFGS, LBFGS: no need to choose learning rate, faster.
