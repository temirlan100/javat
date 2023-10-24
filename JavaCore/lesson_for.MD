## `for` loop in Java
The `for` loop provides a concise way of writing the loop structure. Unlike a `while` loop, a `for` loop is usually used when you know beforehand how many times you want to execute a statement or a block of statements.

### Syntax:
```java
for (initialization; termination; increment/decrement) {
    // Body of loop
}
```

1. **Initialization** - It is executed once at the beginning of the loop. Here, we initialize the loop control variable.
2. **Termination** - This is the condition that determines when the loop will terminate. As long as this condition evaluates to `true`, the loop will continue to run. If it evaluates to `false`, the loop will terminate.
3. **Increment/Decrement** - This statement allows the loop control variable to be incremented or decremented after each iteration.

### Standard Incrementing Direction:
This is the most common usage of the `for` loop, where we initialize a variable, provide a termination condition, and increment the loop variable in each iteration.

```java
// Prints numbers from 1 to 5
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

**Output:**
```
1
2
3
4
5
```

### Reverse Decrementing Direction:
Here, we initialize the loop variable with a high value, provide a termination condition, and decrement the loop variable in each iteration.

```java
// Prints numbers from 5 to 1
for (int i = 5; i >= 1; i--) {
    System.out.println(i);
}
```

**Output:**
```
5
4
3
2
1
```

### Increment in Steps:
Instead of incrementing by 1, you can increment by any value. In this example, we'll increment by 2:

```java
// Prints even numbers between 0 and 10
for (int i = 0; i <= 10; i += 2) {
    System.out.println(i);
}
```

**Output:**
```
0
2
4
6
8
10
```

### Nested `for` loops:
We can use one `for` loop inside another. This is commonly used for matrix traversal or generating patterns.

```java
// Prints a pattern of stars in increasing order
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print("*");
    }
    System.out.println(); // Move to the next line after inner loop completes
}
```

**Output:**
```
*
**
***
****
*****
```

### Using a `for` loop without all three statements:
You can use the `for` loop without initialization, condition, or iteration, but you should handle these aspects within the loop to avoid infinite loops.

```java
int i = 1;
for (; i <= 5;) {
    System.out.println(i);
    i++;
}
```

**Output:**
```
1
2
3
4
5
```

### Enhanced `for` loop:
Java also introduced an enhanced `for` loop (often referred to as the "foreach" loop) which is used to traverse arrays and collections.

```java
int[] numbers = {1, 2, 3, 4, 5}; // this array will be learned in the next lesson

for (int num : numbers) {
    System.out.println("The number is: " + num);
}
```

The enhanced `for` loop automatically iterates over the array or collection, assigning each value to the loop variable (`num` in this case) one at a time.


### Recommended Resources
- [Java for loop](https://www.programiz.com/java-programming/for-loop)
- [FOR loop in Java](https://www.w3schools.com/java/java_for_loop.asp)
- [for loop in Java](https://www.geeksforgeeks.org/java-for-loop-with-examples)
- [The for Statement](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/for.html)


## Tasks

<details>
  <summary>Task 1: Print Square Pattern</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Print Square Pattern**
## **Description:**
Write a Java program that prints a square pattern of stars (`*`) using a `for` loop. The user should input the size of the square.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter the size of the square: 3

#### _Sample Output 1:_
```
***
***
***
```

#### _Sample Input 2:_
Enter the size of the square: 5

#### _Sample Output 2:_
```
*****
*****
*****
*****
*****
```

</pre>
</details>

---

<details>
  <summary>Task 2: Number Triangle</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Number Triangle**
## **Description:**
Write a Java program that prints a triangle pattern of numbers using a `for` loop. The user should input the height of the triangle.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter the height of the triangle: 3

#### _Sample Output 1:_
```
  1
 12
123
```

#### _Sample Input 2:_
Enter the height of the triangle: 5

#### _Sample Output 2:_
```
    1
   12
  123
 1234
