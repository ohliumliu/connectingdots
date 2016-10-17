### Notes from Spark Summit 2016 class 3: advanced apache spark with Wiki

#### Archetecture of infrastructure on databricks.
* 3x workers. 3.7 G total. They are JVMs.
* 5x REPL to allow 5 notebooks to simultaneously connect (databricks specific).
* Chauffer. 1 G. Communication between notebook and JVMs.
* 3x Python processes. 1.5 G total. PySpark has to go through these processes to run JVMs. _Python interface is thus slower
  than scala._

#### Tips
* Because there are 3 JVMs for each cluster, it makes sense to divide the data into multiples of 3 partitions.
* Avoid using udfs to process data and use SparkSQL as much as possible, because catalyst doesn't optimize udf.
* Avoid using RDD api, because of the lack of catalyst optimization and Tungsten encoder/decoder. Use DataSet api or SQL api.
* If one wants to cache a dataframe, consider registerTempTable. It will provide a readable name in spark UI and also allow
the use of SQL query directly.
* More on RDD, DataSet and DataFrame. [Ref](https://databricks.com/blog/2016/07/14/a-tale-of-three-apache-spark-apis-rdds-dataframes-and-datasets.html)
  * RDD is for low level operation or unstructured data (text stream). No catalyst optimization.
  * As of 2.0, DataSet and DataFrame are merged as DataSet. It has a typed version and an untyped version. For Python interface,
only untyped version is available, which is DataFrame.
