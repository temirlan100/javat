Managing database transactions in Java with JDBC is a critical aspect of building reliable and consistent database applications. Transactions ensure that a series of SQL operations are executed atomically, meaning either all operations succeed or none do, thereby maintaining data integrity. Here's an overview of how to manage database transactions using JDBC.

### Understanding Transactions
A transaction is a sequence of one or more SQL statements that are executed as a single unit of work. The primary properties of transactions are often summarized by the acronym ACID, which stands for Atomicity, Consistency, Isolation, and Durability:

- **Atomicity**: Ensures that all operations within the work unit are completed successfully; otherwise, the transaction is aborted.
- **Consistency**: Ensures that the database properly changes states upon a successfully committed transaction.
- **Isolation**: Ensures that transactions are securely and independently processed at the same time without interference.
- **Durability**: Ensures that the result or effect of a committed transaction is permanently stored in the database.

### Enabling Transactions in JDBC
By default, a JDBC connection operates in auto-commit mode, meaning each SQL statement is treated as a transaction and is automatically committed right after it is executed. To manage transactions manually, you must disable auto-commit mode and control the transaction flow using commit and rollback operations. Here's how you can do it:

#### 1. Disable Auto-Commit Mode
Upon establishing a connection, disable the auto-commit mode:

```java
connection.setAutoCommit(false);
```

#### 2. Execute SQL Statements
Execute your SQL statements using `Statement` or `PreparedStatement` objects. These could be SELECT, INSERT, UPDATE, or DELETE operations.

```java
try {
    // Example of executing a SQL statement
    Statement statement = connection.createStatement();
    String updateSql = "UPDATE accounts SET balance = balance - 100 WHERE account_id = 1";
    statement.executeUpdate(updateSql);

    // You can execute more statements here as part of the transaction

    // If all operations are successful, commit the transaction
    connection.commit();
} catch (SQLException e) {
    // If there is any error, rollback the transaction
    try {
        if (connection != null) connection.rollback();
    } catch (SQLException ex) {
        ex.printStackTrace();
    }
    e.printStackTrace();
}
```

#### 3. Commit the Transaction
If all the SQL operations execute successfully, commit the transaction to make all changes permanent:

```java
connection.commit();
```

#### 4. Rollback on Error
If an error occurs during any of the SQL operations, rollback the transaction to undo all changes made since the transaction began:

```java
connection.rollback();
```

#### 5. Re-enable Auto-Commit Mode (Optional)
After completing the transaction, you can re-enable auto-commit mode if needed:

```java
connection.setAutoCommit(true);
```

### Handling Transactions
Proper error handling is crucial when managing transactions. Use try-catch blocks to catch `SQLExceptions`, and ensure that rollback is called in the catch block if any operation within the transaction fails. This prevents partial updates to the database that could lead to data inconsistency.

### Best Practices
- **Use `try-with-resources`** to ensure that resources like `Connection`, `Statement`, and `ResultSet` objects are closed properly.
- **Test transactions** thoroughly under various scenarios to ensure data integrity is maintained.
- **Be mindful of database locks** that might occur during transactions, as they can impact performance and concurrency. Optimize transaction logic to minimize lock contention.

### Example: Complete Transaction Management
Here's a complete example that demonstrates managing a simple transaction:

```java
String url = "jdbc:sqlite:path_to_your_database.db";
String user = "myuser";
String password = "mypassword";

try (Connection connection = DriverManager.getConnection(url, user, password)) {
    // Disable auto-commit mode
    connection.setAutoCommit(false);
    
    try {
        // Execute SQL operations
        // ...

        // Commit the transaction
        connection.commit();
    } catch (SQLException e) {
        // Attempt to rollback the transaction if something goes wrong
        try {
            connection.rollback();
        } catch (SQLException ex) {
            ex.printStackTrace();
        }
        e.printStackTrace();
    }
} catch (SQLException e) {
    e.printStackTrace();
}
```

This example demonstrates establishing a connection, disabling auto-commit, executing SQL operations, handling exceptions, committing the transaction, or rolling it back in case of errors, and finally ensuring that resources are properly closed.
