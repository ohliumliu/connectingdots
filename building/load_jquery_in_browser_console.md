```
var jq = document.createElement('script');

jq.src = "https://ajax.googleapis.com/ajax/libs/jquery/2.1.4/jquery.min.js";

document.getElementsByTagName('head')[0].appendChild(jq);
```
* create a node (element) in the DOM tree that is a script
* set the src attribute of the element
* add the element to the head portion of the document
