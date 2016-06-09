## Capybara
### Installation
capybara comes with cucumber-rails gem
### Outline
Capybara is a ruby domain specific language to perform operation on html files. For example, it can look for certain html
elements, click buttons or fill in forms.
### Workflow
Use a browser, find the element to use by using "inspect element". In browser's developer tool console, make sure the css selector
works using the search function. This css selector can be used as input for capybara command

This following is some sample code. Note that some steps are refactored out to be a separate method. These methods can also
be used by other step definitions files in the features folder.
```ruby
When(/^User "([^"]*)":"([^"]*)" has( not)? logged in$/) do |email, password, bool|
  to_sign_in = !bool
  if to_sign_in
    sign_in_user(email, password)# Write code here that turns the phrase above into concrete actions
  else
    sign_in_user(email, password*2)
  end
  @current_user = User.find_by_email(email)
end

Then(/^I should( not)? see "([^"]*)"$/) do |bool, str|
  expected = !bool
  actual = page.has_content?(str)
  msg = 'I should#{bool} see #{str}#'
  assert_equal expected, actual, msg
end


def sign_in_user(email, password)
  visit root_path
  click_link("Log In")
  fill_in("inputEmail", with: email)
  fill_in("inputPassword", with: password)
  click_button("Sign in")
end
```
Capybara's in-code comment is actually very helpful ([Github](https://github.com/jnicklas/capybara/blob/master/lib/capybara/node/matchers.rb#L201)).

### Browser
Capybara simulates operations on a browser, and it supports several browsers, called driver in this context. The default doesn't
support javascript, so we need to use an alternative. I am using [PhantomJS with Poltergeist](phantomjs.md).
