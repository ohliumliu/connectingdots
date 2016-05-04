In html.erb, the content from instance variables is eascaped, thus not rendered as html by the browser. Need to use html_safe as follows.
```html
<p>
  <% @user.notes.html_safe %>
</p>
```

If `@user.notes.html` is used, html tags will become something like `&lt...`
