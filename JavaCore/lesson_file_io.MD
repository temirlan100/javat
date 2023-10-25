## **Basic File Operations in Java**

### **1. Introduction**
File handling is one of the core aspects of programming. Java provides robust capabilities for performing file operations through its I/O package `java.io` and NIO package `java.nio.file`.

### **2. File Class**
Before diving into file operations, let's introduce the `File` class from the `java.io` package.

```java
import java.io.File;

File myFile = new File("filename.txt");
```

This doesn't create a new file, but rather provides an abstract representation of file and directory pathnames.

**Common methods:**
- `exists()`: Checks if the file exists.
- `isFile()`: Determines if the represented object is a file.
- `isDirectory()`: Determines if the represented object is a directory.
- `getName()`: Returns the name of the file or directory.

### **3. Reading from a File**

Java provides `FileReader` and `BufferedReader` classes to read text files.

**Example**:

```java
import java.io.*;

public class ReadFile {
    public static void main(String[] args) {
        try {
            FileReader reader = new FileReader("filename.txt");
            BufferedReader bufferedReader = new BufferedReader(reader);

            String line;
            while ((line = bufferedReader.readLine()) != null) {
                System.out.println(line);
            }
            bufferedReader.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

### **4. Writing to a File**
Java uses `FileWriter` and `BufferedWriter` classes to write to text files.

**Example**:

```java
import java.io.*;

