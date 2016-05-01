Rake tasks reside in /lib/tasks with extension .rake.

Here is a sample file

```
desc 'import amazon'
task import_amazon: :environment do
  # ... set options if any
  user_id = User.where(isadmin: true).first.id
  Delayed::Job.enqueue ImportAmazonJob.new(user_id)

end
```
Explanation:
* desc: a short description of the task
* name of the task is import_amazon
* `:environment` loads the app environment

Check if the task is available using `rake -T`

Run the task using `bundle exec rake import_amazon`
