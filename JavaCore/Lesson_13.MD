### Introduction to the Map Interface:
The `Map` interface is part of the Java Collections Framework and represents a collection of key-value pairs. 
Each key is mapped to exactly one value. Keys are unique, but values can be duplicated.

### Characteristics of Map:
1. **Key-Value Pairs**: At its core, the `Map` interface represents a collection of key-value pairs where each key is associated with exactly one value. This relationship is often termed as a mapping.
2. **Unique Keys**: `Map` doesn't allow duplicate keys. If you try to insert a new key-value pair with a key that already exists in the map, the new value will replace the old value.
3. **Nullable**: Depending on the implementation, a `Map` can allow null keys and null values. For example, `HashMap` allows one null key and multiple null values. However, `TreeMap` doesn't allow any null key, but it allows multiple null values.
4. **Not a Collection**: While the `Map` interface is a part of the Java Collections Framework, it doesn't actually extend the `Collection` interface. This means operations you might expect from collections (like `add` or `remove`) don't exist in the `Map` interface in the same form. Instead, operations are key-centric like `put`, `get`, and `remove`.
5. **Ordering**: The order of the key-value pairs in a `Map` depends on its implementation. For instance:
    - `HashMap`: Doesn't guarantee any specific order of the entries.
    - `TreeMap`: Stores entries in a sorted (ascending) order according to natural ordering of its keys or a custom comparator.
    - `LinkedHashMap`: Maintains the order in which keys were inserted (or accessed, if constructed appropriately).
6. **Generics**: `Map` supports generic types, allowing users to specify the type of keys and values at the time of declaration. This ensures type safety:
   ```java
   Map<String, Integer> nameToAgeMapping = new HashMap<>();
   ```
7. **Thread Safety**: By default, most of the core implementations of `Map` (like `HashMap`, `TreeMap`) are not synchronized. They are not thread-safe. If multiple threads access a map concurrently, and at least one of the threads modifies it structurally, it must be synchronized externally. There are thread-safe or synchronized versions available like `ConcurrentHashMap` or you can wrap a map using `Collections.synchronizedMap()`.
8. **Derived Interfaces & Classes**: There are several derived interfaces like `SortedMap` and `NavigableMap` which provide extended functionalities. Similarly, there are several classes that implement the `Map` interface, each with its unique features and characteristics.
9. **Lambda Operations**: From Java 8 onwards, `Map` has been enhanced with lambda operations to perform certain operations more concisely, like `compute`, `merge`, `forEach`, and `replace`.
10. **No Direct Support for Bi-directional Mapping**: While the primary function of a map is to map a key to a value, if there's a need to map a value back to its key, another map or a bidirectional map (like from third-party libraries) is needed.

### The HashMap Class:
`HashMap` is a class that implements the `Map` interface. It uses a technique called Hashing.

#### Characteristics of HashMap:
- It allows one null key and multiple null values.
- It doesn’t maintain the order of the keys or values.
- It is not synchronized, which means it's not thread-safe.

### Basic Operations with HashMap:
#### **a. Creating a HashMap:**
```java
Map<String, Integer> map = new HashMap<>();
```

#### **b. Adding elements to HashMap:**
```java
map.put("One", 1);
map.put("Two", 2);
```

#### **c. Retrieving a value by key:**
```java
int value = map.get("One");  // value will be 1
```

#### **d. Removing a value by key:**
```java
map.remove("One");
```

#### **e. Checking if a key exists:**
```java
boolean hasKey = map.containsKey("Two");  // true
```

#### **f. Iterating over a HashMap:**
```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    String key = entry.getKey();
    int val = entry.getValue();
    System.out.println(key + " => " + val);
}
```

### Important Methods of HashMap:
- `put(K key, V value)`: Inserts the specified value with the specified key.
- `get(Object key)`: Returns the value to which the specified key is mapped.
- `remove(Object key)`: Removes the mapping for a key.
- `containsKey(Object key)`: Checks if this map contains a mapping for the specified key.
- `size()`: Returns the number of key-value mappings.
- `isEmpty()`: Checks if the map is empty.
- `clear()`: Removes all the mappings.

### Differences Between HashMap and Hashtable:
- **Thread Safety:** `HashMap` is not synchronized, whereas `Hashtable` is. This means `Hashtable` is thread-safe, but `HashMap` is faster.
- **Null keys/values:** `HashMap` allows one null key and multiple null values, while `Hashtable` doesn’t allow any null key or value.
- **Superclass:** `HashMap` extends `AbstractMap` class while `Hashtable` extends `Dictionary` class.

### **Example: Storing and Retrieving Student Grades**
```java
import java.util.HashMap;
import java.util.Map;

public class GradesExample {
    public static void main(String[] args) {
        // Create a HashMap to store student names and their grades
        Map<String, String> studentGrades = new HashMap<>();

        // Add some students and their grades to the map
        studentGrades.put("Alice", "A");
        studentGrades.put("Bob", "B");
        studentGrades.put("Charlie", "A");

        // Retrieve and print the grade of a student
        String aliceGrade = studentGrades.get("Alice");
        System.out.println("Alice's grade: " + aliceGrade);

        // Output: Alice's grade: A
    }
}
```

