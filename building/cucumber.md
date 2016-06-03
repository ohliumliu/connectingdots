## Cucumber
### Installation and initialization
1. In Gemfile, add
```ruby
group :test do
  gem 'cucumber-rails', require: false
  gem 'database_cleaner'
end
```
2. Run `bundle install`
3. Run `bundle exec rails generate cucumber:install` to set up cucumber and generate feature folder

### Feature definition
* features/foo.feature
* step_definitions/foo_steps.rb
These two files work together. The first one define a feature in plain language, and the next one contains code to 
realize the steps using ruby code. The naming of the step definition files is flexible as long as its extension is rb. In fact,
by default, all .rb file under features/ folder (recursively) are accessible from any feature files.

### Good reference
https://github.com/cucumber/cucumber/wiki/Cucumber-Backgrounder
