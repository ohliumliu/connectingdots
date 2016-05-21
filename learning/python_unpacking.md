### The * operator in python
The star operator (*) convert a list or tuple to separate items so that the result can be used as function argument.

Along the same line, the double star (**) does the same to a hash.

This is often found in function definitions `def fun(x, *args, **dicts)`. In this case the function expect the first parameter
`x`, followed by separate args (could be empty), and then separate dicts. For example, `fun(5, 'a', 'b', 'id': 222)`. The twist
is that inside the function, `args = ['a', 'b']` and 'dicts={'id': 222}'. In another word, the function expects that the input
is the unpacked version of args or dicts, but args and dicts themselves are still packed. Normally, in preparation for the function
call, data are organized in containers (array or hash), for example, `arr = ['a', 'b']` and `option = {'id': 222}`, and then it
it natural to call the function by `fun(x0, *arr, **option)` following the signature of the function.
