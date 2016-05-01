http://stackoverflow.com/questions/4091765/assign-click-handlers-in-for-loop
# Assign click handlers dynamically.

* Use a factory method to generate callback (what I am using for deleteAlert)
* Parse html attribute 

In javascript, when building a button,

```
{...
click: function1()
}
```
click is assigned the value of function, so function1 has to be executed when
the button is first constructed. If we want to assign a function to click, then
function1() has to return a function2 which is what is assigned to click.
