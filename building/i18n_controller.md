### Set up and use i18n in controller
* Setup
 ```ruby
    # class ApplicationController < ActionController::Base
    ...
      before_action :set_locale
      
      # This method would insert a scope field (/en/ or /zh-CN/) in front of all the urls generated by url helper methods.
      # If url is hard-coded, of course, one needes to include the locale info in the url. 
      def default_url_options(options = {})
        { locale: I18n.locale }.merge options
      end 
      
      # This method get the locale param from the url before each action.
      def set_local:
        I18n.locale = params[:locale]||I18n.default_locale
      end
    ```
 Before an action is initiated, `I18n.locale` is set by `set_locale`. Aftwards, whenever `url_for` is called, a hash `{locale: I18n.locale}` is
 merged with other options in order to persist the current locale in the url.
 
* Use of helper method

 The helper methods `I18n.t` and `I18n.l` are also available with lazy lookup.
