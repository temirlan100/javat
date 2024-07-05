### Module: Data Access with Spring Data

#### Overview
This module will introduce you to Spring Data, a powerful framework that simplifies data handling with Spring 
applications, offering consistent, declarative, and convenient ways to access data from various data stores. 
We'll cover key concepts, repository interfaces, and how to integrate Spring Data with JPA, JDBC, and REST 
APIs using Spring Boot. This module is designed for students who already have a foundation in Java, Spring Boot, 
and RESTful services.

#### Learning Objectives
By the end of this module, you should be able to:
1. Understand the core principles and benefits of using Spring Data in Spring applications.
2. Define and use repository interfaces to abstract data access.
3. Configure Spring Data with JPA to perform database operations without boilerplate code.
4. Integrate Spring Data repositories with Spring Boot applications.
5. Develop a REST API that leverages Spring Data for CRUD operations.

#### Pre-requisites

- Basic knowledge of Java and Java Core.
- Understanding of JDBC and its limitations.
- Familiarity with Spring Boot and building REST APIs.

### Part 1: Introduction to Spring Data
#### Content
- **What is Spring Data?**
    - Simplifies data access operations
    - Reduces boilerplate code
    - Supports NoSQL and relational databases
- **Key Features of Spring Data**
    - Repository abstraction
    - Query derivation from method names
    - Implementation domain base classes

#### Example
```java
public interface UserRepository extends CrudRepository<User, Long> {
}
```

This simple example shows a repository interface extending `CrudRepository`, providing CRUD operations for `User` entities.


### Part 2: Configuring Spring Data with JPA
#### Content
- **Integration with JPA**
    - Setting up JPA in Spring Boot
    - Configuring data source and EntityManager
- **Defining Entity Models**
    - Annotating classes with `@Entity`
    - Mapping relationships with `@OneToMany`, `@ManyToOne`
- **Repository Interfaces**
    - Extending `JpaRepository`
    - Benefits of using JpaRepository interface

#### Example
```java
@Entity
public class Book {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;

    private String title;
    private String author;

    // getters and setters
}

public interface BookRepository extends JpaRepository<Book, Long> {
}
```
This example defines a `Book` entity and a repository interface for accessing `Book` records.

### Part 3: Creating Repository Methods
#### Content
- **Custom Query Methods**
    - Defining query methods in repositories
    - Query creation from method names

- **Using `@Query` Annotation**
    - Writing JPQL and SQL queries with `@Query`
    - Parameters binding in queries

#### Example
```java
public interface UserRepository extends JpaRepository<User, Long> {
    List<User> findByLastName(String lastName);

    @Query("SELECT u FROM User u WHERE u.email = ?1")
    User findByEmail(String email);
}
```

### Part 4: Integrating Spring Data with REST
#### Content
- **Building a REST Controller**
    - Autowiring repository interfaces
    - Implementing CRUD operations

- **Exception Handling**
    - Handling common data access exceptions
    - Custom exception responses

#### Example
```java
@RestController
@RequestMapping("/api/books")
public class BookController {
    @Autowired
    private BookRepository bookRepository;

    @GetMapping("/{id}")
    public ResponseEntity<Book> getBookById(@PathVariable Long id) {
        Book book = bookRepository.findById(id)
                .orElseThrow(() -> new ResourceNotFoundException("Book not found"));
        return ResponseEntity.ok().body(book);
    }

    // Additional CRUD endpoints
}
```

---

### Conclusion
This module on Data Access with Spring Data offers a streamlined approach to integrating database operations into your 
Spring Boot applications. By the end of this module, you should be comfortable setting up repositories, configuring 
entities, and extending Spring Data to meet your specific data access needs. Continue practicing with different entity 
models and explore advanced querying capabilities to deepen your understanding of Spring Data.

### Practical Exercise: Book Management System with SQLite Database

