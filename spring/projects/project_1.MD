### Title: Automated Teller Machine (ATM) System
### Description:
The objective of this project is to develop a secure and efficient Automated Teller Machine (ATM) System using 
Java and Spring technologies. The system will simulate common ATM functionalities such as account access, balance 
inquiries, deposits, withdrawals, and transfers between accounts. The project should demonstrate the capability to 
handle user authentication, session management, and secure transaction processing.

#### Business Case:
With banking customers increasingly relying on electronic banking services for daily transactions, ATMs play a critical 
role in the banking ecosystem. A robust ATM system enhances customer satisfaction by providing quick and secure access 
to banking services outside of traditional banking hours. This project will allow students to understand and implement 
essential features of banking systems, emphasizing security, data integrity, and user interaction.

#### Suggested Architecture & Database Description:
- **Database Schema:**
    - **Users**: `id`, `account_number`, `pin`, `balance`
    - **Transactions**: `id`, `type`, `amount`, `date`, `account_number`
- **Backend Framework**: Spring Boot
- **Security**: Spring Security for authentication and securing transaction endpoints
- **Data Handling**: Spring Data JPA for transaction and user management
- **API**: RESTful services using Spring Web for transaction processing

### User Stories:
1. **As a bank customer, I want to:**
    - Insert my card (simulate by entering an account number and PIN).
    - View my current account balance.
    - Withdraw cash from my account.
    - Deposit money into my account.
    - Transfer funds to another account.
    - Log out securely from the ATM.
2. **As a bank administrator, I want to:**
    - Monitor and log all ATM transactions.
    - Manage ATM system issues such as replenishing cash or addressing transaction errors.
    - Update account information and PINs securely.
3. **As a system, I need to:**
    - Validate user credentials.
    - Handle sessions to ensure that customers’ operations are secure and personal information is protected.
    - Process transactions accurately and securely, updating account balances in real-time.
    - Provide timely feedback to the user about the status of their transactions.

### API Requirements:
- **Authentication and Session Management:**
    - `POST /auth/login`: Authenticate user and create a session.
    - `POST /auth/logout`: Terminate the session.
- **Account Operations:**
    - `GET /accounts/balance`: Check the current balance.
    - `POST /accounts/deposit`: Deposit an amount to the user's account.
    - `POST /accounts/withdraw`: Withdraw an amount from the user's account.
    - `POST /accounts/transfer`: Transfer amount to another account.
- **Admin Functions:**
    - `GET /admin/transactions`: View all transactions processed by the ATM.

### Acceptance Criteria:
1. **Spring Boot Application Setup:**
    - Properly configure and initialize a Spring Boot application using Gradle as the build tool. Include dependencies for Spring Boot, Spring Data JPA, Spring Security, and Spring Web.
2. **Database and Entity Configuration:**
    - Define JPA entities corresponding to the database schema for Users and Transactions.
    - Set up a PostgreSQL database and configure Spring Data JPA to interact with it.
    - Create repositories for each entity with necessary custom methods to support CRUD operations beyond the basic functionalities provided by Spring Data.
3. **User Authentication:**
    - Implement a secure login system that authenticates users by account number and PIN.
    - Ensure that all account transactions require user authentication.
    - Sessions must expire automatically after a period of inactivity or explicitly upon user logout.
4. **Transaction Processing:**
    - Develop endpoints to handle deposit, withdrawal, and balance inquiries. These must update and fetch account balances accurately.
    - Implement a transfer service that allows users to transfer funds between accounts securely and update both accounts' balances accordingly.
    - All transactional operations must handle errors gracefully and return meaningful error messages to the user.
5. **Admin Functions:**
    - Provide endpoints for administrators to view all transactions.
    - Implement functionality for administrators to intervene in case of transaction discrepancies or system errors.
6. **Testing and Documentation:**
    - Write integration tests for all critical functionalities such as login, withdrawal, deposit, and transfer.
    - Document the API using Swagger or Spring Rest Docs, including all request and response models, expected error messages, and status codes.

