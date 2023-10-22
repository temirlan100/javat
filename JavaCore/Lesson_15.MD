## **TreeMap in Java**

### **1. Introduction to TreeMap**
- Definition: A `TreeMap` is a Red-Black tree based NavigableMap implementation in Java. It is a part of Java’s collection framework and implements the `Map` interface.
- Key properties:
    - Stores key-value pairs in a sorted order based on the keys.
    - Allows rapid access to the entries.
    - Does not allow duplicate keys but can have duplicate values.
    - Allows only one null key (as long as a custom comparator isn't used).

### **2. Declaration & Initialization**
```java
TreeMap<K, V> treeMap = new TreeMap<>();
```
- Here, `K` is the type of the key and `V` is the type of the value.

### **3. Basic Operations**
#### **3.1. Adding Entries**
```java
treeMap.put("key1", "value1");
treeMap.put("key2", "value2");
```

#### **3.2. Retrieving a Value**
```java
String value = treeMap.get("key1");
```

#### **3.3. Removing an Entry**
```java
treeMap.remove("key1");
```

#### **3.4. Checking if TreeMap Contains a Key**
```java
boolean hasKey = treeMap.containsKey("key2");
```

#### **3.5. Size of TreeMap**
```java
int size = treeMap.size();
```

### **4. Advanced Features**

#### **4.1. Navigating through TreeMap**
- `firstKey()`: Returns the first (lowest) key.
- `lastKey()`: Returns the last (highest) key.
- `higherKey(K key)`: Returns the next higher key than the given key.
- `lowerKey(K key)`: Returns the next lower key than the given key.

#### **4.2. EntrySet, KeySet, and Values**
- Retrieving all keys, values, or key-value pairs.
```java
Set<K> keys = treeMap.keySet();
Collection<V> values = treeMap.values();
Set<Map.Entry<K, V>> entries = treeMap.entrySet();
```

#### **4.3. Sorting in Reverse Order**
```java
TreeMap<K, V> reversed = new TreeMap<>(Collections.reverseOrder());
```

#### **4.4. Using a Custom Comparator**
- You can use a custom comparator to define the order in which the keys are stored.

```java
TreeMap<String, String> customSortedMap = new TreeMap<>(new CustomComparator());
```

### **5. Comparison with Other Map Implementations**
- `TreeMap` vs `HashMap`: While both store key-value pairs, `TreeMap` maintains order whereas `HashMap` does not. `HashMap` generally offers better performance for insertion, deletion, and locate operations.
- `TreeMap` vs `LinkedHashMap`: `LinkedHashMap` maintains the order of insertion, while `TreeMap` maintains a natural ordering or the order defined by a comparator.

### **Example 1: Word Frequency Counter**

The purpose of this example is to demonstrate how `TreeMap` can be used to count the frequency of each word in a given text. Here, words will be sorted alphabetically, allowing easy identification of word frequency in an ordered manner.

```java
import java.util.TreeMap;

public class WordFrequencyCounter {
    public static void main(String[] args) {
        String text = "hello world hello user world world";
        String[] words = text.split(" ");

        TreeMap<String, Integer> wordFrequency = new TreeMap<>();

        for (String word : words) {
            wordFrequency.put(word, wordFrequency.getOrDefault(word, 0) + 1);
        }

        for (Map.Entry<String, Integer> entry : wordFrequency.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}

// Output:
// hello: 2
// user: 1
// world: 3
```

### **Example 2: Employee Records Sorted by IDs**

In this example, we'll use a `TreeMap` to store Employee objects using their unique IDs as keys. This ensures that records are always sorted based on employee IDs.

```java
import java.util.TreeMap;

class Employee {
    int id;
    String name;
    double salary;

    public Employee(int id, String name, double salary) {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

    @Override
    public String toString() {
        return "Employee [id=" + id + ", name=" + name + ", salary=" + salary + "]";
    }
}

public class EmployeeRecords {
    public static void main(String[] args) {
        Employee e1 = new Employee(103, "Alice", 50000);
        Employee e2 = new Employee(101, "Bob", 55000);
        Employee e3 = new Employee(102, "Charlie", 60000);

        TreeMap<Integer, Employee> employees = new TreeMap<>();

        employees.put(e1.id, e1);
        employees.put(e2.id, e2);
        employees.put(e3.id, e3);

        for (Map.Entry<Integer, Employee> entry : employees.entrySet()) {
            System.out.println(entry.getKey() + " => " + entry.getValue());
        }
    }
}

// Output:
// 101 => Employee [id=101, name=Bob, salary=55000.0]
// 102 => Employee [id=102, name=Charlie, salary=60000.0]
// 103 => Employee [id=103, name=Alice, salary=50000.0]
```

### **6. Conclusion**
- Recap the importance and use cases of `TreeMap`.
- Reinforce the notion that while `TreeMap` is useful for sorted data, it might not always be the best choice depending on the specific requirements of an application.


### Recommended Resources
- [Java TreeMap class](https://www.javatpoint.com/java-treemap)
- [TreeMap in Java](https://www.geeksforgeeks.org/treemap-in-java)
- [A Guide to TreeMap in Java](https://www.baeldung.com/java-treemap)
- [Java TreeMap](https://www.programiz.com/java-programming/treemap)

## Tasks

<details>
  <summary>Task 1: Simple Insert and Retrieve</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Simple Insert and Retrieve
## Description:
Create a TreeMap and add a few key-value pairs to it. Then retrieve the value of a given key.

### _Inputs & Outputs:_
#### _Sample Input 1:_
```
Insert: "Apple", 100
Insert: "Banana", 150
Retrieve: Apple
```

#### _Sample Output 1:_
```
100
```

#### _Sample Input 2:_
```
Insert: "Car", 30000
Insert: "Bike", 15000
Retrieve: Bike
```

#### _Sample Output 2:_
```
15000
```

</pre>
</details>

---

<details>
  <summary>Task 2: First and Last Entries</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# First and Last Entries
## Description:
Insert a series of key-value pairs into a TreeMap and retrieve the first and last entries based on the key order.

### _Inputs & Outputs:_
#### _Sample Input 1:_
```
Insert: "Dog", "Mammal"
Insert: "Fish", "Aquatic"
Insert: "Bird", "Aerial"
Retrieve: First and Last
```

#### _Sample Output 1:_
```
First: Bird=Aerial
Last: Fish=Aquatic
```

#### _Sample Input 2:_
```
Insert: "Tulip", "Flower"
Insert: "Oak", "Tree"
Retrieve: First and Last
```

#### _Sample Output 2:_
```
First: Oak=Tree
Last: Tulip=Flower
```

</pre>
</details>

---

<details>
  <summary>Task 3: Library Book Tracker</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Library Book Tracker
## Description:
In a small town, the local library is trying to maintain a system to track books borrowed by its patrons. Use a TreeMap where the key is the name of the borrower and the value is the title of the book borrowed. When a new book is borrowed, add it to the TreeMap. If the borrower returns a book, remove their entry. Display a list of current borrowers and their books.

### _Inputs & Outputs:_
#### _Sample Input 1:_
```
Borrow: Alice, "Moby Dick"
Borrow: Bob, "War and Peace"
Return: Alice
Display
```

#### _Sample Output 1:_
```
Bob=War and Peace
```

#### _Sample Input 2:_
```
Borrow: John, "Pride and Prejudice"
Display
```

#### _Sample Output 2:_
```
John=Pride and Prejudice
```

</pre>
</details>

---

<details>
  <summary>Task 4: Product Inventory Price Tracker</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Product Inventory Price Tracker
## Description:
Jane runs a small grocery shop. She wants a simple tool to track the prices of products in her inventory. Using TreeMap, where the product name is the key and the price is the value, she can easily update or check the price of a product. Implement this for her.

### _Inputs & Outputs:_
#### _Sample Input 1:_
```
Add: "Milk", 1.50
Add: "Eggs", 2.00
Update: "Milk", 1.75
Check: "Milk"
```

#### _Sample Output 1:_
```
Milk: 1.75
```

#### _Sample Input 2:_
```
Add: "Bread", 1.00
Check: "Eggs"
```

#### _Sample Output 2:_
```
Eggs: 2.00
```

</pre>
</details>

---

<details>
  <summary>Task 5: Student Grade Analyzer</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Student Grade Analyzer
## Description:
Mr. Smith, a high school teacher, wants to analyze the grades of his students in Mathematics. He decides to use a TreeMap where student names are keys and their grades are values. He wants to easily find out the student with the highest and lowest grades. Implement a system to help him with this.

### _Inputs & Outputs:_
#### _Sample Input 1:_
```
Add: "Alex", 85
Add: "Brian", 90
Add: "Charlie", 78
Analyze: Highest and Lowest
```

#### _Sample Output 1:_
```
Highest: Brian=90
Lowest: Charlie=78
```

#### _Sample Input 2:_
```
Add: "Diana", 88
Analyze: Highest and Lowest
```

#### _Sample Output 2:_
```
Highest: Brian=90
Lowest: Charlie=78
```

</pre>
</details>


