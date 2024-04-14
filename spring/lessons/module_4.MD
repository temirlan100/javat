# Module 4: Building RESTful Web Services with Spring Boot

## Overview
In this module, we explore how to build RESTful web services using Spring Boot. Spring Boot simplifies the development of production-ready applications with its convention-over-configuration approach and its suite of out-of-the-box functionalities for web services. We will cover the fundamental concepts of REST, how to set up a Spring Boot project, and how to develop RESTful endpoints with detailed examples.

### Key Concepts
- **REST Architecture**: REST (Representational State Transfer) is an architectural style that defines a set of constraints for creating web services. RESTful services are stateless and separate the concerns of client and server.
- **Spring Boot**: A framework that helps developers create stand-alone, production-grade Spring-based applications easily.
- **Spring Web MVC**: A framework based on the Model-View-Controller design pattern that helps in building flexible and loosely coupled web applications.

## Setting Up Spring Boot
Before diving into the creation of RESTful services, it's essential to set up a Spring Boot environment:

1. **Project Initialization**: Use [Spring Initializr](https://start.spring.io/) to generate a project by selecting dependencies like 'Spring Web', 'Spring Data JPA', and others as required.
2. **Maven or Gradle**: Choose a build tool. Maven and Gradle are both supported by Spring Boot and help in managing project dependencies and building configurations.
3. **IDE Setup**: Import the generated project into an Integrated Development Environment (IDE) like IntelliJ IDEA or Eclipse.

### Sample `build.gradle` for Gradle
Here's how can set up your `build.gradle` file for a Spring Boot project using Gradle:

```groovy
plugins {
    id 'org.springframework.boot' version '3.2.2'
    id 'io.spring.dependency-management' version '1.0.15.RELEASE'
    id 'java'
}

group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '17' // Use your required Java version

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    // Other dependencies as needed
}

test {
    useJUnitPlatform()
}
```

This `build.gradle` file accomplishes the same setup as the `pom.xml` example but using Gradle:
- **Plugins**: The `org.springframework.boot` plugin simplifies managing Spring Boot applications with Gradle. The `io.spring.dependency-management` plugin brings Maven-like dependency management capabilities to Gradle.
- **Java Version**: Set the `sourceCompatibility` to match your development environment's JDK version.
- **Repositories**: It's configured to use Maven Central, where it can fetch Spring Boot and other dependencies.
- **Dependencies**: It includes the Spring Boot Web Starter, which provides all necessary dependencies to build a web application.


## Developing RESTful Services
### Creating a Simple RESTful Controller
Here’s how you can create a basic controller in Spring Boot to handle HTTP requests:

```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, World!";
    }
}
```

This controller is a simple Java class annotated with `@RestController`, which makes it a web controller capable of handling HTTP requests. The `@GetMapping` annotation defines that the `sayHello` method responds to HTTP GET requests directed at the `/hello` URL.

### Handling CRUD Operations
To handle CRUD operations, define endpoints in the controller that correspond to HTTP methods:
- **Create**: HTTP POST
- **Read**: HTTP GET
- **Update**: HTTP PUT/PATCH
- **Delete**: HTTP DELETE

#### Example of a CRUD Controller
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/users")
public class UserController {
    
    @Autowired
    private UserRepository userRepository;

    @GetMapping("/{id}")
    public User getUser(@PathVariable Long id) {
        return userRepository.findById(id).orElseThrow(() -> new UserNotFoundException(id));
    }

    @PostMapping("/")
    public User createUser(@RequestBody User newUser) {
        return userRepository.save(newUser);
    }

    @PutMapping("/{id}")
    public User updateUser(@RequestBody User newUser, @PathVariable Long id) {
        return userRepository.findById(id)
            .map(user -> {
                user.setName(newUser.getName());
                user.setEmail(newUser.getEmail());
                return userRepository.save(user);
            })
            .orElseGet(() -> {
                newUser.setId(id);
                return userRepository.save(newUser);
            });
    }

    @DeleteMapping("/{id}")
    public void deleteUser(@PathVariable Long id) {
        userRepository.deleteById(id);
    }
}
```
In this example, the `UserController` manages user data with basic CRUD operations. It uses `UserRepository` (not shown) to interact with the database.

### Practical Exercise: In-Memory Book Management System
This Spring Boot application will include a `Book` class, a controller to handle HTTP requests, and a simple in-memory repository to simulate database operations.

#### 1. Setup the Book Model
First, let's define the `Book` class which will act as the data model.
```java
package com.example.restservice.models;

public class Book {
    private Long id;
    private String title;
    private String author;

    public Book() {
    }

    public Book(Long id, String title, String author) {
        this.id = id;
        this.title = title;
        this.author = author;
    }

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }
}
```

#### 2. Implement a Simple Repository
Here's a basic in-memory repository using a `HashMap`.

```java
package com.example.restservice.repository;

import com.example.restservice.models.Book;
import java.util.*;
import java.util.concurrent.atomic.AtomicLong;

public class BookRepository {
    private static final Map<Long, Book> books = new HashMap<>();
    private static final AtomicLong counter = new AtomicLong();

    static {
        // pre-load some books
        save(new Book(null, "1984", "George Orwell"));
        save(new Book(null, "To Kill a Mockingbird", "Harper Lee"));
    }

    public static List<Book> findAll() {
        return new ArrayList<>(books.values());
    }

    public static Book findById(Long id) {
        return books.get(id);
    }

