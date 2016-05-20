### How to localize a view
* Helper methods: 
  * `I18n.t`: translate. input argument is the key (a symbol or string) to the dictionary.
  * `I18n.l`: localize. Used for Time and Date object
* Use helper methods in a view or controller.
  * `t(:hello)`: use the string corresponding to the `hello` entry in the dictionary.
  * `t(:hello, default: "HELLO")`: if no locale is given, use "HELLO".
  * `t(:hello, name: current_user.name)`: The translation can take input arguments. Use `%{name}` to access the variable in dictionary.
  * `t('.hello')`: use lazy (relative) look up. See [i18n dictionary](i18n_dictionary.md) for details. It works only in view and controller. For helpers, use
                  the full path.
  
