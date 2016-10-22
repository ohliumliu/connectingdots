## How to work with external databases in spark

#### Spark is blind to storage options.
It is possible to use different data storage, as long as the driver is specified. For example, the following command
starts pyspark with mysql driver connected.
```shell
pyspark --jars mysql-connector-java-5.1.40/mysql-connector-java-5.1.40-bin.jar --driver-class-path mysql-connector-java-5.1.40/mysql-connector-java-5.1.40-bin.jar
```

#### Read and write from mysql database
* For Spark 2.0.x, use the following to read a database into a dataframe
```python
# read a table products and generate a dataframe
products_df = sqlContext.read.jdbc(url = url, 
                                   table="products", 
                                   properties=properties)
```
* Use the following to write a dataframe to a database
```python
# write categoreis_df as a table categories in the database
categories_df.write.jdbc(url=url, table="categories", mode = "append", properties=properties)
```
* The parameters:
  * url: url = "jdbc:mysql://localhost:3306/flashdeals" The name of the database is shown here.
  * properties: a list of hash to provide options. The most important ones are username and password. For example,
  ```python
  properties = {
    "user": "root",
    "password": ""
  }
  ```
 