### **Example: Counting the Occurrences of Words in a Sentence**
```java
import java.util.HashMap;
import java.util.Map;

public class WordCountExample {
    public static void main(String[] args) {
        String sentence = "hello world hello user world user";
        String[] words = sentence.split(" ");

        Map<String, Integer> wordCount = new HashMap<>();

        for (String word : words) {
            // Get the current count and increment it, or set it to 1 if the word isn't in the map yet
            wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);
        }

        // Print word occurrences
        for (Map.Entry<String, Integer> entry : wordCount.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }

        // Output:
        // hello: 2
        // world: 2
        // user: 2
    }
}
```


### Recommended Resources
- [Java HashMap](https://www.w3schools.com/java/java_hashmap.asp)
- [HashMap](https://www.javatpoint.com/java-hashmap)
- [HashMap in Java](https://www.geeksforgeeks.org/java-util-hashmap-in-java-with-examples)
- [Java HashMap lesson](https://www.programiz.com/java-programming/hashmap)
- [Java HashMap - HashMap in Java](https://www.digitalocean.com/community/tutorials/java-hashmap)


## Tasks

<details>
  <summary>Task 1: Frequency Counter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Frequency Counter
## Description:
Write a program that takes a list of words and returns a `HashMap` containing each word as a key and its frequency as the corresponding value.

### _Inputs & Outputs:_
#### _Sample Input 1:_
["apple", "banana", "apple", "orange"]

#### _Sample Output 1:_
{apple=2, banana=1, orange=1}

#### _Sample Input 2:_
["cat", "dog", "cat", "fish", "dog", "dog"]

#### _Sample Output 2:_
{cat=2, dog=3, fish=1}

</pre>
</details>

---

<details>
  <summary>Task 2: Reverse Map</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Reverse Map
## Description:
Write a program that reverses the key-value pairs of a given `HashMap`. If there are duplicate values, keep any one key-value pair.

### _Inputs & Outputs:_
#### _Sample Input 1:_
{1="A", 2="B", 3="A"}

#### _Sample Output 1:_
{A=3, B=2}

#### _Sample Input 2:_
{1="X", 2="Y", 3="Z"}

#### _Sample Output 2:_
{X=1, Y=2, Z=3}

</pre>
</details>

---

<details>
  <summary>Task 3: Merge Two HashMaps</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Merge Two HashMaps
## Description:
Write a program that merges two `HashMaps` into one. If a key is present in both the maps, append the value from the second map to the value in the first map.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Map1: {a="apple", b="banana"}
Map2: {b="berry", c="cherry"}

#### _Sample Output 1:_
{a="apple", b="bananaberry", c="cherry"}

#### _Sample Input 2:_
Map1: {x="xenon", y="yttrium"}
Map2: {y="yellow", z="zinc"}

#### _Sample Output 2:_
{x="xenon", y="yttriumyellow", z="zinc"}

</pre>
</details>

---

<details>
  <summary>Task 4: Key Exists?</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Key Exists?
## Description:
Write a program that checks if a given key is present in a `HashMap`. Return `true` if present, otherwise `false`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
HashMap: {1="One", 2="Two", 3="Three"}
Key: 2

#### _Sample Output 1:_
true

#### _Sample Input 2:_
HashMap: {A="Alpha", B="Bravo", C="Charlie"}
Key: D

#### _Sample Output 2:_
false

</pre>
</details>

---

<details>
  <summary>Task 5: Value Lookup</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Value Lookup
## Description:
Write a program that retrieves the key(s) associated with a given value in a `HashMap`. Return a list of all keys that have the specified value.

### _Inputs & Outputs:_
#### _Sample Input 1:_
HashMap: {1="Blue", 2="Red", 3="Green", 4="Blue", 5="Yellow"}
Value: "Blue"

#### _Sample Output 1:_
[1, 4]

#### _Sample Input 2:_
HashMap: {A="Dog", B="Cat", C="Dog", D="Bird"}
Value: "Dog"

#### _Sample Output 2:_
[A, C]

</pre>
</details>

---

<details>
  <summary>Task 6: Remove Entries</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Remove Entries
## Description:
Write a program that removes all entries in a `HashMap` where the value matches a specified string.

### _Inputs & Outputs:_
#### _Sample Input 1:_
HashMap: {1="Apple", 2="Banana", 3="Apple", 4="Cherry"}
Value to Remove: "Apple"

#### _Sample Output 1:_
{2="Banana", 4="Cherry"}

#### _Sample Input 2:_
HashMap: {A="Hello", B="World", C="Hello", D="Java"}
Value to Remove: "Hello"

#### _Sample Output 2:_
{B="World", D="Java"}

</pre>
</details>

---

<details>
  <summary>Task 7: First Non-Repeated Character</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# First Non-Repeated Character
## Description:
Write a program that finds the first non-repeated character in a given string using a `HashMap`.

### _Inputs & Outputs:_
#### _Sample Input 1:_
String: "swiss"

#### _Sample Output 1:_
"w"

#### _Sample Input 2:_
String: "repetition"

#### _Sample Output 2:_
"r"

</pre>
</details>

---

<details>
  <summary>Task 8: Group Anagrams</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Group Anagrams
## Description:
Given a list of strings, group anagrams together. An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, using all the original letters exactly once.

### _Inputs & Outputs:_
#### _Sample Input 1:_
["bat", "tab", "rat", "tar", "atb", "art"]

#### _Sample Output 1:_
[["bat", "tab", "atb"], ["rat", "tar", "art"]]

#### _Sample Input 2:_
["listen", "enlist", "rat", "tar", "silent"]

#### _Sample Output 2:_
[["listen", "enlist", "silent"], ["rat", "tar"]]

</pre>
</details>

---

<details>
  <summary>Task 9: Intersection of Two Arrays</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Intersection of Two Arrays
## Description:
Given two arrays, write a program to compute their intersection using a `HashMap`. The result can be in any order.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Array1: [1, 2, 2, 1]
Array2: [2, 2]

#### _Sample Output 1:_
[2, 2]

#### _Sample Input 2:_
Array1: [4, 9, 5]
Array2: [9, 4, 9, 8, 4]

#### _Sample Output 2:_
[4, 9]

**Note:** Each element in the result should appear as many times as it shows in both arrays. The result can be in different order.

</pre>
</details>

---

<details>
  <summary>Task 10: Common Elements in Lists</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Common Elements in Lists
## Description:
Given two lists, return a list of common elements between them. Use a `HashMap` for efficient lookup.

### _Inputs & Outputs:_
#### _Sample Input 1:_
List1: [1, 2, 3, 4, 5]
List2: [4, 5, 6, 7, 8]

#### _Sample Output 1:_
[4, 5]

#### _Sample Input 2:_
List1: ["apple", "banana", "cherry"]
List2: ["date", "banana", "fig", "apple"]

#### _Sample Output 2:_
["apple", "banana"]

</pre>
</details>

---

<details>
  <summary>Task 11: Customer Purchases</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Customer Purchases
## Description:
You are a software developer at a local retail store. Your task is to create a program to keep track of the total amount each customer has spent. Whenever a purchase is made, update the total for that customer.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Customer: "Alice"
Purchase Amount: 50

#### _Sample Output 1:_
{"Alice": 50}

#### _Sample Input 2:_
Customer: "Bob"
Purchase Amount: 20

#### _Sample Input 3:_
Customer: "Alice"
Purchase Amount: 30

#### _Sample Output 3:_
{"Alice": 80, "Bob": 20}

</pre>
</details>

---

<details>
  <summary>Task 12: Library Book Catalogue</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Library Book Catalogue
## Description:
You're tasked to create a catalogue for a local library. For each book, you need to store the ISBN and its title. Design a program that allows you to add, remove, and look up a book by its ISBN.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Action: Add
ISBN: "123-456-789"
Title: "Moby Dick"

#### _Sample Output 1:_
{"123-456-789": "Moby Dick"}

#### _Sample Input 2:_
Action: Lookup
ISBN: "123-456-789"

#### _Sample Output 2:_
"Moby Dick"

</pre>
</details>

---

<details>
  <summary>Task 13: Sales Commission</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Sales Commission
## Description:
You work in the finance department of a sales company. The company wants to reward its best salespeople with bonuses. Each salesperson has a unique ID. For every sale, you should update the total sales for each salesperson. At the end of the month, retrieve the IDs of salespeople whose total sales exceed a certain threshold.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Salesperson ID: 101
Sale Amount: 500

#### _Sample Output 1:_
{101: 500}

#### _Sample Input 2:_
Salesperson ID: 102
Sale Amount: 700

#### _Sample Input 3:_
Salesperson ID: 101
Sale Amount: 600

#### _Sample Output 3:_
{101: 1100, 102: 700}

#### _Sample Input 4:_
Threshold: 1000

#### _Sample Output 4:_
[101]

</pre>
</details>

---

<details>
  <summary>Task 14: Flight Boarding Passes</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Flight Boarding Passes
## Description:
You're developing a system for an airline. Each passenger has a unique ticket number, and for each ticket, you need to store the flight number. Design a program that allows you to assign a flight to a ticket, remove a ticket, and retrieve the flight for a given ticket number.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Action: Assign
Ticket Number: "A1234"
Flight Number: "FL789"

#### _Sample Output 1:_
{"A1234": "FL789"}

#### _Sample Input 2:_
Action: Retrieve
Ticket Number: "A1234"

#### _Sample Output 2:_
"FL789"

</pre>
</details>

