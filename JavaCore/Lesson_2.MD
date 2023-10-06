
# Java for Beginners

## 1. Data Types
In Java, data types determine the kind of values a variable can hold. They are categorized into 
two main groups: **Primitive Data Types** and **Reference Data Types**.
![ROADMAP.png](..%2FImg%2Ftypes.png))

### 1.1. Primitive Data Types
These are the most basic data types available within the Java language. They include:
- **byte**: 8-bit signed two's complement integer (range: -128 to 127)
- **short**: 16-bit signed two's complement integer (range: -32,768 to 32,767)
- **int**: 32-bit signed two's complement integer (range: -2^31 to 2^31 -1)
- **long**: 64-bit signed two's complement integer (range: -2^63 to 2^63 -1)
- **float**: 32-bit IEEE 754 floating point
- **double**: 64-bit IEEE 754 floating point
- **char**: 16-bit Unicode character (range: 0 to 65,535)
- **boolean**: Represents only two possible values, `true` and `false`.

```java
int age = 25;
double salary = 1000.50;
char initial = 'A';
boolean isStudent = true;
```

### 1.2. Reference Data Types
Reference data types are used to store references to objects. The default value of 
a reference variable is `null`. Some examples are:
- **Arrays**
- **Classes**
- **Interfaces**

Java provides built-in reference types like `String` which is actually a class, but it's used so frequently that it feels like a basic data type.

```java
String name = "John";
String[] names = {"John", "Doe", "Jane"};
```

## 2. Operators
Operators are special symbols that perform specific operations on one, two, or three operands and then return a result.

### 2.1. Arithmetic Operators
| Operator | Description             | Example   |
|----------|-------------------------|-----------|
| +        | Addition                | a + b     |
| -        | Subtraction             | a - b     |
| *        | Multiplication          | a * b     |
| /        | Division                | a / b     |
| %        | Modulus (remainder)     | a % b     |

### 2.2. Relational Operators
| Operator | Description             | Example   |
|----------|-------------------------|-----------|
| ==       | Equal to                | a == b    |
| !=       | Not equal to            | a != b    |
| >        | Greater than            | a > b     |
| <        | Less than               | a < b     |
| >=       | Greater than or equal to| a >= b    |
| <=       | Less than or equal to   | a <= b    |

### 2.3. Logical Operators
| Operator | Description             | Example     |
|----------|-------------------------|-------------|
| &&       | Logical AND             | a && b      |
| \|\|     | Logical OR              | a \|\| b    |
| !        | Logical NOT             | !a          |

### 2.4. Other Important Operators
- **Assignment Operators** (like `=`, `+=`, `-=`, `*=`, `/=`, and `%=`)
- **Bitwise Operators** (like `&`, `|`, `^`, `~`, `<<`, `>>`, and `>>>`)

```java
int result = (10 > 5) ? 1 : 0; // result will be 1
```

### Recommended Resources
- [Introduction to Java Primitives](https://www.baeldung.com/java-primitives#:~:text=2.-,Primitive%20Data%20Types,objects%20and%20represent%20raw%20values.)
- [Java data types](https://www.geeksforgeeks.org/data-types-in-java/)
- [Java Operators](https://www.w3schools.com/java/java_operators.asp)
- [Operators in Java](https://www.geeksforgeeks.org/operators-in-java/)

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

# **Basic Calculator for Two Integers**
## **Description:**
Write a Java program that takes two integer inputs from the user and outputs their sum, product and variance.
### _Input:_
5
3
### _Output:_
Sum: 8
Product: 15
Variance: 2
</pre>
</details>

---

<details>
  <summary>Task 3</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Name Concatenation**
## **Description:**
Write a Java program that asks the user for their first name and last name separately.
The program should then display the full name by concatenating the first and last name.
### _Input:_
John
Doe
### _Output:_
Full Name: John Doe
</pre>
</details>

---

<details>
  <summary>Task 4</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Basic String Length Checker**
## **Description:**
Write a Java program that asks the user for a word or phrase. The program should then display
the length of the inputted string.
### _Input:_
Java Rocks!
### _Output:_
Length: 11
</pre>
</details>

---

<details>
  <summary>Task 5</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Modulo Tester**
## **Description:**
Write a Java program that takes two integers, the first being the number you want to test and the second being
the divisor. The program should display the remainder when the first number is divided by the second
number using the modulo operator.
### _Input:_
10
3
### _Output:_
The remainder is 1.
</pre>
</details>

---

<details>
  <summary>Task 6</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Switching Bit Positions**
## **Description:**
Write a Java program that takes a byte (8 bits) as input. The task is to switch the positions of the 1st and 2nd bits
with the 7th and 8th bits. Display the resulting byte.
For simplicity, the input can be provided as an 8-character long string of ones and zeros.

Hints:
- Use the bitwise AND operator & to isolate certain bits.
- Use the bitwise OR operator | to combine bits.
- Use left shift << and right shift >> to move bits to the appropriate positions.
### _Input:_
11001010
### _Output:_
10101001
</pre>
</details>


## **General hints for Students:**  
1. Use the `Scanner` class for input.
2. Use `System.out.printf()` to control the precision of the output to two decimal places.