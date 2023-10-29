## **If-Else Operator in Java**

### **1. Introduction**
The `if-else` construct in Java is used to perform conditional operations, i.e., it lets you execute a block of code only if a particular condition is `true` and optionally another block of code if the condition is `false`.

### **2. Syntax**
```java  
if (condition) {  
    // code to be executed if condition is true  
} else {  
    // code to be executed if condition is false  
}  
```  

**Note**: The `else` block is optional.
### **3. Simple Examples**

**Example 1**: Check if a number is positive
```java  
int number = 5;  
  
if (number > 0) {  
    System.out.println("The number is positive.");  
} else {  
    System.out.println("The number is not positive.");  
}  
```  
**Output**:
```  
The number is positive.  
```  

**Example 2**: Decide if one should wear a jacket based on temperature
```java  
int temperature = 15;  // in Celsius  
  
if (temperature < 20) {  
    System.out.println("Wear a jacket.");  
} else {  
    System.out.println("No jacket needed.");  
}  
```  
**Output**:
```  
Wear a jacket.  
```  

### **4. Nested If-Else**
You can have an `if-else` inside another `if-else`. This is called nested if-else.  
**Syntax**:
```java  
if (condition1) {  
    // code  
} else if (condition2) {  
    // code  
} else {  
    // code  
}  
```  

**Example**: Classify a given number
```java  
int num = 0;  
  
if (num > 0) {  
    System.out.println("Positive number.");  
} else if (num < 0) {  
    System.out.println("Negative number.");  
} else {  
    System.out.println("Zero.");  
}  
```  
**Output**:
```  
Zero.  
```  

### **5. Using Logical Operators**
Java provides three main logical operators:
- `&&`: Logical AND
- `||`: Logical OR
- `!`: Logical NOT

These can be used to combine or modify conditions in `if-else` constructs.

#### **5.1 Logical AND (`&&`)**
It checks two conditions and returns `true` only if both conditions are `true`.

**Example**: Check if a number is both positive and even.
```java  
int number = 6;  
  
if (number > 0 && number % 2 == 0) {  
    System.out.println("The number is positive and even.");  
} else {  
    System.out.println("The number does not meet the criteria.");  
}  
```  
**Output**:
```  
The number is positive and even.  
```  

#### **5.2 Logical OR (`||`)**
It checks two conditions and returns `true` if at least one of the conditions is `true`.

**Example**: Check if a number is either negative or odd.
```java  
int number = 7;  
  
if (number < 0 || number % 2 != 0) {  
    System.out.println("The number is either negative or odd.");  
} else {  
    System.out.println("The number is positive and even.");  
}  
```  
**Output**:
```  
The number is either negative or odd.  
```  

#### **5.3 Logical NOT (`!`)**
This operator inverts the value of a boolean. If the boolean is `true`, it will become `false` and vice versa.

**Example**: Check if a number is not zero.
```java  
int number = 5;  
  
if (! (number == 0)) {  
    System.out.println("The number is not zero.");  
} else {  
    System.out.println("The number is zero.");  
}  
```  
**Output**:
```  
The number is not zero.  
```  

### **6. Ternary Operator (Conditional Operator)**

Apart from the `if-else` structure, Java also provides a shorthand way to perform conditional operations, which is the ternary operator `?:`.  
**Syntax**:
```java  
(condition) ? value_if_true : value_if_false;  
```  

**Example**: Find the largest of two numbers.
```java  
int a = 5, b = 7;  
  
int max = (a > b) ? a : b;  
System.out.println("The larger number is: " + max);  
```  
**Output**:
```  
The larger number is: 7  
```  

### **7. Important Points with Complex Scenarios**

