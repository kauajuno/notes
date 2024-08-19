# Basics

Let's start with the SQL basics.

## Creating a database

To create a database in SQL, the following command is used:

```SQL
CREATE DATABASE database_name;
```

In order to apply any change to the now created database, it's necessary to run the following command:

```SQL
USE DATABASE database_name;
```

## Creating tables

Tables are the main component of relational databases. They're composed by columns and rows, which define the attributes or properties of the data being stored and represents the data being stored, respectively. Rows are also often called records (which semantically makes more sense) and tuples (a frequently used term in relational database theory).

In order to create a table in SQL, you must specify the name of the table and which columns it is going to have.

```SQL
CREATE TABLE customers (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100),
    phone_number VARCHAR(20),
    address VARCHAR(255),
    city VARCHAR(50),
    state VARCHAR(50),
    zip_code VARCHAR(20),
    country VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

In the example above, a table named customers is being created. This table has the following attributes: customer_id, first_name, last_name, email, phone_number, address, city, state, zip_code, country, created_at and updated_at. The keywords after each attribute define their [[SQL types|type]].

Now the table has its columns defined, but it doesn't have any rows yet as no data was inserted into it yet. Let's keep that table in mind for the following examples.

## Inserting data into a table

There are multiple ways of inserting data into a table, let's start with the easy ones.

First, one at a time:

```SQL
INSERT INTO customers (first_name, last_name, email, phone_number, address, city, state, zip_code, country)

VALUES ('John', 'Doe', 'johndoe@example.com', '123-456-7890', '123 Main St', 'Anytown', 'CA', '12345', 'USA');

  
INSERT INTO customers (first_name, last_name, email, phone_number, address, city, state, zip_code, country)

VALUES ('Jane', 'Smith', 'janesmith@example.com', '987-654-3210', '456 Elm St', 'Othertown', 'NY', '54321', 'USA');
```

Now multiple at once:

```SQL
INSERT INTO customers (first_name, last_name, email, phone_number, address, city, state, zip_code, country) VALUES

('Michael', 'Johnson', 'michaeljohnson@example.com', '555-123-4567', '789 Oak Ave', 'Somewhere', 'TX', '78901', 'USA'),

('Emily', 'Davis', 'emilydavis@example.com', '444-555-6666', '101 Pine Rd', 'Anothertown', 'FL', '34567', 'USA'),

('David', 'Lee', 'davidlee@example.com', '333-222-1111', '202 Cedar Ln', 'Anycity', 'IL', '67890', 'USA');
```

## Consulting the data

To see everything stored in the table, i.e., every column of every row, the following command can be ran.

```SQL
SELECT * FROM customers;
```

This outputs every record in the table without any filter.