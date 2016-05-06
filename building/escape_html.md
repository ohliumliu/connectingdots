In html.erb, the content from instance variables is eascaped, thus not rendered as html by the browser. Need to use html_safe as follows.
```html
<p>
  <% @user.notes.html_safe %>
</p>
```

If `@user.notes.html` is used, html tags will become something like `&lt...`

An alternative is to use .raw which also handles nil better. But neither one is safe from xss attack, so we need to be careful.
https://www.tigraine.at/2012/08/23/when-to-use-raw-and-when-to-use-html_safe