- The condition inside the if or else if should always return a boolean value (true or false).
- Only one block among the if, else if, or else will get executed based on the first true condition.
- Parentheses () are mandatory after if and else if.
- Ensure your conditions are clear and readable. If you have many conditions or complex combinations, consider breaking them into multiple lines or using intermediary variables.
- Remember that Java uses short-circuit evaluation. This means that in a series of `&&` or `||` operators, as soon as one condition determines the result, the subsequent conditions won't be evaluated. For example, in the condition `(a != 0 && 10 / a > 1)`, if `a` is 0, the second condition will not be checked, preventing a division-by-zero error.
- The ternary operator is a concise way to handle simple conditional assignments. However, for more complex scenarios, the traditional `if-else` structure is more readable and maintainable.

### Recommended Resources
- [Java If ... Else](https://www.w3schools.com/java/java_conditions.asp)
- [Java if...else Statement](https://www.programiz.com/java-programming/if-else-statement)
- [Java If-else Statement](https://www.javatpoint.com/java-if-else)
- [Java if-else](https://www.geeksforgeeks.org/java-if-else-statement-with-examples/)


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

# **Odd or Even Checker**
## **Description:**
Write a Java program to determine if a given integer is odd or even.  
The user should input an integer, and the program should display if the number is odd or even.
### _Input:_
5
### _Output:_
The number is odd.
</pre>  
</details>  
  
---  

<details>  
  <summary>Task 3</summary>  
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">  

# **Positive, Negative or Zero**
## **Description:**
Create a Java program that categorizes a given number as positive, negative, or zero.  
The user should input the number, and the program will display the category of that number.
### _Input:_
-7
### _Output:_
The number is negative.
</pre>  
</details>  
  
---  

<details>  
  <summary>Task 4</summary>  
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">  

# **Leap Year Checker**
## **Description:**
Write a Java program that checks if a given year is a leap year.  
A leap year is exactly divisible by 4 except for end-of-century years which must be divisible by 400.  
This means that the year 2000 was a leap year, although 1900 was not.
### _Input:_
2024
### _Output:_
2024 is a leap year.
</pre>  
</details>  
  
---  

<details>  
  <summary>Task 5</summary>  
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">  

# **Palindrome Checker**
## **Description:**
Write a Java program that checks if a given string is a palindrome. A palindrome is a word, phrase, number, or other sequences of characters that reads the same forward and backward (ignoring spaces, punctuation, and capitalization).
### _Input:_
Racecar
### _Output:_
The given string is a palindrome.
</pre>  
</details>  
  
---  

<details>  
  <summary>Task 6</summary>  
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">  

# **Prime Number Finder**
## **Description:**
Design a Java program that checks if a given number is prime. A prime number is a natural number greater than 1 that has no positive divisors other than 1 and itself.
### _Input:_
17
### _Output:_
17 is a prime number.
</pre>  
</details>  
  
---  

<details>  
  <summary>Task 7</summary>  
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">  

# **Triangle Type Identifier**
## **Description:**
Given the lengths of three sides, determine the type of triangle they form. Write a Java program that categorizes the triangle as equilateral (all sides are equal), isosceles (two sides are equal), or scalene (no sides are equal). Additionally, the program should verify if the given sides can form a triangle in the first place (the sum of the lengths of any two sides must be greater than the length of the third side).
### _Input:_
5 5 5
### _Output:_
The triangle is equilateral.
</pre>  
</details>  
  
---  

<details>  
  <summary>Task 8</summary>  
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">  

# **Advanced Personal Tax Calculator**
## **Description:**
Develop a Java program that calculates the tax someone owes based on their income and other factors. Here's how the tax should be calculated:

- If the person's age is under 18 or over 60, they get a 10% discount on their tax.
- Base tax rate:
    - Income up to $20,000: 2%
    - Income between $20,001 and $40,000: 5%
    - Income between $40,001 and $80,000: 10%
    - Income over $80,001: 20%

- Additional factors:
    - If the person has more than 3 dependents, reduce the tax by 5%.
    - If the person is married, reduce the tax by 3%.

### _Input:_
```  
Age: 65  
Income: $55,000  
Dependents: 4  
Married: Yes  
```  

### _Output:_
```  
Total tax owed: $4,620  
```  
(Note: The above output is just an example. You'd need to use the provided rules to calculate the correct amount.)

</pre>  
</details>