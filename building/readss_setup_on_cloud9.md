* Setup a rails project and clone from https://github.com/Techbay/readss.git
* Setup a new ruby environment using [rbenv](rbenv.md). Follow this [instruction](https://github.com/Techbay/server-bootstrap/blob/master/production.sh#L60-L76),
 with $ruby_version set to 2.3.0. Remember to replace .bashrc with .profile and source it.
* Follow [cloud9 postgresql](https://community.c9.io/t/setting-up-postgresql/1573] to set up [postgresql](postgresql.md) db user
and password. I use postgres that comes with the db. It's ok to make a new one. Create a table "readss". 
Start the db server (`sudo service postgresql start`)
* Copy config/application.example.yml to config/application.yml. This is used by [figaro](figaro.md). 
Change the development db user name and password.
* `bundle install` in project directory.
* `bundle exec rake db:migrate`
* `rails s -b $IP -p $PORT`
* It's running http://readss-ohliumliu.c9users.io:8080
