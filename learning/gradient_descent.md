* Slope determines the size and direction of searching step. This is sort of counter-intuitive, 
  but necessary to avoid divergence at local minimum. __It is also a natural first-order approximation 
  of the step size which must dependent on the slope and should be zero when the slope is zero (but not for saddle point).__
  
  ** steep curve: large step
  
  ** shallow curve: small step

* Newton's method is related to gradient descent with a changing learning rate that make more sense.
  
  ** steep curve: small rate
  
  ** shallow curve: large rate

* Feature scaling: similar to nondimensionalization in physics. Here features are the independent variables 
  and they are better similar in scale. Since there is no physical scale to use, we normally use mean and std 
  to center and scale the features. An alternative is to do minmax. sklearn has a scaler.
