### General ideas of apache spark
* It tries to address the challenges of big data.
* It's based on the parallel processing of data in the _memory_ of a cluster of machines. This is opposite to MapReduce/Hadoop which uses hard drives for IO.
* Spark divides the data into unique subsets, each of which is stored on one of the machines in a cluster. These are called
resilient distributed datasets (RDD).
* Spark hides the implementation details.
* Performance optimization:
  - Catalyst optimization engine
  - Tungsen off-heap memory: use less memory 75% less
