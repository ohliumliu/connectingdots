In order to use delayed job, need to install the following

* gem 'delayed_job_active_record'
* gem 'daemons'

Delayed job needs a table (as active record), so one needs to generate the table and migrate

* rails generate delayed_job:active_record
* bundle exec rake db:migrate

Jobs can be invoked in two ways

```
controller.delay.method
```
or

```
Delayed::Job.enqueue JobClass.new(users, users.count)
```
Here JobClass must define a method "perform" which is enqueued. Either way, the job is added to delayed_jobs table. 

In order to run the job, one need to add a worker by

```
bundle exec rake jobs:work
```
This has to be done before enqueueing the job.

[progress job](progress_job.md) can be used with delayed job to implement status update.
