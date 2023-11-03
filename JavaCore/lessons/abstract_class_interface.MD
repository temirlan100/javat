### Abstract Classes in Java
#### Concept
An abstract class in Java is a class that cannot be instantiated and is used as a base for other classes. It can include both abstract methods (without an implementation) and concrete methods (with an implementation). Abstract classes are used when you want to provide a common template for derived classes, ensuring that certain methods are implemented.

#### Key Points
- Abstract classes cannot be instantiated directly.
- They can have both abstract and non-abstract methods.
- When a class inherits from an abstract class, it must implement all its abstract methods or be declared abstract itself.
- Abstract classes can have constructors and can be used in inheritance.

#### Example
```java
abstract class Animal {
    // Abstract method
    abstract void makeSound();

    // Concrete method
    public void eat() {
        System.out.println("I can eat.");
    }
}

class Dog extends Animal {
    public void makeSound() {
        // Implementing abstract method
        System.out.println("Bark bark");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.makeSound(); // Outputs: Bark bark
        myDog.eat();       // Outputs: I can eat.
    }
}
```

### Interfaces in Java
#### Concept
An interface in Java is a completely abstract class that is used to group related methods with empty bodies. Interfaces are used to achieve abstraction and multiple inheritance in Java.

#### Key Points
- Interfaces can contain only abstract methods (Java 8 onwards, they can also have default and static methods).
- Methods in an interface are implicitly public and abstract.
- A class implements an interface, inheriting the abstract methods of the interface.
- Interfaces cannot be instantiated.
- They can have constants (public static final variables).

#### Example
```java
interface Animal {
    void makeSound();
}

class Dog implements Animal {
    public void makeSound() {
        // Implementing the interface method
        System.out.println("Bark bark");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.makeSound(); // Outputs: Bark bark
    }
}
```

### Abstract Class vs. Interface

#### Differences
- **Purpose**: Abstract classes are for objects that are closely related, whereas interfaces are for capabilities that can be shared across different classes.
- **Type of methods**: Abstract classes can have a mix of methods with and without implementation, but all methods in interfaces are abstract (except default and static methods in Java 8 onwards).
- **Access Modifiers**: Interface methods are public by default, while abstract class methods can have any visibility.
- **Multiple Inheritance**: Classes can implement multiple interfaces, but they can extend only one abstract class.

#### When to Use
- Use an abstract class when creating a class hierarchy with shared code.
- Use an interface when different classes from disparate class hierarchies need to share a contract for what methods they implement.


### Advanced Concepts
#### Default Methods in Interfaces (Java 8+)
With Java 8, interfaces can have default methods with implementation. This feature helps to add new methods to interfaces without breaking the existing implementation of classes.

```java
interface Animal {
    void makeSound();

    // Default method in the interface
    default void breathe() {
        System.out.println("I can breathe.");
    }
}

class Dog implements Animal {
    public void makeSound() {
        System.out.println("Bark bark");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.makeSound(); // Outputs: Bark bark
        myDog.breathe();   // Outputs: I can breathe.
    }
}
```

#### Static Methods in Interfaces (Java 8+)
Interfaces can also have static methods that belong to the interface and not to objects of the implementing class.

```java
interface Animal {
    static void info() {
        System.out.println("I am an animal.");
    }
    void makeSound();
}

public class Main {
    public static void main(String[] args) {
        Animal.info(); // Outputs: I am an animal.
    }
}
```

### Real-world Use Cases
1. **Abstract Classes**: Often used as a base class in a hierarchy. For example, in a graphics application, you might have an abstract class `Shape` with subclasses like `Circle`, `Rectangle`, and `Triangle`.
2. **Interfaces**: Widely used for defining contracts, like `List`, `Map`, and `Set` in Java Collections Framework. They are also used in JDBC for database connections.

### Best Practices and Considerations
- **Favor Composition Over Inheritance**: Prefer using interfaces over abstract classes for greater flexibility. Java supports multiple interface implementations, overcoming the limitations of single inheritance.
- **Design**: Use interfaces to define types that can be implemented in many unrelated classes. Use abstract classes when you need to share code among closely related classes.
- **Evolution**: Adding a new method to an interface can break all implementing classes. With default methods in interfaces (Java 8+), this issue can be mitigated.

