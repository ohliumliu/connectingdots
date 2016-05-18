* When building html elements using jQuery, make sure the object is reused properly.
* A variable can be assigned an html element, and this is the only copy of it. If it is manipulated multiple time, you only see
the end result. In the following, what is shown is "notice1notice1.twice"
```javascript
notice1 = $("<div></div>")
notice1.attr("class", "alert alert-notice").append("notice1");
$(".top_alert").append(notice1)
notice1.attr("class", "alert alert-notice").append("notice1.twice");
$(".top_alert").append(notice1)
$(".top_alert").append(notice1)
```
* To get multiple copy, need to re-initialize an object. The new one can share the same name with the earlier, but they refer to
different object. The variable is still a single copy, but it points to different html object at different time. In the following,
"notice2" shows up twice separately.
```javascript
notice2 = $("<div></div>")
notice2.attr("class", "alert alert-notice").append("notice2");
    $(".top_alert").append(notice2)
notice2 = $("<div></div>")
notice2.attr("class", "alert alert-notice").append("notice2");
    $(".top_alert").append(notice2)
```
* If the same object is used multiple time, only the last one counts. In the following, "notice3" only shows up in .bottom_alert
```javascript
notice3 = $("<div></div>")
notice3.attr("class", "alert alert-notice").append("notice3");
$(".top_alert").append(notice3)
$(".bottom_alert").append(notice3)
```
[jsfiddle demo](https://github.com/ifad/data-confirm-modal)
