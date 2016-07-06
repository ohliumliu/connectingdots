## Priority Queue
1. [Reference](https://docs.python.org/2/library/queue.html)
1. [Tutorial](http://www.bogotobogo.com/python/python_PriorityQueue_heapq_Data_Structure.php)
1. Priority queue comes in handy when we want to keep track of the top n list (for example, top 10 most frequently used words).
1. When using `my_queue.put(item)`, make sure it is not full. Or else, it will be blocked and the program is stuck. In using `put_nowait`,
   the operation may raise an error if the queue is full.
1. The item in the queue could be anything. By default, it is a tuple whose first element is used for ranking. If one defines a custom class
   with a custom `__cmp__` method, the ranking method can be more flexible. For example,
   
   ```python
   def __cmp__(self, other):
        return cmp(self.priority, other.priority)
  ```
