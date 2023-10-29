### **One-Dimensional Arrays in Java**

#### Introduction to Arrays
An array is a collection of variables that are of the same type. Instead of declaring individual variables, such as `number0`, `number1`, ..., and `number99`, you can declare one array variable such as `numbers` and use `numbers[0]`, `numbers[1]`, ..., `numbers[99]` to represent an individual variable. This is particularly useful when you want to store large amounts of data of the same type.

#### Declaration & Initialization
*Syntax for Declaring an Array:*
```java
dataType[] arrayName;
```
For instance:
```java
int[] numbers;
```

*Syntax for Instantiating an Array:*
```java
arrayName = new dataType[arraySize];
```
For instance:
```java
numbers = new int[10];
```

You can also declare and instantiate at the same time:
```java
int[] numbers = new int[10];
```

*Initialize an Array During Declaration:*
```java
int[] numbers = {1, 2, 3, 4, 5};
```

#### Accessing Array Elements
Each item in an array is called an element, and each position in an array has a number index starting from 0.

To access an array element:
```java
numbers[2] = 50; // This assigns the value 50 to the third element.
int x = numbers[2]; // This retrieves the value stored in the third element.
```

#### Array Length
Every array has a property called `length` that holds the number of elements in the array:
```java
int len = numbers.length; // This will assign 5 to len since there are 5 elements in the numbers array.
```

#### Looping Through an Array
You can use loops to iterate over the array:

*Using for loop:*
```java
for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}
```

*Using enhanced for loop (also called for-each loop):*
```java
for (int num : numbers) {
    System.out.println(num);
}
```

#### Common Mistakes
- **ArrayIndexOutOfBoundsException**: This error occurs when you try to access an index that does not exist. Always make sure the index is within `0` to `array.length - 1`.

  ```java
  int[] arr = new int[3];
  arr[3] = 10; // This will throw an ArrayIndexOutOfBoundsException.
  ```

- Not initializing an array. Just declaring an array variable doesn't allocate memory for the array elements.

  ```java
  int[] arr;
  arr[0] = 10; // This will throw a NullPointerException.
  ```
  
### `int` Array Example:

**Objective:** Create an array of integers, fill it with random numbers, calculate their sum and average, then print the results.
```java
public class IntArrayExample {
  public static void main(String[] args) {
    int[] numbers = new int[5];  // Declare an int array of size 5
    int sum = 0;

    // Fill the array with random numbers between 1 and 100
    for (int i = 0; i < numbers.length; i++) {
      numbers[i] = (int) (Math.random() * 100 + 1);
      System.out.println("Element at index " + i + ": " + numbers[i]);

      sum += numbers[i];  // Calculate the sum
    }

    double average = (double) sum / numbers.length;  // Calculate the average

    System.out.println("Sum: " + sum);
    System.out.println("Average: " + average);
  }
}
```

### `String` Array Example:

**Objective:** Create an array of strings containing names, print them in reverse order, and count how many names start with the letter 'A'.

```java
public class StringArrayExample {
    public static void main(String[] args) {
        String[] names = {"Alice", "Bob", "Andrew", "Diana", "Aria"};  // Declare and initialize a String array
        int countNamesStartingWithA = 0;

        System.out.println("Names in reverse order:");
        for (int i = names.length - 1; i >= 0; i--) {
            System.out.println(names[i]);

            if (names[i].startsWith("A")) {  // Check if the name starts with 'A'
                countNamesStartingWithA++;
            }
        }

        System.out.println("Number of names starting with 'A': " + countNamesStartingWithA);
    }
}
```

### `char` Array example
**Objective:** Create an array of characters. Use the `foreach` loop to count how many vowels are in the array and print the result.

```java
public class CharArrayExample {
    public static void main(String[] args) {
        char[] letters = {'a', 'b', 'c', 'e', 'i', 'o', 'u', 'x', 'y', 'z'}; // Declare and initialize a char array
        int vowelCount = 0;

        // Count the vowels using foreach loop
        for (char letter : letters) {
            if (isVowel(letter)) {
                vowelCount++;
            }
        }

        System.out.println("Number of vowels in the array: " + vowelCount);
    }

    public static boolean isVowel(char c) {
        return "AEIOUaeiou".indexOf(c) != -1; // Check if the character is a vowel
    }
}
```

Here, we used the `foreach` loop to iterate over each character in the `letters` array. The `isVowel` 
method checks if a given character is a vowel or not. If it's a vowel, we increment the `vowelCount`. 
The result is then printed out.


