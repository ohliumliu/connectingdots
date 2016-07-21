## Here is some note regarding Active Record scope in the context of kaminari

1. Scope

  In activerecord, one can define a so called scope. From a coding perspective, it is simply a _class_ method that returns
the result of a query. Of course, it is also possible to explicitly define it as a "scope".

  The scope is more than the method itself. In addition to the operations defined in the method, it also stores the input
arguments and other variables.

  The scope doesn't return the result of the query per se. Instead, it turns an ActiveRecord Relation which has a `each` method.

  The use of scope allows user to extend it by adding more refinement scopes later on.

1. Kaminari as an example

  1. Define `page` scope
  
  In earlier version of kaminari, page scope is explicitly defined as a scope. Later versions of rails recommends the use
  of class method. In addtion, the name of the page method is also configurable. 
  ```ruby
        #   Model.page(5)
      eval <<-RUBY
        def self.#{Kaminari.config.page_method_name}(num = nil)
          limit(default_per_page).offset(default_per_page * ((num = num.to_i - 1) < 0 ? 0 : num)).extending do
            include Kaminari::ActiveRecordRelationMethods
            include Kaminari::PageScopeMethods
          end
        end

      RUBY
  ```
  The line of code inside the method defintion does two things:
    
    * provide `limit_value` and `offset_value` to page scope. `limit` and `offset` are both ActiveRecord class methods. It
    returns a scope which includes the result of query as a relation and also sets `limit_value` and `offset_value` that come
    with the scope. `limit_value` and `offset_value` are used as the values for `LIMIT` and `OFFSET` keywords in SQL query.
    * Extend page scope with more methods.
    
  1. Define `per` method
  This method essentially redefines limit and offset given the new parameter for the number of itmes in each page. It uses 
  the existing offset_value and limit_value to calculate the page number.
  ```ruby
  def per(num)
      if (n = num.to_i) < 0 || !(/^\d/ =~ num.to_s)
        self
      elsif n.zero?
        limit(n)
      elsif max_per_page && max_per_page < n
        limit(max_per_page).offset(offset_value / limit_value * max_per_page)
      else
        limit(n).offset(offset_value / limit_value * n)
      end
    end
  ```
