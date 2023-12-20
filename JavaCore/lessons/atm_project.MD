### ATM Simulator

#### Project Goals:
1. **Understanding Transactions and Security**: Mastery of handling financial transactions and data security fundamentals.
2. **Working with Interfaces and Polymorphism**: Application of interfaces and polymorphism to create a flexible and scalable architecture.
3. **Mastery of Java Basics**: Utilizing collections, exceptions, multithreading, and file systems.

#### Project Description:
Create a console application that simulates the operation of an ATM, allowing users to:
- Check balances, withdraw and deposit cash.
- Transfer money between accounts.
- Change PIN codes.
- Maintain a transaction log.
- Handle various user scenarios and errors.

#### Technical Requirements:
1. **Security**: User data encryption and secure storage of PIN codes.
2. **Transaction Handling**: Management of transactions and their sequencing.
3. **Multithreading**: Processing simultaneous requests in a multi-user environment.

#### Tasks:
1. Implementation of core account and user classes.
2. Creation of interfaces and their implementations for managing accounts, user interfaces, and transaction logging.
3. Implementation of security, including data encryption and secure PIN code storage.
4. Exception handling and creation of a reliable and robust system.
5. (Optional) Development of multithreaded processing to support concurrent operations.

### Structure
#### Overall Interaction Scheme:
1. **View**: Receives user input and delegates the execution of operations to the `service` layer.
2. **Service**: Contains all the application's business logic.
3. **DAO (Data Access Object)**: Interacts with the file system retrieval.

#### 1. View
- Responsibility: Interacting with the user, displaying menus, and obtaining user input.
- Classes:
   - `ATMConsoleView`: Manages the entire console-based user interface.
   - `UserInputHandler`: Processes user input and calls the corresponding methods in the `service` layer.

#### 2. Service
- Responsibility: Contains all the application's business logic.
- Classes:
   - `AccountService`: Manages account operations such as balance checking, deposits, cash withdrawals, and transfers.
   - `UserService`: Manages user information, including authentication and PIN code changes.
   - `TransactionService`: Handles and logs transactions.

#### 3. DAO (Data Access Object)
- Responsibility: Interacts with the data storage system (files, databases, etc.).
- Classes:
   - `AccountDAO`: Manages the storage and retrieval of account data.
   - `UserDAO`: Manages the storage and retrieval of user data.
   - `TransactionDAO`: Manages the storage and retrieval of transaction data.

#### Example Interactions:
- When a user wants to check their balance:
   - `ATMConsoleView` receives the request and calls `AccountService`.
   - `AccountService` requests account data through `AccountDAO` and returns the information to `ATMConsoleView`.
- During a transaction:
   - `ATMConsoleView` forwards the request to `TransactionService`.
   - `TransactionService` processes the transaction and uses `TransactionDAO` to store transaction details.

#### Interfaces and Their Implementations:
1. **Account Management Interface (`AccountManager`)**:
   - Methods: `checkBalance`, `deposit`, `withdraw`, `transferFunds`, `changePin`.
   - Implementations: `SimpleAccountManager` for basic functionality and `SecureAccountManager` with additional security measures.

2. **User Interaction Interface (`UserInterface`)**:
   - Methods: `displayMainMenu`, `handleUserActions`.
   - Implementations: `ConsoleUserInterface` and optionally, `GraphicalUserInterface` as an extension.

3. **Transaction Logging Interface (`TransactionLogger`)**:
   - Methods: `logTransaction`.
   - Implementations: `SimpleTransactionLogger` for file-based logging or `DatabaseTransactionLogger` for database interaction.

#### Additional Notes:
- **Security and Validation**: All necessary validation and security measures (e.g., PIN code verification) are performed in the `service` layer.
- **Separation of Responsibilities**: Each layer has well-defined responsibilities, making code management and testing easier.
