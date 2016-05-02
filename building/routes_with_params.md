Two ways to define params in routes

|In routes                      |                                        In html|
|----|---|
|get ‘products/show’, to: ‘product#show’|               domain/products/show?id=xxx|
|get ‘products/show/:id/:category_id’, to: ‘product#show’          |domain/products/show/xxx/yyy|

The first method allows more flexibility in the front end, but viewer would know what params are used. 
The second method limit the possible params.
