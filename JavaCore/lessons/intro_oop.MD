### In-Depth Introduction to Objects and Classes in Java

#### 1. **Introduction to Object-Oriented Programming (OOP)**
- **Why OOP?**
    - Mimics real-world entities: Easier to model complex systems.
    - Enhances code reusability and maintainability.
    - Facilitates clearer, more logical program structure.

#### 2. **Understanding Classes in Java**
- **What is a Class?**
    - A blueprint for objects, defining a data type by bundling data and methods.
- **Why Use Classes?**
    - To create user-defined data types.
    - For organizing and structuring code.
    - To encapsulate data and functionalities, making code more manageable and secure.
- **Example**: `Animal` Class
  ```java
  public class Animal {
      String name;

      public Animal(String name) {
          this.name = name;
      }

      public void makeSound() {
          System.out.println(name + " makes a sound.");
      }
  }
  ```

#### 3. **Exploring Objects in Java**
- **What is an Object?**
    - An instance of a class, representing an entity with state and behavior.
- **Why Objects?**
    - They are the building blocks of OOP, representing real-life entities.
    - Enable programmers to create modular and reusable code.
- **Example**: Creating and using an `Animal` object.
  ```java
  public class Zoo {
      public static void main(String[] args) {
          Animal lion = new Animal("Leo");
          lion.makeSound();
      }
  }
  ```

#### 4. **Constructors in Java**
- **Purpose of Constructors**
    - To initialize object state upon creation.
- **Why Constructors?**
    - Ensure that objects start in a valid state.
    - Provide flexibility through overloading for different initialization scenarios.
- **Example**: `Rectangle` Constructors
  ```java
  public class Rectangle {
      int length;
      int width;

      public Rectangle() {
          length = width = 0;
      }

      public Rectangle(int l, int w) {
          length = l;
          width = w;
      }
  }
  ```

#### 5. **Class Members: Fields and Methods**
- **Fields for Data Storage**
    - Why Fields? To store object-specific data.
- **Methods for Behavior**
    - Why Methods? To define actions or behaviors that an object can perform.
- **Example**: `Calculator` Class
  ```java
  public class Calculator {
      public int add(int a, int b) {
          return a + b;
      }
  }
  ```

#### 6. **Hands-On Code Example**
- **Creating a `Student` Class**
    - Why a `Student` Class? To demonstrate a real-world entity as a Java object.
- **Instantiating and Using `Student` Objects**
- **Example**: `Student` and `School` Classes
  ```java
  public class Student {
      String name;
      int age;

      public Student(String name, int age) {
          this.name = name;
          this.age = age;
      }

      public void displayInfo() {
          System.out.println("Student: " + name + ", Age: " + age);
      }
  }

  public class School {
      public static void main(String[] args) {
          Student student1 = new Student("Alice", 20);
          student1.displayInfo();
      }
  }
  ```

#### 7. **Best Practices in Using Classes and Objects**
- **Why Best Practices?**
    - To ensure code is readable, maintainable, and efficient.
    - To prevent common pitfalls and enhance code quality.


