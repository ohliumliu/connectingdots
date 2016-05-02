Do the following to add dealer model. Branch: add_dealer

* Generate model and migrate. Add two dealers: Amazon and Fry's. Associate dealers and products.

* Rewrite _left.html to update catalogue links to include dealer_id as second param. Update routes.

* update show#show to handle dealer_id

* update banners to show products from different dealers.

* update AmazonApi to set dealer_id

* For catalogue links, it uses unobstrusive js, and the url contains dealer_id provided by @dealer_id. 
For search function, it uses javascript and ajax, the action should handle dealer_id provided in session. 

* Need to make sure to update session[:dealer_id] and @dealer_id when needed.