### Interface Segregation Principle (SOLID Principles)
Part of the SOLID principles of Object-Oriented Design, the Interface Segregation Principle states that clients should not be forced to depend on interfaces they do not use. This principle promotes the creation of more specific interfaces.

### Practical Tips
- Use `abstract` classes when you want to share code among several closely related classes.
- Use `interfaces` to define a role that other unrelated classes can implement.
- Abstract classes are a good choice when future versions may add new methods.
- Use interfaces to provide a layer of abstraction to your code, making it easier to refactor, change, and test your application.


### Recommended Resources
- [Java Abstraction](https://www.w3schools.com/java/java_abstract.asp)
- [Java Interface](https://www.w3schools.com/java/java_interface.asp)
- [Abstract Methods and Classes](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html)
- [Abstract class in Java](https://www.javatpoint.com/abstract-class-in-java)
- [What Is an Interface?](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html)
- [Interfaces in Java](https://www.geeksforgeeks.org/interfaces-in-java)
- [Java Interfaces](https://www.baeldung.com/java-interfaces)
- [Object-Oriented Programming in Java – A Beginner's Guide](https://www.freecodecamp.org/news/object-oriented-programming-concepts-java)


## Tasks

<details>
  <summary>Task 1: Implement an Abstract Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Implement an Abstract Class
## Description:
Create an abstract class named 'Shape' with an abstract method 'area()'. Then, create two subclasses 'Circle' and 'Rectangle' that implement the 'area' method.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Radius of Circle = 5

#### _Sample Output 1:_
Area of Circle: 78.54

#### _Sample Input 2:_
Length of Rectangle = 4, Breadth of Rectangle = 6

#### _Sample Output 2:_
Area of Rectangle: 24

</pre>
</details>

---

<details>
  <summary>Task 2: Define and Implement an Interface</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Define and Implement an Interface
## Description:
Define an interface 'Playable' with a method 'play'. Then, create two classes 'Guitar' and 'Piano' that implement this interface.

### _Inputs & Outputs:_
No specific input/output. Focus on the implementation.

</pre>
</details>

---

<details>
  <summary>Task 3: Use Default Methods in Interfaces</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Use Default Methods in Interfaces
## Description:
Modify the 'Playable' interface to include a default method 'tuneInstrument'. Implement the interface in classes 'Guitar' and 'Piano', and demonstrate the use of 'tuneInstrument'.

### _Inputs & Outputs:_
No specific input/output. Demonstrate the default method invocation.

</pre>
</details>

---

<details>
  <summary>Task 4: Abstract Class with Constructors</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Abstract Class with Constructors
## Description:
Create an abstract class 'Vehicle' with a constructor that sets the name of the vehicle. Create subclasses 'Car' and 'Bike' with their own constructors and invoke the super constructor.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Create a Car object named 'Tesla'

#### _Sample Output 1:_
Vehicle Name: Tesla

#### _Sample Input 2:_
Create a Bike object named 'Yamaha'

#### _Sample Output 2:_
Vehicle Name: Yamaha

</pre>
</details>

---

<details>
  <summary>Task 5: Multiple Interface Implementation</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Multiple Interface Implementation
## Description:
Create two interfaces, 'Flyable' and 'Swimmable'. Then, create a class 'Duck' that implements both interfaces, providing appropriate method implementations.

### _Inputs & Outputs:_
No specific input/output. Focus on implementation.

</pre>
</details>

---

<details>
  <summary>Task 6: Interface Segregation Principle</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Interface Segregation Principle
## Description:
Given a bulky interface 'SmartDevice' with methods like 'call', 'browseInternet', 'takePhoto', 'playMusic', and 'setAlarm', split it into smaller, more specific interfaces, and implement them in appropriate classes.

### _Inputs & Outputs:_
No specific input/output. Focus on splitting the interface and implementing it.

</pre>
</details>

---

<details>
  <summary>Task 7: Payment Processing System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Payment Processing System
## User Story:
As a developer for an e-commerce application, I need to create a payment processing system. This system should handle different types of payment methods like credit cards and PayPal.

## Task:
Create an abstract class `PaymentMethod` with an abstract method `processPayment(double amount)`. Implement this abstract class in `CreditCard` and `PayPal` classes, providing specific processing mechanisms.

### _Scenario:_
#### _Sample Input 1:_
Process a payment of $100 using a credit card.

#### _Sample Output 1:_
Credit card payment processed for $100.

#### _Sample Input 2:_
Process a payment of $75 using PayPal.

#### _Sample Output 2:_
PayPal payment processed for $75.

</pre>
</details>

---

<details>
  <summary>Task 8: Vehicle Telemetry System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Vehicle Telemetry System
## User Story:
As a software engineer at a vehicle manufacturing company, I need to develop a telemetry system that collects data from various types of vehicles like cars, trucks, and motorcycles.

## Task:
Create an abstract class `VehicleTelemetry` with abstract methods `collectEngineData()` and `collectTransmissionData()`. Subclass it into `CarTelemetry`, `TruckTelemetry`, and `MotorcycleTelemetry`, with specific data collection implementations.

### _Scenario:_
#### _Sample Input 1:_
Collect telemetry data from a car.

#### _Sample Output 1:_
Car engine and transmission data collected.

#### _Sample Input 2:_
Collect telemetry data from a motorcycle.

#### _Sample Output 2:_
Motorcycle engine and transmission data collected.

</pre>
</details>

---

<details>
  <summary>Task 9: Social Media Integration</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Social Media Integration
## User Story:
As a developer of a news website, I want to integrate social media sharing functionality, allowing users to share articles on different platforms like Facebook, Twitter, and LinkedIn.

## Task:
Create an interface `SocialMediaSharer` with a method `sharePost(String postContent)`. Implement this interface in classes `FacebookSharer`, `TwitterSharer`, and `LinkedInSharer`.

### _Scenario:_
#### _Sample Input 1:_
Share a post on Facebook: "New article on Java features!"

#### _Sample Output 1:_
Post shared on Facebook: "New article on Java features!"

#### _Sample Input 2:_
Share the same post on LinkedIn.

#### _Sample Output 2:_
Post shared on LinkedIn: "New article on Java features!"

</pre>
</details>

---

<details>
  <summary>Task 10: Notification System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Notification System
## User Story:
As the lead developer for a project management tool, I need to create a notification system that sends updates to users via email, SMS, and in-app notifications.

## Task:
Create an interface `Notifier` with a method `sendNotification(String message)`. Implement this interface in classes `EmailNotifier`, `SMSNotifier`, and `InAppNotifier`.

### _Scenario:_
#### _Sample Input 1:_
Send an email notification: "Your task deadline is approaching."

#### _Sample Output 1:_
Email sent: "Your task deadline is approaching."

#### _Sample Input 2:_
Send an in-app notification with the same message.

#### _Sample Output 2:_
In-app notification sent: "Your task deadline is approaching."

</pre>
</details>

---

<details>
  <summary>Task 11: Fitness Tracker Integration</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Fitness Tracker Integration
## User Story:
As a developer for a health and fitness app, I need to integrate various fitness tracking devices to sync activity data like steps walked, heart rate, and sleep patterns.

## Task:
Create an interface `FitnessTracker` with methods `syncSteps()`, `syncHeartRate()`, and `syncSleepPatterns()`. Implement this interface in classes `FitbitTracker`, `GarminTracker`, and `AppleWatchTracker`.

### _Scenario:_
#### _Sample Input 1:_
Sync data from a Fitbit device.

#### _Sample Output 1:_
Fitbit data synced: 8000 steps, 72 bpm heart rate, 7 hours sleep.

#### _Sample Input 2:_
Sync data from an Apple Watch.

#### _Sample Output 2:_
Apple Watch data synced: 10000 steps, 68 bpm heart rate, 6.5 hours sleep.

</pre>
</details>




