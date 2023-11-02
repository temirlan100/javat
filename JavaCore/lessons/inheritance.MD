## Module: Inheritance in Java

### Introduction to Inheritance
- **Definition**: Inheritance is a mechanism in Java where one class acquires the properties (fields) and behaviors (methods) of another class. It supports the concept of hierarchical classification.
- **Key Terms**: Base class (or parent class), Derived class (or child class), `extends` keyword.

### Why Use Inheritance?
- **Code Reusability**: Inheritance supports the reuse of existing code.
- **Method Overriding**: Child classes can override methods of the parent class.

### Basic Syntax
- Demonstrate how to declare a class that inherits from another class using the `extends` keyword.

    ```java
    class ParentClass {
        // ...
    }

    class ChildClass extends ParentClass {
        // ...
    }
    ```

### Types of Inheritance in Java
- Single Inheritance
- Multilevel Inheritance
- Hierarchical Inheritance
- (Note: Java does not support multiple inheritance with classes. It uses interfaces to achieve it.)

### Single Inheritance
- Explain with a simple example where one class inherits from another class.

    ```java
    class Animal {
        void eat() {
            System.out.println("Eating...");
        }
    }

    class Dog extends Animal {
        void bark() {
            System.out.println("Barking...");
        }
    }
    ```

### Multilevel Inheritance
- Describe inheritance involving more than two levels.

    ```java
    class Animal { ... }
    
    class Dog extends Animal { ... }

    class BabyDog extends Dog {
        void weep() {
            System.out.println("Weeping...");
        }
    }
    ```

### Hierarchical Inheritance
- Explain with an example where one class serves as a base class for more than one derived class.

    ```java
    class Animal { ... }

    class Dog extends Animal { ... }

    class Cat extends Animal {
        void meow() {
            System.out.println("Meowing...");
        }
    }
    ```

### Method Overriding
- **Concept**: When a method in a subclass has the same name, return type, and arguments as a method in its superclass, it's known as method overriding.
- **Rules and Concepts**:
    - `@Override` annotation.
    - Method overriding vs method overloading.
    - `super` keyword to call superclass methods.

    ```java
    class Animal {
        void sound() {
            System.out.println("Some sound...");
        }
    }

    class Dog extends Animal {
        @Override
        void sound() {
            System.out.println("Bark");
        }
    }
    ```

### The `super` Keyword

- Use of `super` to invoke parent class constructor and methods.
- Example to illustrate the use of `super`.

    ```java
    class Animal {
        Animal() {
            System.out.println("Animal is created");
        }
    }

    class Dog extends Animal {
        Dog() {
            super();
            System.out.println("Dog is created");
        }
    }
    ```

### Constructor Chaining
- **Definition**: Constructor chaining is the process of calling one constructor from another constructor with respect to current object creation.
- **How it Works**:
    - In Java, when a subclass is instantiated, the constructors of all superclasses must be called. This starts with the topmost superclass and moves down the hierarchy.
    - By default, the no-argument constructor of the superclass is called. If the superclass doesn't have a no-argument constructor, you must explicitly call a different constructor using `super`.

    ```java
    class Base {
        Base(int x) {
            System.out.println("Base Constructor Called with value: " + x);
        }
    }

    class Derived extends Base {
        Derived() {
            super(10); // Calling superclass constructor explicitly
            System.out.println("Derived Constructor Called");
        }
    }
    ```

    - In this example, creating an instance of `Derived` will first call the constructor of `Base` with the argument `10`.

### Protected Members
- **Definition & Usage**:
    - The `protected` access level in Java sits between `private` and `public`. It makes a member accessible within its own package (like default access) and also to subclasses, even if they are in different packages.
- **Importance in Inheritance**:
    - Protected members are often used in superclass-subclass relationships.
    - This access level helps maintain encapsulation while still allowing inheritance-related classes to share common functionality or data.

    ```java
    class Parent {
        protected int value = 10;
        protected void display() {
            System.out.println("Value: " + value);
        }
    }

    class Child extends Parent {
        void test() {
            display(); // Accessing protected method
        }
    }
    ```

    - Here, the `Child` class can access the protected method `display()` from the `Parent` class.

