## **Access Modifiers in Java**

### **1. Introduction to Access Modifiers**

Access modifiers in Java are special keywords used to set the accessibility of classes, methods, or variables. They are foundational to one of the key principles of Object-Oriented Programming – encapsulation – and are crucial for controlling how and from where your class components can be accessed and modified.

### **2. Types of Access Modifiers**

There are four main access modifiers in Java, each with its level of access:

1. **Public**
    - **Explanation:** The public access modifier makes the code entity accessible from any other class in any package. It's the least restrictive level.
    - **Example:**
      ```java
      public class Car {
          public void display() {
              System.out.println("I am a car.");
          }
      }
      ```
      Here, the `Car` class and the `display` method can be accessed from any other class.

2. **Private**
    - **Explanation:** Private elements are accessible only within the class they are declared in. It's the most restrictive access level.
    - **Example:**
      ```java
      public class Person {
          private String name;
 
          public String getName() {
              return name;
          }
 
          public void setName(String newName) {
              name = newName;
          }
      }
      ```
      In this example, the `name` field is private, so it cannot be accessed directly outside the `Person` class. Instead, public getter and setter methods are provided.

3. **Protected**
    - **Explanation:** Protected elements are accessible within all classes in the same package and within subclasses even if they are in different packages.
    - **Example:**
      ```java
      // In package1
      public class Animal {
          protected void display() {
              System.out.println("I am an animal.");
          }
      }
 
      // In package2
      public class Dog extends Animal {
          public void printMessage() {
              display(); // Accessing protected method
          }
      }
      ```
      The `display` method can be accessed within the `Dog` class, which is a subclass of `Animal`.

4. **Default (Package-Private)**
    - **Explanation:** When no access modifier is specified, the default access level is package-private, meaning the element is accessible only within its own package.
    - **Example:**
      ```java
      // In package example
      class ExampleClass {
          void display() {
              System.out.println("Default access modifier used.");
          }
      }
      ```
      Here, both `ExampleClass` and its `display` method have package-private access, and can only be accessed from within the same package.


### **3. Best Practices**
- **Use the Most Restrictive Access Level Needed:** Default to using private access for fields, and only increase accessibility as needed.
- **Encapsulation:** Use private and protected modifiers to encapsulate your data, preventing unauthorized access and modifications from outside of the class or package.
- **Consider Future Changes:** When designing a class, consider how its elements might need to be accessed in the future. A public API should be stable and well thought out.
- **Avoid Public Fields:** In general, avoid making fields public since this exposes internal implementation details and breaks encapsulation. Use getter and setter methods instead.


### **4. Practical Examples**

1. **Public Access Modifier Example**
Let's imagine a simple calculator program. Here, the `Calculator` class contains a public method which allows it to be accessible from anywhere in the program.

```java
public class Calculator {
    // Public method which can be accessed from anywhere
    public int add(int a, int b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println("Sum: " + calc.add(5, 3)); // Accessible
    }
}
```
In this example, the `add` method is declared as public, meaning it can be called from outside the `Calculator` class, like in the `Main` class.


2. **Private Access Modifier Example**
Consider a `BankAccount` class where the balance should be securely hidden from external access.

```java
public class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    // Public method to safely modify private balance
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(1000);
        account.deposit(500);
        System.out.println("Balance: " + account.getBalance());
    }
}
```

Here, `balance` is a private field to prevent direct access and modification. Public methods `deposit` and `getBalance` allow controlled access to this field.

3. **Protected Access Modifier Example**
Consider a scenario with a superclass `Vehicle` and a subclass `Car`.

```java
public class Vehicle {
    protected String licensePlate = "Unknown";

    protected void startEngine() {
        System.out.println("Engine started.");
    }
}

public class Car extends Vehicle {
    public void setLicensePlate(String plate) {
        this.licensePlate = plate;
    }

    public void displayInfo() {
        startEngine();
        System.out.println("License Plate: " + licensePlate);
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.setLicensePlate("XYZ 123");
        myCar.displayInfo();
    }
}
```

In this example, `licensePlate` and `startEngine` are protected in `Vehicle`. This means they are not accessible from outside these classes, except in a subclass like `Car`.

