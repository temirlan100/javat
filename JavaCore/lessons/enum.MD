### What is an Enum Class in Java?

1. **Definition**: An Enum (short for Enumeration) class in Java is a special data type that enables for a variable to be a set of predefined constants. The variable must be equal to one of the values that have been predefined for it.

2. **Characteristics**:
    - Enums are used to define a collection of constants.
    - More powerful than traditional `static final` constants.
    - An enum can have fields, methods, and constructors.

3. **Syntax**:
   ```java
   public enum Day {
       MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
   }
   ```

### How to Use Enum Class

1. **Basic Usage**:
   ```java
   Day day = Day.MONDAY;
   ```

2. **Switch Case**:
   ```java
   switch (day) {
       case MONDAY:
           System.out.println("Mondays are tough!");
           break;
       // other cases
   }
   ```

3. **Enum with Methods**:
   ```java
   public enum Day {
       MONDAY("Workday"),
       SUNDAY("Weekend");

       private final String type;

       Day(String type) {
           this.type = type;
       }

       public String getType() {
           return type;
       }
   }
   ```

4. **Iterating Over Enums**:
   ```java
   for (Day day : Day.values()) {
       System.out.println(day);
   }
   ```

### When to Use Enum Class

1. **Fixed Set of Constants**: When you have a fixed set of constants, like days of the week, months, directions, etc.

2. **Replacing Magic Numbers or Strings**: Enums can replace multiple static final constants or strings representing a limited set of options.

3. **State Machine**: When implementing state machines or status values.

4. **Singleton Implementations**: Since Enum instances are by default singletons, they can be used to implement Singleton design pattern.

5. **Type Safety**: Enums provide a type-safe way of working with a set of constants.

### Advantages of Using Enums

- **Type Safety**: Ensures that the variable can only have one of the predefined constants.
- **Readability**: Enhances the readability of your code.
- **Strongly Typed**: Enums are strongly typed, so errors are easier to detect at compile time.

### Best Practices

- Use enums when your data can only take on one of a limited set of values.
- Don't use enums for open sets of values (like customer names).
- Enums can have fields and methods, but they should be used sparingly and appropriately.

### Example Scenario

Imagine you're building an application for a coffee shop, and you need to represent the sizes of coffee cups. You can use an enum to define these sizes:

```java
public enum CoffeeSize {
    SMALL, MEDIUM, LARGE;
}
```

Then, you can use this enum to specify the size of a coffee order:

```java
CoffeeSize myCoffeeSize = CoffeeSize.MEDIUM;
```

This use of enums makes your code more readable and less prone to errors than using plain strings or numbers.

### Example Without Enum
In this example, we'll use integer constants to represent directions:

```java
public class WithoutEnumExample {
    public static final int NORTH = 0;
    public static final int EAST = 1;
    public static final int SOUTH = 2;
    public static final int WEST = 3;

    public static void navigate(int direction) {
        switch (direction) {
            case NORTH:
                System.out.println("Going North");
                break;
            case EAST:
                System.out.println("Going East");
                break;
            case SOUTH:
                System.out.println("Going South");
                break;
            case WEST:
                System.out.println("Going West");
                break;
            default:
                System.out.println("Unknown direction");
        }
    }

    public static void main(String[] args) {
        navigate(NORTH); // Correct usage
        navigate(3);     // Less readable
        navigate(7);     // Error prone, no compile-time check
    }
}
```

#### Issues with this Approach:
- **Lack of Type Safety**: Passing any integer to `navigate()` is valid at compile time, even if it doesn't represent a direction.
- **Readability**: Magic numbers (like `3` for WEST) make the code less readable.
- **Maintenance**: Adding a new direction requires changes in multiple places.

### Example With Enum

Now, let's refactor the code to use an enum for directions:

```java
public enum Direction {
    NORTH, EAST, SOUTH, WEST;
}

public class WithEnumExample {

    public static void navigate(Direction direction) {
        switch (direction) {
            case NORTH:
                System.out.println("Going North");
                break;
            case EAST:
                System.out.println("Going East");
                break;
            case SOUTH:
                System.out.println("Going South");
                break;
            case WEST:
                System.out.println("Going West");
                break;
        }
    }

    public static void main(String[] args) {
        navigate(Direction.NORTH); // Correct and readable
        // navigate(3); // Compile-time error, type safety
    }
}
```

