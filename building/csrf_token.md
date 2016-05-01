## Purpose

It is required as a safety feature to guard against cross site request forgery. See [csrf](http://guides.rubyonrails.org/security.html#cross-site-request-forgery-csrf)

## Implementation in rails

* Add `protect_from_forgery` toapplication_controller.rb
* Every new request will get a new csrf token from the site. The next request starts with comparing this token with the server. 
If they are not the same, the token along with the whole session will be reset and a csrf token warning issued. 
But the token in user's browser stays the same. The next request will not go through if it needs token authentication.

## How to send token with request

*Form: add a hidden field `<%= hidden_field_tag :authenticity_token, form_authenticity_token %>`
*Form helper: don't need to worry about it.
*Ajax call: see [Ajax and JQuery](ajax_and_jquery.md)

## Example

User signup form doesn't have csrf-token field

|Step|Local token|server token|comment|
|---|---|---|---|
|homepage|token1|token1||
|signup page|token2|token2||
|submit signup info|token2|token2->nil| no csrf token field in form, so server token = nil due to failed verification|
|signin|token2|token3->nil||
|add alert|token2|token4->nil|token mismatch warning and session[:user_id].nil?. The later is the direct cause of error (see controller code)|
|signout|token3|token3||
|signin|token3|token3||
|add alert|token3|token3|works|

Reference: http://stackoverflow.com/a/11943243
