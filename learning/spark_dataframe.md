## DataFrame in spark
* Spark's data are called DataFrame. It's very similar to Pandas dataframe. For example, it can be accessed by either [] or dot.
* There are two kinds of operations that could be applied to a data frame: transformation or action.
  - Transformation includes createDataFrame, filter and etc.
  - DataFrame is actually immutable once created, so each transformation generates a copy.
  - Action includes show, and etc.
  - The key difference is that transformation is lazy, i.e., spark only remembers what transformation to perform, and wait for an 
     action to initiate the actual work of transformation. In case something fails, it's always possible to recover from somewhere.

### Transformation
* select, drop, ...
* UDF: user defined function.
    `my_func = udf(named or lambda, returnType)
* filter, where, distinct


### Action
* show: print out
* take
* collect _DO NOT USE_ it might be too big for your memory
* count
* describe

### cache
* `df.cache()`: without cache() action, df will be recomputed from scratch every time it is referenced by an action. 

### driver vs worker
* Driver is the python program to set up the spark operation sequences. Work is the actual clusters doing the job.
* Python code is executed by the driver.
* Spark transformation is executed by the worker.
* Spark action involves both driver and worker.
* Use spark transformation as much as possible for scalability.
