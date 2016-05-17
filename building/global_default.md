Python's default input variable is "global".

```python
def extendList(val, root=None):
    root = [] if root==None else root
    root.append(val)
    return root

l1 = extendList(1)
l2 = extendList(1, [])
l3 = extendList('a')

print "l1 = %s" %l1  #=> l1 = [1]
print "l2 = %s" %l2  #=> l2 = [1]
print "l3 = %s" %l3  #=> l3 = ['a']
```
* If root defaults to None, the first line is necessary because None does't have a method called append.
* root cannot default to []:
```python
def extendList(val, root=[]):
    root.append(val)
    return root
```
The output will be
```
l1 = [1, 'a']
l2 = [1]
l3 = [1, 'a']
```
From this point, if we change the defintion
```python
def extendList(val, root=[x]):
    root.append(val)
    return root
```
The result would be
```
l1 = ['x', 1, 'a']
l2 = [1]
l3 = ['x', 1, 'a']
```
Basically, the first and the third all of extendList is applied to the same variable.
