### Sorting in python
* List
Use `a_list.sort()` to sort in place or `sorted(a_list)` to get a copy of the sorted list (original list remains the same).

* Dict
Use `sorted` with a custom key
```python
  import operator
  d = {'a': 2, 'b': -1, 'c': 5}
  d_sorted = sorted(d.iteritems(), key=operator.itemgetter(1))
  # iteritmes returns a list of tuples using the dict. It's essentially the same as d.items(), but iteritems is an iterator,
  # so it is generated on the fly.
  # itemgetter(1) is a function (callable object). Since it is the key, it is applied to every item, i.e., item[1] is used
  # for sorting.
  # Alternatively, one could use
  d_sorted = sorted(d.iteritems(), key=lambda item: item[1])
```
