---
title: Create and delete tables and indexes using Access SQL
ms.prod: access
ms.assetid: 44c9e6a7-ac29-7a88-e0c6-b7eaec1e95ea
ms.date: 09/18/2021
ms.localizationpriority: medium
---


# Create and delete tables and indexes using Access SQL

Tables are the primary building blocks of a relational database. A table contains rows (or records) of data, and each row is organized into a finite number of columns (or fields). To build a new table in Access by using Access SQL, you must name the table, name the fields, and define the type of data that the fields will contain. Use the **[CREATE TABLE](/office/client-developer/access/desktop-database-reference/create-table-statement-microsoft-access-sql)** statement to define the table in SQL. Suppose that you are building an invoicing database. The first step is to build the initial customers table.

```sql
CREATE TABLE tblCustomers  
    (CustomerID INTEGER, 
    [Last Name] TEXT(50), 
    [First Name] TEXT(50), 
    Phone TEXT(10), 
    Email TEXT(50)) 

```

Be aware of the following issues when creating and deleting tables:

- If a field name includes a space or some other nonalphanumeric character, you must enclose that field name within square brackets ([ ]).     
- If you don't declare a length for text fields, they will default to 255 characters. For consistency and code readability, you should always define your field lengths. 
    
You can declare a field to be **NOT NULL**, which means that null values cannot be inserted into that particular field; a value is always required. A null value should not be confused with an empty string or a value of 0; it is simply the database representation of an unknown value.

```sql
CREATE TABLE tblCustomers  
    (CustomerID INTEGER NOT NULL, 
    [Last Name] TEXT(50) NOT NULL, 
    [First Name] TEXT(50) NOT NULL, 
    Phone TEXT(10), 
    Email TEXT(50)) 

```

To remove a table from the database, use the **[DROP TABLE](/office/client-developer/access/desktop-database-reference/drop-statement-microsoft-access-sql)** statement.

```sql
DROP TABLE tblCustomers 

```
## Create and delete indexes

An index is an external data structure used to sort or arrange pointers to data in a table. When you apply an index to a table, you are specifying a certain arrangement of the data so that it can be accessed more quickly. However, if you apply too many indexes to a table, you may slow down the performance because there is extra overhead involved in maintaining the index, and because an index can cause locking issues when used in a multiuser environment. Used in the correct context, an index can greatly improve the performance of an application.

To build an index on a table, you must name the index, name the table to build the index on, name the field or fields within the table to use, and name the options you want to use. You use the **[CREATE INDEX](/office/client-developer/access/desktop-database-reference/create-index-statement-microsoft-access-sql)** statement to build the index. For example, you could build an index on the customers table in the invoicing database mentioned earlier by using the following code:

```sql
CREATE INDEX idxCustomerID  
    ON tblCustomers (CustomerID) 

```

Indexed fields can be sorted in one of two ways: ascending (**ASC**) or descending (**DESC**). The default order is ascending, and it does not have to be declared. If you use ascending order, the data will be sorted from 1 to 100. If you specify descending order, the data will be sorted from 100 to 1. You should declare the sort order with each field in the index.

```sql
CREATE INDEX idxCustomerID  
    ON tblCustomers (CustomerID DESC) 

```

There are four main options that you can use with an index: **PRIMARY**, **DISALLOW NULL**, **IGNORE NULL**, and **UNIQUE**. The **PRIMARY** option designates the index as the primary key for the table. You can have only one primary key index per table, although the primary key index can be declared with more than one field. Use the WITH keyword to declare the index options.

```sql
CREATE INDEX idxCustomerID  
    ON tblCustomers (CustomerID) 
    WITH PRIMARY 

```

To create a primary key index on more than one field, include all of the field names in the field list.

```sql
CREATE INDEX idxCustomerName  
    ON tblCustomers ([Last Name], [First Name]) 
    WITH PRIMARY 

```

The **DISALLOW NULL** option prevents insertion of null data in the field. (This is similar to the **NOT NULL** declaration used in the **CREATE TABLE** statement.)

```sql
CREATE INDEX idxCustomerEmail  
    ON tblCustomers (Email) 
    WITH DISALLOW NULL 

```

The **IGNORE NULL** option causes null data in the table to be ignored for the index. That means that any record that has a null value in the declared field will not be used (or counted) in the index.

```sql
CREATE INDEX idxCustomerLastName  
    ON tblCustomers ([Last Name]) 
    WITH IGNORE NULL 

```

In addition to the **PRIMARY**, **DISALLOW NULL**, and **IGNORE NULL** options, you can also declare the index as **UNIQUE**, which means that only unique, non-repeating values can be inserted in the indexed field.

```sql
CREATE UNIQUE INDEX idxCustomerPhone  
    ON tblCustomers (Phone) 

```

To remove an index from a table, use the **DROP INDEX** statement.

```sql
DROP INDEX idxName 
    ON tblCustomers 

```

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
