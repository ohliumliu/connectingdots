* http://c9.io
* directly clone from git hub or bitbucket (doesn't work, because I don't know how to force rails update to 4.2. 
see [Gemfile.lock](gemfile_lock.md). It's recommended to use rbenv or rvm. 
* gem install rails
* gem install mysql2 and follow https://docs.c9.io/docs/setting-up-mysql
* generate a new rails project flash-deals-c9
* gem 'protected_attributes' in order to use deprecated attr_accessible helper
* change the first line of routes.rb to     `Rails.application.routes.draw do`
* `mysql-ctrl restart` and then create database for the project
* bundle exec db:migrate
* bundle exec db:seed
* for git, see [gitconfig](gitconfig.md) and [gitignore](gitignore.md)
