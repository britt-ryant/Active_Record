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

Active Record will perform queries on the database for you and is compatible with most database systems, including MySQL, MariaDB, PostgreSQL, and SQLite. Regardless of which database system you're using, the Active Record method format will always be the same.

Retrieving from db:

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



Active Record
# Find the client with primary key (id) 10.
client = Client.find(10)

SQL
SELECT * FROM clients WHERE (clients.id = 10) LIMIT 1

Active Record
# Find the clients with primary keys 1 and 10.
client = Client.find([1, 10]) # Or even Client.find(1, 10)

SQL
SELECT * FROM clients WHERE (clients.id IN (1,10))


Active Record
client = Client.first(3)

SQL
SELECT * FROM clients ORDER BY clients.id ASC LIMIT 3

Active Record
Client.where(first_name: 'Lifo').take

SQL
SELECT * FROM clients WHERE (clients.first_name = 'Lifo') LIMIT 1
