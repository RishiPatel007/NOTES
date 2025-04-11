A database is an electronically stored, systematic collection of data. It can contain any type of data, including words, numbers, images, videos, and files. You can use software called a database management system (DBMS) to store, retrieve, and edit data.

# Advantages 

- More secure by giving different access to different people
- Inbuilt data manipulation tools
- Efficient data retrieval and updation (In file we have to read and write every time , and we can't access particular entries like products with this price and this quantity)
- Reduce redundency
- Crash and Backup recovery
- Complex data operation like relation between two tables
- Maintained data integrity , consistency and systematic data 

# Structured query language (SQL)

To interact with relational databases, we use Structured Query Language (SQL). This powerful language enables us to query, insert, update, and delete data, as well as perform complex operations like joining data from multiple tables. SQL's structured nature ensures data integrity and consistency through ACID properties:

- **Atomicity**: All operations within a transaction are treated as a single unit, ensuring that either all changes are committed or none are.
- **Consistency**: Data remains in a valid state throughout a transaction, adhering to predefined constraints and rules.
- **Isolation**: Transactions are executed independently as if they were the only operation happening on the database.
- **Durability**: Once a transaction is committed, its changes are permanent, even in the event of system failures.

# Different keys

- Super Key : Set of combination of keys which can uniquely identify a tuple
- Composite Key :  Set of combination of keys which can uniquely identify a tuple when there is no primary key
- Candidate Key : Potential primary key
- Primary Key : Minimum combination of keys which can uniquely identify a tuple
- Foreign Key : Primary key of other table

# Normalization

Normalization, in this context, is the process of organizing data within a database to eliminate data anomalies, such as redundancy.

In simpler terms, it involves breaking down a large, complex table into smaller and simpler tables while maintaining data relationships.

Normalization is commonly used when dealing with large datasets.


# Orm & Odm

## ORM

ORM is **Object Relational Mapping,** basically a technique to query or perform _CRUD_ (Create, Read, Update, Delete) operations to the database, mainly RDBMS (Relational Databases), using an _object-oriented paradigm_.

With the help of ORM, you don’t actually need to use SQL at all. You can directly interact with the database and perform queries in the same language you are using for your back-end code!

### Example : Using Sequelize (library for sql database)

## ODM

ODM is **Object Document Mapping**. It is like an ORM for non-relational databases or distributed databases such as MongoDB, i.e., mapping an object model and NoSQL database 

### Example : Using Mongoose

