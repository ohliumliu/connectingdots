http://blog.markusproject.org/?p=3313

render can keep the instance variables and flash messages. redirect_to is a new request and instance
variables/flash messages will be lost because of the stateless nature of http request.
