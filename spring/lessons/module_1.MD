### Module 1: Introduction to Spring Framework

#### Theoretical Part

**1. Introduction to Spring Framework**
Spring Framework is an essential platform for developing Java-based applications, offering comprehensive infrastructure support. It facilitates building, deploying, and maintaining complex applications with ease.

**2. Core Concepts of Spring**
- **Inversion of Control (IoC):** Central to Spring, IoC shifts the responsibility of managing components from the application code to the framework, promoting loose coupling and flexibility.
- **Dependency Injection (DI):** A form of IoC, DI allows Spring to inject dependencies into components, simplifying management and configuration.

**3. Architecture of Spring Framework**
Spring’s modular architecture includes:
- **Core Container:** Foundation of the framework, providing IoC and DI features.
- **AOP and Instrumentation:** Supports aspect-oriented programming including cross-cutting concerns.
- **Data Access/Integration:** Facilitates interaction with databases and transaction management.
- **Web and Web MVC:** Forms the basis for web applications in Spring, including RESTful services.

**4. Advantages of Using Spring**
Benefits include:
- Reduced boilerplate code
- Improved application scalability and maintainability
- Robust abstraction layers allowing for easy integration with other frameworks.

#### Practical Exercise

**Setting Up IntelliJ IDEA**
- Download and install IntelliJ IDEA if not already installed.
- Ensure you have the Java Development Kit (JDK) installed, version 8 or above.

**Creating a Spring Boot Application**
- Open IntelliJ IDEA and select "New Project".
- Choose "Spring Initializr" from the options on the left and set up the project SDK (Java version).
- Fill in the project metadata (Group, Artifact, Name) and select "Spring Web" as the dependency.
- Click "Finish" to generate the project.

**Hello, Spring! Application**
Navigate to `src/main/java` in your project, find the main application class (named as per your project, e.g., `HelloSpringApplication`), and enter the following code:

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class HelloSpringApplication {
    public static void main(String[] args) {
        SpringApplication.run(HelloSpringApplication.class, args);
    }
}
```

**Exploring Beans and ApplicationContext**
Define a `GreetingService` class in the `service` package and annotate it with `@Service`:

```java
import org.springframework.stereotype.Service;

@Service
public class GreetingService {
    public String getGreeting() {
        return "Welcome to Spring!";
    }
}
```

Inject this service into a component that uses it, such as a command-line runner:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

@Component
public class AppRunner implements CommandLineRunner {
    @Autowired
    private GreetingService greetingService;

    @Override
    public void run(String... args) {
        System.out.println(greetingService.getGreeting());
    }
}
```

**Configuration and Properties**
Utilize `src/main/resources/application.properties` to manage application settings. For example, to change the server port:

```
server.port=8082
```

#### Conclusion and Next Steps
This module introduced you to the Spring Framework, highlighting its core concepts, architecture, and benefits. The practical exercise aimed to give a hands-on experience in setting up a basic Spring Boot application.

#### Assignment
Enhance the `GreetingService` to read a message from `application.properties` and display that message when the application runs. This will introduce you to property management in Spring applications.

### Recommended Resources
- [Spring Modules](https://www.javatpoint.com/spring-modules)
- [Spring Example](https://www.javatpoint.com/steps-to-create-spring-application)
- [IoC Container](https://www.javatpoint.com/ioc-container)
- [Dependency Injection](https://www.javatpoint.com/dependency-injection-in-spring)

### Practical Exercise: In-Memory Task Manager Console Application
**Objective:**  
Develop a console-based task manager application using Spring Boot, which allows adding, retrieving, and deleting tasks stored in memory.
**Requirements:**
- IntelliJ IDEA with Spring Boot setup.
- Understanding of basic Spring concepts like dependency injection and beans.
**Task Overview:**  
Create an application that manages tasks in memory (using a `List` or `Map`) and allows interaction through the console (standard input/output).

#### Step 1: Set Up the Project
- Start a new Spring Boot project in IntelliJ IDEA, using Spring Initializr.
- Choose Maven as the build tool and Java as the language.

#### Step 2: Define the Task Model
- In the `model` package, create a `Task` class with fields like `id`, `name`, and `completed`.
```java
package com.yourdomain.project.model;

public class Task {
    private Long id;
    private String name;
    private boolean completed;

    // Constructors, getters, and setters
}
```

#### Step 3: Create the Task Service
- In the `service` package, create a `TaskService` class to manage the in-memory list of tasks.
- Implement methods to add, retrieve, and delete tasks.
```java
package com.yourdomain.project.service;

import com.yourdomain.project.model.Task;
import org.springframework.stereotype.Service;

import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.atomic.AtomicLong;

@Service
public class TaskService {
    private final List<Task> tasks = new ArrayList<>();
    private final AtomicLong counter = new AtomicLong();

    public Task addTask(String name) {
        Task task = new Task();
        task.setId(counter.incrementAndGet());
        task.setName(name);
        task.setCompleted(false);
        tasks.add(task);
        return task;
    }

    public List<Task> getAllTasks() {
        return tasks;
    }

    public void deleteTask(Long taskId) {
        tasks.removeIf(task -> task.getId().equals(taskId));
    }
}
```

#### Step 4: Create a Command-Line Runner
- Implement a command-line runner in your main application class to interact with the `TaskService`.
```java
import com.yourdomain.project.service.TaskService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

import java.util.Scanner;

@Component
public class TaskManagerRunner implements CommandLineRunner {
    @Autowired
    private TaskService taskService;

    @Override
    public void run(String... args) throws Exception {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("Enter 1 to add a task, 2 to view tasks, 3 to delete a task, 4 to exit");
            int input = scanner.nextInt();
            switch (input) {
                case 1:
                    System.out.println("Enter task name:");
                    scanner.nextLine(); // Consume newline left-over
                    String name = scanner.nextLine();
                    taskService.addTask(name);
                    break;
                case 2:
                    System.out.println("Tasks:");
                    taskService.getAllTasks().forEach(task -> System.out.println(task.getId() + ": " + task.getName()));
                    break;
                case 3:
                    System.out.println("Enter task ID to delete:");
                    Long taskId = scanner.nextLong();
                    taskService.deleteTask(taskId);
                    break;
                case 4:
                    System.out.println("Exiting...");
                    return;
                default:
                    System.out.println("Invalid input, try again.");
                    break;
            }
        }
    }
}
```
#### Step 5: Run and Test Your Application
- Execute the application and interact with it through the console to manage tasks.


