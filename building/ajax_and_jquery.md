__First Apporach__

This is how to use AJax and JQuery in RoR.

* In view, set remote-data=true in html tag such as form or button tags. 
This will make the element to process the action as JS.
* In controller foo.rb, add the following block: 
   ```
   respond_to format do
     format.js
   end
```
    But I am not sure if this step is absolutely  necessary

* Generate a file foo.js.erb with the following as required by remote-data=true

```
$("#id").html("<%= escape_javascript(render partial: 'foo') %>")
```

It looks like a partial _foo.html.erb is what rails is looking for, even if you use render 'foo'. 
If only foo.html is available, rails complains about missing template.

It seems very straightforward, but is a mix of front end and back end. 
The alternative of putting ajax calls in js involves more lines of code.

This note is related to the work in [20th January 2016](notes_1_20_2016.md)

The problem of this approach: limited to rails. Rails refines the meaning of attribute data-remote. 
See unobstrusive javascript.

__Second Approach__

Calling javascript has a ajax call, which takes a hash as input. There are simpler version of ajax call.

```
function func(var){
    $.ajax({
        method: "GET",
        beforeSend: function(xhr)  {xhr.setRequestHeader('X-CSRF-Token', $('meta[name="csrf-token"]').attr('content'))},
        url: "controller/action.html",
        data: "param1=" + var + $("#fieldid").val(),
        success: function(data){
             //process data
             $("#fieldid").html(data);
        }
    })
{
```

Note the use of [csrf token](csrf_token.md). The url specifies what data format is requested and the controller 
is responsible for returning the data. In this example, the returned data is used to update a html portion.

The following is the controller code.

```
respond_to format do
   format.html {render partial: "foo"}
end
```
Here a partial is returned to the calling ajax function.

__Third Approach__

The ajax call is essentially the same, but url ends with .json. The controller has to provide the data in jason format.

```
respond_to format do
   format.json {render json: {data: @variable, status: "ok"}}
end
```
Here a hash (or just instance variable) is returned as a jason object, which is automatically parsed for processing 
in ajax call using javascript. The javascript dynamically updates html view using jQuery based on the data.
