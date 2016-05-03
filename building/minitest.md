* Rails uses minitest
* Fixtures.
  In fixtures folder, one can provide some instance of a model such that it is not needed to write many `User.new` in the test
  code.
  ```ruby
  test_user:
    name: 'test'
  ```
  This code in fixture/users.yml provides a test_user that can be accessed in test methods by
  * users(:test_user)
  * @test_user (need to turn on auto instantiation to use this one)
  users(:test_user) is local within each test method, so no need to worry about crosstalk between different test methods.
* Rails 5 allows running tests directly
  `rails test path_to_test_file.rb:15`
  Only this file is tested, and only the method containing line 15 is tested.
* Try to use assert_equal and etc rather than plain assert so that the default failure message is provided.
* Test cases
```ruby
test "a test" do
  assert true
end
```
   Alternatively, define a method explicityly.
```ruby
def a_test
  assert true
end
```
   These are equivalent. But the latter allows us to further organize methods into modules.
