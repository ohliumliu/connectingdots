### Set up standalone spark on ubuntu 14.04

#### Basic installation and testing
* Get the precompiled spark from its website. I am using 1.6.2 with hadoop2.6
* Extract the zipped file to any location.
* Add the following to `~/.bashrc` and source it
```bash
export SPARK_HOME=/home/yu/spark/spark-1.6.2-bin-hadoop2.6
export PATH=$SPARK_HOME/bin:$PATH
```
* In a terminal, run `pyspark`. After a while, it will show the spark ascii logo and remind you that `sc` is the spark context.
You will end up with a python shell.
* Simple testing
Run the following in the python shell.
```python
nums = sc.parallelize(xrange(100)) # generate an RDD holding 100 numbers
nums.take(5) # print the first 5 numbers
```
Obviously, there is a lot of output in the shell that is not very relevant. There is no tab completion or syntax hint.
#### Drive with ipython/jupyter
It's easy to run pyspark using ipython (a better shell than bare python) or jupyter notebook.
```bash
PYSPARK_DRIVER_PYTHON=ipython pyspark  # ends up in an ipython shell
PYSPARK_DRIVER_PYTHON=jupyter PYSPARK_DRIVER_PYTHON_OPTS=notebook pyspark 
# start jupyter notebook at localhost:8888 
```
#### Connect remotely
