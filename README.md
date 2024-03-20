![RDB](https://github.com/chigozie-i/Data-Source-Relational-Databases/blob/main/Connecting%20To%20RDB.png)



### Table of Contents

- [Stored Procedure](#Stored-Procedure)
- [Why Use Stored Procedure](#Why-Use-Stored-Procedure)
- [Syntax of a Simple Stored Procedure](#Syntax-of-a-Simple-Stored-Procedure)
- [How To Execute a Stored Procedure](#How-To-Execute-a-Stored-Procedure)
- [Parameters In Stored Procedures](#Parameters-In-Stored-Procedures)
- [Conclusion](#Conclusion)
- [Reference](#Reference)

## What is a Stored Procedure?

A Stored Procedure in T-SQL (Transact-SQL) is a precompiled collection of SQL statements, to be executed whenever needed. It's like a saved set of instructions that can be reused multiple times without rewriting them.

## Why Use Stored Procedures?

Stored procedures provide a structured and efficient way to manage database logic, promote code reusability, optimize performance, and enhance security and transaction management in database applications.

1. **Code Reusability**: You write the code once and reuse it whenever needed.
2. **Performance**: Stored procedures are precompiled, which can improve performance as the SQL statements don't need to be parsed and compiled every time they're executed.
3. **Security**: Stored procedures can control access to data, providing a layer of security.

1. **Modularity**: Stored procedures allow you to break down complex tasks into smaller, more manageable units. This makes it easier to maintain and update your database codebase.

2. **Code Reusability**: By storing SQL code in procedures, you can reuse it across multiple applications and queries without having to rewrite it each time. This promotes consistency and reduces the chance of errors.

3. **Performance Optimization**: Stored procedures are precompiled and stored on the database server, which can improve execution speed. Additionally, they reduce network traffic by executing multiple SQL statements on the server rather than sending individual queries from client applications.

4. **Security**: Stored procedures can help enhance security by controlling access to database objects. Instead of granting direct access to tables, you can grant permissions to execute specific procedures, allowing you to implement security policies and restrict data access more effectively.

5. **Transaction Management**: Stored procedures can be used to define transactions, ensuring that a series of SQL statements are executed as a single unit of work. This helps maintain data integrity and consistency, especially in complex operations involving multiple database changes.


## Syntax of a Simple Stored Procedure:

```sql
CREATE PROCEDURE procedure_name
AS
BEGIN
    -- SQL statements here
END
```

### Example:

Let's create a simple stored procedure that selects all records from a table called `Customers`:

```sql
CREATE PROCEDURE SelectAllCustomers
AS
BEGIN
    SELECT * FROM Customers;
END
```

## How to Execute a Stored Procedure?

Once a stored procedure is created, you can execute it using the `EXEC` command:

```sql
EXEC SelectAllCustomers;
```

## Parameters in Stored Procedures:

Stored procedures can accept parameters, which allow you to pass values into the procedure when it's executed.

```sql
CREATE PROCEDURE SelectCustomerByID
    @CustomerID INT
AS
BEGIN
    SELECT * FROM Customers WHERE CustomerID = @CustomerID;
END
```

In this example, `@CustomerID INT` declares a parameter named `@CustomerID` of type integer.

### Executing a Parameterized Stored Procedure:

```sql
EXEC SelectCustomerByID @CustomerID = 123;
```

### Output Parameters:

Stored procedures can also have output parameters, which can return values back to the caller.

```sql
CREATE PROCEDURE GetTotalOrders
    @CustomerID INT,
    @TotalOrders INT OUTPUT
AS
BEGIN
    SELECT @TotalOrders = COUNT(*) FROM Orders WHERE CustomerID = @CustomerID;
END
```

### Executing and Getting Output from the Stored Procedure:

```sql
DECLARE @TotalOrders INT;
EXEC GetTotalOrders @CustomerID = 123, @TotalOrders = @TotalOrders OUTPUT;
PRINT 'Total Orders: ' + CAST(@TotalOrders AS VARCHAR(10));
```

## Conclusion:

Stored procedures in T-SQL are powerful tools for organizing and reusing SQL code. They can accept parameters, return values, and enhance performance and security in database operations.

#### Help and Support

#### Did you find this document helpful? Leave a Star

[![GitHub stars](https://img.shields.io/github/stars/chigozie-i/Stored-Procedure.svg?style=social)](https://github.com/chigozie-i/Stored-Procedure/stargazers)

#### You may make a contribution to help us improve on our documentation by submitting a pull request.

