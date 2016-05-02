Reference: http://www.bitstorm.org/weblog/2012-1/Deferred_and_promise_in_jQuery.html

Ajax calls can be treated as a promise object.

```
promise1=$.ajax({url: "/users/1"});
promise1.done(function1(data));
promise1.done(function2(data));
$.when(promise1, promise2).then(function(data1, data2);
```

In general, Deferred object can be handled similarly.
