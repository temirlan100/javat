
# Module 3: Introduction to Spring Boot

## 3.1 Overview of Spring Boot

Spring Boot simplifies the development of Spring applications by providing defaults and auto-configuration options. It's designed to get you up and running quickly with minimal configuration.

### Key Features of Spring Boot
- **Convention over Configuration:** Defaults and assumptions to reduce setup complexity.
- **Embedded Servers:** Inbuilt servers like Tomcat for easy web development.
- **Auto-configuration:** Automatic setup based on included dependencies.
- **Standalone Applications:** Directly run applications without deploying to a web server.

## 3.2 Setting Up Spring Boot

### Getting Started with Spring Boot
Use [Spring Initializr](https://start.spring.io/) to create a new Spring Boot project with Java and Maven or Gradle. Import this project into your IDE to begin development.

#### Project Structure
- `src/main/java/`: Contains Java code.
- `src/main/resources/`: Holds resources (properties files, static contents).
- `pom.xml` or `build.gradle`: Manages project dependencies and configurations.

### Hello World Application
Create a basic application to display "Hello, World!" in the console.

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class ConsoleApplication {

    public static void main(String[] args) {
        SpringApplication.run(ConsoleApplication.class, args);
        System.out.println("Hello, World!");
    }
}
```

## 3.3 Spring Boot Core Concepts

### Auto-configuration
Spring Boot auto-configures the setup based on the dependencies you include, streamlining application development.

### Spring Boot Starters
Starters are pre-configured sets of dependencies that cater to specific development needs.

## 3.4 Practical Task: In-Memory Medical Record Management

Create a simple console application to manage medical records using in-memory data storage.

### Task Description
Develop a console-based Java application using Spring Boot, which allows adding, viewing, and deleting patient records stored in-memory.

### Implementation Steps

1. **Define a Patient Model:**
   Create a `Patient` class to represent patient records.

   ```java
   public class Patient {
       private String id;
       private String name;
       private int age;

       // Constructor, getters, and setters
   }
   ```

2. **Create a Patient Service:**
   Implement business logic for managing patient records.

   ```java
   import java.util.HashMap;
   import java.util.Map;

   public class PatientService {
       private final Map<String, Patient> patients = new HashMap<>();

       public void addPatient(Patient patient) {
           patients.put(patient.getId(), patient);
           System.out.println("Added patient: " + patient.getName());
       }

       public void listPatients() {
           patients.values().forEach(patient -> 
               System.out.println(patient.getId() + " - " + patient.getName()));
       }

       // Methods for updating and deleting patients
   }
   ```

3. **Create Application Runner:**
   Use `CommandLineRunner` to interact with the console.

   ```java
   import org.springframework.boot.CommandLineRunner;
   import org.springframework.stereotype.Component;

   @Component
   public class AppRunner implements CommandLineRunner {

       private final PatientService patientService = new PatientService();

       @Override
       public void run(String... args) {
           // Add some patients
           patientService.addPatient(new Patient("1", "John Doe", 30));
           patientService.addPatient(new Patient("2", "Jane Roe", 25));

           // List all patients
           patientService.listPatients();
       }
   }
   ```

### Conclusion
This task helps understand basic Spring Boot concepts and Java programming by developing a simple in-memory application for medical record management.

### Recommended Resources
- [spring-boot-docs](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#getting-started)
- [What is Java Spring Boot?](https://www.ibm.com/topics/java-spring-boot)

### Practical Exercise: In-Memory Patient Management System
#### Objective:
Develop a console-based Java application using Spring Boot that manages patient records in-memory. The application should allow adding, updating, viewing, and deleting patient information.

#### Tools and Technologies:
- Java
- Spring Boot
- Maven or Gradle

#### Requirements:
1. **Patient Model:**
   Create a `Patient` class with the following properties:
    - `id` (String)
    - `name` (String)
    - `age` (int)
    - `condition` (String) – describes the patient's medical condition

2. **Patient Service:**
   Implement a service class (`PatientService`) that manages the in-memory storage and manipulation of patient records. It should support the following operations:
    - Add a new patient
    - Update an existing patient's information
    - View a patient's details
    - Delete a patient record
    - List all patients

3. **Console Interface:**
   Use `CommandLineRunner` to interact with the user through the console. Provide a simple menu-driven interface to perform the following actions:
    - Add a new patient record
    - Update an existing patient record
    - View a patient's details
    - Delete a patient record
    - List all patients
    - Exit the program

#### Implementation Steps:
1. **Set up a Spring Boot Project:**
    - Use Spring Initializr to generate a new Spring Boot project.
    - Choose appropriate dependencies (Spring Boot Starter).
2. **Implement the Patient Model:**
    - Create the `Patient` class with the specified properties and methods (getters and setters).
3. **Develop the Patient Service:**
    - Implement the `PatientService` class with methods to add, update, view, delete, and list patients.
    - Use a `HashMap` or similar data structure to store patient records in memory.
4. **Create the Console Interface:**
    - Implement `CommandLineRunner` in a class, providing a menu and handling user input to interact with the `PatientService`.
5. **Testing:**
    - Run the application and test each menu option to ensure the application correctly manages the patient records in-memory.

#### Example Code Snippets:
- **Patient Class:**
    ```java
    public class Patient {
        private String id;
        private String name;
        private int age;
        private String condition;

        // Constructor, getters, and setters
    }
    ```

- **PatientService Class:**
    ```java
    import java.util.HashMap;
    import java.util.Map;

    public class PatientService {
        private final Map<String, Patient> patients = new HashMap<>();

        public void addPatient(Patient patient) {
            patients.put(patient.getId(), patient);
        }

        // Implement other methods
    }
    ```

- **Console Interface with CommandLineRunner:**
    ```java
    import org.springframework.boot.CommandLineRunner;
    import org.springframework.stereotype.Component;

    @Component
    public class ConsoleApplication implements CommandLineRunner {

        private final PatientService patientService = new PatientService();

        @Override
        public void run(String... args) throws Exception {
            // Implement console interaction logic
        }
    }
    ```

