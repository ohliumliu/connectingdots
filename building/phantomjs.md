## PhantomJS and Poltergeist
### Outline
PhantomJS is a headless browser. It supports javascripts. In order for Capybara to talk with PhantomJS, Poltergeist is needed.
Poltergeist can also perform browser interaction, such as click at a certain location or take a screenshot, but its main use is
to be a bridge between capybara and PhantomJS.
### Installation
  * PhantomJS is not part of rails app. It needs to be installed as a system package.
  * Poltergeist is a gem.
  * After installation, we need to tell capybara to use them by the following to `features/support/env.rb`.
  ```ruby
  require 'capybara/poltergeist'

  Capybara.default_driver = :poltergeist # use this driver for all capybara tests. If not set, need to add @javascript tag before
                                         # the features to be tested using this driver.
  Capybara.register_driver :poltergeist do |app|
    Capybara::Poltergeist::Driver.new(app, {debug: false})
  end

  Capybara.javascript_driver = :poltergeist
  ```
  In fact, it is recommended to save this settings in a separate rb file because `env.rb` may be overwritten by future upgrade
  of capybara or cucumber.
  
### Usage
  Sometimes it's helpful to set a break point and take a screenshot: `page.save_screenshot('path_to_png_file', full: true)`.
