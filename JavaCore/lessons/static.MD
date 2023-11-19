### Understanding Static Elements in Java

In Java, the keyword `static` is used to denote elements of a class that are shared among all instances of the class. 
These elements belong to the class itself, rather than to any particular object instance.

#### 1. Static Variables
- **Definition**: Also known as static fields or class variables, they are shared among all instances of the class.
- **Usage**: They are typically used for constants or variables that should be consistent across all instances.
- **Example**:
  ```java
  class MyClass {
      static int counter = 0; // Static variable

      MyClass() {
          counter++;
      }
  }
  ```
- **Deeper Insight**: A static variable gets memory only once in the class area at the time of class loading. It makes it a common property for all objects (instances) of that class. This is why changing the value of a static variable by one object affects all other instances.
- **Extended Example**:
  ```java
  class Student {
      static String schoolName = "Global High"; // Common for all students
      String name; // Individual for each student

      Student(String name) {
          this.name = name;
      }

      void displayInfo() {
          System.out.println(name + " studies in " + schoolName);
      }
  }
  ```

#### 2. Static Methods
- **Definition**: Methods declared with the `static` keyword belong to the class, not to any specific instance.
- **Usage**: Often used for utility or helper methods that don't require any object state.
- **Example**:
  ```java
  class MathUtils {
      static int add(int a, int b) {
          return a + b;
      }
  }
  // Can be called as MathUtils.add(5, 3)
  ```
- **Deeper Insight**: They cannot directly access instance variables or instance methods. They are often used for operations that don't require any data from an instance of the class (from `this`).
- **Static and Non-static Together**:
  ```java
  class Calculator {
      static int add(int a, int b) {
          return a + b;
      }

      int multiply(int a, int b) {
          return a * b;
      }
  }
  // Static method called without an object: Calculator.add(5, 3)
  // Non-static method called with an object: new Calculator().multiply(5, 3)
  ```

#### 3. Static Blocks
- **Definition**: Static blocks are used for static initialization of a class. This block gets executed when the class is loaded into memory.
- **Usage**: Useful for complex initialization that can't be handled in a single statement.
- **Example**:
  ```java
  class Config {
      static int configValue;

      static {
          // Initialize static variables or perform static operations
          configValue = fetchConfigFromDatabase();
      }
  }
  ```
- **Deeper Insight**: Static blocks are executed before the main method, at the time of class loading. It's mainly used for initializing static variables. It can't access non-static data (variables and methods).
- **Extended Example**:
  ```java
  class DatabaseConnector {
      static String dbURL;

      static {
          // This block of code is executed once when the class is loaded.
          dbURL = System.getenv("DATABASE_URL");
      }
  }
  ```

#### 4. Static Inner Classes
- **Definition**: Nested classes declared as static are called static nested classes.
- **Usage**: Useful when a nested class doesn't need access to an instance of the outer class.
- **Example**:
  ```java
  class Outer {
      static class Nested {
          int nestedVar = 0;
      }
  }
  // Can be instantiated as Outer.Nested nestedInstance = new Outer.Nested();
  ```
- **Deeper Insight**: A static inner class is associated with its outer class. Unlike inner classes, it doesn't need a reference to an instance of the outer class. It can access static data members of the outer class including private ones.
- **Extended Example**:
  ```java
  class Outer {
      private static String msg = "Hello";

      static class Inner {
          void display() {
              System.out.println(msg); // Can access outer class's static variable
          }
      }
  }
  Outer.Inner innerObj = new Outer.Inner();
  innerObj.display();
  ```

### Key Points to Remember
- Static elements are shared across all instances of the class.
- They are used for elements that logically belong to the type itself, rather than to instances of the type.
- Static methods can’t access instance methods and instance variables directly; they need an object reference.
- Static blocks and variables are initialized in the order they appear in a class.
- **When to Use Static Variables**: For shared properties (like configuration settings, constants).
- **When to Use Static Methods**: For utility or helper methods; methods that don't require any object state.
- **Considerations**:
    - Overusing static can lead to issues with object-oriented design principles, as it promotes state sharing which can complicate testing and debugging.
    - Static methods can't be overridden, but they can be hidden by another static method in a subclass.

### Use Cases
- Constants (`static final` variables).
- Utility functions that don't require object state.
- Counters shared across all instances of a class.


### Recommended Resources
- [Static in Java: An Overview of Static Keyword With Examples](https://www.simplilearn.com/tutorials/java-tutorial/static-keyword-in-java#:~:text=Static%20keyword%20in%20java%20in,create%20one%20instance%20of%20it.)
- [Java static keyword](https://www.javatpoint.com/static-keyword-in-java)
- [static Keyword](https://www.w3schools.com/java/ref_keyword_static.asp)
- [static Keyword in Java](https://www.geeksforgeeks.org/static-keyword-java)
- [A Guide to the Static Keyword in Java](https://www.baeldung.com/java-static)


## Tasks

<details>
  <summary>Task 1: Static Counter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Static Counter
## Description:
Create a class 'Counter' with a static variable 'count' and a constructor that increments this count each time a new object is created. Write a main method to demonstrate this.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Create 3 objects of Counter class.

#### _Sample Output 1:_
Count: 3

#### _Sample Input 2:_
Create 5 objects of Counter class.

#### _Sample Output 2:_
Count: 5

</pre>
</details>

---

<details>
  <summary>Task 2: Static Utility Method</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Static Utility Method
## Description:
Implement a static method 'findMax' in a class 'ArrayOperations' that takes an array of integers and returns the maximum value.

### _Inputs & Outputs:_
#### _Sample Input 1:_
[3, 5, 9, 1, 2]

#### _Sample Output 1:_
9

#### _Sample Input 2:_
[10, 21, 4, 18, 6]

#### _Sample Output 2:_
21

</pre>
</details>

---

<details>
  <summary>Task 3: Static Initialization Block</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Static Initialization Block
## Description:
Create a class 'DatabaseConfig' with a static block to initialize a static variable 'dbURL' with a value. Display this value in a main method.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Run the main method.

#### _Sample Output 1:_
Database URL: [The initialized URL]

</pre>
</details>

---

<details>
  <summary>Task 4: Static Inner Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Static Inner Class
## Description:
Create a class 'Outer' with a private static variable. Inside it, create a static inner class 'Inner' with a method to display the outer class's variable. Demonstrate this in a main method.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Create an object of the inner class and call its display method.

#### _Sample Output 1:_
Value of the outer class's variable.

</pre>
</details>

---

