### Simplified Database Assignment for Beginners: Medical System Context

#### Overview
This assignment introduces you to database design and SQL in the context of a medical system. You will design 
a database schema relevant to a medical clinic, create the database, populate it with data, and perform basic SQL 
operations.

#### Part A: Design a Simple Database Schema
1. **Objective**: Develop a basic schema for a Medical Clinic system.
2. **Schema Requirements**:
    - **Entities**: Patients, Doctors, Appointments, Medications, and Departments.
    - **Patients**: Attributes include PatientID (primary key), Name, DateOfBirth, and Gender.
    - **Doctors**: Attributes include DoctorID (primary key), Name, Specialty, and DepartmentID (foreign key).
    - **Appointments**: Attributes include AppointmentID (primary key), PatientID (foreign key), DoctorID (foreign key), AppointmentDate, and Issue.
    - **Medications**: Attributes include MedicationID (primary key), Name, and CommonUses.
    - **Departments**: Attributes include DepartmentID (primary key), DepartmentName, and Location.
    - Sketch a simple diagram showing these entities and their relationships (e.g., Patients to Appointments, Doctors to Departments).

#### Part B: Create and Populate the Database
1. **Objective**: Construct the database using your schema and add sample data.
2. **Steps**:
    - Use SQL commands to create the five tables: Patients, Doctors, Appointments, Medications, and Departments.
    - Add at least 15 entries to each table.


#### Part C: Advanced SQL Queries
1. **Objective**: Enhance your SQL proficiency by executing a variety of complex queries on your medical clinic database.
2. **Query Tasks**:

    - **Data Retrieval**:
        - **Find Appointments**: Write a query to find all appointments for a specific patient.
        - **Medication by Issue**: Write a query to list all medications commonly used for a specific issue mentioned in appointments.
        - **Doctor's Patient Count**: Write a query to display the total number of patients seen by each doctor.

    - **Data Update**:
        - **Reschedule Appointment**: Write a query to change the appointment date for a particular appointment.
        - **Update Patient Details**: Write a query to update a patient's information in case of change in their contact details or other relevant data.

    - **Join Operation**:
        - **Patient-Doctor Overview**: Write a query to show a list of patients along with their appointed doctor's name and specialty.
        - **Doctors and Patients by Department**: Write a query to display all doctors in a specific department along with their patients' names.
        - **Yearly Checkup Reminder**: Write a query to find any patients who have not had an appointment within the last year.

    - **Aggregate Data**:
        - **Average Daily Appointments**: Write a query to generate a report showing the average number of appointments per day.

#### Deliverables
- The same as previously listed, now including the enhanced SQL queries and their detailed explanations.

#### Assessment Criteria
- Accuracy and sophistication of SQL queries.
- Demonstrated understanding of advanced SQL operations, particularly join and aggregate functions.
- Clear and concise explanations of the purpose and expected results of each query.

#### Deliverables
- A diagram of your medical clinic database schema.
- SQL commands used for creating and populating tables.
- SQL queries for Part C with a brief explanation for each.

