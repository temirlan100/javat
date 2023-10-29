### List Interface
Before understanding the `ArrayList` class, it's essential to know about the `List` interface, as `ArrayList` is just one implementation of this interface.

**List Interface**: It's a part of the Java Collections Framework and extends the `Collection` interface. 
It's an ordered collection of elements and allows duplicate values. Elements can be inserted or accessed by their position in the list.
Some of the primary methods defined in the `List` interface include `add()`, `remove()`, `get()`, `set()`, 
and more. All of these methods are implemented by classes that implement the `List` interface, like `ArrayList`.

**Declaration using the List interface**:
```java
import java.util.List;
import java.util.ArrayList;

List<String> list = new ArrayList<String>();  // It's a good practice to use the interface as a type
```

### Immutable Lists using List.of()
Java introduced a way to create immutable lists with the `List.of()` method. An immutable list is a list that 
cannot be modified after its creation.

**Usage**:
```java
List<String> immutableList = List.of("Apple", "Banana", "Cherry");
```

Advantages:
1. **Thread-safe**: Since the list is immutable, you don't need external synchronization.
2. **Efficient**: Memory efficient because of its fixed size.
3. **Prevents unintended modifications**: As the list is unmodifiable, there's no risk of accidentally changing its contents.

However, remember that trying to modify an immutable list (like adding or removing elements) will throw an `UnsupportedOperationException`.

### Declaring with List

Using the `List` interface to declare and instantiate your list is a good practice because it gives you the flexibility to change the implementing class without changing the reference type.

```java
List<String> list = new ArrayList<>();
```

This way, you're programming to an interface, not an implementation. This is a fundamental principle in Java and object-oriented programming in general.

### Summary
Understanding the `List` interface and its implementations, such as `ArrayList`, is crucial for Java developers. 
Additionally, Java provides ways like `List.of()` to create immutable lists, which offer benefits like thread-safety 
and prevention against unintended modifications. Always consider using the `List` interface as the type for more 
flexibility in your code.

### Introduction to ArrayList
The `ArrayList` class is a part of Java's Collection framework. It's a resizable array, which means it can grow and 
shrink dynamically. Unlike arrays, which have a fixed length, `ArrayLists` are more flexible and provide many 
useful methods for manipulating data.

### Basics of ArrayList

**Declaration & Initialization**
```java
import java.util.ArrayList;

List<String> list = new ArrayList<String>();  // Creating an ArrayList of String type
List<Integer> numbers = new ArrayList<>();   // Diamond syntax (Java 7+)
```

**Adding elements**
```java
list.add("Apple");
list.add("Banana");
numbers.add(5);
numbers.add(10);
```

**Accessing elements**
```java
String fruit = list.get(0);  // Gets the element at index 0
int number = numbers.get(1);  // Gets the element at index 1
```

**Modifying elements**
```java
list.set(1, "Cherry");  // Replaces the element at index 1 with "Cherry"
```

**Removing elements**
```java
list.remove(0);  // Removes the element at index 0
```

**Finding the size**
```java
int size = list.size();  // Returns the number of elements in the list
```

### Important Methods

- `add(E element)`: Adds an element to the end of the list.
- `add(int index, E element)`: Inserts an element at the specified position.
- `remove(int index)`: Removes the element at the specified position.
- `set(int index, E element)`: Replaces the element at the specified position with the specified element.
- `get(int index)`: Returns the element at the specified position.
- `size()`: Returns the number of elements in the list.
- `clear()`: Removes all elements from the list.
- `contains(Object o)`: Checks if the list contains the specified element.
- `indexOf(Object o)`: Returns the index of the first occurrence of the specified element, or -1 if the list doesn't contain it.

### Iterating over an ArrayList

You can iterate over an `ArrayList` using a standard `for` loop, enhanced `for` loop (for-each loop), or iterators.

**1. Using standard for loop**
```java
for (int i=0; i<list.size(); i++) {
    System.out.println(list.get(i));
}
```

**Using for-each loop**
```java
for (String fruit : list) {
    System.out.println(fruit);
}
```

**Using Iterator**
```java
import java.util.Iterator;

Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    String fruit = iterator.next();
    System.out.println(fruit);
}
```

### Advantages of using ArrayList
1. **Dynamic Size:** Unlike arrays, ArrayLists can grow or shrink automatically.
2. **Built-in Methods:** ArrayLists provide built-in methods to perform operations like addition, removal, etc.
3. **Allows Null & Duplicates:** ArrayLists can have null elements and duplicate values.

### Limitations
1. **Not Synchronized:** ArrayList is not synchronized, which means it's not thread-safe. If needed, it can be synchronized using `Collections.synchronizedList()`.
2. **Slower than arrays:** Due to the dynamic resizing property, it's typically slower than arrays.