#### Advantages of Using Enum:
- **Type Safety**: Only valid `Direction` enum values can be passed to `navigate()`.
- **Readability**: The code is more readable as `Direction.NORTH` is clearer than a magic number.
- **Maintainability**: Adding a new direction is easier and safer, as it's centralized in the `Direction` enum.

### Conclusion

Using enums in Java provides significant advantages in terms of type safety, readability, and maintainability. In scenarios where a variable represents a fixed set of constants (like directions, states, modes), enums are a superior choice compared to primitive data types like integers or strings. They prevent invalid values at compile time and make the code more expressive and less error-prone.


### Recommended Resources
- [Java Enums](https://www.w3schools.com/java/java_enums.asp)
- [Enum Types](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html)
- [A Guide to Java Enums](https://www.baeldung.com/a-guide-to-java-enums)
- [enum in Java](https://www.geeksforgeeks.org/enum-in-java/)


## Tasks

<details>
  <summary>Task 1: Creating a Basic Enum</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Creating a Basic Enum
## Description:
Create a basic enum representing days of the week.

### _Inputs & Outputs:_
#### _Task:_
Define an enum named 'Day' with constants for the seven days of the week.

#### _Sample Usage:_
Create an instance of the Day enum with the value 'MONDAY'.

</pre>
</details>

---

<details>
  <summary>Task 2: Enum in Switch Case</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Enum in Switch Case
## Description:
Use the Day enum in a switch case statement to print out a message for each day.

### _Inputs & Outputs:_
#### _Task:_
Implement a method that takes a Day enum as a parameter and uses a switch case to print out a unique message for each day.

#### _Sample Usage:_
Pass 'Day.WEDNESDAY' to your method and expect a custom message for Wednesday.

</pre>
</details>

---

<details>
  <summary>Task 3: Enum with Methods</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Enum with Methods
## Description:
Extend the Day enum to include a method that returns whether the day is a weekday or weekend.

### _Inputs & Outputs:_
#### _Task:_
Add a method 'getType()' to the Day enum that returns "Weekday" for Monday to Friday and "Weekend" for Saturday and Sunday.

#### _Sample Usage:_
Call 'Day.SATURDAY.getType()' and expect the output "Weekend".

</pre>
</details>

---

<details>
  <summary>Task 4: Enum Constructors</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Enum Constructors
## Description:
Modify the Day enum to include a constructor that accepts a string representing the type of the day (Weekday or Weekend).

### _Inputs & Outputs:_
#### _Task:_
Update the Day enum to include a private field for the type and a constructor to initialize it.

#### _Sample Usage:_
Create an instance of 'Day.MONDAY' and use a method to retrieve its type (e.g., 'getType()').

</pre>
</details>

---

<details>
  <summary>Task 5: Iterating Over Enums</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Iterating Over Enums
## Description:
Write a method to iterate over all values in the Day enum and print them.

### _Inputs & Outputs:_
#### _Task:_
Create a method that iterates over all constants in the Day enum and prints each one.

#### _Sample Output:_
The output should list all days of the week, each on a new line.

</pre>
</details>

---

<details>
  <summary>Task 6: Enums for Command Line Arguments</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Enums for Command Line Arguments
## Description:
Create an application that uses an enum to handle different command line arguments for a simple text-based menu.

### _Inputs & Outputs:_
#### _Task:_
1. Define an enum 'MenuOption' with values like START, STOP, SETTINGS, HELP.
2. Write a method that takes a string argument and uses the MenuOption enum to determine what action to perform.
3. Handle incorrect or undefined enum values gracefully.

#### _Sample Usage:_
Run your application with the command line argument 'START' and trigger the corresponding action in your program.

</pre>
</details>

---

<details>
  <summary>Task 7: Enum with Abstract Methods</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Enum with Abstract Methods
## Description:
Implement an enum representing different types of calculations (e.g., ADD, SUBTRACT, MULTIPLY, DIVIDE) and define an abstract method within the enum that each constant implements differently.

### _Inputs & Outputs:_
#### _Task:_
1. Define an enum 'Operation' with constants like ADD, SUBTRACT, MULTIPLY, DIVIDE.
2. Include an abstract method 'apply' that takes two double parameters and returns a double.
3. Each enum constant should implement the 'apply' method to perform its respective operation.

#### _Sample Usage:_
Call 'Operation.ADD.apply(10, 5)' and expect the result 15. Similarly, use other operations.

</pre>
</details>


