```
<% flash.each do |key, value| %>
    <div class="alert alert-<%= key %>"><%= value %></div>
<% end %>
```
In controller, one can set flash[:success] or flash[:error] to show in view.