#### Objective
Develop a simple book management system using Spring Boot, Spring Data JPA, and SQLite. This system will allow users to perform CRUD (Create, Read, Update, Delete) operations on books stored in an SQLite database.

#### Tools and Technologies
- **Java**: Programming language.
- **Spring Boot**: Framework for easy bootstrapping and development of new Spring Applications.
- **Spring Data JPA**: Simplifies data access operations.
- **SQLite**: Lightweight, file-based database management system.
- **Gradle**: Dependency management.

### Setup Instructions
1. **Project Setup**:
  - Create a new Spring Boot project using [Spring Initializr](https://start.spring.io/).
  - Choose Gradle as the build tool and Java as the language.
  - Add dependencies for 'Spring Web' and 'Spring Data JPA'.

2. **Dependencies**:
  - Modify your `build.gradle` file to include the necessary dependencies for SQLite. Here's how your `dependencies` section might look:
```gradle
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    runtimeOnly 'org.xerial:sqlite-jdbc:3.36.0.3'

    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```

3. **Configure the SQLite Database**:
  - In the `src/main/resources` directory, create an `application.properties` file.
  - Add the following properties to configure the connection to the SQLite database:

```properties
spring.datasource.url=jdbc:sqlite:books.db
spring.datasource.driver-class-name=org.sqlite.JDBC
spring.jpa.database-platform=org.hibernate.dialect.SQLiteDialect
spring.jpa.hibernate.ddl-auto=update
```

4. **Entity Creation**:
  - Define a Book entity.

   ```java
   @Entity
   public class Book {
       @Id
       @GeneratedValue(strategy = GenerationType.AUTO)
       private Long id;
       private String title;
       private String author;
       private String isbn;

       // Standard getters and setters
   }
   ```

5. **Repository Interface**:
  - Create a repository interface for the `Book` entity.

   ```java
   public interface BookRepository extends JpaRepository<Book, Long> {
       List<Book> findByAuthor(String author);
   }
   ```

6. **REST Controller**:
  - Implement a REST controller to manage books.

   ```java
   @RestController
   @RequestMapping("/api/books")
   public class BookController {
       @Autowired
       private BookRepository bookRepository;

       @PostMapping
       public Book addBook(@RequestBody Book book) {
           return bookRepository.save(book);
       }

       @GetMapping
       public List<Book> getAllBooks() {
           return bookRepository.findAll();
       }

       @GetMapping("/{id}")
       public Book getBookById(@PathVariable Long id) {
           return bookRepository.findById(id).orElseThrow(() -> new RuntimeException("Book not found"));
       }

       @PutMapping("/{id}")
       public Book updateBook(@PathVariable Long id, @RequestBody Book updatedBook) {
           return bookRepository.findById(id)
                   .map(book -> {
                       book.setTitle(updatedBook.getTitle());
                       book.setAuthor(updatedBook.getAuthor());
                       book.setIsbn(updatedBook.getIsbn());
                       return bookRepository.save(book);
                   })
                   .orElseGet(() -> {
                       updatedBook.setId(id);
                       return bookRepository.save(updatedBook);
                   });
       }

       @DeleteMapping("/{id}")
       public void deleteBook(@PathVariable Long id) {
           bookRepository.deleteById(id);
       }
   }
   ```

#### Exercise Tasks
- **Implement the Entity and Repository**: Define the `Book` entity and create the corresponding repository interface.
- **Create the REST Controller**: Develop the controller with endpoints to handle CRUD operations.
- **Test the Application**:
  - Run your application and use tools like Postman or Curl to test the REST API.
  - Add, retrieve, update, and delete book entries from the SQLite database.


### Recommended Resources
- [Accessing Data with JPA](https://spring.io/guides/gs/accessing-data-jpa)
- [Introduction to Spring Data JPA](https://www.baeldung.com/the-persistence-layer-with-spring-data-jpa)
- [Spring Data JPA Tutorial](https://www.javatpoint.com/spring-and-jpa-integration)