public class WriteFile {
    public static void main(String[] args) {
        try {
            FileWriter writer = new FileWriter("filename.txt");
            BufferedWriter bufferedWriter = new BufferedWriter(writer);

            bufferedWriter.write("This is a sample text.");
            bufferedWriter.newLine();
            bufferedWriter.write("File operations in Java are fun!");

            bufferedWriter.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

### **5. Java NIO**
Java NIO (New I/O) provides more advanced capabilities for handling I/O operations. The `Files` class from the `java.nio.file` package offers several methods to manipulate files.

**Example**: Reading all lines from a file using NIO:
```java
import java.nio.file.*;

public class NIOReadFile {
    public static void main(String[] args) {
        try {
            Path path = Paths.get("filename.txt");
            List<String> lines = Files.readAllLines(path);

            for (String line : lines) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

### **6. Handling Exceptions**
During file operations, exceptions can occur. The most common exception is `IOException`. 
It's essential to handle this exception using try-catch blocks, as demonstrated in the above examples.


### **Example: Append to a File**

Let's consider a scenario where you wish to append text to an existing file without overwriting its current content.

```java
import java.io.*;

public class AppendToFile {
    public static void main(String[] args) {
        try {
            // Set the second parameter to 'true' for FileWriter to append to the file
            FileWriter writer = new FileWriter("filename.txt", true);
            BufferedWriter bufferedWriter = new BufferedWriter(writer);

            bufferedWriter.newLine(); // Move to a new line
            bufferedWriter.write("This text will be appended to the file.");
            bufferedWriter.newLine();
            bufferedWriter.write("Appending is useful to keep existing content intact.");

            bufferedWriter.close();
        } catch (IOException e) {
            System.out.println("An error occurred while writing to the file.");
            e.printStackTrace();
        }
    }
}
```

In this example, we used the **try-catch** mechanism to handle possible `IOException` that could be thrown when 
performing file operations. If such an exception occurs, a message is printed to the console, and the stack trace 
of the exception is printed using `e.printStackTrace()`, which helps in debugging.

Note: In real-world scenarios, you might also encounter `FileNotFoundException` if the specified file does not exist. 
However, since `FileNotFoundException` is a subclass of `IOException`, catching `IOException` is sufficient in this context.

### Recommended Resources
- [Reading, Writing, and Creating Files](https://docs.oracle.com/javase/tutorial/essential/io/file.html)
- [Java’s File APIs](https://www.marcobehler.com/guides/java-files)
- [File Handling in Java](https://www.geeksforgeeks.org/file-handling-in-java)
- [File Handling in Java – How To Work With Java Files?](https://www.edureka.co/blog/file-handling-in-java)


## Tasks
<details>
  <summary>Task 1: File Checker</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# File Checker
## Description:
Write a program that checks if a given file name exists in the current directory.

### _Inputs & Outputs:_
#### _Sample Input 1:_
filename.txt

#### _Sample Output 1:_
File "filename.txt" exists.

#### _Sample Input 2:_
notpresent.txt

#### _Sample Output 2:_
File "notpresent.txt" does not exist.

</pre>
</details>

---

<details>
  <summary>Task 2: Line Counter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Line Counter
## Description:
Write a program that counts the number of lines in a given text file.

### _Inputs & Outputs:_
#### _Sample Input 1:_
document1.txt (with content: "Hello\nWorld")

#### _Sample Output 1:_
File "document1.txt" has 2 lines.

#### _Sample Input 2:_
document2.txt (with content: "Java\nis\nawesome")

#### _Sample Output 2:_
File "document2.txt" has 3 lines.

</pre>
</details>

---

<details>
  <summary>Task 3: Word Finder</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Word Finder
## Description:
Write a program that searches for a specific word in a given text file and displays the line numbers where the word appears.

### _Inputs & Outputs:_
#### _Sample Input 1:_
File: data.txt (with content: "Java is a programming language.\nI love Java.\nJava is powerful.")
Word: Java

#### _Sample Output 1:_
Word "Java" found on lines: 1, 2, 3

#### _Sample Input 2:_
File: data.txt (with content as above)
Word: Python

#### _Sample Output 2:_
Word "Python" not found.

</pre>
</details>

---

<details>
  <summary>Task 4: Content Reverser</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Content Reverser
## Description:
Write a program that reads the content of a text file and writes its content in reverse order to another file.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Source File: input.txt (with content: "Hello\nWorld")
Destination File: output.txt

#### _Sample Output 1:_
Content in output.txt: "World\nHello"

</pre>
</details>

---

<details>
  <summary>Task 5: Word Counter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Word Counter
## Description:
Write a program that reads a text file and outputs the frequency of each word in the file.

### _Inputs & Outputs:_
#### _Sample Input 1:_
File: words.txt (with content: "apple orange apple banana apple orange")

#### _Sample Output 1:_
apple: 3
orange: 2
banana: 1

</pre>
</details>

---

<details>
  <summary>Task 6: Personal Diary</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Personal Diary
## User Story:
Alex loves journaling and wants a simple program to write, save, and read back journal entries by date.

## Description:
Develop a program where the user can input a date and a journal entry for that date. If a date already has an entry, the user should be given an option to overwrite or append. The user should also be able to read back an entry by entering a date.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Date: 2023-10-25
Entry: "Today was a great day! I learned about file operations in Java."

#### _Sample Output 1:_
Entry saved successfully.

#### _Sample Input 2:_
Date: 2023-10-25

#### _Sample Output 2:_
Entry for 2023-10-25: "Today was a great day! I learned about file operations in Java."

</pre>
</details>

---

<details>
  <summary>Task 7: Expense Tracker</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Expense Tracker
## User Story:
Emma is trying to save money and wants to track her daily expenses. She needs a program to record, update, and view her expenses.

## Description:
Create a program where Emma can enter the date, item, and expense amount. She should also be able to view expenses by date and get a total for a particular date.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Date: 2023-10-24
Item: "Coffee"
Amount: $5

#### _Sample Output 1:_
Expense added successfully.

#### _Sample Input 2:_
Date: 2023-10-24

#### _Sample Output 2:_
Expenses for 2023-10-24:
Coffee - $5
Total: $5

</pre>
</details>

---

<details>
  <summary>Task 8: Quiz Score Analyzer</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Quiz Score Analyzer
## User Story:
Mr. Johnson is a school teacher and takes weekly quizzes. He wants a program to input students' scores, calculate the class average, and identify students scoring below the average.

## Description:
Develop a program where Mr. Johnson can input students' names and their scores. The program should calculate the average score and list the names of students who scored below the average.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Students:
John - 85
Anna - 78
Michael - 90
Sarah - 72

#### _Sample Output 1:_
Class Average: 81.25
Students below average: Anna, Sarah

</pre>
</details>



