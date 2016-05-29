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
* To add new resources:
  * Add route with resources scope
  * Add controller
  * Add dashboard file
  * [optional] add view
 
* To customize how a resource is displayed when being referenced, follow the in code doc,
```ruby
  # In dashboard file
  # Overwrite this method to customize how videos are displayed
  # across all pages of the admin dashboard.
  #
  def display_resource(tag)
    "Tag ##{tag.id} #{tag.name}"
  end
 ```
 This is necessary for has_many field. Administrate uses a jQuery library selectize to control
 the drop down selection menu. After reading the source code, I realized that this is controlled by `display_resource`
 in `BaseDashboard`. Because each resource's dashboard subclasses this base dashboard class, we can change the behavior
 of `display_resource` for each resource. This is suggested in the dashboard.rb file, but I didn't realize that this also applies to has_many selection menus.
