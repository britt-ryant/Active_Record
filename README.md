# Active_Record
Ruby slips for Active Record




Active Record is the interface that Rails gives you between the database and your application.
It is the Object/Relational Mapping (ORM) layer supplied with Rails.
So:
-tables map to classes,
-rows map to objects and
-columns map to object attributes.

Active Record takes data which is stored in a database table using rows and columns,
which needs to be modified or retrieved by writing SQL statements
(if you’re using a SQL database),
and it lets you interact with that data as though it was a normal Ruby object.

Each Active Record object has CRUD (Create, Read, Update, and Delete) methods for database access.
This strategy allows simple designs and straight forward mappings between database tables and application objects.

--Creating Active Record Files--

similar to SQL, active record tables will use the id column that is created for all items in the table.

naming convention of camelcase for the Model/Class and underscore plural for the Table /Schema

Active Record will perform queries on the database for you and is compatible with most database systems, including MySQL, MariaDB, PostgreSQL, and SQLite. Regardless of which database system you're using, the Active Record method format will always be the same.

#1) This would link to the products table in the database:

    class Product < ApplicationRecord
    end


#2) SQL that was used to create corresponding table:

      CREATE TABLE products (
         id int(11) NOT NULL auto_increment,
         name varchar(255),
         PRIMARY KEY  (id)
      );

#3) CREATE
      user = User.new
      product.name = "John"
      product.occupation = "developer"

#4) READ
      users = User.all

      user = User.first

      david = User.find_by(name: 'David')

      users = User.where(name: 'David', occupation: 'Code Artist').order(created_at: :desc)

#5) UPDATE
      user = User.find_by(name: 'David')
      user.name = 'Dave'
      user.save

    *Multiples*
      User.update_all "max_login_attempts = 3, must_change_password = 'true'"

#6) DELETE
      user = User.find_by(name: 'David')
      user.destroy



Rails provides a domain specific language used for managing a database schema call MIGRATIONS

    *** this sill run MySQL & PostgreSQL, it is database-agnostic ***

      class CreatePublications < ActiveRecord::Migration[5.0]
        def change
          create_table :publications do |t|
            t.string :title
            t.text :description
            t.references :publication_type
            t.integer :publisher_id
            t.string :publisher_type
            t.boolean :single_issue

            t.timestamps
          end
          add_index :publications, :publication_type_id
        end
      end



#Retrieving from db:

find
create_with
distinct
eager_load
extending
from
group
having
includes
joins
left_outer_joins
limit
lock
none
offset
order
preload
readonly
references
reorder
reverse_order
select
where



#Active Record
# Find the client with primary key (id) 10.
client = Client.find(10)

#SQL
SELECT * FROM clients WHERE (clients.id = 10) LIMIT 1

#Active Record
# Find the clients with primary keys 1 and 10.
client = Client.find([1, 10]) # Or even Client.find(1, 10)

#SQL
SELECT * FROM clients WHERE (clients.id IN (1,10))


#Active Record
client = Client.first(3)

#SQL
SELECT * FROM clients ORDER BY clients.id ASC LIMIT 3

#Active Record
Client.where(first_name: 'Lifo').take

#SQL
SELECT * FROM clients WHERE (clients.first_name = 'Lifo') LIMIT 1
