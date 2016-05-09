# Administrate
* Reference: https://github.com/thoughtbot/administrate
* For Rails 5: https://github.com/thoughtbot/administrate/issues/404
```rails
gem 'administrate', github: 'hayesr/administrate', branch: 'rails5_compat'
```
* Need authentication in admin/application_controller
* To customize the view, need to generate a adminstrate view first
```rails
rails generate administrate:views:index
```
