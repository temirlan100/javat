### Introduction to Custom Exceptions in Java
- **What are Exceptions?**
    - Briefly recap standard exceptions in Java, highlighting the importance of exception handling for robust software.

- **Why Create Custom Exceptions?**
    - Discuss the need for more specific error handling.
    - Custom exceptions can make code more readable and maintainable.

### Understanding Exception Hierarchy
- **Throwable Class**: The superclass of all errors and exceptions.
- **Two Main Subclasses**: `Error` (used by JVM) and `Exception` (used by applications).
- **Checked vs. Unchecked Exceptions**: Explain the difference and when to use each.

### Creating a Custom Exception

- **Extending the Exception Class**
    - Show how to create a new class that extends either `Exception` (for checked exceptions) or `RuntimeException` (for unchecked exceptions).

#### Example 1: A Simple Custom Exception
```java
public class MyCustomException extends Exception {
    public MyCustomException(String message) {
        super(message);
    }
}

// Usage
throw new MyCustomException("This is a custom message");
```

#### Example 2: Adding Extra Functionality
```java
public class DatabaseException extends Exception {
    private int errorCode;

    public DatabaseException(String message, int errorCode) {
        super(message);
        this.errorCode = errorCode;
    }

    public int getErrorCode() {
        return errorCode;
    }
}

// Usage
throw new DatabaseException("Database connection failed", 500);
```

### Integrating Custom Exceptions in Code
- **Example Scenarios**: Provide a few scenarios or case studies where custom exceptions would be beneficial.
- **Code Integration**: Show how to integrate these exceptions into existing code, including try-catch blocks.

### Further Reading
- Suggest books or online resources for deeper understanding.
- Link to official Java documentation on exceptions.

### Example: Custom Exception for Input Validation

#### Scenario
Imagine you have an application where you need to validate user input. If the input doesn't meet certain criteria, you want to throw an exception that specifically handles this scenario.

#### Creating the Custom Exception
First, create a custom exception class. In this case, we'll call it `InvalidInputException`. This exception is a checked exception, so it extends `Exception`.

```java
public class InvalidInputException extends Exception {
    public InvalidInputException(String message) {
        super(message);
    }
}
```

#### Explanation
- `InvalidInputException` extends `Exception`, making it a checked exception.
- The constructor accepts a `String` message, which can be used to provide detailed information about the validation error.

#### Using the Custom Exception
Now, let's use this exception in a method that validates a user's age.

```java
public class UserInputValidator {

    public void validateAge(int age) throws InvalidInputException {
        if (age < 18) {
            throw new InvalidInputException("Age must be 18 or above.");
        }
        System.out.println("Age is valid.");
    }
    
    public static void main(String[] args) {
        UserInputValidator validator = new UserInputValidator();
        try {
            validator.validateAge(16);
        } catch (InvalidInputException e) {
            System.err.println("Validation error: " + e.getMessage());
        }
    }
}
```

#### Explanation
- The `validateAge` method throws `InvalidInputException` when the age is below 18.
- In the `main` method, we create an instance of `UserInputValidator` and call `validateAge`.
- We use a try-catch block to handle `InvalidInputException`.

### Best Practices and Integration
- **Use Meaningful Names**: Name exceptions clearly to indicate their specific purpose.
- **Avoid Overuse**: Only create custom exceptions when necessary.
- **Documentation**: Always document custom exceptions to explain their purpose and usage.
- Use this exception to enforce input validation rules throughout your application.
- Ensure that the exception is caught and handled appropriately, providing meaningful feedback to the user or the calling method.

### Recommended Resources
- [Java Custom Exception](https://www.javatpoint.com/custom-exception#:~:text=In%20order%20to%20create%20custom,belongs%20to%20java.lang%20package.&text=Consider%20the%20following%20example%2C%20where,public%20WrongFileNameException(String%20errorMessage)%20%7B)
- [Create a Custom Exception in Java](https://www.baeldung.com/java-new-custom-exception)
- [How can we create a custom exception in Java?](https://www.tutorialspoint.com/how-can-we-create-a-custom-exception-in-java)
- [User-defined Custom Exception in Java](https://www.geeksforgeeks.org/user-defined-custom-exception-in-java)


## Tasks

<details>
  <summary>Task 1: Simple Custom Exception</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Simple Custom Exception
## Description:
Create a custom exception called `SimpleException` that extends `Exception`. It should take a string message as its constructor argument.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Throw `SimpleException` with the message "Simple error occurred"

#### _Sample Output 1:_
Exception message: "Simple error occurred"

</pre>
</details>

---

<details>
  <summary>Task 2: Parameter Validation Exception</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Parameter Validation Exception
## Description:
Create a custom exception named `ParameterValidationException`. Use this exception in a method `validateNumber` that takes an integer. If the number is negative, throw `ParameterValidationException`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
validateNumber(5)

#### _Sample Output 1:_
No exception thrown

#### _Sample Input 2:_
validateNumber(-3)

#### _Sample Output 2:_
Exception message: "Negative numbers are not allowed."

</pre>
</details>

---

<details>
  <summary>Task 3: Advanced Custom Exception</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Advanced Custom Exception
## Description:
Create a custom exception `AdvancedException` that includes a constructor to pass a message and an error code. Write a method `processData` that throws `AdvancedException` with different messages and error codes based on various conditions.

### _Inputs & Outputs:_
#### _Sample Input 1:_
processData(1)

#### _Sample Output 1:_
Exception message: "Data is insufficient", Error Code: 100

#### _Sample Input 2:_
processData(2)

#### _Sample Output 2:_
Exception message: "Data is invalid", Error Code: 200

</pre>
</details>

---

<details>
  <summary>Task 4: Custom Unchecked Exception</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Custom Unchecked Exception
## Description:
Create a custom unchecked exception called `MyRuntimeException` that extends `RuntimeException`. Demonstrate its use in a scenario where it's thrown and caught.

### _Inputs & Outputs:_
#### _Sample Input 1:_
A scenario where `MyRuntimeException` is thrown due to invalid user input.

#### _Sample Output 1:_
Runtime exception caught with message: "Invalid user input."

</pre>
</details>

