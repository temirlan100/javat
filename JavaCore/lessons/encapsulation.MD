### Enhanced Educational Material on Encapsulation in Java

**1. Introduction to Encapsulation**
- **Definition**: Explain encapsulation as a concept of bundling the data (variables) and code (methods) that operates on the data into a single unit or class.
- **Objective**: Discuss how encapsulation helps in controlling the data and preventing unauthorized access and modification.

**2. The Importance of Encapsulation**
- **Data Hiding**: Elaborate on how encapsulation helps to hide the internal state of an object from the outside, known as data hiding. This is crucial for securing sensitive data.
- **Modularity**: Explain how encapsulation enhances the modularity of the code, making it more organized and manageable.

**3. Implementing Encapsulation in Java**
- **Using Access Modifiers**: Provide a detailed explanation of different access modifiers (private, public, protected, default) and their scope.
- **Getter and Setter Methods**: Offer examples showing the creation and use of getter and setter methods for accessing private variables.
- **Immutable Classes**: Discuss the concept of immutable classes in Java (classes whose objects cannot be modified once created) as an example of encapsulation.

**4. Detailed Examples**
- **Basic Encapsulation Example**: Revisit the `Account` class example with more detailed explanations.
- **Advanced Example**: Create a more complex class, like `Employee`, that includes private fields, public getter/setter methods, and methods that manipulate the data internally.
- **Immutable Class Example**: Show an example of creating an immutable class in Java, explaining the rationale behind its design.

**5. Best Practices in Encapsulation**
- **Use private Fields**: Always start with private fields and provide public getter/setter methods if external access is necessary.
- **Validate Data**: Use setter methods to validate data before modifying any field.
- **Limit the Use of Setters**: Avoid unnecessary setter methods to keep the class' state more predictable and secure.
- **Immutable Classes for Constant Data**: Use immutable classes when an object does not need to change after it's created.
- **Minimize Class and Member Visibility**: Follow the principle of least privilege - only expose what is necessary, keep everything else private.
- **Avoid public Fields**: Public fields tend to break encapsulation and should be avoided except in certain cases (like constants).

**6. Further Reading and Resources**
- Suggest comprehensive resources for deeper understanding, like Oracle's Java documentation, relevant books, and online tutorials.

### Example: Immutable Class

```java
public final class Employee {
    private final String name;
    private final int id;

    public Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public int getId() {
        return id;
    }
}
```
In this example, `Employee` is an immutable class. The `final` keyword ensures that the class can't be extended and 
its variables can't be changed once initialized. The absence of setter methods also ensures that the state of an 
object of this class can't be altered after its creation.


### Example: Encapsulation with a `Car` Class

```java
public class Car {
    private String model;
    private int speed;
    private boolean engineOn;

    // Constructor
    public Car(String model) {
        this.model = model;
        this.speed = 0; // Initial speed is 0
        this.engineOn = false; // Engine is off initially
    }

    // Getter for model
    public String getModel() {
        return model;
    }

    // Method to turn on the engine
    public void turnEngineOn() {
        engineOn = true;
        System.out.println(model + " engine is now on.");
    }

    // Method to turn off the engine
    public void turnEngineOff() {
        engineOn = false;
        speed = 0; // Speed resets to 0 when engine is off
        System.out.println(model + " engine is now off.");
    }

    // Method to increase speed
    public void accelerate(int increment) {
        if (engineOn && increment > 0) {
            speed += increment;
            System.out.println(model + " is now going at " + speed + " km/h.");
        } else {
            System.out.println("Cannot accelerate. Either engine is off, or increment is non-positive.");
        }
    }

    // Method to apply brakes
    public void applyBrakes(int decrement) {
        if (speed > decrement && decrement > 0) {
            speed -= decrement;
            System.out.println(model + " slowed down to " + speed + " km/h.");
        } else {
            System.out.println("Cannot apply brakes. Either decrement is too high or non-positive.");
        }
    }

    // Main method for demonstration
    public static void main(String[] args) {
        Car myCar = new Car("Tesla Model S");
        myCar.turnEngineOn();
        myCar.accelerate(50);
        myCar.applyBrakes(20);
        myCar.turnEngineOff();
    }
}
```
In this `Car` class:
- The fields `model`, `speed`, and `engineOn` are private, encapsulating the state of the car.
- Public methods like `turnEngineOn`, `turnEngineOff`, `accelerate`, and `applyBrakes` provide controlled access to modify the state of the car.
- The `main` method demonstrates how an object of the `Car` class can be used.


