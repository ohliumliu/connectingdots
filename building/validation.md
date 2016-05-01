* One or two blocks of codes are needed for validation to work

  * define in model.rb what to be validated using `validates :field, validation_hash`

  * add necessary components, for example, unique index, to the database by migration 

* In view, the following helper method iterative through the errors and display them. 
(this example also [use erb to switch html view](use_erb_to_switch_html_view.md))

```
<% if @user.errors.any? %>
  <div id="error_explanation">
    <h2> found <%= pluralize(@user.errors.count, "error") %> </h2>
    <ul>
    <% @user.errors.full_messages.each do |msg| %>
      <li><%= msg %></li>
    </ul>
  </div>
<% end %>
```  

* In controller, make sure @user is defined

* @user is available after render, but not after redirect_to

* It is possible to add additional error message in controller

```
@user.errors.add(:password, "not the same")
```

This example adds an error message about password field. It is handled
the same as those validation errors generated automatically.


