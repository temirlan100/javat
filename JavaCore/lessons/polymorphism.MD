### Understanding Polymorphism

Polymorphism in Java refers to the ability of a single method to operate on objects of different classes. 
It's a concept where one interface can be used for a general class of actions. The specific action is determined by 
the exact nature of the situation.

There are two types of polymorphism in Java:
1. **Compile-time Polymorphism (Static Binding)**: This is achieved by method overloading and operator overloading. However, Java doesn't support operator overloading.
2. **Run-time Polymorphism (Dynamic Binding)**: This is achieved by method overriding, which occurs in the context of inheritance.

### Compile-time Polymorphism
Compile-time polymorphism is achieved when multiple methods have the same name but different parameters (number, types, or order of parameters).

**Example:**
```java
class Adder {
    static int add(int a, int b) {
        return a + b;
    }
    static double add(double a, double b) {
        return a + b;
    }
}

public class TestPolymorphism {
    public static void main(String[] args) {
        System.out.println(Adder.add(5, 6));       // Calls the first add method
        System.out.println(Adder.add(5.0, 6.0));   // Calls the second add method
    }
}
```

### Run-time Polymorphism
Run-time polymorphism is achieved by method overriding, where a subclass provides a specific implementation of a method that is already provided by one of its superclasses.

**Example:**
```java
class Animal {
    void sound() {
        System.out.println("The animal makes a sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("The dog barks");
    }
}

public class TestPolymorphism {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        Animal myDog = new Dog();
        
        myAnimal.sound();   // Outputs: The animal makes a sound
        myDog.sound();      // Outputs: The dog barks
    }
}
```

In the above example, even though `myDog` is of type `Animal`, it uses the `sound` method of the `Dog` class because 
it was overridden.

### Key Points
- Polymorphism allows for flexibility and loose coupling in code.
- The `instanceof` keyword can be used to test whether an object is an instance of a specific class or subclass.
- Polymorphism can be achieved with abstract classes and interfaces.


### Recommended Resources
- [Polymorphism in Java with Examples](https://www.mygreatlearning.com/blog/polymorphism-in-java/#:~:text=Polymorphism%20in%20Java%20is%20the,instance%2C%20is%20one%20such%20language.)
- [Java Polymorphism](https://www.w3schools.com/java/java_polymorphism.asp)
- [Polymorphism in Java](https://www.geeksforgeeks.org/polymorphism-in-java)
- [Polymorphism](https://www.javatpoint.com/runtime-polymorphism-in-java)
- [What Is Polymorphism in Java?](https://blog.hubspot.com/website/polymorphism-java)
- [Polymorphism documentation](https://docs.oracle.com/javase/tutorial/java/IandI/polymorphism.html)
- [Object-Oriented Programming in Java – A Beginner's Guide](https://www.freecodecamp.org/news/object-oriented-programming-concepts-java)


## Tasks

<details>
  <summary>Task 1: Method Overloading</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Method Overloading
## Description:
Create a class 'Multiplier' that has several 'multiply' methods with different parameter lists (overloaded methods) to multiply two integers, two doubles, and one double and one integer.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Multiplier.multiply(3, 4)

#### _Sample Output 1:_
12

#### _Sample Input 2:_
Multiplier.multiply(2.5, 3.0)

#### _Sample Output 2:_
7.5

</pre>
</details>

---

<details>
  <summary>Task 2: Method Overriding</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Method Overriding
## Description:
Create a superclass 'Shape' with a method 'draw()' and subclasses 'Circle' and 'Rectangle' that override the 'draw()' method to print the shape being drawn.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Shape shape = new Circle();
shape.draw();

#### _Sample Output 1:_
Drawing Circle

#### _Sample Input 2:_
Shape shape = new Rectangle();
shape.draw();

#### _Sample Output 2:_
Drawing Rectangle

</pre>
</details>

---

<details>
  <summary>Task 3: Runtime Polymorphism with Inheritance</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Runtime Polymorphism with Inheritance
## Description:
Create a base class 'Bank' with a method 'getInterestRate()' and derived classes 'BankA', 'BankB', and 'BankC' that override the method to provide specific interest rates.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Bank bank = new BankA();
bank.getInterestRate();

#### _Sample Output 1:_
2.5% (Assuming BankA offers a 2.5% interest rate)

#### _Sample Input 2:_
Bank bank = new BankB();
bank.getInterestRate();

#### _Sample Output 2:_
3.0% (Assuming BankB offers a 3.0% interest rate)

</pre>
</details>

---

<details>
  <summary>Task 4: Abstract Class and Polymorphism</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Abstract Class and Polymorphism
## Description:
Create an abstract class 'Device' with an abstract method 'start()'. Create concrete classes 'Computer' and 'Smartphone' that extend 'Device' and implement the 'start()' method.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Device device = new Computer();
device.start();

#### _Sample Output 1:_
Computer is starting

#### _Sample Input 2:_
Device device = new Smartphone();
device.start();

#### _Sample Output 2:_
Smartphone is starting

</pre>
</details>

---

<details>
  <summary>Task 5: Interface Polymorphism</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Interface Polymorphism
## Description:
Create an interface 'Animal' with a method 'makeSound()'. Create classes 'Dog' and 'Cat' that implement the 'Animal' interface and provide their versions of 'makeSound()'.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Animal animal = new Dog();
animal.makeSound();

#### _Sample Output 1:_
Bark

#### _Sample Input 2:_
Animal animal = new Cat();
animal.makeSound();

#### _Sample Output 2:_
Meow

</pre>
</details>

---

<details>
  <summary>Task 6: Polymorphic Arrays</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Polymorphic Arrays
## Description:
Create an array of 'Animal' objects where each array element can hold different types of animals like 'Dog', 'Cat', etc. Iterate over the array and invoke the 'makeSound()' method for each animal.

### _Inputs & Outputs:_
#### _No Sample Input (This task is about creating and executing a polymorphic array)_

#### _Sample Output:_
Bark
Meow
[...outputs depend on the animals added to the array...]

</pre>
</details>

---

<details>
  <summary>Task 7: Payment Processing System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Payment Processing System
## Description:
Design a simple payment processing system where you have a base class `Payment` with a method `processPayment()`. Subclasses `CreditCardPayment`, `PaypalPayment`, and `BankTransferPayment` should override this method to provide specific processing mechanisms.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Payment payment = new CreditCardPayment(100.00);
payment.processPayment();

#### _Sample Output 1:_
Processing credit card payment for $100.00

#### _Sample Input 2:_
Payment payment = new PaypalPayment(75.50);
payment.processPayment();

#### _Sample Output 2:_
Processing PayPal payment for $75.50

</pre>
</details>

---

<details>
  <summary>Task 8: Event Notification System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Event Notification System
## Description:
Create an event notification system where you have an interface `Notifier` with a method `sendNotification()`. Classes `EmailNotifier`, `SMSNotifier`, and `PushNotifier` implement the `Notifier` interface to send notifications through their respective channels.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Notifier notifier = new EmailNotifier("user@example.com", "Server Down");
notifier.sendNotification();

#### _Sample Output 1:_
Sending email to user@example.com with message: Server Down

#### _Sample Input 2:_
Notifier notifier = new SMSNotifier("+123456789", "Balance Low");
notifier.sendNotification();

#### _Sample Output 2:_
Sending SMS to +123456789 with message: Balance Low

</pre>
</details> 

