### Basics of Database Design
1. **Understanding the Purpose of the Database:**
    - Determine what information needs to be stored and how it will be used.
    - Example: A student database might need to store details like student ID, name, course enrollments, and grades.
2. **Identifying Entities and Relationships:**
    - Entities represent objects or concepts (like 'Student', 'Course').
    - Relationships show how entities interact (e.g., a student 'enrolls in' a course).
    - Example: Entity 'Student' has a relationship with entity 'Course' through 'Enrollment'.
3. **Designing a Schema:**
    - Create a diagram that outlines entities, their attributes, and relationships.
    - Example: A schema diagram showing 'Students', 'Courses', and 'Enrollments' as entities with their attributes.

### Basics of Normalization
Normalization is the process of organizing a database to reduce redundancy and improve data integrity.
1. **First Normal Form (1NF):**
    - Ensure each table column contains atomic, indivisible values.
    - Example: Splitting a 'FullName' column into 'FirstName' and 'LastName'.
2. **Second Normal Form (2 NF):**
- Meet all requirements of 1NF.
- Ensure that all non-key attributes are fully functional dependent on the primary key.
- Example: If a table contains student data and course data, separate it into two tables, one for each entity.
3. **Third Normal Form (3NF):**
    - Meet all requirements of 2NF.
    - Ensure that all the attributes are only dependent on the primary key, not on other non-key attributes.
    - Example: If a table contains 'StudentID', 'CourseID', and 'CourseInstructor', where 'CourseInstructor' depends on 'CourseID' and not 'StudentID', move 'CourseInstructor' to the course table.
4. **Boyce-Codd Normal Form (BCNF):**
    - A stronger version of 3NF.
    - Ensures that no non-trivial functional dependencies violate the primary key.
    - Example: Address any remaining anomalies not covered by 3NF.

### Case example
### 1. First Normal Form (1NF)
**Problem:** A table containing student information where the `Courses` column contains multiple values.

```sql
CREATE TABLE Students (
    StudentID int,
    StudentName varchar(100),
    Courses varchar(100)  -- Courses column has multiple values (e.g., 'Math, Science')
);
```

**Solution:** Modify the table so that each column has atomic values.

```sql
CREATE TABLE Students (
    StudentID int,
    StudentName varchar(100)
);

CREATE TABLE Enrollments (
    StudentID int,
    CourseName varchar(100)
);
```

### 2. Second Normal Form (2NF)
**Problem:** A table not in 2NF, where non-key attributes don't fully depend on the primary key.

```sql
CREATE TABLE Enrollments (
    StudentID int,
    CourseID int,
    EnrollmentDate date,
    InstructorName varchar(100)  -- Depends only on CourseID, not on StudentID
);
```

**Solution:** Separate the data into two tables to ensure all non-key attributes are fully dependent on the primary key.

```sql
CREATE TABLE Enrollments (
    StudentID int,
    CourseID int,
    EnrollmentDate date
);

CREATE TABLE Courses (
    CourseID int,
    InstructorName varchar(100)
);
```

### 3. Third Normal Form (3NF)
**Problem:** A table not in 3NF, containing transitive dependencies (non-key attribute depending on another non-key attribute).

```sql
CREATE TABLE Courses (
    CourseID int,
    InstructorID int,
    InstructorOffice varchar(100)  -- InstructorOffice depends on InstructorID, not CourseID
);
```

**Solution:** Remove transitive dependencies by creating separate tables.

```sql
CREATE TABLE Courses (
    CourseID int,
    InstructorID int
);

CREATE TABLE Instructors (
    InstructorID int,
    InstructorOffice varchar(100)
);
```

### 4. Boyce-Codd Normal Form (BCNF)
**Problem:** A table where a non-trivial functional dependency violates the primary key.

```sql
CREATE TABLE CourseAssignments (
    CourseID int,
    InstructorID int,
    RoomNumber varchar(50),
    PRIMARY KEY (CourseID, InstructorID)
    -- RoomNumber is functionally dependent on Course

ID, which is part of the composite primary key but not on the entire key.
);

**Solution:** Reorganize the table to ensure that every determinant is a candidate key.

```sql
CREATE TABLE CourseAssignments (
    CourseID int,
    RoomNumber varchar(50),
    PRIMARY KEY (CourseID)
);

CREATE TABLE Instructors (
    InstructorID int,
    CourseID int,
    PRIMARY KEY (InstructorID, CourseID)
);
```

In this BCNF example, the original `CourseAssignments` table had a situation where `RoomNumber` was dependent on 
`CourseID` but not on the entire composite primary key (`CourseID`, `InstructorID`). By splitting the table, 
each attribute in both tables is now functionally dependent only on the entire primary key of its respective table, 
which satisfies the requirements of BCNF.

### Recommended Resources
- [Description of the database normalization basics](https://learn.microsoft.com/en-us/office/troubleshoot/access/database-normalization-description)
- [What is Normalization in DBMS (SQL)? 1NF, 2NF, 3NF Example](https://www.guru99.com/database-normalization.html)
- [database normalization](https://www.techtarget.com/searchdatamanagement/definition/normalization)
- [Database Normalization – Normal Forms 1nf 2nf 3nf Table Examples](https://www.freecodecamp.org/news/database-normalization-1nf-2nf-3nf-table-examples)

