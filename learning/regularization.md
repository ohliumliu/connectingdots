This is how to deal with the issue of overfitting/insufficient data.

|Result|Name|Solution|
|----|----|----|
|Under fitting|High bias (in the model)||
|Over fitting|High variance (in the fitted result)|Need regularization or [model selection](model_selection.md)|

* Regularization: limit the range of parameters, especially those higher order coefficients
  * add terms in cost function to force some parameters to be small, say 1000*theta_1^2. this also makes the prediction 
    smoother while adding some fine tuning.
* How to choose which parameters to limit
  * Limit the size of all parameters (except the constant term) by adding terms (\sum_i\lambda*\theta_i^2) to a simple, 
    base cost function. Here, \lambda controls how strong the limitation is. The resulting regression is hoped to achieve a
    balance between underfitting and overfitting.
  * __Thoughts: Try to fit with different lambda. As lambda is decreasing, some parameters quickly approaches from zero to the 
  result from simple model, while others do it much slower. The speed of convergence tells us which parameters need to be limited
  or of higher order.__
* _Regularization can also be thought of as adding data points to the model._ These data points (1, theta_0) correspond to the constant
  term and the number of these pseudo points is lambda. This picture explains why regularization help resolving noninvertibility 
  issue due to overfitting. There are other ways to add these pseudo points, especially for high-dimensional cases. For example, in 
  the landmark points idea, the introduction of new features (similarity between sample and landmark points) suggests the location 
  of these pseudo points. This picture may be limited to linear model as well.
* Another way to put it is that regularization adds Lagrange multiplier terms with the "assumed" constraints on theta.
* Penalty term could be l1 norm (Lasso), Eculid norm or others.