### Hierarchy of Collection Framework in Java
![collections.png](..%2FImg%2Fcollections.png)

### **Example 1: Managing a List of Students**
Suppose we have to manage a list of students in a classroom:

```java
import java.util.ArrayList;
import java.util.List;

public class Classroom {

    public static void main(String[] args) {
        List<String> students = new ArrayList<>();

        // Add students to the list
        students.add("Alice");
        students.add("Bob");
        students.add("Charlie");

        // Print all students
        System.out.println("Students in the class: " + students);

        // Remove a student
        students.remove("Bob");

        // Add a new student
        students.add("David");

        // Print updated list of students
        System.out.println("Updated list of students: " + students);
    }
}
```

Output:
```
Students in the class: [Alice, Bob, Charlie]
Updated list of students: [Alice, Charlie, David]
```

### **Example 2: Storing and Calculating Grades**
Let's store grades of a student and calculate the average:

```java
import java.util.ArrayList;
import java.util.List;

public class GradeCalculator {

    public static void main(String[] args) {
        List<Integer> grades = new ArrayList<>();

        // Add grades to the list
        grades.add(85);
        grades.add(90);
        grades.add(78);
        grades.add(88);
        grades.add(76);

        // Calculate and print the average grade
        double average = calculateAverage(grades);
        System.out.println("The average grade is: " + average);
    }

    public static double calculateAverage(List<Integer> grades) {
        int sum = 0;
        for (int grade : grades) {
            sum += grade;
        }
        return (double) sum / grades.size();
    }
}
```

Output:
```
The average grade is: 83.4
```

### Conclusion
The `ArrayList` class in Java provides a dynamic and flexible way to store elements. With its easy-to-use methods, 
it's a powerful tool for data manipulation in Java. Make sure to understand its basics, methods, and how to iterate 
over its elements for effective usage.


