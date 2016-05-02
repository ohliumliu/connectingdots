* Installation

* Usage

  ** A fresh install can only be accessed by using a role (user) called postgres. New users can be added using this superuser.
  
  ** Local access to db server doesn't need authentication if db username is the same as system username that is being used.
  
  ** Every connection to the db opens a database. To open a new one, use 
  
  `\c another_db`
  
  ** \dt: display table
  
  ** \list: show databases
