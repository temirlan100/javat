### Lambda expressions in Java
Lambda expressions in Java, introduced in Java 8, are a significant feature that allows you to implement functional 
programming aspects. They provide a clear and concise way to represent one method interface using an expression. 
Lambda expressions are used primarily to define inline implementation of a functional interface, i.e., an interface with a single method only.

Here's a basic structure of a lambda expression in Java:
```java
(parameters) -> expression
```
or
```java
(parameters) -> { statements; }
```

### Key Concepts:
1. **Functional Interfaces**: An interface with just one abstract method. Lambda expressions are often used to implement these interfaces.
2. **Syntax**: Consists of a set of parameters, an arrow symbol (`->`), and a body.
3. **No need for Anonymous Classes**: Lambda expressions eliminate the need for anonymous class for functional interfaces.

### Example 1: Implementing a Comparator
```java
import java.util.Arrays;
import java.util.Comparator;

public class Main {
    public static void main(String[] args) {
        String[] strings = {"One", "Two", "Three"};

        Arrays.sort(strings, (String a, String b) -> {
            return a.compareTo(b);
        });

        for(String str: strings){
            System.out.println(str);
        }
    }
}
```

### Example 2: Using with Threads
```java
public class TestLambda {
    public static void main(String args[]) {
        new Thread(() -> {
            System.out.println("New thread created");
        }).start();
    }
}
```

### Example 3: Iterating Collections
```java
import java.util.Arrays;
import java.util.List;

public class TestLambda {
    public static void main(String args[]) {
        List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7);
        list.forEach(n -> System.out.println(n));
    }
}
```

### Advantages:
- Less code.
- No need to use anonymous class.
- Functional programming style.

### Best Practices:
- Use lambda expressions if you are working with functional interfaces.
- Keep them short and self-explanatory.
- Avoid overusing them, as they can make the code less readable if used excessively.


### Lambda Expressions in an OOP Context
#### 1. Using Lambdas with Interfaces
In Java, lambda expressions are often used with functional interfaces (interfaces with a single abstract method). This is a common pattern in OOP where you use interfaces to define types and use lambda expressions to provide implementation.

**Example: Custom Functional Interface**
```java
@FunctionalInterface
interface Greeting {
    String sayHello(String name);
}

public class LambdaDemo {
    public static void main(String[] args) {
        Greeting greeting = (name) -> "Hello, " + name;

        System.out.println(greeting.sayHello("Alice"));
    }
}
```

#### 2. Lambdas in Design Patterns
Lambda expressions can be used in various design patterns, such as Strategy, Observer, or Command, to provide a more concise way to implement interfaces.

**Example: Strategy Pattern**
```java
@FunctionalInterface
interface BillingStrategy {
    double getActPrice(double rawPrice);
}

public class ShoppingCart {
    private List<Double> prices = new ArrayList<>();
    private BillingStrategy strategy;

    public ShoppingCart(BillingStrategy strategy){
        this.strategy = strategy;
    }

    public void addPrice(double price){
        prices.add(price);
    }

    public double calculateTotal(){
        return prices.stream().mapToDouble(strategy::getActPrice).sum();
    }
}

public class StrategyPatternDemo {
    public static void main(String[] args) {
        ShoppingCart cart = new ShoppingCart((price) -> price * 0.9); // 10% discount strategy
        cart.addPrice(100.0);
        System.out.println("Total: " + cart.calculateTotal());
    }
}
```

#### 3. Lambdas with Collections
In OOP, you often work with collections of objects. Lambda expressions are extremely useful for iterating, filtering, and performing operations on collections.

**Example: Filtering a Collection**
```java
class Person {
    String name;
    int age;

    // Constructor, getters, setters
}

public class OOPWithLambdas {
    public static void main(String[] args) {
        List<Person> people = Arrays.asList(new Person("Alice", 30), new Person("Bob", 25), new Person("Carol", 35));

        // Using lambda to filter and iterate
        people.stream()
              .filter(p -> p.getAge() > 30)
              .forEach(p -> System.out.println(p.getName()));
    }
}
```

### Best Practices in an OOP Context:
- Use lambda expressions to implement single-method interfaces or functional interfaces.
- Leverage lambda expressions in design patterns for concise and flexible code.
- Utilize them with collections for efficient data processing.
- Ensure lambda expressions are readable and maintainable, especially in complex class structures.


