# Database Concepts

A **database** is an organized collection of data that can be easily accessed, managed, and updated. Below are some key concepts related to databases:

## 1. Data
Data refers to raw facts and figures that are stored in a database. It can be structured (e.g., tables) or unstructured (e.g., documents, images).

## 2. Database Management System (DBMS)
A **DBMS** is software that allows users to define, create, maintain, and control access to the database. Examples include MySQL, PostgreSQL, MongoDB, and Oracle.

## 3. Tables
In relational databases, data is stored in **tables**, which consist of rows (records) and columns (fields).

## 4. Primary Key
A **primary key** is a unique identifier for a record in a table. It ensures that no two rows have the same value for this key.

## 5. Foreign Key
A **foreign key** is a field in one table that refers to the primary key in another table, establishing a relationship between the two tables.

## 6. Normalization
**Normalization** is the process of organizing data to reduce redundancy and improve data integrity. It involves dividing large tables into smaller ones and defining relationships between them.

## 7. Transactions
**Transaction** is a sequence of operations performed as a single logical unit of work. Transactions follow the **ACID** properties:

- **Atomicity**: All operations succeed or none do.
- **Consistency**: The database remains in a valid state.
- **Isolation**: Transactions do not interfere with each other.
- **Durability**: Changes are permanent once a transaction is committed.

## 8. Indexing
**Indexing** improves the speed of data retrieval by creating a data structure that allows quick lookups.

## 9. SQL
**Structured Query Language (SQL)** is used to interact with relational databases. Common SQL commands include:
- `SELECT`: Retrieve data.
- `INSERT`: Add new data.
- `UPDATE`: Modify existing data.
- `DELETE`: Remove data.

## 10. NoSQL Databases
**NoSQL databases** are non-relational and are designed for specific use cases like handling large-scale, unstructured data. Examples include MongoDB, Cassandra, and Redis.

## 11. Backup and Recovery
Databases must have mechanisms for **backup** (creating copies of data) and **recovery** (restoring data in case of failure).

## 12. Data Security
Ensuring data security involves controlling access, encrypting sensitive data, and protecting against unauthorized access or breaches.

Understanding these concepts is fundamental for designing, managing, and optimizing databases effectively.