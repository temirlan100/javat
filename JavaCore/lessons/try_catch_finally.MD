### Try-catch-finally in Java

### 1. Basic Structure
- **Try Block**: This is where you place code that might throw an exception.
- **Catch Block**: This block catches and handles the exception. You can have multiple catch blocks for different types of exceptions.
- **Finally Block**: Code in this block executes regardless of whether an exception was thrown or caught. It's typically used for cleanup activities.

### 2. Example Code
```java
public class Main {
    public static void main(String[] args) {
        try {
            // Code that might throw an exception
            int divideByZero = 5 / 0;
        } catch (ArithmeticException e) {
            // This block is to catch and handle ArithmeticException
            System.out.println("Arithmetic exception caught: " + e.getMessage());
        } finally {
            // This code is always executed
            System.out.println("This is the finally block.");
        }
    }
}
```

### Example: Handling Array Index Out of Bounds Exception
This example shows how to handle an `ArrayIndexOutOfBoundsException` when accessing an array element outside of its bounds.

```java
public class ArrayExceptionExample {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        try {
            int number = numbers[5]; // This will throw ArrayIndexOutOfBoundsException
            System.out.println("Number: " + number);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.err.println("Array Index Out Of Bounds Exception caught: " + e.getMessage());
        }
    }
}
```

Key Takeaways:
- The `catch` block is tailored to handle `ArrayIndexOutOfBoundsException`.
- When an attempt is made to access an index that does not exist, the catch block handles the exception gracefully.

### 3. Key Points to Teach
- **Multiple Catch Blocks**: You can have multiple catch blocks for different exceptions. Java will use the first catch block that matches the exception type.
- **Exception Hierarchy**: Catch blocks should be ordered from most specific to most general since Java checks them in sequence.
- **Finally Block Execution**: The finally block is executed even if an exception is not caught. It's also executed if a catch block rethrows an exception.
- **Purpose of Finally**: It's mainly used for resource cleanup, like closing file streams or database connections.

### 4. Practical Tips
- **Resource Management**: Use `finally` to ensure resources are released, or consider using try-with-resources for automatic resource management.
- **Control Flow**: Understand how exceptions affect program flow - an uncaught exception will cause remaining code in the try block to be skipped.
- **Exception Specificity**: Always catch the most specific exception possible to handle errors more accurately.

Certainly! Adding information about the Try-With-Resources statement will provide a more comprehensive understanding of exception handling and resource management in Java.

### Try-With-Resources Statement
Introduced in Java 7, the Try-With-Resources statement is an enhancement to the traditional try-catch-finally block, 
providing a simpler way to handle resources like files, sockets, or database connections. It ensures that each resource 
is closed at the end of the statement, which helps to avoid potential resource leaks.

#### Basic Structure
- **Resource Declaration**: Resources that implement the `AutoCloseable` or `Closeable` interface are declared within the parentheses following the `try` keyword.

#### Example Code

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        String line;
        try (BufferedReader br = new BufferedReader(new FileReader("example.txt"))) {
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.out.println("Error occurred: " + e.getMessage());
        }
    }
}
```

#### Key Points to Teach
- **Automatic Resource Management**: The Try-With-Resources statement automatically closes the resources after the try block is exited, either normally or due to an exception.
- **Implementing AutoCloseable**: For a class to be used with Try-With-Resources, it must implement the `AutoCloseable` or `Closeable` interface and override the `close()` method.
- **Multiple Resources**: You can declare multiple resources in the try-with-resources statement, separated by semicolons.
- **Exception Handling**: Exceptions thrown by the `close()` method can be caught and handled in the catch block.

#### Benefits
- **Simpler Code**: Reduces the need for a finally block to release resources, leading to more readable and maintainable code.
- **Resource Handling**: Helps in avoiding common resource leaks that occur when resources are not properly closed.
- **Exception Suppression**: If both the try block and `close()` method throw exceptions, the exception from the try block is propagated, and the exception from `close()` is suppressed.

#### Practical Tips
- **Use in Modern Java**: Encourage the use of Try-With-Resources when dealing with resources in Java 7 and later.
- **Resource Order**: In the case of multiple resources, they are closed in the reverse order of their creation.
- **Suppressed Exceptions**: Be aware of suppressed exceptions; they can be retrieved using the `Throwable.getSuppressed()` method.

### Recommended Resources
- [Java try-catch block](https://www.javatpoint.com/try-catch-block)
- [Java finally block](https://www.javatpoint.com/finally-block-in-exception-handling)
- [Java try...catch](https://www.programiz.com/java-programming/try-catch)
- [Java Exceptions - Try...Catch](https://www.w3schools.com/java/java_try_catch.asp)
- [The try-with-resources Statement](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html)
- [Java – Try with Resources](https://www.baeldung.com/java-try-with-resources)


## Tasks

<details>
  <summary>Task 1: File Reading with Exception Handling</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# File Reading with Exception Handling
## Description:
Create a program that reads user input for a file name and attempts to open and read the first line of the file. Use a try-catch block to handle FileNotFoundException and IOException, displaying appropriate messages for each.

### _Inputs & Outputs:_
#### _Sample Input 1:_
existingFile.txt

#### _Sample Output 1:_
First line of the file: [Contents of the first line]

#### _Sample Input 2:_
nonExistingFile.txt

#### _Sample Output 2:_
Error: File not found

</pre>
</details>

---

<details>
  <summary>Task 2: NullPointerException Handling</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# NullPointerException Handling
## Description:
Develop a program that attempts to access a method of a null object reference. Use a try-catch block to catch and handle a `NullPointerException`, displaying an appropriate error message.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Null Object Reference

#### _Sample Output 1:_
Error: Attempted to access a method on a null object reference

#### _Sample Input 2:_
Valid Object Reference

#### _Sample Output 2:_
Method accessed successfully

</pre>
</details>

---

<details>
  <summary>Task 3: Using Finally Block</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Using Finally Block
## Description:
Create a program that opens and reads data from a file using FileReader. Use a try-catch block to handle IOException. Ensure to close the FileReader in a finally block, or use try-with-resources.

### _Inputs & Outputs:_
#### _Sample Input 1:_
ValidFilePath.txt

#### _Sample Output 1:_
File content displayed

#### _Sample Input 2:_
InvalidFilePath.txt

#### _Sample Output 2:_
Error: File not found

</pre>
</details>

---


<details>
  <summary>Task 4: Multiple Catch Blocks</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Multiple Catch Blocks
## Description:
Write a program that includes different operations (like array access, arithmetic operations, etc.) that can throw various exceptions. Use multiple catch blocks to handle different types of exceptions specifically.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Choose operation: 1 (Array Access), Input: 4

#### _Sample Output 1:_
Element at index 4: [Value]

#### _Sample Input 2:_
Choose operation: 2 (Division), Input: 10, 0

#### _Sample Output 2:_
Error: Division by zero

</pre>
</details>

---

<details>
  <summary>Task 5: File Processing with Try-With-Resources</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# File Processing with Try-With-Resources
## Description:
Create a program that uses the try-with-resources statement to open and process a file. The program should read a file name from the user, then open and read the contents of the file line by line, displaying each line on the console.

### _Inputs & Outputs:_
#### _Sample Input 1:_
exampleFile.txt

#### _Sample Output 1:_
[Contents of exampleFile.txt]

#### _Sample Input 2:_
missingFile.txt

#### _Sample Output 2:_
Error: File not found

</pre>
</details>