### Recommended Resources
- [Java Lambda Expressions](https://www.w3schools.com/java/java_lambda.asp)
- [Lambda Expressions](https://www.javatpoint.com/java-lambda-expressions)
- [Lambda Expression in Java](https://www.geeksforgeeks.org/lambda-expressions-java-8/)
- [Lambda Expressions by Oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html)
- [Java Lambda Expressions](https://www.programiz.com/java-programming/lambda-expression)
- [Lambda Expressions and Functional Interfaces: Tips and Best Practices](https://www.baeldung.com/java-8-lambda-expressions-tips)


## Tasks

<details>
  <summary>Task 1: Implement a Custom Comparator</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Implement a Custom Comparator
## Description:
Create a custom comparator for sorting a list of `Employee` objects by their age using a lambda expression.

### _Inputs & Outputs:_
#### _Sample Input 1:_
List of Employees: [Employee("Alice", 30), Employee("Bob", 25), Employee("Carol", 35)]

#### _Sample Output 1:_
Sorted List: [Employee("Bob", 25), Employee("Alice", 30), Employee("Carol", 35)]

</pre>
</details>

---

<details>
  <summary>Task 2: File Filtering in a Directory</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# File Filtering in a Directory
## Description:
Write a lambda expression to filter all files with a `.txt` extension in a given directory.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Directory path: "/user/docs"

#### _Sample Output 1:_
List of .txt files in the directory.

</pre>
</details>

---

<details>
  <summary>Task 3: Event Listener for a Button</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Event Listener for a Button
## Description:
Add an event listener to a GUI button using a lambda expression that prints "Button clicked!" to the console when the button is clicked.

### _Inputs & Outputs:_
#### _Sample Input 1:_
User clicks the button.

#### _Sample Output 1:_
Console: "Button clicked!"

</pre>
</details>

---

<details>
  <summary>Task 4: Process Map Entries</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Process Map Entries
## Description:
Use a lambda expression to iterate over a `Map<String, Integer>` and print each key-value pair where the value is greater than 10.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Map: {"apple": 5, "banana": 15, "cherry": 20}

#### _Sample Output 1:_
banana: 15
cherry: 20

</pre>
</details>

---

<details>
  <summary>Task 5: Sum of Numbers in a List</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Sum of Numbers in a List
## Description:
Create a lambda expression to calculate the sum of all numbers in a `List<Integer>`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
List: [1, 2, 3, 4, 5]

#### _Sample Output 1:_
Sum: 15

</pre>
</details>

---

<details>
  <summary>Task 6: Authentication Check</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Authentication Check
## Description:
Write a lambda expression to check if a given username and password are valid (for simplicity, consider valid if both are non-empty strings).

### _Inputs & Outputs:_
#### _Sample Input 1:_
Username: "admin", Password: "1234"

#### _Sample Output 1:_
Authentication: Success

#### _Sample Input 2:_
Username: "", Password: "admin"

#### _Sample Output 2:_
Authentication: Fail

</pre>
</details>

---

<details>
  <summary>Task 7: Transform Collection Elements</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Transform Collection Elements
## Description:
Write a lambda expression to transform all elements of a `List<String>` to their upper case form.

### _Inputs & Outputs:_
#### _Sample Input 1:_
List: ["apple", "banana", "cherry"]

#### _Sample Output 1:_
Transformed List: ["APPLE", "BANANA", "CHERRY"]

</pre>
</details>

---

<details>
  <summary>Task 9: Stream Operations on a Product List</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Stream Operations on a Product List
## Description:
Perform various operations on a list of products using lambda expressions and stream API. Assume each product has properties: `name` (String), `category` (String), and `price` (double).

### Subtasks:
1. **Filter Products by Category**: Write a lambda expression to filter products belonging to the category "Electronics".

   _Inputs:_ List of products.
   _Outputs:_ Filtered list of products in the "Electronics" category.

2. **Calculate Average Price**: Use a lambda expression to calculate the average price of all products.

   _Inputs:_ List of products.
   _Outputs:_ Average price.

3. **List Product Names**: Create a lambda expression to extract and collect names of all products into a new list.

   _Inputs:_ List of products.
   _Outputs:_ List of product names.

4. **Sort Products by Price**: Implement a lambda expression to sort the products by price in ascending order.

   _Inputs:_ List of products.
   _Outputs:_ List of products sorted by price.

</pre>
</details>

---

<details>
  <summary>Task 10: Lambda-Based User Interface Interactions</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Lambda-Based User Interface Interactions
## Description:
Implement various user interface interactions using lambda expressions in a hypothetical GUI application.

### Subtasks:
1. **Button Click Action**: Implement a lambda expression to handle a button click event that prints the button's label to the console.

   _Inputs:_ Button click.
   _Outputs:_ Console output of the button's label.

2. **Dynamic Menu Selection Handler**: Create a lambda expression to handle menu item selections, where each menu item's action is to display its name.

   _Inputs:_ Menu item selection.
   _Outputs:_ Display menu item name.

3. **Slider Change Listener**: Use a lambda expression to listen to changes in a slider's value and display the new value.

   _Inputs:_ Slider value change.
   _Outputs:_ Display new slider value.

4. **Form Submission Validation**: Implement a lambda expression to validate a form submission checking that no fields are empty.

   _Inputs:_ Form fields data.
   _Outputs:_ Validation result (pass/fail).

</pre>
</details>

---

<details>
  <summary>Task 11: Functional Interface Implementation</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Functional Interface Implementation
## Description:
Create and implement custom functional interfaces using lambda expressions for different scenarios.

### Subtasks:
1. **String Manipulation Interface**: Define a functional interface `StringOperation` with a method `String execute(String s)`. Implement this interface using a lambda expression that reverses the input string.

   _Inputs:_ A string.
   _Outputs:_ Reversed string.

2. **Numeric Calculation Interface**: Create a functional interface `NumericCalculation` with a method `double compute(double a, double b)`. Use a lambda expression for implementing an addition operation.

   _Inputs:_ Two double values.
   _Outputs:_ Sum of the inputs.

3. **Conditional Interface**: Define a functional interface `CheckCondition` with a method `boolean test(int n)`. Implement it using a lambda expression that checks if a number is even.

   _Inputs:_ An integer.
   _Outputs:_ `true` if even, `false` otherwise.

4. **Data Processing Interface**: Create an interface `DataProcessor` with a method `List<T> process(List<T> data)`. Implement this interface using a lambda expression that filters out null values from a list.

   _Inputs:_ List of objects (including nulls).
   _Outputs:_ List with null values removed.

</pre>
</details>



