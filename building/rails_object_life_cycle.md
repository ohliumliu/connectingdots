As in Android, rails object also has life cycle and the associated callbacks.
* action controller: before_action, after_action, around_action etc.
* active record: before_save, after_save, around_save and etc.

There are several ways to supply the operational details:
* name of a private or protected method (a symbol)
* name of a wrapper class implementing the needed methods say, before_save. This method will be default send the instance of a
record as input argument. For details, read http://api.rubyonrails.org/classes/ActiveRecord/Callbacks.html
