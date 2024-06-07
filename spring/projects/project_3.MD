# Advanced Financial Services Management System

## Description
The objective of this project is to develop an Advanced Financial Services Management System using Java and Spring 
technologies. The system will facilitate account management, transaction processing, investment portfolio 
management, customer service, and financial advisory.

## Business Case
Financial services are a critical part of the economy, and a well-designed financial services management system 
can greatly improve efficiency and accuracy. This project will allow developers to understand and implement 
essential features of such systems, emphasizing security, data integrity, and user interaction.

## Suggested Architecture & Database Description
The system is divided into two microservices, each with its own database:

1. **Account Management Service**: Handles user registration, login, account management, and transaction operations (deposit, withdrawal, transfer).
2. **Investment and Advisory Service**: Handles investment management, customer service requests, and advisory sessions.

The two services communicate with each other as needed, for example, to check a user's account balance before 
processing an investment.

### Communication example between services
- **Scenario**: A user wants to invest in a new financial product.
- **Steps**:
    1. The user logs in to the system and navigates to the investment section.
    2. The user selects the investment type and amount and submits the request.
    3. The Investment and Advisory Service receives the request and checks the user's account balance by calling the Account Management Service.
    4. The Account Management Service verifies the user's account balance and returns the result to the Investment and Advisory Service.
    5. If the account balance is sufficient, the Investment and Advisory Service processes the investment and updates the user's investment portfolio.
    6. The user receives a notification about the successful investment.
- **Scenario 2**: A user wants to book an advisory session with a financial advisor.
- **Steps**:
    1. The user logs in to the system and navigates to the advisory section.
    2. The user selects a financial advisor, date, and time for the session and submits the request.
    3. The Investment and Advisory Service receives the request and checks the financial advisor's availability.
    4. The Investment and Advisory Service updates the financial advisor's schedule and confirms the session.
    5. The user receives a notification about the confirmed advisory session.

### Account Management Service
- **Database Schema:**
    - **Users**: `id`, `name`, `email`, `password`
    - **Accounts**: `id`, `user_id`, `account_type`, `balance`
    - **Transactions**: `id`, `account_id`, `type`, `amount`, `date`
- **API Requirements:**
    - **Authentication and Session Management:**
        - `POST /auth/register`: Register a new user.
        - `POST /auth/login`: Authenticate user and create a session.
        - `POST /auth/logout`: Terminate the session.
    - **Account Operations:**
        - `POST /accounts`: Create a new account.
        - `GET /accounts`: List all user's accounts.
        - `PUT /accounts/{id}`: Update an existing account.
        - `DELETE /accounts/{id}`: Delete an account.
    - **Transaction Operations:**
        - `POST /transactions/deposit`: Deposit an amount to a specific account.
        - `POST /transactions/withdraw`: Withdraw an amount from a specific account.
        - `POST /transactions/transfer`: Transfer an amount from one account to another.
        - `GET /transactions`: View transaction history.

### Investment and Advisory Service
- **Database Schema:**
    - **Investments**: `id`, `user_id`, `investment_type`, `amount`, `date`
    - **CustomerServiceRequests**: `id`, `user_id`, `request_type`, `description`, `status`
    - **FinancialAdvisors**: `id`, `name`, `specialization`
    - **AdvisorySessions**: `id`, `user_id`, `advisor_id`, `date`, `time`, `status`
- **API Requirements:**
    - **Investment Operations:**
        - `POST /investments`: Create a new investment.
        - `GET /investments`: List all user's investments.
        - `PUT /investments/{id}`: Update an existing investment.
        - `DELETE /investments/{id}`: Delete an investment.
    - **Customer Service Operations:**
        - `POST /service-requests`: Create a new service request.
        - `GET /service-requests`: List all user's service requests.
        - `PUT /service-requests/{id}`: Update an existing service request.
    - **Advisory Session Operations:**
        - `POST /advisory-sessions`: Book a new advisory session.
        - `GET /advisory-sessions`: List all user's advisory sessions.
        - `PUT /advisory-sessions/{id}`: Reschedule an existing advisory session.
        - `DELETE /advisory-sessions/{id}`: Cancel an advisory session.

## User Stories
1. **As a user, I want to:**
    - Register and log in to the system.
    - Create, view, and manage my accounts.
    - Perform transactions (deposit, withdrawal, transfer) on my accounts.
    - View my transaction history.
    - Create, view, and manage my investments.
    - View my investment portfolio.
    - Create customer service requests and view their status.
    - Book advisory sessions with financial advisors.
    - Receive notifications about changes in my account, transactions, investments, service requests, and advisory sessions.
    - Have a user-friendly interface to interact with the system.
    - Have access to a help or FAQ section for guidance.
2. **As a financial advisor, I want to:**
    - Log in to the system.
    - View and manage my schedule.
    - View the list of advisory sessions booked with me.
    - Have a system to manage and update my availability.
    - Receive notifications about new, rescheduled, or cancelled advisory sessions.
3. **As a customer service representative, I want to:**
    - Log in to the system.
    - View and manage customer service requests.
    - Update the status of service requests.
    - Communicate with users through the system.
    - Receive notifications about new or updated service requests.
4. **As a system, I need to:**
    - Validate user credentials.
    - Handle sessions to ensure that users' operations are secure and personal information is protected.
    - Process transactions accurately and securely, updating account balances in real-time.
    - Process investment operations accurately and securely, updating investment portfolios in real-time.
    - Handle customer service requests and update their status in real-time.
    - Manage advisory sessions and update their status in real-time.
    - Provide timely feedback to the user about the status of their transactions, investments, service requests, and advisory sessions.
    - Send notifications to users, financial advisors, and customer service representatives about relevant updates.
    - Maintain a high level of performance and availability.
    - Handle errors gracefully and provide meaningful error messages to the users.

## Acceptance Criteria
1. **Spring Boot Application Setup:**
    - Properly configure and initialize a Spring Boot application using Gradle as the build tool. Include dependencies for Spring Boot, Spring Data JPA, Spring Security, and Spring Web.
2. **Database and Entity Configuration:**
    - Define JPA entities corresponding to the database schema for Users, Accounts, Transactions, Investments, CustomerServiceRequests, FinancialAdvisors, and AdvisorySessions.
    - Set up a PostgreSQL database and configure Spring Data JPA to interact with it.
    - Create repositories for each entity with necessary custom methods to support CRUD operations beyond the basic functionalities provided by Spring Data.
3. **User Authentication:**
    - Implement a secure login system that authenticates users by email and password.
    - Ensure that all operations require user authentication.
    - Sessions must expire automatically after a period of inactivity or explicitly upon user logout.
4. **Transaction, Investment, Service Request, and Advisory Session Processing:**
    - Develop endpoints to handle account management, transaction processing, investment management, service request management, and advisory session management. These must update and fetch data accurately.
    - All operations must handle errors gracefully and return meaningful error messages to the user.
5. **API Documentation:**
    - Set up Swagger for API documentation.
    - Document all API endpoints with Swagger, including all request and response models, expected error messages, and status codes.
6. **Testing:**
    - Write integration tests for all critical functionalities such as login, account management, transaction processing, investment management, service request management, and advisory session management.