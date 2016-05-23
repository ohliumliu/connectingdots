### Bootstrap
In frequentist's view, there is a fixed but unknown distribution governing our observation, and the job of an observer is to
infer the unknown distribution, i.e., the parameters of the unknown distribution, from the observations.

It's impossible to measure all the samples, but it's feasible to measure several batches of samples. The parameters obtained
from each batch are then averaged to get a better estimate of the unknown parameter.

It is often not convenient to have several different batches either, so we have to come up with multiple batches ourselves.

* Split the available sample in many batches.

* Generate fake data using the estimators obtained from the available sample. Get a new estimate.
