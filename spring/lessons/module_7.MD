### Module: Testing Spring Applications
### Why Testing is Essential in Spring Applications
1. **Prevent Regression**: Tests ensure that newly added features don’t break the existing functionality.
2. **Code Quality**: Tests help maintain and improve the quality of code, making it more robust and easier to refactor.
3. **Documentation**: Tests can serve as additional documentation for your code. They show how the application is supposed to work.
4. **Design Feedback**: Writing tests can provide immediate feedback on the application design. If a component is hard to test, it might be a sign that the design could be improved.
5. **Confidence**: Automated testing provides the team with the confidence to make changes and deploy updates, knowing that core functionalities remain intact.

### Types of Tests in Spring
1. **Unit Tests**: These test individual components in isolation, usually by mocking dependencies.
2. **Integration Tests**: These tests check the interaction between multiple components, or with a real database or server.
3. **Functional Tests**: Higher-level tests that interact with the application just like an end-user would, testing complete scenarios.

### Tools for Testing in Spring
- **JUnit**: The most common framework for writing Java tests.
- **Spring Test**: Provides support for loading Spring ApplicationContexts and caching them between tests.
- **Mockito**: Used for mocking objects in unit tests.
- **Spring Boot Test**: Simplifies testing Spring Boot applications by managing application contexts and caches.
- **TestRestTemplate**: For testing RESTful endpoints.

### Practical Examples
Here's how you might approach testing various components of a Spring application:

#### Example 1: Testing Spring MVC Controllers with MockMvc
MockMvc is a powerful tool for testing Spring MVC controllers without needing to start a full HTTP server.

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.AutoConfigureMockMvc;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.web.servlet.MockMvc;

import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.content;

@SpringBootTest
@AutoConfigureMockMvc
public class WebLayerTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    public void shouldReturnDefaultMessage() throws Exception {
        this.mockMvc.perform(get("/"))
                .andExpect(status().isOk())
                .andExpect(content().string(containsString("Hello, World")));
    }
}
```

#### Example 2: Integration Testing with @SpringBootTest
`@SpringBootTest` can be used for integration testing, loading the full application context.

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.context.ApplicationContext;

import static org.assertj.core.api.Assertions.assertThat;

@SpringBootTest
public class ApplicationContextTest {

    @Autowired
    private ApplicationContext context;

    @Test
    public void contextLoads() {
        assertThat(context).isNotNull();
    }
}
```

#### Example 3: Testing Data Layer with DataJpaTest
`@DataJpaTest` is used for testing the repository layer with an in-memory database like H2.

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import org.springframework.dao.DataIntegrityViolationException;

import static org.assertj.core.api.Assertions.assertThat;
import static org.assertj.core.api.Assertions.assertThatThrownBy;

@DataJpaTest
public class UserRepositoryTests {

    @Autowired
    private UserRepository userRepository;

    @Test
    public void shouldSaveUser() {
        User user = new User("Alice", "alice@example.com");
        User savedUser = userRepository.save(user);
        assertThat(savedUser).isNotNull();
        assertThat(savedUser.getId()).isNotNull();
    }

    @Test
    public void shouldFailWhenSavingUserWithoutEmail() {
        User user = new User("Bob", null);

        assertThatThrownBy(() -> userRepository.save(user))
                .isInstanceOf(DataIntegrityViolationException.class);
    }
}
```


### Recommended Resources
- [Testing the Web Layer](https://spring.io/guides/gs/testing-web)
- [Testing in Spring Boot](https://www.baeldung.com/spring-boot-testing)
- [Spring Boot Testing Tutorial - Crash Course](https://www.youtube.com/watch?v=aPoJPESMJBk)


### Practical Exercise: Light medical system
**Objective:** Develop a small-scale medical system where patients can register, and doctors can view/update patient records.

### Requirements
1. **Patient Registration**: Patients can register themselves with their name, age, and medical history.
2. **Doctor Access**: Doctors can view and update patient records.
3. **Security**: Only registered doctors can view and modify patient data. Patients can only register and view their own records.

### System Components
- **Patient Entity**
- **Doctor Entity**
- **Patient Repository**
- **Doctor Repository**
- **Patient Service**
- **Doctor Service**
- **Security Configuration**

### Step-by-Step Implementation Guide
#### Step 1: Set Up the Spring Boot Application
- Initialize a new Spring Boot project with dependencies for Spring Web, Spring Data JPA, Spring Security, and an H2 Database.

#### Step 2: Define the Domain Models
```java
import javax.persistence.*;

