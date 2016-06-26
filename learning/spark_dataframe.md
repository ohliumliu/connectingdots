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
* select is often the entry point, similar to its position in SQL. It takes a column as input. Oftentimes, we want to select a transformation of a column. Many functions are thus defined to take a column as input and return a column. For example,
```python
df_new = df.select(lower('name1')) # 'name1' is a column in df. lower is a built-in function of sparkSQL api
df_new = df.select(my_method(col('name1')))
```
In the second expression, `col('name1')` is a column object. If `'name1'` is used, `my_method` will complain that it doesn't know how to deal with a string `'name1'`. Of course, it is feasible to use `my_method(df.name1)`, but the dataframe `df` is hard coded.

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
