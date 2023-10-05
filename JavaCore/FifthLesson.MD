## `switch` Operator in Java
The `switch` operator is a decision-making statement in Java that selects one of many code blocks to be executed based on the value of an expression.

### Syntax
The basic syntax of the `switch` statement is as follows:

```java
switch (expression) {
    case value1:
        // code block 1
        break;
    case value2:
        // code block 2
        break;
    ...
    default:
        // default code block
}
```

### How It Works
1. The `expression` inside the `switch` is evaluated once.
2. The value of the `expression` is compared with the values of each `case`.
3. If there is a match, the corresponding block of code is executed.
4. The `break` keyword is used to exit the switch block. If omitted, the program will continue to the next case (known as "fallthrough").
5. If no matching cases are found, the code under `default` is executed.

### Important Points
- The `expression` used in the `switch` statement must yield a value of either `char`, `byte`, `short`, `int`, `enum`, or `String`.
- Every `case` label should have a unique value within the same switch.
- The `break` keyword breaks out of the switch block. If omitted, execution will continue with the next case or default, causing a fallthrough.
- The `default` case is optional and can be omitted. It is executed when no case matches the evaluated expression.

### Examples

#### Using `int` with `switch`
```java
int day = 3;
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    default:
        System.out.println("Another day");
}
```
Output:
```
Wednesday
```

#### Using `String` with `switch`
```java
String fruit = "apple";
switch (fruit) {
    case "apple":
        System.out.println("It's an apple!");
        break;
    case "banana":
        System.out.println("It's a banana!");
        break;
    default:
        System.out.println("Not sure what fruit it is.");
}
```
Output:
```
It's an apple!
```

### Multi-Cases (Grouped Cases)
In Java, it's possible to group multiple `case` labels together if they share the same code block. This is particularly useful when multiple inputs should result in the same output or action.

#### Example using Multi-Cases:
```java
int number = 5;

switch (number) {
    case 1:
    case 3:
    case 5:
    case 7:
    case 9:
        System.out.println("The number is odd.");
        break;
    case 2:
    case 4:
    case 6:
    case 8:
    case 10:
        System.out.println("The number is even.");
        break;
    default:
        System.out.println("Number not recognized.");
}
```

Output:
```
The number is odd.
```
In this example, the same code block is executed for any odd number between 1 and 9 (and similarly for even numbers). 
By grouping these `case` labels, we avoid duplicating the code block for each individual case.

### Conclusion
The `switch` operator provides an efficient way to compare a value with multiple possibilities. It offers a cleaner 
and more readable alternative to a chain of `if-else` statements, especially when dealing with a finite set of known values.

### Recommended Resources
- [The switch Statement](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/switch.html)
- [Java Switch](https://www.w3schools.com/java/java_switch.asp)
- [Java switch Statement](https://www.programiz.com/java-programming/switch-statement#google_vignette)
- [Java Switch Statement 2](https://www.javatpoint.com/java-switch)
- [Switch Statement in Java](https://www.geeksforgeeks.org/switch-statement-in-java)


## Tasks

<details>
  <summary>Task 1</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">
# **Temperature Converter**
## **Description:**
Write a Java program that converts temperatures between Fahrenheit and Celsius.
The user should be able to choose the conversion direction (from Fahrenheit to Celsius or from Celsius to Fahrenheit)
and then input the temperature value. The program should then display the converted temperature.
### _Input:_
FtoC  
98.6
### _Output:_
The temperature in Celsius is 37.00°C.
</pre>
</details>

---

<details>
  <summary>Task 2</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Day Name Finder**
## **Description:**
Write a Java program that accepts a number (1 to 7) and outputs the corresponding day of the week. If the number is not between 1 and 7, it should print "Invalid number".
### _Input:_
5
### _Output:_
Thursday
</pre>
</details>

---

<details>
  <summary>Task 3</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Grade Interpreter**
## **Description:**
Write a Java program that accepts a letter grade (A, B, C, D, F) and outputs the corresponding interpretation. Use the following interpretations: A (Excellent), B (Good), C (Average), D (Poor), F (Fail).
### _Input:_
B
### _Output:_
Good
</pre>
</details>

---

<details>
  <summary>Task 4</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Month Days Finder**
## **Description:**
Write a Java program that accepts the name of a month and outputs the number of days in that month. Assume February has 28 days for simplicity.
### _Input:_
April
### _Output:_
April has 30 days.
</pre>
</details>

---

<details>
  <summary>Task 5</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Currency Converter**
## **Description:**
Write a Java program that converts a given amount from one currency to another. The user should be able to select the source and target currency from USD, EUR, GBP, JPY, and AUD. Use static conversion rates for simplicity. If the user enters an invalid currency code, display an appropriate error message.
### _Input:_
USD  
EUR  
50
### _Output:_
Converted amount: 45.00 EUR
### Note: Use static conversion rates such as 1 USD = 0.9 EUR for simplicity.
</pre>
</details>

---

<details>
  <summary>Task 6</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Roman Numeral Converter**
## **Description:**
Write a Java program that takes an integer between 1 and 10 and converts it into its corresponding Roman numeral. If the user enters a number outside this range, display an error message.
### _Input:_
7
### _Output:_
VII
</pre>
</details>

---

<details>
  <summary>Task 7</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Zodiac Sign Finder**
## **Description:**
Write a Java program where the user provides their birth month and day, and the program determines their zodiac sign. If the user provides an invalid month or day, display an error message.
### _Input:_
March  
21
### _Output:_
Your zodiac sign is Aries.
</pre>
</details>

---

<details>
  <summary>Task 8</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Advanced Calculator**
## **Description:**
Design a Java program that performs advanced mathematical operations like addition, subtraction, multiplication, division, and modular operations. The program should allow the user to select a specific operation, then input two numbers, and finally display the result. Additionally:

- Ensure you handle the division by zero scenario gracefully.
- For the modular operation, ensure both numbers are integers. If not, display an appropriate message.
- If the user selects an invalid operation, show an error message.

### _Input:_
Addition  
5.2  
2.3
### _Output:_
Result: 7.5

### _Input:_
Division  
9  
0
### _Output:_
Error: Division by zero is not allowed.

### _Input:_
Modulus  
8.5  
3
### _Output:_
Error: Please ensure both numbers are integers for the modulus operation.
</pre>
</details>

---

<details>
  <summary>Task 9</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Commission Calculator**
## **Description:**
You're tasked with creating a commission calculator for a sales team. Salespeople get commissions based on tiers of total sales:

- Bronze: Sales up to $5,000: 3% commission
- Silver: Sales from $5,001 to $20,000: 5% commission
- Gold: Sales from $20,001 to $50,000: 7% commission
- Platinum: Sales over $50,000: 10% commission

The user will input their total sales, and the program should display their commission tier and the commission amount they earned. If the user inputs an invalid sales amount (like a negative value), display an appropriate error message.

### _Input:_
12000
### _Output:_
Tier: Silver  
Commission Earned: $600.00

### _Input:_
-1500
### _Output:_
Error: Please enter a valid sales amount.

### Note: Use the `switch` operator creatively, possibly in combination with conditionals, to determine the commission tier.
</pre>
</details>



