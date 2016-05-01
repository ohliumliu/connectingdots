Each form has an action attribute. If it's not set, it defaults to the current page. It specifies 
what url we should use upon form submission. In our case, we have an onsubmit js script which also 
contains url and HTML method specifications. So there could be two different requests from the same form. 

* Which one is fired first? js is fired before form submission. 
* If we only want to run the script, use `onsubmit="return script()"` and `return false` from the 
script to disable form submission. 
* The button in a form is normally like this
`<input type="submit" value="text_label">`. Clicking it is the same as hitting enter in the form.

Need to do the similar for attaching js to anchors.

```
<a href="javascript;" onclick="return function()">
```
There are other choice for href, for example, \# (top of the page) or \#!(some elements that are not likely present),
which are just place holders for anchors to work.
