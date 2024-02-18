### Task Description: Kindergarten Management System
This task involves developing a small Java application for managing children in a kindergarten. 
The system will be divided into two main parts: Part A focuses on implementing CRUD functionality, 
and Part B enhances the application with transaction management and error handling. This system aims to provide 
a basic framework for managing child records in a kindergarten setting, including their names, ages, and other 
relevant details.

---
#### Part A: CRUD Functionality
**Objective**: Implement basic CRUD operations to manage children's records in a kindergarten. Each child's record should include at least the child's ID, name, age, and a description of their favorite activities.
**Requirements**:
1. **Model Creation**: Define a `Child` class that includes properties for the child's ID, name, age, and favorite activities.
2. **Database Setup**: Use a relational database (e.g., MySQL, H2) to store child records. Create a table named `children` with appropriate columns for the `Child` class properties.
3. **DAO Layer**:
    - Create a `ChildDAO` interface that defines methods for CRUD operations.
    - Implement the `ChildDAO` interface in a class named `ChildDAOImpl` using JDBC to perform database operations.
4. **Service Layer**: Implement a `ChildService` class that uses `ChildDAO` to perform CRUD operations. This layer will handle business logic, if any (e.g., age validation).
5. **View Layer**: Develop a simple console-based UI (`ChildView`) that allows users to interact with the system. The UI should offer options to add a new child, view all children, update a child's details, and delete a child's record.

**Functionalities**:
- **Create**: Add new child records to the database.
- **Read**: List all children's records and view details of a specific child.
- **Update**: Modify the details of an existing child's record.
- **Delete**: Remove a child's record from the database.

---

#### Part B: Transaction Management and Error Handling
**Objective**: Enhance the kindergarten management system by incorporating transaction management and comprehensive error handling to ensure data integrity and robustness.
**Requirements**:
1. **Transaction Management**:
    - Modify the `ChildService` to manage transactions, especially for operations that involve multiple steps or updates. Ensure that operations either complete fully or roll back in case of any failure, maintaining data integrity.
    - Use `Connection.setAutoCommit(false)` and manage commit/rollback manually in the service layer.
2. **Error Handling**:
    - Implement try-catch blocks around database operations in the DAO layer to catch SQL exceptions.
    - Propagate exceptions to the service layer, where appropriate error messages should be logged/displayed, and decide whether to commit or roll back transactions.
    - In the view layer (`ChildView`), handle exceptions gracefully to inform the user of any errors without exposing system internals or crashing the application.

**Enhancements**:
- **Data Validation**: Before performing any CRUD operation, validate the input data (e.g., ensure age is within a reasonable range) in the service layer.
- **Logging**: Implement logging throughout the application to record key events, especially at the start and end of transactions, and when exceptions occur.
- **User Feedback**: Ensure the console UI provides clear feedback for successful operations as well as descriptive error messages when something goes wrong.

---

**Deliverables**:
- Source code for all parts of the application, including the model, DAO, service, and view layers.
- SQL scripts for creating and setting up the database schema.
- Documentation on how to set up and run the application, including any required dependencies.