### Recommended Resources
- [Java arrays](https://www.w3schools.com/java/java_arrays.asp)
- [Arrays in Java](https://www.geeksforgeeks.org/arrays-in-java)
- [Arrays](https://www.programiz.com/java-programming/arrays)
- [Java-Arrays](https://www.tutorialspoint.com/java/java_arrays.htm)


## Tasks

<details>
  <summary>Task 1: Counter Challenge</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Counter Challenge**
## **Description:**
Given an array of integers, determine how many positive numbers are in the array.

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
  <summary>Task 2: Even-Odd Checker</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Even-Odd Checker**
## **Description:**
Given an array of integers, determine the number of even and odd integers in the array.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number: 4  
Enter a number: 7  
Enter a number: 2  
Enter a number: 8

#### _Sample Output 1:_
You entered 3 even numbers and 1 odd number.

#### _Sample Input 2:_
Enter a number: 3  
Enter a number: 5

#### _Sample Output 2:_
You entered 0 even numbers and 2 odd numbers.

</pre>
</details>

---

<details>
  <summary>Task 3: Vowel Counter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Vowel Counter**
## **Description:**
Given a character array, determine how many vowels are in the array.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a character: a  
Enter a character: e  
Enter a character: b  
Enter a character: z

#### _Sample Output 1:_
You entered 2 vowels.

#### _Sample Input 2:_
Enter a character: c  
Enter a character: n

#### _Sample Output 2:_
You entered 0 vowels.

</pre>
</details>

---

<details>
  <summary>Task 4: Largest Number Finder</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Largest Number Finder**
## **Description:**
Given an array of integers, find and display the largest number from the array.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number: 5  
Enter a number: 9  
Enter a number: 2

#### _Sample Output 1:_
The largest number you entered is 9.

#### _Sample Input 2:_
Enter a number: 8  
Enter a number: -5  
Enter a number: 7

#### _Sample Output 2:_
The largest number you entered is 8.

</pre>
</details>

---

<details>
  <summary>Task 5: Reverse Array</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Reverse Array**
## **Description:**
Given an array of integers, reverse the elements in the array and display the reversed array.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number: 5  
Enter a number: 9  
Enter a number: 2

#### _Sample Output 1:_
Reversed array: 2 9 5

#### _Sample Input 2:_
Enter a number: 8  
Enter a number: -5  
Enter a number: 7

#### _Sample Output 2:_
Reversed array: 7 -5 8

</pre>
</details>

---

<details>
  <summary>Task 6: Remove Duplicates</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Remove Duplicates**
## **Description:**
Given an array of integers, create and display a new array that has all the duplicate elements removed.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number: 4  
Enter a number: 7  
Enter a number: 4  
Enter a number: 8

#### _Sample Output 1:_
Array after removing duplicates: 4 7 8

#### _Sample Input 2:_
Enter a number: 3  
Enter a number: 3

#### _Sample Output 2:_
Array after removing duplicates: 3

</pre>
</details>

---

<details>
  <summary>Task 7: Array Rotation</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Array Rotation**
## **Description:**
Given an array of integers and a positive integer `k`, rotate the array to the right by `k` steps.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a number: 1  
Enter a number: 2  
Enter a number: 3  
Enter a number: 4  
Enter a number: 5  
Enter the rotation count: 2

#### _Sample Output 1:_
Rotated array: 4 5 1 2 3

#### _Sample Input 2:_
Enter a number: 6  
Enter a number: 7  
Enter a number: 8  
Enter the rotation count: 1

#### _Sample Output 2:_
Rotated array: 8 6 7

</pre>
</details>

---

<details>
  <summary>Task 8: Palindrome Checker</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Palindrome Checker**
## **Description:**
Given an array of strings, check and display which strings are palindromes (i.e., they read the same forwards and backwards).

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a string: radar  
Enter a string: hello  
Enter a string: level

#### _Sample Output 1:_
Palindromes: radar, level

#### _Sample Input 2:_
Enter a string: abc  
Enter a string: def

#### _Sample Output 2:_
No palindromes found.

</pre>
</details>

---

<details>
  <summary>Task 9: String Sorter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **String Sorter**
## **Description:**
Given an array of strings, sort them in alphabetical order and display the sorted array.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter a string: banana  
Enter a string: apple  
Enter a string: cherry

#### _Sample Output 1:_
Sorted array: apple, banana, cherry

#### _Sample Input 2:_
Enter a string: tiger  
Enter a string: lion

#### _Sample Output 2:_
Sorted array: lion, tiger

</pre>
</details>

---

<details>
  <summary>Task 10: Transaction Matcher (Fintech)</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Transaction Matcher**
## **Description:**
You're developing software for a fintech startup that helps businesses reconcile their transactions. The company receives two lists every day: one from the bank detailing every transaction that hit their account, and another from their internal sales system. Your job is to match these transactions to ensure no discrepancies.

Write a program to match the transactions from both lists and identify any unmatching transactions.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Bank Transactions:  
$50  
$20  
$30

Sales System Transactions:  
$30  
$50

#### _Sample Output 1:_
Matching Transactions: $50, $30  
Unmatched Transactions from the Bank: $20  
Unmatched Transactions from the Sales System: None

#### _Sample Input 2:_
Bank Transactions:  
$100  
$25

Sales System Transactions:  
$25  
$100  
$10

#### _Sample Output 2:_
Matching Transactions: $25, $100  
Unmatched Transactions from the Bank: None  
Unmatched Transactions from the Sales System: $10

</pre>
</details>

---

<details>
  <summary>Task 11: Inventory Tracker (Logistics)</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Inventory Tracker**
## **Description:**
You are a software developer for a logistics company. They have warehouses around the country and need software to track the inventory in each warehouse. Each item has a unique ID, name, and count. Your program should be able to match items by their IDs between different warehouses, compare their counts, and report discrepancies.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Warehouse A Items:  
ID: 001, Name: Widget, Count: 20  
ID: 002, Name: Gizmo, Count: 15

Warehouse B Items:  
ID: 001, Name: Widget, Count: 18  
ID: 003, Name: Gear, Count: 10

#### _Sample Output 1:_
Matching Items:  
ID: 001, Name: Widget, Count in A: 20, Count in B: 18

Unmatched Items in Warehouse A:  
ID: 002, Name: Gizmo, Count: 15

Unmatched Items in Warehouse B:  
ID: 003, Name: Gear, Count: 10

#### _Sample Input 2:_
Warehouse A Items:  
ID: 004, Name: Bolt, Count: 50

Warehouse B Items:  
ID: 005, Name: Screw, Count: 45

#### _Sample Output 2:_
No Matching Items Found.

Unmatched Items in Warehouse A:  
ID: 004, Name: Bolt, Count: 50

Unmatched Items in Warehouse B:  
ID: 005, Name: Screw, Count: 45

</pre>
</details>




