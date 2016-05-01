##Installation

* gem 'whenever', require: false (whenever is installed but not loaded unless required explicitly)
* bundle install
* wheneverize . (in root directory. a sample config/schedule.rb is generated)
* edit schedule.rb
* run whenever to preview the entry to be written to the crontab
* whenever -w to save the crontab (check the result using crontab -e)
* whenever -c to remove all the tasks

Whenever by default can handle three kinds of tasks

* [rake task](rake_task.md)
* method in the app
* executable in the OS

