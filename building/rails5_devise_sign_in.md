When writing a controller test, I need to mock a user sign in event. Since devise is used to manager user resource and it provides
some helpers such as sign_in (see [cheatsheet](http://ricostacruz.com/cheatsheets/devise.html)). But it doesn't work due to several
reasons.

1. Integration test vs controller test
In rails5, controller test is generated as an integration test. However, devise helper functions are not supposed to be used for 
integration tests, because you want to test the actual sign_in and etc in the integration test. See https://github.com/plataformatec/devise/issues/3913.
The current workaround:
  * Use post or other proper http request to sign in
  For example, one can have a sign_in helper in test_helper.rb
  ```ruby
  def sign_in(user)
    post user_session_path, params: { user: {email: user[:email], password: user[:password]}}
  end
  ```
  In order for this to work, user is a hash containing email and password. This is how it's used in a test:
  ```ruby
  setup do
    @video = videos(:one)
    user = {email: users(:test_user).email, password: "passwd"}
    sign_in(user)
  end
  ```
  The assumption here is that there is a test_user in the fixture and its password is "passwd". It's ok to use a freshly made user
  just for the sake of testing. For example, another sign_in helper could consists of user.create and post.
  * Use warden
  
  TBD
1. Use of fixture
Of course, it sounds better to use fixture. First of all, password cannot be saved as plain text in the database, so yml file
has to encrypt the password by using Devise:Encryptor.digest. When we do the post in sign_in method, however, we cannot get the 
original, unencrypted password from the fixture variable. In the above, I need to know the password of users(:test_user)
is "password". To avoid this "hard" link, maybe the password can be saved somewhere when setting up the fixture.
