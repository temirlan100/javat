### Overview of Inner Classes in Java

Inner classes in Java are defined within the scope of another class. They are useful for logically grouping classes that are only used in one place, increasing encapsulation, and creating more readable and maintainable code.

There are four types of inner classes in Java:

1. **Member Inner Class:** A non-static class that is created inside a class but outside a method.
2. **Static Inner Class:** Similar to the member inner class but is static and cannot access non-static members of the outer class directly.
3. **Local Inner Class:** Class defined within a block or method.
4. **Anonymous Inner Class:** An inner class without a name and for which only a single object is created.

### Educational Material with Examples

#### 1. Member Inner Class

```java
class OuterClass {
    private String message = "Hello from Outer Class";

    class InnerClass {
        void display() {
            System.out.println(message); // Accessing outer class member
        }
    }

    public void callInner() {
        InnerClass inner = new InnerClass();
        inner.display();
    }
}

public class Main {
    public static void main(String[] args) {
        OuterClass outer = new OuterClass();
        outer.callInner(); // Displays: Hello from Outer Class
    }
}
```

#### 2. Static Inner Class

```java
class OuterClass {
    private static String staticMessage = "Hello from Static Inner Class";

    static class StaticInner {
        void display() {
            System.out.println(staticMessage); // Accessing static member of outer class
        }
    }
}

public class Main {
    public static void main(String[] args) {
        OuterClass.StaticInner inner = new OuterClass.StaticInner();
        inner.display(); // Displays: Hello from Static Inner Class
    }
}
```

#### 3. Local Inner Class

```java
class OuterClass {

    void outerMethod() {
        class LocalInner {
            void display() {
                System.out.println("Inside local inner class");
            }
        }
        LocalInner localInner = new LocalInner();
        localInner.display(); // Inside local inner class
    }
}

public class Main {
    public static void main(String[] args) {
        OuterClass outer = new OuterClass();
        outer.outerMethod();
    }
}
```

#### 4. Anonymous Inner Class

```java
interface Message {
    void display();
}

class OuterClass {

    public void method() {
        Message message = new Message() {
            public void display() {
                System.out.println("Hello from Anonymous Inner Class");
            }
        };
        message.display(); // Hello from Anonymous Inner Class
    }
}

public class Main {
    public static void main(String[] args) {
        OuterClass outer = new OuterClass();
        outer.method();
    }
}
```

### Usage Tips
- Inner classes are useful when a class is only useful to one other class. They help to logically group classes and control the visibility of variables and methods.
- They can lead to more readable and maintainable code by encapsulating the functionality within the outer class.
- However, overusing them can make the code more complex and harder to read, so it's important to use them judiciously.


### Recommended Resources
- [Nested Classes](https://docs.oracle.com/javase/tutorial/java/javaOO/nested.html#:~:text=it%20is%20used.-,Inner%20Classes,define%20any%20static%20members%20itself.)
- [Java Inner Classes](https://www.w3schools.com/java/java_inner_classes.asp)
- [Inner Classes (Nested Classes)](https://www.javatpoint.com/java-inner-class)
- [Java - Inner classes](https://www.tutorialspoint.com/java/java_innerclasses.htm)
- [Inner Class in Java](https://www.geeksforgeeks.org/inner-class-java)


## Tasks

<details>
  <summary>Task 1: Create a Member Inner Class</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Create a Member Inner Class
## Description:
Create a member inner class named 'Inner' within a public class 'Outer'. The inner class should have a method `display()` that prints "Inner class called." Create an instance of the inner class within the outer class and call `display()` method.

### _Inputs & Outputs:_
#### _Sample Input 1:_
No input required.

#### _Sample Output 1:_
Inner class called.

</pre>
</details>

---

<details>
  <summary>Task 2: Static Inner Class with Static Method</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Static Inner Class with Static Method
## Description:
Create a static inner class named 'StaticInner' inside a class 'Outer'. The static inner class should contain a static method `sayHello()` that returns "Hello from Static Inner Class!" Access this method from a main method without creating an instance of 'Outer'.

### _Inputs & Outputs:_
#### _Sample Input 1:_
No input required.

#### _Sample Output 1:_
Hello from Static Inner Class!

</pre>
</details>

---

<details>
  <summary>Task 3: Local Inner Class in a Method</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Local Inner Class in a Method
## Description:
In a class 'LocalOuter', define a method 'localInnerDemo()' which contains a local inner class named 'LocalInner'. The local inner class should have a method `showMessage()` that prints "Local Inner Class Message." Call this method from within 'localInnerDemo()'.

### _Inputs & Outputs:_
#### _Sample Input 1:_
No input required.

#### _Sample Output 1:_
Local Inner Class Message.

</pre>
</details>

---

<details>
  <summary>Task 4: Anonymous Inner Class Implementing an Interface</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Anonymous Inner Class Implementing an Interface
## Description:
Create an interface 'Greeting' with a method `sayHello()`. In a class 'AnonymousDemo', create an anonymous inner class that implements 'Greeting', overriding `sayHello()` to return "Hello from Anonymous Inner Class!" Print the result of `sayHello()` in the main method.

### _Inputs & Outputs:_
#### _Sample Input 1:_
No input required.

#### _Sample Output 1:_
Hello from Anonymous Inner Class!

</pre>
</details>

---

<details>
  <summary>Task 5: Accessing Outer Class Variables</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Accessing Outer Class Variables
## Description:
Create a class 'Outer' with a private variable `privateString` initialized to "Accessed from Inner Class". Inside it, create a member inner class 'Inner' with a method `accessOuter()` which prints the value of `privateString` from the outer class.

### _Inputs & Outputs:_
#### _Sample Input 1:_
No input required.

#### _Sample Output 1:_
Accessed from Inner Class.

</pre>
</details>

---

