## Rails internationalization
  [Reference](http://guides.rubyonrails.org/i18n.html)
### The following is the big picture of i18n procedure
  * Model configuration: optional
  
  * View configuration: necessary
    Change strings to reference to variables in locale files. For example, `t(:hello)` will be translated (hence the short cut `t`) to 
    different languages according to locale.
    [Details](i18n_view.md)
  * Controller configuration: necessary
  
    Let controller parse the URL to extract locale setting.
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
    [Details](i18n_controller.md)
  * Route configuration: normally necessary
  
    Add an __optional__ locale scope (/en/ or /zh-CN/) to the routes.
    ```ruby
    scope "(/:locale)", locale: /en|zh-CN/ do
      #all the route definitions
    end
    ```
    
    root needs some special treatment to handle requests with a locale parameter such as `http://site/`.
    ```ruby
      get '/:locale' => 'videos#index' 
      root to: 'videos#index'
    ```
    [Details](i18_routes.md)
  * Dictionary: necessary
  
    Provide locale dictionary in config/locale or other places. [Detail](i18n_dictionary.md)
