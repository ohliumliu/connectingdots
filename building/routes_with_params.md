Two ways to define params in routes

|In routes                      |                                        In html| In erb.html
|----|---|---|
|get ‘products/show’, to: ‘product#show’|               domain/products/show?id=xxx|link_to 'a link', show_path(id: 'xxx'), method: :get OR link_to 'a link', :controller => :users, :action => :show
|get ‘products/show/:id/:category_id’, to: ‘product#show’          |domain/products/show/xxx/yyy|lind_to 'a link', '/products/show/' + id + category_di|

The first method allows more flexibility in the front end, but viewer would know what params are used. 
The second method limit the possible params.
