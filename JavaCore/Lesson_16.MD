# Scanner Class

The standard input is like a data stream that enters a program, and it's managed by the operating system. By default, it takes data from keyboard input, but it's also possible to redirect it from a file.

Not all programs require standard input, but it's essential for many programming tasks. It follows a common pattern:

1. **Read Data**: Get data from standard input (System.in).
2. **Process Data**: Manipulate the data to obtain the desired outcome.
3. **Output Result**: Display the result to standard output (System.out).

This approach makes it easy to test code with different input formats, which is why we use it frequently.

## 1. Using the Scanner Class

The Scanner class simplifies reading data from standard input. It can handle various data types, such as strings and numbers. Let's explore its usage:

1.1. **Import the Scanner**: Start by adding this import statement at the top of your source code file:
```java
import java.util.Scanner;
```
1.2. **Create a Scanner Object**: After the import, create a Scanner object for standard input:
```java
Scanner scanner = new Scanner(System.in);
```

This line initializes the Scanner, allowing you to use its methods. You'll learn more about creating objects in other topics. **System.in** indicates that the program will read text from the standard input.

## 2. Reading Strings
You can read strings using two Scanner methods. If your input is an integer or a single word, use the **next()** method. For example, this code reads a user's name and greets them:
```java
String name = scanner.next();
System.out.println("Hello, " + name + "!");
```
For instance, if the user's name is James, the output will be "Hello, James!"

If the input is an integer, like 123, the program will output it as a string:
```java
Hello, 123!
```
If the user enters a compound name like "Erich Maria," the program only captures the first word:
```java
Hello, Erich!
```
For multi-word input, use the **nextLine()** method, which reads and outputs the entire line:
```java
Hello, Erich Maria!
```
Note that **next()** reads only one word, excluding spaces, while **nextLine()** includes all encountered spaces.

## 3. Handling Multiline Input
Reading multiline input requires attention to the cursor's position and the behavior of reading methods. Here's an example:
```java
|This is a simple
multiline input,
that is being read
```
The cursor is initially marked with "|". When you use **next()**, the program reads until the next space, shown in blue:
```java
This| is a simple
multiline input,
that is being read
```
With **nextLine()**, the program reads from the cursor position to the end of the line, indicated in green:
```java
This is a simple
|multiline input,
that is being read
```
Using **next()** twice reads two words, as shown in orange:
```java
This is a simple
multiline| input,
that is being read
```
Another **next()** reads the second word without spaces, no matter how many there are, as indicated in light blue:
```java
This is a simple
multiline input,|
that is being read
```
**nextLine()** behaves differently, returning an empty line if it starts right before a new line:
```java
This is a simple
multiline input,
|that is being read
```
To summarize, we've explored how to use the Scanner class to read data from standard input and differentiate between **next()** and **nextLine()** for different input types.
## Conclusion
Utilizing the Scanner class simplifies reading data from standard input. The **next()** and **nextLine()** methods are crucial for reading strings. They have distinct behaviors: **next()** reads until the next space, while **nextLine()** reads until the end of the line.

We recommend using the Scanner class when tackling programming challenges, as it's one of the easiest ways to obtain values from standard input. More advanced data reading techniques will be covered in future topics.