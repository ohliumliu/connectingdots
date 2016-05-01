Firefox's javascript engine allows the specification of default input param in function declaration, i.e.,

```
function foo(a, b="default"){
}
```
However, this will lead to an error in Chrome or Opera, because default value cannot be defined this way. 
To make things more confusing, the error is complaining something else. Instead, use the following

```
b = typeof b === 'undefined' ? "default":b;
```
If foo is called without supplying b, the "default" will be used.

