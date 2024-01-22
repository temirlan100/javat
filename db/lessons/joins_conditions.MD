### Advanced SQL Concepts: Joins, Conditions, Subqueries, Views, and Indexes
#### 1. Joins
Joins are used to combine rows from two or more tables.
**Example**:
Tables: `Patients`, `Doctors`, and `Appointments`.

- To list all appointments along with patient and doctor names:

```sql
SELECT Patients.PatientName, Doctors.DoctorName, Appointments.Date
FROM Appointments
JOIN Patients ON Appointments.PatientID = Patients.PatientID
JOIN Doctors ON Appointments.DoctorID = Doctors.DoctorID;
```

### 2. Conditions (WHERE, HAVING)

These clauses are used in SQL to filter records based on specific conditions.

#### WHERE Clause
The `WHERE` clause is used to filter records before any grouping, making it useful for setting conditions on individual rows.

**Examples**:
1. **Find Appointments for a Specific Doctor**:
    - If you want to get a list of all appointments for 'Dr. Smith':
      ```sql
      SELECT *
      FROM Appointments
      WHERE DoctorID = (SELECT DoctorID FROM Doctors WHERE DoctorName = 'Dr. Smith');
      ```

2. **Find Patients with Appointments on a Specific Date**:
    - To retrieve all patients who have an appointment on '2023-01-21':
      ```sql
      SELECT Patients.PatientName
      FROM Patients
      JOIN Appointments ON Patients.PatientID = Appointments.PatientID
      WHERE Appointments.Date = '2023-01-21';
      ```

3. **Find Doctors who have Appointments in a Specific Department (e.g., 'Cardiology')**:
    - Assuming there's a `Department` column in `Doctors` table:
      ```sql
      SELECT DoctorName
      FROM Doctors
      WHERE Department = 'Cardiology';
      ```

#### HAVING Clause
The `HAVING` clause is used to filter groups of rows after `GROUP BY` has been applied. It's especially useful for working with aggregate functions like `COUNT`, `SUM`, `AVG`, etc.
**Examples**:
1. **Find Doctors with More Than a Certain Number of Appointments**:
    - If you want to find doctors who have more than 10 appointments:
      ```sql
      SELECT Doctors.DoctorName, COUNT(Appointments.AppointmentID) AS NumberOfAppointments
      FROM Doctors
      JOIN Appointments ON Doctors.DoctorID = Appointments.DoctorID
      GROUP BY Doctors.DoctorName
      HAVING COUNT(Appointments.AppointmentID) > 10;
      ```

2. **Find Departments with Average Appointment Duration Exceeding a Certain Threshold**:
    - Assuming there's a `Duration` column in `Appointments` table:
      ```sql
      SELECT Doctors.Department, AVG(Appointments.Duration) AS AverageDuration
      FROM Doctors
      JOIN Appointments ON Doctors.DoctorID = Appointments.DoctorID
      GROUP BY Doctors.Department
      HAVING AVG(Appointments.Duration) > 30; -- for example, if the duration is in minutes
      ```

3. **Find Days with a Number of Appointments Above Average**:
    - To find dates with an above-average number of appointments:
      ```sql
      SELECT Date, COUNT(AppointmentID) AS NumberOfAppointments
      FROM Appointments
      GROUP BY Date
      HAVING COUNT(AppointmentID) > (SELECT AVG(NumberOfAppointments) FROM (SELECT Date, COUNT(AppointmentID) AS NumberOfAppointments FROM Appointments GROUP BY Date) AS AverageAppointments);
      ```
These examples should provide a deeper understanding of how to use `WHERE` and `HAVING` clauses effectively in SQL, especially in scenarios related to the medical field. They are crucial for querying databases efficiently and are widely used in real-world applications.

#### 3. Subqueries
A subquery is a nested query.

**Example**:
- To find doctors who have appointments with a patient named 'John Doe':

```sql
SELECT DoctorName
FROM Doctors
WHERE DoctorID IN (SELECT DoctorID FROM Appointments WHERE PatientID = (SELECT PatientID FROM Patients WHERE PatientName = 'John Doe'));
```

#### 4. Views
A view is a virtual table.
**Example**:
- Creating a view for appointment details:

```sql
CREATE VIEW AppointmentDetails AS
SELECT Patients.PatientName, Doctors.DoctorName, Appointments.Date
FROM Appointments
JOIN Patients ON Appointments.PatientID = Patients.PatientID
JOIN Doctors ON Appointments.DoctorID = Doctors.DoctorID;
```

Then query the view:

```sql
SELECT * FROM AppointmentDetails;
```

#### 5. Indexes
Indexes improve the speed of data retrieval.

**Example**:
- Creating an index on the `PatientID` in the `Appointments` table:

```sql
CREATE INDEX idx_patient
ON Appointments (PatientID);
```

### Integrating with Java and SQLite
To use these SQL concepts in Java with SQLite, here’s a basic structure:

```java
import java.sql.*;

public class MedicalDatabaseExample {
    public static void main(String[] args) {
        try {
            // Establishing connection to SQLite database
            Connection con = DriverManager.getConnection("jdbc:sqlite:path_to_your_database.db");

            // Creating a statement
            Statement stmt = con.createStatement();

            // Executing a query with WHERE condition
            ResultSet rs = stmt.executeQuery("SELECT * FROM AppointmentDetails WHERE DoctorName = 'Dr. Smith'");

            // Iterating through the result set
            while (rs.next()) {
                System.out.println(rs.getString("PatientName") + " - " + rs.getString("DoctorName") + " - " + rs.getString("Date"));
            }

            // Closing connections
            rs.close();
            stmt.close();
            con.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```
This example retrieves data from the `AppointmentDetails` view for appointments with 'Dr. Smith'.


### Recommended Resources
- [JOINS](https://www.w3schools.com/sql/sql_join.asp)
- [WHERE Clause](https://www.w3schools.com/sql/sql_where.asp)
- [VIEWS](https://www.w3schools.com/sql/sql_view.asp)
- [CREATE INDEX](https://www.w3schools.com/sql/sql_create_index.asp)