4. **Default (Package-Private) Access Modifier Example**
In a library management system, let's assume we have a `Book` class and a `Library` class in the same package.

```java
// In the 'library' package
class Book {
    String title;
    String author;

    Book(String title, String author) {
        this.title = title;
        this.author = author;
    }
}

public class Library {
    public static void main(String[] args) {
        Book book = new Book("1984", "George Orwell");
        System.out.println("Title: " + book.title); // Accessible within the same package
        System.out.println("Author: " + book.author); // Accessible within the same package
    }
}
```
In this case, `Book` class and its fields `title` and `author` have package-private access. They are accessible within the `Library` class as they are in the same package.

### Recommended Resources
- [Modifiers](https://www.w3schools.com/java/java_modifiers.asp)
- [Controlling Access to Members of a Class](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html)
- [Access Modifiers](https://www.programiz.com/java-programming/access-modifiers)
- [Access Modifiers](https://www.javatpoint.com/access-modifiers)
- [Object-Oriented Programming in Java – A Beginner's Guide](https://www.freecodecamp.org/news/object-oriented-programming-concepts-java)


## Tasks

<details>
  <summary>Task 1: Implementing Encapsulation</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Implementing Encapsulation
## Description:
Create a class `Person` with private fields `name` and `age`. Provide public getter and setter methods for these fields.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Creating an instance of `Person` and setting name and age.

#### _Sample Output 1:_
No direct output; internally, the fields should be set and retrieved correctly.

</pre>
</details>

---

<details>
  <summary>Task 2: Understanding Protected Access</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Understanding Protected Access
## Description:
Create a class `Garden` with a protected method `waterPlants()`. Then, within the same package, create a different class `Gardener` and demonstrate how it can or cannot access the `waterPlants()` method from an instance of `Garden`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Creating an instance of `Gardener` and attempting to call `Garden`'s `waterPlants` method.

#### _Sample Output 1:_
Understanding whether the access to the `waterPlants` method is allowed or not and explaining why.

</pre>
</details>

---

<details>
  <summary>Task 3: Package-Private Access</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Package-Private Access
## Description:
Create two classes `Book` and `Library` in the same package. `Book` should have package-private fields `title` and `author`. `Library` should be able to access these fields but prevent access from outside the package.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Create a `Book` instance in `Library` and try to access its fields.

#### _Sample Output 1:_
Display the `title` and `author` of the `Book`.

</pre>
</details>

---

<details>
  <summary>Task 4: Public Interface</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Public Interface
## Description:
Design a `Calculator` class with public methods for basic operations (add, subtract, multiply, divide). Ensure these methods can be accessed from outside the class.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Perform an addition operation using the `Calculator` class.

#### _Sample Output 1:_
The result of the addition.

</pre>
</details>

---

<details>
  <summary>Task 5: Restricting Access</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Restricting Access
## Description:
Create a class `UserData` with a private field `password`. Implement a public method `isPasswordCorrect` that checks if the given password matches the private one, without exposing the actual password.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Provide a password to the `isPasswordCorrect` method.

#### _Sample Output 1:_
Return `true` or `false` based on whether the provided password matches the private one.

</pre>
</details>

---

<details>
  <summary>Task 6: Private Methods and Class Interaction</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Private Methods and Class Interaction
## Description:
Create a class `Account` with a private method `logTransaction()`. Then, create a public method `deposit` that uses `logTransaction()` internally. Demonstrate calling `deposit` from another class, and discuss whether `logTransaction()` is directly accessible or not.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Depositing an amount in `Account`.

#### _Sample Output 1:_
A confirmation of the deposit, but no direct output from `logTransaction()` as it's private.

</pre>
</details>

---

<details>
  <summary>Task 7: Default Access Modifier in Practice</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Default Access Modifier in Practice
## Description:
Create two classes `Printer` and `PrintManager` in the same package. `Printer` should have a default access level method `printDocument()`. From `PrintManager`, try to access `printDocument()`. Then, attempt to access the same method from a class in a different package and discuss the result.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Creating an instance of `PrintManager` and calling `printDocument()`.

#### _Sample Output 1:_
Successful printing operation or access denial, depending on the package of the calling class.

</pre>
</details>


