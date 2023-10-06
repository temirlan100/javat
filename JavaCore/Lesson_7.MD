## **`while` loop in Java**
In Java, a `while` loop is used to repeatedly execute a block of code as long as a particular condition remains true. It's similar to the `do-while` loop, but the key difference is in the condition-checking sequence. In a `do-while` loop, the code block is executed at least once before checking the condition. On the other hand, in a `while` loop, the condition is checked before the loop body is executed.

### **Syntax:**
```java
while(condition) {
    // code to be executed
}
```

### **Example:**
Here is a simple example of a `while` loop that prints numbers from 1 to 5:

```java
int i = 1; 
while(i <= 5) {
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

### Sum of Natural Numbers
This program calculates the sum of the first `n` natural numbers:

```java
int n = 10;  // You can change this value
int sum = 0;
int i = 1;

while(i <= n) {
    sum += i;
    i++;
}

System.out.println("The sum of first " + n + " natural numbers is: " + sum);
```

**Output:**
```
The sum of first 10 natural numbers is: 55
```

### Checking for a Prime Number

This program checks if a given number is prime:

```java
int num = 29;  // You can change this value
boolean isPrime = true;
int i = 2;

while(i <= num/2) {
    if(num % i == 0) {
        isPrime = false;
        break;
    }
    i++;
}

if(isPrime) {
    System.out.println(num + " is a prime number.");
} else {
    System.out.println(num + " is not a prime number.");
}
```

**Output:**
```
29 is a prime number.
```

### **Key Points:**
1. The loop condition is checked before the loop body is executed. If the condition is false initially, the loop body may never execute.
2. It's crucial to ensure that the loop condition changes during the iterations to avoid an infinite loop.

### Recommended Resources
- [Java while loop](https://www.w3schools.com/java/java_while_loop.asp)
- [While loop with examples](https://www.geeksforgeeks.org/java-while-loop-with-examples)
- [while and do-while](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/while.html)

## Tasks

<details>
  <summary>Task 1: Counter Challenge</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Counter Challenge**
## **Description:**
Write a Java program that counts how many times the user inputs a positive number using a `while` loop. The program should stop when the user inputs a negative number and then display the total count of positive numbers entered.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number: 5  
Enter a number: 9  
Enter a number: 2  
Enter a number: 6  
Enter a number: -1

#### _Sample Output 1:_
You entered 4 positive numbers.

#### _Sample Input 2:_
Enter a number: 8  
Enter a number: -5

#### _Sample Output 2:_
You entered 1 positive number.

</pre>
</details>

---

<details>
  <summary>Task 2: Number Guesser</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Number Guesser**
## **Description:**
Write a Java program where the computer randomly selects a number between 1 and 10. Ask the user to guess this number. After each guess, the program should inform the user whether their guess was too high, too low, or correct. The program should continue until the user guesses the correct number.

### _Inputs & Outputs:_
#### _Sample Input:_
Guess the number: 5  
Guess the number: 8

#### _Sample Output:_
Too low!  
Correct!

</pre>
</details>

---

<details>
  <summary>Task 3: Sum of Digits</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Sum of Digits**
## **Description:**
Write a Java program that calculates the sum of the digits of an integer. If the sum is a single-digit number, the program should display it. However, if the sum results in a multiple-digit number, it should continue adding the digits until a single-digit number is obtained.

### _Inputs & Outputs:_
#### _Sample Input:_
Enter a number: 9875

#### _Sample Output:_
Single-digit sum is: 2

_Reasoning: 9 + 8 + 7 + 5 = 29, then 2 + 9 = 11, and finally 1 + 1 = 2._

</pre>
</details>

---

<details>
  <summary>Task 4: Collatz Sequence</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Collatz Sequence**
## **Description:**
The Collatz sequence is defined for a positive integer as:
- If the number is even, divide it by 2.
- If the number is odd, multiply it by 3 and add 1.

Continue this process until the number becomes 1. Write a Java program that takes a positive integer as input and displays its Collatz sequence. Also, count the number of steps taken to reach 1.

### _Inputs & Outputs:_
#### _Sample Input:_
Enter a number: 6

#### _Sample Output:_
Collatz sequence: 6 3 10 5 16 8 4 2 1  
Number of steps to reach 1: 8

</pre>
</details>
