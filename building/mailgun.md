Cloud9 doesn't allow the use of sendmail to send smtp email. Mailgun is a free service that provides a ruby gem api.

* Gemfile: need rest-client and mailgun-ruby

There are multiple ways to use mailgun in a rails project

* Write the code following the samples from mailgun. 

The method can be put in a class and saved in lib 
(for example, sendMailgun.rb in lib to act as a mailer). Remember to require 'libfilename.rb' in the controllers that 
need to send email. In this case, the content of the email is generated by the controller.

* Use a gem [mailgun_rails](https://github.com/jorgemanrubia/mailgun_rails). 

This gem provides a wrapper
for mailgun api so that changing the configuration file is all needed to invoke mailgun. It works.

* Hook up mailgun with actionmailer

Reference: [http://www.alanverga.com/blog/2014/01/03/custom-rails-mailer-and-mandrill] and
[https://codedecoder.wordpress.com/2014/02/10/email-through-api-override-action_mailer-deliver/]
I am not done with this method.