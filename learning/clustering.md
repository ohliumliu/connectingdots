### K-mean method
  Randomly initialize k points (focus points) in the feature space and then repeat the following
  * Cluster assignment: Assign each sample point to one of the k clusters based on its distance to the k points. 
  This step minimizes the distortion (average distance between the sample points and the corresponding focus points) 
  while keeping the focus points unchanged.
  * Centroid movement: Move the focus points such that its new location minimizes the average distance between the 
  focus point and the members in its group, i.e., the new location of the point is the centroid of the member points. 
  This step minimizes the distortion (average distance between the sample points and the corresponding focus points) 
  while keeping the cluster assignments unchanged.
* Cost function should be monotonous as iteration cycle number increases.
* How to initialize focus points
  * randomly select k sample points.
  * randomly select k groups and use their centroid. this is linear transformation of the initial points.
* K-mean method might suffer from local optima.
  * Some clusters may merge to a bigger one.
  * Run many random initialization.
  * Perform k-mean on big clusters trying to separate them and then run k-mean on the whole training set again 
  (optionally dropping the smallest cluster).
* Choose the number of clusters
  * Check cost function vs number of clusters and look for "elbow". May not be obvious.
  * Based on the requirement of next step.
  *

### Mean-shift method
  For each data point, do the following:
  * Consider the points within a certain radius from the point and find the mean.
  * Consider the pints within a certain raidus from the mean, and find the new mean.
  * Until the mean positions doesn't change.
  For a given distance, there are a limited number of outcomes as the man.