### Recommended Resources
- [Encapsulation in Java](https://www.javatpoint.com/encapsulation)
- [What is Encapsulation in Java and How to Implement It](https://www.simplilearn.com/tutorials/java-tutorial/java-encapsulation)
- [JAVA - ENCAPSULATION](https://people.computing.clemson.edu/~yfeaste/cpsc215/cpsc2150F15/cpsc215Fall215/Notes/Tutorialspoint_webpages/24java_encapsulation.pdf)
- [Java Encapsulation](https://www.w3schools.com/java/java_encapsulation.asp)
- [Object-Oriented Programming in Java – A Beginner's Guide](https://www.freecodecamp.org/news/object-oriented-programming-concepts-java)


## Tasks

<details>
  <summary>Task 1: Create a Simple Encapsulated Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Create a Simple Encapsulated Class
## Description:
Create a class named `Book` with private fields `title` and `author`. Implement getter and setter methods for these fields.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Create an instance of `Book` and set its title to "Java Fundamentals" and author to "John Doe".

#### _Sample Output 1:_
No direct output, but the object should hold the provided data internally.

</pre>
</details>

---

<details>
  <summary>Task 2: Implement Data Validation</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Implement Data Validation
## Description:
Enhance the `Book` class by adding a page count field. Implement a setter method that validates the page count to be a positive integer before setting its value.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Set the page count to 300.

#### _Sample Output 1:_
No output, but the page count should be set correctly.

#### _Sample Input 2:_
Try setting the page count to -50.

#### _Sample Output 2:_
An error message should be displayed, and the page count should not be set.

</pre>
</details>

---

<details>
  <summary>Task 3: Design an Immutable Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Design an Immutable Class
## Description:
Create an immutable class named `Rectangle` with final fields `length` and `width`. Provide only getter methods.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Create an instance of `Rectangle` with length 5 and width 3.

#### _Sample Output 1:_
No direct output, but object state should reflect the given dimensions.

</pre>
</details>

---

<details>
  <summary>Task 4: Encapsulate a Complex Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Encapsulate a Complex Class
## Description:
Design a class `Student` with private fields `name`, `age`, and a list of grades. Provide methods to add grades and calculate the average grade.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Add grades 85, 92, and 78 to a student object.

#### _Sample Output 1:_
The average grade should be calculated and displayed.

</pre>
</details>

---

<details>
  <summary>Task 5: Control Field Access</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Control Field Access
## Description:
Create a class `Counter` with a private integer field `count`. Implement methods to increment, decrement, and retrieve the current count. Ensure that the count never falls below zero.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Increment the count three times and then decrement it two times.

#### _Sample Output 1:_
The current count should be 1.

</pre>
</details>

---

<details>
  <summary>Task 6: Encapsulating Behavior</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Encapsulating Behavior
## Description:
Create a class `Thermostat` with private fields `temperature` and `mode`. Implement methods to set the temperature within a range (e.g., 16°C to 28°C) and change the mode (e.g., "HEAT", "COOL", "OFF").

### _Inputs & Outputs:_
#### _Sample Input 1:_
Set the temperature to 21°C and mode to "HEAT".

#### _Sample Output 1:_
No direct output, but the thermostat's state should reflect these settings.

#### _Sample Input 2:_
Try setting the temperature to 35°C.

#### _Sample Output 2:_
An error message indicating the temperature is out of range.

</pre>
</details>

---

<details>
  <summary>Task 7: User Profile Management System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# User Profile Management System
## Description:
Create a class `UserProfile` that encapsulates user data such as username, email, and password. Implement methods for updating the email and password after validating them.

### User Story:
As a user, I want to be able to securely update my email and password so that my user profile stays up to date and secure.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Update the email to "newemail@example.com" and password to "NewP@ssw0rd".

#### _Sample Output 1:_
Confirmation messages indicating successful email and password updates.

#### _Sample Input 2:_
Try updating the password to "short".

#### _Sample Output 2:_
An error message indicating the password is too short.

</pre>
</details>

---

<details>
  <summary>Task 8: Bank Account Transaction System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Bank Account Transaction System
## Description:
Develop a `BankAccount` class with private fields for account balance and account holder's name. Include methods to deposit, withdraw (with balance checks), and view the current balance.

### User Story:
As an account holder, I want to securely deposit and withdraw money from my bank account and view my current balance, ensuring that my transactions are safe and my balance never becomes negative.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Deposit $200 and then withdraw $150.

#### _Sample Output 1:_
Updated balance after each transaction.

#### _Sample Input 2:_
Attempt to withdraw $300 from an account with a $250 balance.

#### _Sample Output 2:_
An error message indicating insufficient funds.

</pre>
</details>