    public static Book save(Book book) {
        if (book.getId() == null) {
            book.setId(counter.incrementAndGet());
        }
        books.put(book.getId(), book);
        return book;
    }

    public static void deleteById(Long id) {
        books.remove(id);
    }
}
```

#### 3. Create the Book Controller
The controller will handle all HTTP methods for interacting with books.

```java
package com.example.restservice.controllers;

import com.example.restservice.models.Book;
import com.example.restservice.repository.BookRepository;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/books")
public class BookController {

    @GetMapping("/")
    public List<Book> getAllBooks() {
        return BookRepository.findAll();
    }

    @GetMapping("/{id}")
    public Book getBookById(@PathVariable Long id) {
        return BookRepository.findById(id);
    }

    @PostMapping("/")
    public Book addBook(@RequestBody Book book) {
        return BookRepository.save(book);
    }

    @PutMapping("/{id}")
    public Book updateBook(@PathVariable Long id, @RequestBody Book book) {
        book.setId(id);
        return BookRepository.save(book);
    }

    @PatchMapping("/{id}")
    public Book updateBookPartial(@PathVariable Long id, @RequestBody Map<String, String> updates) {
        Book book = BookRepository.findById(id);
        if (updates.containsKey("title")) {
            book.setTitle(updates.get("title"));
        }
        if (updates.containsKey("author")) {
            book.setAuthor(updates.get("author"));
        }
        return BookRepository.save(book);
    }

    @DeleteMapping("/{id}")
    public void deleteBook(@PathVariable Long id) {
        BookRepository.deleteById(id);
    }
}
```

### Explanation of the HTTP Methods in the Controller
- **GET `/books/`**: Fetches a list of all books.
- **GET `/books/{id}`**: Retrieves a single book by its ID.
- **POST `/books/`**: Adds a new book to the collection.
- **PUT `/books/{id}`**: Updates a book completely, replacing its title and author.
- **PATCH `/books/{id}`**: Partially updates a book; this could be just the title or the author.
- **DELETE `/books/{id}`**: Removes the book from the collection by its ID.

### 1. **Create a BookService Interface**
Start by defining an interface for your service layer. This interface will declare methods that your controller will use.

```java
package com.example.restservice.services;

import com.example.restservice.models.Book;
import java.util.List;

public interface BookService {
    List<Book> findAll();
    Book findById(Long id);
    Book save(Book book);
    void deleteById(Long id);
    List<Book> findByAuthor(String author);
}
```

### 2. **Implement the BookService Interface**
Now, implement the interface in a concrete class where you will add your business logic.

```java
package com.example.restservice.services;

import com.example.restservice.models.Book;
import com.example.restservice.repository.BookRepository;
import org.springframework.stereotype.Service;

import java.util.List;
import java.util.stream.Collectors;

@Service
public class BookServiceImpl implements BookService {

    @Override
    public List<Book> findAll() {
        return BookRepository.findAll();
    }

    @Override
    public Book findById(Long id) {
        return BookRepository.findById(id);
    }

    @Override
    public Book save(Book book) {
        return BookRepository.save(book);
    }

    @Override
    public void deleteById(Long id) {
        BookRepository.deleteById(id);
    }

    @Override
    public List<Book> findByAuthor(String author) {
        // Business logic for filtering books by author
        List<Book> allBooks = BookRepository.findAll();
        return allBooks.stream()
                .filter(book -> book.getAuthor().equalsIgnoreCase(author))
                .collect(Collectors.toList());
    }
}
```

### 3. **Update the Controller to Use the Service Layer**
Modify the controller to use the `BookService` for handling business logic, rather than directly interacting with the repository.

```java
package com.example.restservice.controllers;

import com.example.restservice.models.Book;
import com.example.restservice.services.BookService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/books")
public class BookController {

    @Autowired
    private BookService bookService;

    @GetMapping("/")
    public List<Book> getAllBooks() {
        return bookService.findAll();
    }

    @GetMapping("/{id}")
    public Book getBookById(@PathVariable Long id) {
        return bookService.findById(id);
    }

    @GetMapping("/author/{author}")
    public List<Book> getBooksByAuthor(@PathVariable String author) {
        return bookService.findByAuthor(author);
    }

    @PostMapping("/")
    public Book addBook(@RequestBody Book book) {
        return bookService.save(book);
    }

    @PutMapping("/{id}")
    public Book updateBook(@PathVariable Long id, @RequestBody Book book) {
        book.setId(id);
        return bookService.save(book);
    }

    @PatchMapping("/{id}")
    public Book updateBookPartial(@PathVariable Long id, @RequestBody Book book) {
        return bookService.save(book);
    }

    @DeleteMapping("/{id}")
    public void deleteBook(@PathVariable Long id) {
        bookService.deleteById(id);
    }
}
```

### Business Logic Addition: Filtering Books by Author
In the service layer (`BookServiceImpl`), the method `findByAuthor` adds simple business logic to filter books based on the author name. This functionality demonstrates how you can encapsulate business rules within the service layer, keeping them separate from the persistence logic (repository) and the web layer (controller), adhering to the principles of clean architecture. This approach ensures that your application is easier to maintain and extend, particularly as business requirements evolve.


### Recommended Resources
- [Building an Application with Spring Boot](https://spring.io/guides/gs/spring-boot)
- [What is a REST API?](https://www.ibm.com/topics/rest-apis)
- [What is RESTful API?](https://aws.amazon.com/what-is/restful-api/)
- [What Is a REST API? Examples, Uses, and Challenges](https://blog.postman.com/rest-api-examples)