12345
```

</pre>
</details>

---

<details>
  <summary>Task 3: Even or Odd</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Even or Odd**
## **Description:**
Write a Java program that reads a series of numbers until a negative number is entered. For each number, the program should print whether the number is even or odd using a `for` loop combined with an `if` condition.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number: 3  
Enter a number: 6  
Enter a number: 9  
Enter a number: 12  
Enter a number: -1

#### _Sample Output 1:_
3 is Odd  
6 is Even  
9 is Odd  
12 is Even

</pre>
</details>

---

<details>
  <summary>Task 4: Day of the Week</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Day of the Week**
## **Description:**
Write a Java program that asks the user to enter a number between 1 to 7, and then displays the corresponding day of the week using a `for` loop combined with a `switch` statement. If the user enters a number out of the range, print "Invalid input."

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number between 1 to 7: 3

#### _Sample Output 1:_
Wednesday

#### _Sample Input 2:_
Enter a number between 1 to 7: 8

#### _Sample Output 2:_
Invalid input.

</pre>
</details>

---

<details>
  <summary>Task 5: Fibonacci Series</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Fibonacci Series**
## **Description:**
Write a Java program that prints the Fibonacci series up to `n` numbers. The Fibonacci series starts with 0 and 1, and every subsequent number in the series is the sum of the previous two.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter the length of the Fibonacci series: 5

#### _Sample Output 1:_
0 1 1 2 3

#### _Sample Input 2:_
Enter the length of the Fibonacci series: 8

#### _Sample Output 2:_
0 1 1 2 3 5 8 13

</pre>
</details>

---

<details>
  <summary>Task 6: Prime Numbers</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Prime Numbers**
## **Description:**
Write a Java program that checks and prints all the prime numbers between 2 and a given number `n`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter the range for prime numbers: 10

#### _Sample Output 1:_
2 3 5 7

#### _Sample Input 2:_
Enter the range for prime numbers: 20

#### _Sample Output 2:_
2 3 5 7 11 13 17 19

</pre>
</details>

---

<details>
  <summary>Task 7: String Reversal</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **String Reversal**
## **Description:**
Write a Java program that reverses an input string without using any in-built string reversal methods.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a string: hello

#### _Sample Output 1:_
olleh

#### _Sample Input 2:_
Enter a string: java

#### _Sample Output 2:_
avaj

</pre>
</details>

---

<details>
  <summary>Task 8: Sum of Digits</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Sum of Digits**
## **Description:**
Write a Java program that calculates the sum of digits of a positive integer entered by the user.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a positive integer: 1234

#### _Sample Output 1:_
Sum of digits: 10

#### _Sample Input 2:_
Enter a positive integer: 5678

#### _Sample Output 2:_
Sum of digits: 26

</pre>
</details>

---

<details>
  <summary>Task 9: Simple Interest Calculator</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Simple Interest Calculator**
## **Description:**
In the fintech domain, understanding basic financial calculations is crucial. Write a Java program that calculates the simple interest for a given principal amount, rate of interest, and time period. The formula for simple interest is:

![simpleInterest.png](..%2FImg%2FsimpleInterest.png)

Where:
- \( P \) is the principal amount
- \( R \) is the rate of interest per annum (in percentage)
- \( T \) is the time in years

The program should also display the total amount after interest, which is the sum of the principal and the simple interest.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter the principal amount: 1000  
Enter the rate of interest (in %): 5  
Enter the time (in years): 2

#### _Sample Output 1:_
Simple Interest: 100.0  
Total Amount after 2 years: 1100.0

#### _Sample Input 2:_
Enter the principal amount: 5000  
Enter the rate of interest (in %): 3.5  
Enter the time (in years): 4

#### _Sample Output 2:_
Simple Interest: 700.0  
Total Amount after 4 years: 5700.0

</pre>
</details>

---

<details>
  <summary>Task 10: String Manipulator</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **String Manipulator**
## **Description:**
Develop a Java program that iterates through each character of a string and performs the following operations using a `for` loop:

1. Converts each vowel to uppercase.
2. Converts each consonant to lowercase.
3. Leaves numbers and other characters unchanged.

The program should then output the modified string.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a string: Hello World123!

#### _Sample Output 1:_
hEllO wOrld123!

#### _Sample Input 2:_
Enter a string: JAVA Programming4545!!

#### _Sample Output 2:_
jAvA prOgrAmmIng4545!!

### **Implementation Hints:**
- Use the `for` loop to traverse each character in the string.
- Use `Character.isLowerCase()` and `Character.isUpperCase()` methods to check the casing of a character.
- Convert the string to a character array for easier manipulation.

</pre>
</details>


