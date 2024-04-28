### Module: Securing Spring Applications with Spring Security
#### Overview of Spring Security
Spring Security is a powerful and highly customizable authentication and access-control framework. 
It is the de-facto standard for securing Spring-based applications. Spring Security is a framework that focuses 
on providing both authentication and authorization to Java applications. It integrates well with Spring MVC and other 
Spring Modules, but can also be used independently.

#### Why We Need Spring Security
1. **Strong Authentication**: Spring Security provides comprehensive support for authentication. It can integrate with a wide range of authentication mechanisms.
2. **Fine-grained Authorization**: Allows you to define who can access what in your application, down to individual URL or method level.
3. **Protection Against Attacks**: Offers protection against common vulnerabilities such as session fixation, clickjacking, cross-site request forgery (CSRF), and more.
4. **Enterprise Ready**: It supports LDAP, OAuth2, and can be extended to meet custom requirements, making it suitable for large enterprise applications.

#### Use Cases
1. **Secure Web Applications**: Protecting web pages based on user roles, redirecting users to a login page when they try to access protected resources.
2. **Method Security**: Using annotations to protect service layer operations based on authenticated user roles.
3. **OAuth2 Integration**: Allowing your applications to use third-party authentication providers like Google, Facebook, etc.
4. **REST API Security**: Securing REST APIs with token-based authentication such as JWT.
5. **LDAP Authentication**: Integrating with LDAP for authentication and authorization in enterprise environments.

#### Key Components
- **SecurityContextHolder**: to provide access to the SecurityContext.
- **SecurityContext**: to hold the Authentication and possibly request-specific security information.
- **Authentication**: to represent the principal in a Spring Security-specific manner.
- **GrantedAuthority**: to reflect the application-wide permissions granted to a principal.
- **UserDetails**: to provide necessary information to build an Authentication object from your application's DAOs or other source of security data.

#### Code Examples
##### 1. Configuring HTTP Security
This example shows how to configure HTTP security, specifying which endpoints are public and which are secured.

```java
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
            .antMatchers("/", "/home", "/about").permitAll()  // Allow public access to these pages
            .antMatchers("/admin/**").hasRole("ADMIN")         // Only users with 'ADMIN' role can access /admin/**
            .anyRequest().authenticated()                      // All other requests need to be authenticated
            .and()
            .formLogin()
            .loginPage("/login")                               // Custom login page
            .permitAll()
            .and()
            .logout()
            .permitAll();
    }
}
```

**Explanation**: This configuration secures your application by requiring authentication for any request that doesn't match the specified patterns. It also configures a custom login page and allows everyone to view it.

##### 2. Method Level Security
Spring Security can also secure individual methods using annotations:

```java
import org.springframework.security.access.prepost.PreAuthorize;

public class SomeService {

    @PreAuthorize("hasRole('ADMIN')")
    public void adminOnlyService() {
        // logic here
    }
}
```

**Explanation**: The `@PreAuthorize` annotation ensures that this method can only be accessed by users who have the 'ADMIN' role.

#### Conclusion
Spring Security is essential for protecting Spring applications. It provides robust authentication and authorization 
capabilities, making it suitable for securing enterprise applications, protecting sensitive data, and ensuring that 
only authorized users can perform certain operations. Its integration with Spring Boot and other Spring modules makes 
it a seamless and powerful choice for developers.

### Recommended Resources
- [Spring Security Tutorial](https://www.youtube.com/watch?v=b9O9NI-RJ3o)
- [Spring Security](https://docs.spring.io/spring-security/reference/index.html)
- [Security with Spring](https://www.baeldung.com/security-spring)

### Practical Exercise: Book Management System with SQLite and Spring Security
This practical exercise involves creating a simple Book Management System using Spring Boot, 
Spring Security for authentication, and SQLite as the database. The system will allow users to view a list 
of books, add new books, and delete books, with different access levels for admins and regular users.

#### Objectives
1. **Set up a Spring Boot project with Gradle**.
2. **Configure Spring Security for authentication and authorization**.
3. **Use SQLite to store book data**.
4. **Implement CRUD (Create, Read, Update, Delete) operations for managing books**.

#### Tools and Technologies
- Spring Boot
- Spring Security
- Spring Data JPA
- SQLite
- Gradle
- Java

#### Setup Instructions
##### 1. Project Setup with Gradle
Create a new Spring Boot project either using [Spring Initializr](https://start.spring.io/) or manually. 
Select Gradle Project, Java, and Spring Boot version. Add dependencies: Spring Web, Spring Security, Spring Data JPA, 
and SQLite.
`build.gradle` file should include:

```gradle
plugins {
    id 'org.springframework.boot' version '3.2.0'
    id 'java'
}

group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '17'

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    implementation 'org.springframework.boot:spring-boot-starter-security'
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    runtimeOnly 'org.xerial:sqlite-jdbc'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
    testImplementation 'org.springframework.security:spring-security-test'
}
```

##### 2. Configure SQLite Database
Create `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:sqlite:books.db
spring.datasource.driver-class-name=org.sqlite.JDBC
spring.jpa.database-platform=org.hibernate.dialect.SQLiteDialect
spring.jpa.hibernate.ddl-auto=update
```

##### 3. Spring Security Configuration
Implement a basic configuration in `src/main/java/com/example/demo/SecurityConfig.java`:

```java
import org.springframework.context.annotation.Bean;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;

@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication()
            .withUser("admin").password(passwordEncoder().encode("adminPass")).roles("ADMIN")
            .and()
            .withUser("user").password(passwordEncoder().encode("userPass")).roles("USER");
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
            .antMatchers("/").permitAll()
            .antMatchers("/admin/**").hasRole("ADMIN")
            .anyRequest().authenticated()
            .and()
            .formLogin()
            .and()
            .logout();
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

##### 4. Implementing CRUD Operations
Create the `Book` entity, repository, and service classes to manage book data. Use Spring Data JPA to interact with 
the SQLite database.

###### Book Entity:

```java
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class Book {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;
    private String title;
    private String author;

    // Constructors, getters and setters
}
```

###### Book Repository:
```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface BookRepository extends JpaRepository<Book, Long> {
}
```

##### 5. Create a simple controller
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/books")
public class BookController {
    @Autowired
    private BookRepository bookRepository;

    @GetMapping
    public List<Book> getAllBooks() {
        return bookRepository.findAll();
    }

    @PostMapping
    public Book createBook(@RequestBody Book book) {
        return bookRepository.save(book);
    }

    @DeleteMapping("/{id}")
    public void deleteBook(@PathVariable Long id) {
        bookRepository.deleteById(id);
    }
}
```

#### Conclusion
This setup will create a basic Book Management System where users can manage books with different privileges based 
on their roles. Admins have full access to the system, while regular users can only view books. This project 
helps students understand how to integrate Spring Security with a real-world application, managing authentication 
and authorization effectively.
