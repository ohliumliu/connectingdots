# General procedure to setup associations in active records
  [Reference](http://guides.rubyonrails.org/association_basics.html)
  Take many-to-many (users, books) as an example, one needs to set it up in both the model and the database
  1. In model files
    * usr.rb
  
    `has_many_and_belongs_to :books`
    * book.rb
    
    `has_many_and_belongs_to: users`
  1. In the migration file to set up a join table. The default of the table name is BooksUsers

    ```ruby
    class CreateBooksAndUsers < ActiveRecord::Migration[5.0]
      def change
        create_table :books_users, id: false do |t|
          t.belongs_to :user, index: true
          t.belongs_to :book, index: true
        end
      end
    end
    ```
    It does the following:
      * Generate a table
      * This table belongs to :user and :book at the same time. And foreign keys are added accordingly by setting `index:true`.
      * Because of the use of `has_many_and_belongs_to`, Rails knows that users and books `has_many` this new join table.
      * This join table doesn't have an index. This is important to avoid confusion.
  
  ----
  After this operation and migration, it is possible to run something like these
  ```ruby
  User.first.books # all the books associated with the first user
  User.first.books.create(params) # create a new book and associate it with the first user
  User.first.books << Book.find_by(:name => "a book for you") # associate a book with the first user
  ```
# Work with administrate
  [Administrate](administrate.md) is smart enough to include the associated items in the dashboard. One just needs to add to the user dashboard by doing the following
  ```ruby
  # set up a field to show books associated with a user
  ATTRIBUTE_TYPES = {
    # ommited
    books: Field::HasMany,
    # commited
  }
  
  # later
  # decide where to show the books field
  SHOW_PAGE_ATTRIBUTES = [
    #ommited
    :videos,
    #ommited
  }
  ```
