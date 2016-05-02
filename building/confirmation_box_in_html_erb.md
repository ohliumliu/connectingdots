```
<%= link_to(
 "#{page.resource_name.titleize.downcase} Import from Amazon",
      "/admin/products/import",
      class: "button",
      method: "post",
      data: {:confirm => "click to start import and wait for an email after it's done."}
    ) %>
```
Here, data hash is used for confirmation box. This is probably similar to the data-remote method (unobstrusive javascript).
