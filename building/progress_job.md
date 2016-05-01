Reference [Progress Job](https://infinum.co/the-capsized-eight/articles/progress-bar-in-rails)

Progress job gem provides useful helper functions to update the status of the job. 

Run the following to use it

```
 $ rails generate delayed_job:active_record
 $ rails generate progress_job:install
 $ rake db:migrate
```
It adds three new fields to the delayed_job table.

* progress_stage: string
* progress_current: integer
* progress_max: integer

It provides a GET resource to obtain json data of a particular job. URL is `/progress-job/id@`

A job is enqueued the same way as [Delayed job](delayed_job.md), with the exception that progress_max 
needs to be supplied in the initialization step. Normally, job class is in job folder, so variables 
from other controllers have to be transferred as initialization parameter as well.

To update the progress of a long running task, ajax call is used to query the status of a job at constant interval
(setInterval) and update the html accordingly. Remember to clear the interval when there is an error 
(if job.last_error != null) or when the job is done (ajax return status is error).

In flashDeals, see admin/products_controller. The button to import amazon has `remote=true` as an attribute, 
and js.erb file should be provided to run the status query ajax calls.

There is currently a huge security risk. The handler field of the job entry contains all the details of the job, 
because I transferred the user field. Either only transfer the user_id (done), or add authentication for /progress-job/id resource.
