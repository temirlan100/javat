### Task Description
#### **Objective:**
Gain hands-on experience with JDBC by connecting to an SQLite database and performing basic SQL operations through a Java application.

#### **Prerequisites:**
- Ensure SQLite is installed on your system or accessible for your students.
- Include the SQLite JDBC driver in your project's classpath.

#### Part A: Establish a JDBC Connection to SQLite
**Task:**
Create a Java program that establishes a JDBC connection to an SQLite database named `students.db`. 
SQLite will create the database file if it does not exist, so there's no need to manually create the file.

**Instructions:**

1. **Set Up the JDBC Driver:** Make sure the SQLite JDBC driver is correctly set up in your project.
2. **Establish Connection:** Write code to establish a connection to the `students.db` database.
3. **Connection Feedback:** The program should indicate whether the connection was successfully established.

#### Part B: Execute Basic SQL Queries using JDBC
**Task:**
Extend your program to interact with a database table named `students`. 
The table should have columns for `id` (INTEGER), `name` (TEXT), and `grade` (INTEGER).
Perform basic SQL operations on this table.

**Instructions:**
1. **Table Setup:** Ensure your program checks for the existence of the `students` table and creates it if it doesn't exist.
2. **CRUD Operations:** Implement functionality to insert, select, update, and delete student records in the `students` table. Specifically, you should:
    - Insert at least three student records.
    - Select and display all student records.
    - Update the grade of at least one student.
    - Delete at least one student record.
3. **Transaction Management:** Apply transaction management techniques where appropriate, especially for operations that modify data (INSERT, UPDATE, DELETE). Ensure your program can roll back changes if an operation fails.

**Deliverables:**
Submit a Java program that demonstrates:
- Connecting to an SQLite database.
- Checking for and creating a necessary table if it doesn't exist.
- Performing INSERT, SELECT, UPDATE, and DELETE operations on the table.
- Managing transactions with commit and rollback mechanisms.

**Evaluation Criteria:**

Your submission will be evaluated based on:
- Code clarity and organization.
- Proper use of JDBC for database connection and operations.
- Effective implementation of transaction management.
- Handling of SQL exceptions and resource management (ensuring connections, statements, and result sets are closed properly).