### Inheritance and Polymorphism
- **Polymorphism Definition**: Polymorphism is a concept where an object can take on many forms. The most common use of polymorphism in OOP is when a parent class reference is used to refer to a child class object.
- **How Inheritance Enables Polymorphism**:
    - **Method Overriding**: Through inheritance, a subclass can override methods of its superclass. This allows different subclasses to provide specific implementations for the same method defined in the superclass.
    - **Dynamic Method Dispatch**: It's the mechanism by which a call to an overridden method is resolved at runtime rather than compile-time. This is a crucial aspect of polymorphism in Java.

    ```java
    class Animal {
        void sound() {
            System.out.println("Animal makes a sound");
        }
    }

    class Dog extends Animal {
        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

    class Main {
        public static void main(String args[]) {
            Animal a = new Dog(); // Polymorphism
            a.sound(); // Outputs: Dog barks
        }
    }
    ```
In this example, even though the reference is of type `Animal`, it refers to an instance of `Dog`, and the `Dog`'s `sound` method is called.


### Understanding `this` and `super` Keywords
#### The `this` Keyword

- **Usage**: The `this` keyword in Java is a reference variable that refers to the current object.
- **Purposes**:
    1. **Differentiate Between Instance Variables and Parameters**: If the instance variables and parameters of a method have the same name, `this` can be used to distinguish between them.
    2. **Invoke Current Class Constructor**: Useful in constructor chaining within the same class.
    3. **Pass an Instance as an Argument**: `this` can be passed as an argument in method calls.
    4. **Return the Current Class Instance**: A method can return `this` to return the current class instance.

    ```java
    class Box {
        int width;
        int height;

        Box(int width, int height) {
            this.width = width; // Refers to instance variable width
            this.height = height; // Refers to instance variable height
        }

        void displayDimensions() {
            System.out.println("Width: " + width + ", Height: " + height);
        }
    }
    ```

#### The `super` Keyword
- **Usage**: The `super` keyword in Java is a reference variable used to refer to the immediate parent class object.
- **Purposes**:
    1. **Accessing Parent Class Methods**: To call methods of the parent class when overridden in the child class.
    2. **Accessing Parent Class Constructor**: To explicitly call a parent class constructor from a child class.

    ```java
    class Parent {
        Parent() {
            System.out.println("Parent Constructor");
        }

        void display() {
            System.out.println("Parent Display");
        }
    }

    class Child extends Parent {
        Child() {
            super(); // Calls the constructor of Parent class
            System.out.println("Child Constructor");
        }

        void display() {
            super.display(); // Calls display method of Parent class
            System.out.println("Child Display");
        }
    }
    ```

### Examples Demonstrating `this` and `super`
#### Example Using `this`
```java
class Rectangle {
    private int length;
    private int breadth;

    Rectangle(int length, int breadth) {
        this.length = length; // Using 'this' to refer to instance variables
        this.breadth = breadth;
    }

    int area() {
        return this.length * this.breadth; // Optional use of 'this' here
    }

    // Method that returns current class instance
    Rectangle get() {
        return this;
    }
}
```

#### Example Using `super`
```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void eat() {
        System.out.println("Dog is eating");
    }

    void anotherEat() {
        super.eat(); // Using 'super' to call the eat method of Animal class
    }
}

class TestInheritance {
    public static void main(String args[]) {
        Dog d = new Dog();
        d.eat(); // Calls Dog's eat method
        d.anotherEat(); // Calls Animal's eat method
    }
}
```



