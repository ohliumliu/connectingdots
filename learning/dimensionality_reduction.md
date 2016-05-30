* If correlation can be detected between feature sets, new feature can be defined to replaced the correlated ones.
  * If x1 is approximately linearly correlated with x2, then one can project (x1, x2) to the line fitted from x1 and x2 
   and use the new line as an axis.
  * The method to find the correction dimension is through principal component analysis. This is essentially the same as 
  finding the principal axis of inertia tensor with each data point representing a unit mass point. 
  See also prolate and oblate tops. The axis with the bigger eigenvalues are retained and can be used to construct a 
  hyperplane (linear space) on to which data points can be projected to have a smaller dimension.
  * Use mean and standard deviation to scale the feature first. 
* Calculate the inertia tensor, here called covariance matrix by the outer product of sample vectors and sum over all samples.
  * Find the eigenvectors, eigenvalues of the covariance matrix. Use eig or svd (for symmetric semi-positive matrix, svd is the same as eig).
  * Choose k eigenvectors and find the projection of the samples onto the space spanned by these vectors. 
    Choose the eigenvectors such that most (say, 99%) of the variance in the sample features are retained. 
    The percentage of variance retained is proportional to the eigenvalue.
  __Need to think through the analogy between moment of inertia and PCA more carefully.__
* Use PCA on training set only. Don't use it on test or cross validation set. Because PCA is essentially a regression procedure.
* Do and don't
  * PCA reduces dimensionality and makes it faster to run regression.
  * PCA can help visualize the data.
  * Don't use PCA to address overfitting. It throws away variance. Use regularization. __This is debatable I think.__
  * Don't use PCA at first trial. Use it when have to.
 * A summary of methods
  * Linear methods: it fails when linear regression fails -- error is not normally distributed.
   * PCA
   * SVD
   * MDS: Multi-dimensional scaling.
  * Nonlinear methods:
   * IsoMap
   * Local linearly embedding
