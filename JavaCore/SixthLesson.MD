## **do-while Loop in Java**

### **Introduction**
The `do-while` loop is one of the looping constructs available in Java. It is similar to the `while` loop but with a key difference: the condition is evaluated **after** the loop body executes. This guarantees that the loop will execute its body at least once.

### **Syntax**
```java
do {
    // code to be executed
} while (condition);
```

### **How It Works**
1. The code inside the loop executes once.
2. The condition is checked.
3. If the condition is `true`, the loop will execute again. If the condition is `false`, the loop will exit and the program will continue with the statements following the loop.

### **Key Point**
The `do-while` loop will **always execute the loop body at least once**, regardless of the condition. This is because the condition is checked **after** the loop body has been executed.

### **Example**
Consider a scenario where you want to prompt a user to enter a positive number. Using a `do-while` loop ensures that the user is prompted at least once:

```java
import java.util.Scanner;

public class DoWhileExample {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int number;

        do {
            System.out.println("Enter a positive number:");
            number = scanner.nextInt();
        } while (number <= 0);

        System.out.println("You entered: " + number);
    }
}
```

In the above code:

- We prompt the user to enter a positive number.
- If the user enters a non-positive number, they are prompted again.
- This continues until the user enters a positive number.

### **When to Use the do-while Loop**
You should use the `do-while` loop when you want the loop body to execute at least once, regardless of the initial condition. It is especially useful in situations where an initial action is required before a condition can be evaluated (like reading user input).

---

### **Example 1: Simple Counter with if Condition**

In this example, we'll increment a counter and print its value. If the counter reaches a certain value, we'll break out of the loop using an `if` condition:

```java
public class DoWhileWithIfExample {

    public static void main(String[] args) {
        int counter = 1;

        do {
            System.out.println("Counter value: " + counter);

            if (counter >= 5) {
                System.out.println("Counter reached 5. Exiting loop.");
                break;
            }

            counter++;
        } while (true);
    }
}
```

Here, the loop will keep executing indefinitely (`while(true)`), but we use the `if` condition to break out of it once the counter reaches or exceeds the value of 5.

---

### **Example 2: Menu Selection**

In this example, we present a simple menu to the user and prompt them for a choice. If the user chooses to exit, the loop will terminate. Otherwise, the user will be shown the menu again:

```java
import java.util.Scanner;

public class MenuSelectionExample {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("---- Menu ----");
            System.out.println("1. Option One");
            System.out.println("2. Option Two");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");

            choice = scanner.nextInt();

            switch(choice) {
                case 1:
                    System.out.println("You selected Option One.");
                    break;
                case 2:
                    System.out.println("You selected Option Two.");
                    break;
                case 3:
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice. Please select again.");
            }

        } while (choice != 3);

        System.out.println("Program terminated.");
    }
}
```

In this example, the `do-while` loop ensures that the menu is displayed at least once. If the user doesn't choose to exit, they are shown the menu again, ensuring that invalid choices won't terminate the program prematurely.

### Recommended Resources
- [Java do-while Loop](https://www.javatpoint.com/java-do-while-loop)
- [Java do-while loop with Examples](https://www.geeksforgeeks.org/java-do-while-loop-with-examples)
- [Java do while loop](https://www.digitalocean.com/community/tutorials/java-do-while-loop)

## Tasks

<details>
  <summary>Task 1</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Temperature Converter**
## **Description:**
Write a Java program that converts temperatures between Fahrenheit and Celsius using a `do-while` loop. The formulas to convert between the two are:
- Fahrenheit to Celsius: \( C = (F - 32) \times \frac{5}{9} \)
- Celsius to Fahrenheit: \( F = C \times \frac{9}{5} + 32 \)

The user should be able to choose the conversion direction (from Fahrenheit to Celsius or from Celsius to Fahrenheit) and then input the temperature value. The program should then display the converted temperature. The user should be prompted to make conversions as many times as they want until they decide to exit.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Choose conversion direction (FtoC/CtoF): FtoC  
Enter the temperature in Fahrenheit: 98.6
#### _Sample Output 1:_
The temperature in Celsius is 37.00°C.

#### _Sample Input 2:_
Choose conversion direction (FtoC/CtoF): CtoF  
Enter the temperature in Celsius: 100
#### _Sample Output 2:_
The temperature in Fahrenheit is 212.00°F.
</pre>
</details>

---

<details>
  <summary>Task 2</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Password Validator**
## **Description:**
Write a Java program that prompts users to enter a password using a `do-while` loop.
The password should have at least 8 characters, one uppercase letter, one lowercase letter, and one number.
If the password doesn't meet these criteria, inform the user about the shortcomings and prompt them again.
Continue this process until the user enters a valid password.
### _Input:_
password123
### _Output:_
Password should contain at least one uppercase letter.
### _Input:_
Password
### _Output:_
Password should contain at least one number.
### _Input:_
Password123
### _Output:_
Password accepted.
</pre>
</details>

---

<details>
  <summary>Task 3</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Number Summation**
## **Description:**
Using a `do-while` loop, create a Java program that prompts the user to enter numbers continuously. The program should sum all the numbers entered by the user. The process should continue until the user enters a negative number. Once a negative number is entered, the program should display the sum of all previously entered numbers (excluding the negative number) and then terminate.

Remember: The loop should ensure that the user is prompted at least once.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number: 5  
Enter a number: 6  
Enter a number: 7  
Enter a number: -1
#### _Sample Output 1:_
The sum of the numbers is 18.

#### _Sample Input 2:_
Enter a number: 10  
Enter a number: -5
#### _Sample Output 2:_
The sum of the numbers is 10.
</pre>
</details>