### Recommended Resources
- [Java Inheritance](https://www.w3schools.com/java/java_inheritance.asp)
- [Inheritance in Java](https://www.geeksforgeeks.org/inheritance-in-java)
- [Inheritance](https://www.javatpoint.com/inheritance-in-java)
- [The Java Platform Class Hierarchy](https://docs.oracle.com/javase/tutorial/java/IandI/subclasses.html)
- [Object-Oriented Programming in Java – A Beginner's Guide](https://www.freecodecamp.org/news/object-oriented-programming-concepts-java)


## Tasks

<details>
  <summary>Task 1: Implement Single Inheritance</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Implement Single Inheritance
## Description:
Create a simple single inheritance structure where a `Vehicle` class is the superclass and a `Car` class is the subclass. Implement a method in each class: `Vehicle` should have a `move()` method and `Car` should have a `honk()` method.

### _Inputs & Outputs:_
#### _Sample Input 1:_
No input required.

#### _Sample Output 1:_
Vehicle is moving...
Car is honking...

</pre>
</details>

---

<details>
  <summary>Task 2: Hierarchical Inheritance</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Hierarchical Inheritance
## Description:
Implement hierarchical inheritance with a base class `Animal` and two subclasses `Dog` and `Cat`. Each subclass should override a method `sound()` from `Animal` to print respective sounds.

### _Inputs & Outputs:_
#### _Sample Input 1:_
No input required.

#### _Sample Output 1:_
Dog barks
Cat meows

</pre>
</details>

---

<details>
  <summary>Task 3: Multilevel Inheritance</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Multilevel Inheritance
## Description:
Create a multilevel inheritance structure with three classes: `Shape`, `TwoDimensionalShape`, and `Circle`. `TwoDimensionalShape` should inherit from `Shape`, and `Circle` should inherit from `TwoDimensionalShape`. Add relevant methods to each class.

### _Inputs & Outputs:_
#### _Sample Input 1:_
radius = 5

#### _Sample Output 1:_
Shape is created
2D shape is created
Circle with radius 5 is created

</pre>
</details>

---

<details>
  <summary>Task 4: Constructor Chaining</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Constructor Chaining
## Description:
Demonstrate constructor chaining in inheritance by creating two classes: `BaseClass` and `DerivedClass`. Each class should have a constructor which prints a message when it is called. Show how the constructors are called in the inheritance chain.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Create an instance of `DerivedClass`.

#### _Sample Output 1:_
BaseClass constructor called
DerivedClass constructor called

</pre>
</details>

---

<details>
  <summary>Task 5: Method Overriding and `super` Keyword</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Method Overriding and `super` Keyword
## Description:
Create a class `Parent` with a method `show()`. Then create a class `Child` which extends `Parent` and overrides the `show()` method. In the `Child`'s `show()` method, use the `super` keyword to call the `show()` method of the `Parent` class before executing its own code.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Call `show()` on an instance of `Child`.

#### _Sample Output 1:_
Parent's show()
Child's show()

</pre>
</details>

---

<details>
  <summary>Task 6: Dynamic Method Dispatch and Polymorphism</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">
Dynamic Method Dispatch and Polymorphism
Description:
Create a superclass Bank with a method getInterestRate() that returns a default interest rate value. Derive multiple subclasses like SavingsBank, CurrentBank, and InvestmentBank, each overriding getInterestRate() with specific values. Demonstrate dynamic method dispatch by referring to subclass objects with a Bank reference and calling getInterestRate().

Inputs & Outputs:
Sample Input 1:
Bank reference to a SavingsBank object.

Sample Output 1:
Interest Rate: 4%

Sample Input 2:
Bank reference to an InvestmentBank object.

Sample Output 2:
Interest Rate: 6%

</pre>
</details>

---

<details>
  <summary>Task 7: Inheritance with Overloaded Methods</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Inheritance with Overloaded Methods
## Description:
Create a class `Shape` with overloaded methods `draw()` that take different parameters (like no parameters, one integer parameter for radius, two integer parameters for length and breadth, etc.). Then, create a subclass `ColoredShape` that inherits from `Shape` and adds a color attribute. Override one of the `draw()` methods to include color information in the output.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Draw a shape with no parameters in `ColoredShape`.

#### _Sample Output 1:_
Drawing Shape

#### _Sample Input 2:_
Draw a colored shape (e.g., red) with one parameter (radius) in `ColoredShape`.

#### _Sample Output 2:_
Drawing Red Circle with radius 5

</pre>
</details>

---

<details>
  <summary>Task 8: Using `super` in Subclass Constructors</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Using `super` in Subclass Constructors
## Description:
Create a superclass `Person` with attributes like name and age, and a corresponding constructor. Create a subclass `Employee` which adds an employee ID and its constructor. Use `super` in `Employee`'s constructor to invoke `Person`'s constructor and ensure all attributes are properly initialized.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Create an `Employee` object with name 'Alice', age 30, and ID 'E123'.

#### _Sample Output 1:_
Employee Details - Name: Alice, Age: 30, ID: E123

</pre>
</details>

---

<details>
  <summary>Task 9: Inheritance and Method Overriding</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Inheritance and Method Overriding
## Description:
Create a class `Vehicle` with a method `fuelEfficiency()`. Create two subclasses, `Car` and `Bike`, which override the `fuelEfficiency()` method to return specific values for each. Demonstrate method overriding by creating instances of `Car` and `Bike` and calling their `fuelEfficiency()` methods.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Call `fuelEfficiency()` on an instance of `Car`.

#### _Sample Output 1:_
Car Fuel Efficiency: 15 km/l

#### _Sample Input 2:_
Call `fuelEfficiency()` on an instance of `Bike`.

#### _Sample Output 2:_
Bike Fuel Efficiency: 40 km/l

</pre>
</details>



