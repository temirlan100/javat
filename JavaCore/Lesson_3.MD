## Java Basics: `final`, Code Blocks, and Variable Scope

### 1. Constants with `final`

#### What is `final`?
In Java, the `final` keyword is used to declare that something cannot be changed. When applied to variables, it means the variable becomes a constant, and its value cannot be modified once assigned.

#### Code Example:
```java
public class FinalExample {
    public static final double PI = 3.141592653589793;

    public static void main(String[] args) {
        System.out.println("Value of PI: " + PI);
        // Uncommenting the next line will cause a compile error
        // PI = 3.14;
    }
}
```

#### Deep Dive:
- A `final` variable must be initialized when it's declared if it's an instance or static variable.
- Local `final` variables (inside methods) can be assigned later but only once.
- The `final` keyword can also be used with classes to prevent inheritance and with methods to prevent overriding.

### 2. Code Blocks and Variable Scope

#### What is a Code Block?
In Java, a code block is a section of code enclosed by curly braces `{}`. It can define the body of a method, constructor, or a local block within methods.

#### What is Variable Scope?
The scope of a variable refers to the region of the code where the variable can be accessed or modified.

#### Code Example:
```java
public class ScopeExample {
    private int classLevelVariable = 5;

    public void demonstrateScope() {
        int methodLevelVariable = 10;
        System.out.println("Class Level: " + classLevelVariable);
        System.out.println("Method Level: " + methodLevelVariable);

        {
            int blockLevelVariable = 15;
            System.out.println("Block Level: " + blockLevelVariable);
        }

        // Uncommenting the next line will cause a compile error
        // System.out.println(blockLevelVariable);
    }

    public static void main(String[] args) {
        ScopeExample example = new ScopeExample();
        example.demonstrateScope();
    }
}
```

#### Deep Dive in future:
- **Class-Level Scope (Instance Variables):** Variables declared inside a class but outside any method. They can be accessed by any method within the class.
- **Method-Level Scope (Local Variables):** Variables declared within a method. They're accessible only within that method.
- **Block-Level Scope:** Variables declared inside a specific block of code. Their scope is limited to that block.

### Recommended Resources
- [Final keyword](https://www.geeksforgeeks.org/final-keyword-in-java/)
- [Final keyword](https://www.javatpoint.com/final-keyword)
- [Java final keyword](https://www.w3schools.com/java/ref_keyword_final.asp)
- [Java variable scope](https://coderslegacy.com/java/java-variable-scope/)
- [Java scope](https://www.w3schools.com/java/java_scope.asp)

## Tasks
<details>
  <summary>Task 1</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Final Value Holder**
## **Description:**
Write a Java program that stores a `final` value for the speed of light (299,792,458 meters per second). The program should display this value when run.
### _Input:_
None (since the value is a constant).
### _Output:_
Speed of Light: 299,792,458 m/s

</pre>
</details>

---

<details>
  <summary>Task 2</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Block Scope Identifier**
## **Description:**
Write a Java program that has a main method with a variable called `outsideBlock`. Inside the main method, define a code block with a variable named `insideBlock`. Display both variables before and after the code block.
### _Input:_
None (you're simply initializing and displaying variables).
### _Output:_
Outside Variable (before block): [value]
Inside Block Variable: [value]
Outside Variable (after block): [value]

</pre>
</details>

---

<details>
  <summary>Task 3</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Temperature Converter**
## **Description:**
Write a Java program that converts a given temperature in Fahrenheit to Celsius. Use a `final` variable to store the conversion factor.
### _Input:_
98.6 (Fahrenheit value)
### _Output:_
Body temperature in Celsius: 37°C

</pre>
</details>