### Recommended Resources
- [ArrayList](https://www.w3schools.com/java/java_arraylist.asp)
- [Java ArrayList](https://www.programiz.com/java-programming/arraylist#google_vignette)
- [ArrayList 2](https://www.javatpoint.com/java-arraylist)
- [ArrayList in Java](https://www.geeksforgeeks.org/arraylist-in-java)
- [ArrayList in Java With Examples](https://beginnersbook.com/2013/12/java-arraylist)
- [Guide to the Java ArrayList](https://www.baeldung.com/java-arraylist)


## Tasks

<details>
  <summary>Task 1: Fruit Manager</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Fruit Manager
## Description:
Implement a program that adds, removes, and lists fruits from an `ArrayList`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
ADD Apple
LIST
REMOVE Apple
LIST

#### _Sample Output 1:_
[Apple]
[]

#### _Sample Input 2:_
ADD Banana
ADD Cherry
LIST
REMOVE Banana

#### _Sample Output 2:_
[Banana, Cherry]
[Cherry]

</pre>
</details>

---

<details>
  <summary>Task 2: Duplicate Detector</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Duplicate Detector
## Description:
Write a program to detect and display the duplicate elements in an `ArrayList`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
5 3 5 6 7 3

#### _Sample Output 1:_
Duplicates: 5, 3

#### _Sample Input 2:_
1 2 3 4

#### _Sample Output 2:_
No duplicates found.

</pre>
</details>

---

<details>
  <summary>Task 3: Element Swapper</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Element Swapper
## Description:
Swap two elements in an `ArrayList` based on their indices.

### _Inputs & Outputs:_
#### _Sample Input 1:_
1 2 3 4 5
SWAP 0 4

#### _Sample Output 1:_
5 2 3 4 1

#### _Sample Input 2:_
A B C D
SWAP 1 3

#### _Sample Output 2:_
A D C B

</pre>
</details>

---

<details>
  <summary>Task 4: Reverse ArrayList</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Reverse ArrayList
## Description:
Reverse the elements in an `ArrayList`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
1 2 3 4 5

#### _Sample Output 1:_
5 4 3 2 1

#### _Sample Input 2:_
A B C

#### _Sample Output 2:_
C B A

</pre>
</details>

---

<details>
  <summary>Task 5: Find the Largest and Smallest</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Find the Largest and Smallest
## Description:
Given an `ArrayList` of integers, determine the largest and smallest numbers.

### _Inputs & Outputs:_
#### _Sample Input 1:_
1 5 3 8 2

#### _Sample Output 1:_
Largest: 8
Smallest: 1

#### _Sample Input 2:_
4 7 6 4 9

#### _Sample Output 2:_
Largest: 9
Smallest: 4

</pre>
</details>

---

<details>
  <summary>Task 6: Clear Every Other</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Clear Every Other
## Description:
Clear every other element in an `ArrayList`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
A B C D E

#### _Sample Output 1:_
A C E

#### _Sample Input 2:_
1 2 3 4 5 6

#### _Sample Output 2:_
1 3 5

</pre>
</details>

---

<details>
  <summary>Task 7: Element Frequency</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Element Frequency
## Description:
Count the frequency of each element in an `ArrayList`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
apple orange apple banana orange

#### _Sample Output 1:_
apple: 2
orange: 2
banana: 1

#### _Sample Input 2:_
hello world hello universe

#### _Sample Output 2:_
hello: 2
world: 1
universe: 1

</pre>
</details>

---

<details>
  <summary>Task 8: ArrayList Intersection</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# ArrayList Intersection
## Description:
Find the common elements in two `ArrayLists`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
List 1: A B C D E
List 2: C E F G

#### _Sample Output 1:_
Intersection: C E

#### _Sample Input 2:_
List 1: 1 2 3 4
List 2: 3 4 5 6

#### _Sample Output 2:_
Intersection: 3 4

</pre>
</details>


---

<details>
  <summary>Task 9: Edu Domain Student Filter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Edu Domain Student Filter
## Description:
You are given a list of students' names and their corresponding email addresses. Your task is to filter out and display only the names of students with email addresses from the ".edu" domain. Additionally, for each of these filtered students, display the institution domain without the ".edu" part.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Names: Alice Bob Charlie David
Emails: alice@gmail.com bob@university.edu charlie@college.edu david@hotmail.com

#### _Sample Output 1:_
Edu Students:
Bob - Institution: university
Charlie - Institution: college

#### _Sample Input 2:_
Names: Eve Frank Grace Hannah
Emails: eve@tech.edu frank@gmail.com grace@school.edu hannah@yahoo.com

#### _Sample Output 2:_
Edu Students:
Eve - Institution: tech
Grace - Institution: school

### _Instructions:_
1. Split the input names and emails into separate `ArrayLists`.
2. Loop through the email `ArrayList` to find addresses that end with ".edu".
3. For each ".edu" email, extract and display the corresponding student name and institution.

</pre>
</details>

---

<details>
  <summary>Task 10: Ed-tech Domain Course Filter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Ed-tech Domain Course Filter
## Description:
You're given a list of online courses with corresponding email addresses of course coordinators. Identify and list down all the courses coordinated by someone with an ".ed-tech" email domain. Also, find and display the most common domain name (excluding the ".ed-tech" part) among these email addresses.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Courses: Python101 JavaAdvanced WebDevelopment AIForBeginners
Emails: instructor1@code.ed-tech instructor2@java.ed-tech instructor3@design.com instructor4@aiworld.ed-tech

#### _Sample Output 1:_
Ed-tech Courses:
Python101 - Coordinator: instructor1@code.ed-tech
JavaAdvanced - Coordinator: instructor2@java.ed-tech
AIForBeginners - Coordinator: instructor4@aiworld.ed-tech

Most common domain: code

### _Instructions:_
1. Split the input courses and emails into separate `ArrayLists`.
2. Identify the ".ed-tech" domain courses and coordinators.
3. Find the most common domain among these ".ed-tech" emails.

</pre>
</details>

---

<details>
  <summary>Task 11: Medical Domain Patient Filter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Medical Domain Patient Filter
## Description:
You have a list of patient names and their associated diseases. Identify and display all the patients who have "Influenza". Additionally, calculate the average age of these patients.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Patients: John Adam Eve Susan
Diseases: Cold Influenza Influenza Malaria
Ages: 20 30 40 25

#### _Sample Output 1:_
Patients with Influenza:
Adam - Age: 30
Eve - Age: 40

Average Age: 35

### _Instructions:_
1. Split the input patient names, diseases, and ages into separate `ArrayLists`.
2. Loop through the diseases `ArrayList` to identify patients with "Influenza".
3. Calculate the average age of these patients.

</pre>
</details>

---

<details>
  <summary>Task 12: Medical Prescription Tracker</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Medical Prescription Tracker
## Description:
Given a list of medicines prescribed to patients over a week, identify which medicine was prescribed most frequently. If there's a tie, display all the top medicines.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Medicines: Paracetamol Amoxicillin Paracetamol Ibuprofen Amoxicillin Ibuprofen Ibuprofen

#### _Sample Output 1:_
Most Prescribed Medicine(s):
Ibuprofen

#### _Sample Input 2:_
Medicines: Aspirin Aspirin Paracetamol Paracetamol Amoxicillin

#### _Sample Output 2:_
Most Prescribed Medicine(s):
Aspirin, Paracetamol

### _Instructions:_
1. Split the input medicines into an `ArrayList`.
2. Track the frequency of each medicine using a suitable approach.
3. Identify and display the most frequently prescribed medicine(s).

</pre>
</details>


