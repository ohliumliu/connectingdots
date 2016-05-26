* To minimize cost function, there are several choices:
  * Normal function: analytical solution of the minimization problem. Often in matrix format for high dimensions, 
    thus doesn't scale very well. For LinearRegression in sklearn, this is used and called Ordinary Least Square. Gauss-Markov
    Theorem.
  * [Gradient descent](gradient_descent.md): need to choose learning rate, simple.
  * Conjugate gradient, BFGS, LBFGS: no need to choose learning rate, faster.
* It's not just to minimize the cost function. The distribution of the cost is also important. One of the fundamental
  assumption is that the error term is independently distributed. If we plot error vs X and there is obvious trend, that
  invalidates the regression.
* Regression can be thought of as a projection with the error term being the distance between y and the plan onto which data
  point is projected.