### Recommended Resources
- [Object-Oriented Programming Concepts](https://docs.oracle.com/javase/tutorial/java/concepts)
- [OOP](https://www.w3schools.com/java/java_oop.asp)
- [Classes and Objects](https://www.w3schools.com/java/java_classes.asp)
- [Class Attributes](https://www.w3schools.com/java/java_class_attributes.asp)
- [Class Methods](https://www.w3schools.com/java/java_class_methods.asp)
- [Constructors](https://www.w3schools.com/java/java_constructors.asp)
- [Object-Oriented Programming in Java – A Beginner's Guide](https://www.freecodecamp.org/news/object-oriented-programming-concepts-java)


## Tasks

<details>
  <summary>Task 1: Create a Simple Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Create a Simple Class
## Description:
Create a simple Java class named 'Book'. The class should have two fields: 'title' and 'author', both of type String. Also, write a constructor to initialize these fields and a method named 'displayBookInfo()' to print the book information.

### _Inputs & Outputs:_
#### _Sample Input 1:_
N/A

#### _Sample Output 1:_
N/A (This task is more about writing a class than input/output operations)

</pre>
</details>

---

<details>
  <summary>Task 2: Instantiate an Object</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Instantiate an Object
## Description:
Using the 'Book' class from Task 1, create an object named 'myBook' in a 'Main' class, initialize it with the title "1984" and the author "George Orwell", and call the 'displayBookInfo()' method to print the book details.

### _Inputs & Outputs:_
#### _Sample Input 1:_
N/A

#### _Sample Output 1:_
Title: 1984, Author: George Orwell

</pre>
</details>

---

<details>
  <summary>Task 3: Create a Parameterized Constructor</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Create a Parameterized Constructor
## Description:
Modify the 'Book' class by adding a parameterized constructor that allows setting the 'title' and 'author' at the time of object creation.

### _Inputs & Outputs:_
#### _Sample Input 1:_
N/A

#### _Sample Output 1:_
N/A (Focus on class structure and constructor implementation)

</pre>
</details>

---

<details>
  <summary>Task 4: Understanding Object References</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Understanding Object References
## Description:
Demonstrate object references by creating two 'Book' objects in the 'Main' class. Assign one object reference to another and change the title of one book. Print out the titles of both books to show how references work.

### _Inputs & Outputs:_
#### _Sample Input 1:_
N/A

#### _Sample Output 1:_
Title: New Title (for both objects, since they reference the same object)

</pre>
</details>

---

<details>
  <summary>Task 5: Create and Use a Person Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Create and Use a Person Class
## Description:
Create a Java class named 'Person'. It should have three fields: 'name' (String), 'age' (int), and 'email' (String). Include a constructor to initialize these fields and a method 'displayPersonInfo()' to print the person's information.

### Tasks:
1. Write the 'Person' class.
2. In a 'Main' class, create a 'Person' object and initialize it with sample data.
3. Call 'displayPersonInfo()' to print out the object's details.

### _Sample Output:_
Name: John Doe, Age: 30, Email: johndoe@example.com

</pre>
</details>

---

<details>
  <summary>Task 6: Class with Method Overloading</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Class with Method Overloading
## Description:
Modify the 'Person' class to include a method 'updateDetails()' that is overloaded. One version should accept a new age, and another should accept a new age and email.

### Tasks:
1. Implement both versions of 'updateDetails()'.
2. Create a 'Person' object in 'Main', update its details using both methods, and display the updated information.

### _Sample Output:_
Original: Name: Alice, Age: 25, Email: alice@example.com
Updated with new age: Name: Alice, Age: 26, Email: alice@example.com
Updated with new age and email: Name: Alice, Age: 27, Email: alice.new@email.com

</pre>
</details>

---

<details>
  <summary>Task 7: Exploring Constructors</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Exploring Constructors
## Description:
Create a new class 'Rectangle' with fields 'length' and 'width'. Write multiple constructors for different initialization scenarios (no parameters, one parameter for a square, and two parameters for a rectangle).

### Tasks:
1. Implement the 'Rectangle' class with different constructors.
2. In the 'Main' class, create different 'Rectangle' objects using each constructor.
3. Display the dimensions of each rectangle.

### _Sample Output:_
Rectangle 1 (No Params): Length: 0, Width: 0
Rectangle 2 (Square): Length: 5, Width: 5
Rectangle 3: Length: 4, Width: 6

</pre>
</details>

---

<details>
  <summary>Task 8: Advanced Book Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Advanced Book Class
## Description:
Enhance the 'Book' class by adding a field for 'yearPublished' and 'genre'. Implement multiple constructors to allow flexibility in object creation (e.g., only title and author, all fields, etc.). Add methods to update the book's year and genre after creation.

### Tasks:
1. Implement the enhanced 'Book' class with multiple constructors.
2. In 'Main', create various 'Book' objects using different constructors.
3. Demonstrate updating the year and genre of a book object.

### _Sample Output:_
Book 1: Title: Dracula, Author: Bram Stoker
Book 2: Title: 1984, Author: George Orwell, Year: 1949, Genre: Dystopian

</pre>
</details>

---

<details>
  <summary>Task 9: Calculator with Overloaded Methods</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Calculator with Overloaded Methods
## Description:
Create a 'Calculator' class that includes overloaded methods for different arithmetic operations (e.g., add, subtract). Each method should handle different numbers of parameters (e.g., two or three numbers).

### Tasks:
1. Implement the 'Calculator' class with overloaded methods.
2. In 'Main', create a 'Calculator' object and perform various calculations.

### _Sample Output:_
Addition (5, 10): 15
Addition (4, 6, 2): 12

</pre>
</details>

---

<details>
  <summary>Task 10: Product Inventory System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Product Inventory System
## Description:
Create a 'Product' class with fields like 'id', 'name', and 'price'. Write a method to update the price. Then, create an 'Inventory' class that can store multiple products and has methods to add a product and to display all products.

### Tasks:
1. Implement the 'Product' and 'Inventory' classes.
2. In 'Main', create an 'Inventory' object, add several 'Product' objects to it, and display the inventory.

### _Sample Output:_
Inventory:
Product ID: 1, Name: Apple, Price: $0.99
Product ID: 2, Name: Banana, Price: $0.59

</pre>
</details>

---

<details>
  <summary>Task 11: Library Management System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Library Management System
## Description:
Create a 'Library' class that can store an array of 'Book' objects (use the 'Book' class from earlier tasks). Include methods to add a new book and to find a book by title.

### Tasks:
1. Implement the 'Library' class with methods to manage books.
2. In 'Main', create a 'Library' object, add some books, and demonstrate finding a book by its title.

### _Sample Output:_
Found Book: Title: The Hobbit, Author: J.R.R. Tolkien

</pre>
</details>

---

<details>
  <summary>Task 12: Employee Management System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Employee Management System
## Description:
Create an 'Employee' class with fields like 'id', 'name', and 'department'. Write methods to update the department. Then, build an 'EmployeeManager' class to manage an array of employees, including adding and retrieving an employee by ID.

### Tasks:
1. Implement the 'Employee' and 'EmployeeManager' classes.
2. In 'Main', create an 'EmployeeManager', add employees, and retrieve an employee by ID.

### _Sample Output:_
Employee Retrieved: ID: 102, Name: Alice Johnson, Department: HR

</pre>
</details>

---

<details>
  <summary>Task 13: Building a Simple Banking System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Building a Simple Banking System
## Description:
Create a 'BankAccount' class with fields for 'accountNumber', 'accountHolder', and 'balance'. Include methods for 'deposit', 'withdraw', and 'displayAccountInfo'. Then, create a 'Bank' class that can hold multiple bank accounts and has methods to add an account and to find an account by the account number.

### Tasks:
1. Implement the 'BankAccount' and 'Bank' classes.
2. In 'Main', create a 'Bank' object, add several 'BankAccount' objects, perform some transactions, and display account information.

### _Sample Output:_
Account No: 12345, Holder: John Doe, Balance: $200.00
Depositing $150.00 to Account No: 12345
New Balance: $350.00

</pre>
</details>

---

<details>
  <summary>Task 14: Course Registration System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Course Registration System
## Description:
Develop a 'Student' class with fields like 'studentId', 'name', and a list of 'courses'. Implement methods to enroll in a course and display enrolled courses. Then, create a 'Course' class with details like 'courseId', 'courseName', and 'capacity', and a method to check if the course is available for enrollment.

### Tasks:
1. Implement the 'Student' and 'Course' classes.
2. In 'Main', create several 'Course' objects and a few 'Student' objects. Simulate students enrolling in different courses and display their enrolled courses.

### _Sample Output:_
Student: Alice Smith
Enrolled Courses:
1. Course ID: 101, Name: Introduction to Java
2. Course ID: 102, Name: Data Structures

</pre>
</details>