@Entity
public class Patient {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private int age;
    private String medicalHistory;

    // Getters and setters
}

@Entity
public class Doctor {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String specialty;

    // Getters and setters
}
```

#### Step 3: Create Repositories
```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface PatientRepository extends JpaRepository<Patient, Long> {}

public interface DoctorRepository extends JpaRepository<Doctor, Long> {}
```

#### Step 4: Develop Services
```java
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

@Service
public class PatientService {
    private final PatientRepository patientRepository;

    public PatientService(PatientRepository patientRepository) {
        this.patientRepository = patientRepository;
    }

    @Transactional
    public Patient registerPatient(Patient patient) {
        return patientRepository.save(patient);
    }

    @Transactional(readOnly = true)
    public Patient getPatient(Long id) {
        return patientRepository.findById(id).orElse(null);
    }
}

@Service
public class DoctorService {
    private final DoctorRepository doctorRepository;

    public DoctorService(DoctorRepository doctorRepository) {
        this.doctorRepository = doctorRepository;
    }

    @Transactional(readOnly = true)
    public Doctor getDoctor(Long id) {
        return doctorRepository.findById(id).orElse(null);
    }
}
```

#### Step 5: Configure Spring Security
```java
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

@Configuration
@EnableWebSecurity
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .csrf().disable()
            .authorizeRequests()
            .antMatchers("/patients/**").hasRole("DOCTOR")
            .antMatchers("/register", "/login").permitAll()
            .anyRequest().authenticated()
            .and()
            .formLogin()
            .and()
            .httpBasic();
    }
}
```

#### Step 6: Develop REST Controllers
```java
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/patients")
public class PatientController {
    private final PatientService patientService;

    public PatientController(PatientService patientService) {
        this.patientService = patientService;
    }

    @PostMapping("/register")
    public Patient registerPatient(@RequestBody Patient patient) {
        return patientService.registerPatient(patient);
    }

    @GetMapping("/{id}")
    public Patient getPatient(@PathVariable Long id) {
        return patientService.getPatient(id);
    }
}
```

### Writing Tests for the Medical System
#### Unit Tests for Services
```java
import org.junit.jupiter.api.Test;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.MockitoAnnotations;
import static org.mockito.Mockito.when;
import static org.mockito.Mockito.verify;
import static org.assertj.core.api.Assertions.assertThat;

class PatientServiceTest {

    @Mock
    private PatientRepository patientRepository;

    @InjectMocks
    private PatientService patientService;

    @BeforeEach
    void setUp() {
        MockitoAnnotations.openMocks(this);
    }

    @Test
    void registerPatientTest() {
        Patient patient = new Patient();
        patient.setName("John Doe");
        when(patientRepository.save(any(Patient.class))).thenReturn(patient);

        Patient created = patientService.registerPatient(patient);

        assertThat(created.getName()).isEqualTo("John Doe");
        verify(patientRepository).save(patient);
    }
}
``

`

#### Integration Tests Using Spring Boot Test

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.test.web.client.TestRestTemplate;
import org.springframework.boot.test.context.SpringBootTest.WebEnvironment;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;

@SpringBootTest(webEnvironment = WebEnvironment.RANDOM_PORT)
public class PatientIntegrationTests {

    @Autowired
    private TestRestTemplate restTemplate;

    @Test
    public void testRegisterPatient() {
        Patient patient = new Patient();
        patient.setName("Jane Doe");
        ResponseEntity<Patient> response = restTemplate.postForEntity("/patients/register", patient, Patient.class);

        assertThat(response.getStatusCode()).isEqualTo(HttpStatus.OK);
        assertThat(response.getBody().getName()).isEqualTo("Jane Doe");
    }
}
```
