http://stackoverflow.com/questions/18226598/how-to-add-a-button-dynamically-using-jquery

See this for several methods.

I am using something like this

```
var $alertItem = $('<span>', {text: alerts[i].content,
id: 'alert'+alerts[i].id
})
```
$alertItem can be appended to another selector.
