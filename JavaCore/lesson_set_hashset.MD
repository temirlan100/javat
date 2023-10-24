## Set Interface and HashSet in Java

### Introduction:
In Java, the `Collection` framework provides several interfaces and classes to handle a group of objects. 
One of the core interfaces is the `Set` interface. A set represents a collection that does not contain duplicate elements.

### 1. Set Interface:
- **Definition:** The `Set` interface extends the `Collection` interface. It represents a collection of elements where each element is unique.
- **Characteristics:**
    - Does not allow duplicate values.
    - May or may not maintain insertion order, depending on the implementing class.
    - It has methods like `add()`, `remove()`, `contains()`, etc., inherited from the `Collection` interface.

### 2. HashSet Class:
- **Definition:** `HashSet` is a class that implements the `Set` interface.
- **Characteristics:**
    - It uses a hashing mechanism to store elements.
    - Does not maintain insertion order.
    - Allows one null value.
    - It is not synchronized, meaning it's not thread-safe by default.

### **Example: HashSet and fruits!**
```java
import java.util.HashSet;
import java.util.Set;

public class HashSetExample {
    public static void main(String[] args) {
        // Create a new HashSet
        Set<String> fruits = new HashSet<>();

        // Add elements to the HashSet
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");
        fruits.add("Apple");  // This won't be added again

        // Display the HashSet
        System.out.println("Fruits: " + fruits);

        // Check if an element exists
        System.out.println("Contains Apple? " + fruits.contains("Apple"));
        
        // Remove an element
        fruits.remove("Banana");
        System.out.println("After removing Banana: " + fruits);

        // Iterate over a HashSet
        for(String fruit : fruits) {
            System.out.println(fruit);
        }
    }
}
```

### **Example: HashSet and duplicates!**
```java
import java.util.HashSet;
import java.util.Set;

public class IntegerHashSetExample {
    public static void main(String[] args) {
        // Creating a HashSet to store Integer objects
        Set<Integer> numbers = new HashSet<>();

        // Adding elements to the HashSet
        numbers.add(10);
        numbers.add(20);
        numbers.add(30);
        numbers.add(40);
        numbers.add(50);
        numbers.add(10);  // Duplicate element
        numbers.add(20);  // Duplicate element

        // Displaying the elements of the HashSet
        System.out.println("Original HashSet: " + numbers);

        // Removing an element from the HashSet
        numbers.remove(30);

        // Displaying the HashSet after removal
        System.out.println("After removing 30: " + numbers);

        // Checking if a number exists in the HashSet
        if (numbers.contains(40)) {
            System.out.println("HashSet contains 40.");
        } else {
            System.out.println("HashSet does not contain 40.");
        }

        // Iterating over the elements of the HashSet using enhanced for loop
        System.out.println("Iterating through HashSet:");
        for (Integer number : numbers) {
            System.out.println(number);
        }
    }
}
```

**Expected Output:**

```plaintext
Original HashSet: [20, 50, 40, 10, 30]
After removing 30: [20, 50, 40, 10]
HashSet contains 40.
Iterating through HashSet:
20
50
40
10
```

### Explanation:
- **Adding Duplicate Elements:**
    - After the initial five unique elements are added, we attempt to add two more elements, 10 and 20, which are already in the set.
    - `HashSet` does not allow duplicate elements. Thus, adding 10 and 20 a second time will have no effect on the set, and no exception will be thrown.
    - Despite adding elements seven times (including duplicates), the output after all add operations shows five elements, demonstrating that the duplicates were not added.


### Key Points:
- The `add` method is used to add elements. If the element already exists, it won't be added again.
- The `contains` method is used to check if an element exists in the `HashSet`.
- The `remove` method is used to delete an element from the `HashSet`.

## Immutability and HashSet

### 3. Immutability:

- **Definition:** An object is considered immutable if its state cannot be modified after it is created.
- **In Java:** Strings in Java are a classic example of immutable objects. Once a String object is created, it cannot be changed.
- **Why Important:** Immutable objects are thread-safe and can be shared among multiple threads without synchronization issues. They also enhance the robustness and security of the application.

### How Immutability Interacts with HashSet:

**a. Immutability of Elements:**

- **HashSet and Mutable Elements:**
    - If mutable objects are used as elements in a `HashSet` and their values are modified after insertion, it can produce unexpected results since the hashcode will change.
    - Example: If an object of a class with mutable fields is placed in a `HashSet`, and later one of its fields (that affects hashcode) is modified, this object might be lost in the set because the hashcode is used to determine where it is stored.

- **Using Immutable Elements:**
    - Ensuring that elements are immutable prevents issues related to changes in the hashcode of stored objects and provides more predictable behavior.
    - Example: Common immutable objects like `String` or `Integer` are often used as elements in a `HashSet` to prevent such issues.

**b. Immutability of the HashSet Itself:**

- **Unmodifiable Set:**
    - Java Collections framework provides methods to make a collection unmodifiable (read-only).
    - Example: `Collections.unmodifiableSet(HashSet)`.
    - This doesn’t make the set itself immutable, but it prevents modification through the reference where this method is applied.

```java
import java.util.Collections;
import java.util.HashSet;
import java.util.Set;

public class ImmutableHashSetExample {
    public static void main(String[] args) {
        Set<String> originalSet = new HashSet<>();
        originalSet.add("Apple");
        originalSet.add("Banana");
        originalSet.add("Cherry");

        // Creating an unmodifiable set
        Set<String> unmodifiableSet = Collections.unmodifiableSet(originalSet);

        // This line will throw UnsupportedOperationException
        // unmodifiableSet.add("Dragonfruit");
    }
}
```

**c. Creating Immutable Sets with `Set.of()`:**

- **Definition:**
    - `Set.of()` is a static method available in the `Set` interface from Java 9 onwards.
    - It allows you to create an immutable set in a very straightforward and clean way.

- **Characteristics:**
    - The returned set is immutable; attempting to modify it will throw an `UnsupportedOperationException`.
    - `null` elements are not allowed.
    - Duplicate elements are not allowed; attempting to create a set with duplicate elements will throw an `IllegalArgumentException`.

- **Example:**

```java
import java.util.Set;

public class SetOfExample {
    public static void main(String[] args) {
        // Creating an immutable set using Set.of()
        Set<String> immutableSet = Set.of("Apple", "Banana", "Cherry");
        
        // Displaying the set
        System.out.println("Immutable Set: " + immutableSet);

        // The following line will throw UnsupportedOperationException
        // immutableSet.add("Dragonfruit");
        
        // The following line will throw NullPointerException in runtime
        // Set<String> nullSet = Set.of("Apple", null);

        // The following line will throw IllegalArgumentException in runtime
        // Set<String> duplicateSet = Set.of("Apple", "Apple");
    }
}
```

### Key Points:
- **Immutable Elements:** Ensure that elements stored in a `HashSet` are immutable to prevent unexpected behavior due to hashcode changes.
- **Unmodifiable Set:** While you cannot make a `HashSet` truly immutable, you can create a read-only view of it using `Collections.unmodifiableSet()`.
- **Using `Set.of()`:**
    - Offers a succinct, convenient way to create an immutable set.
    - Ensures no modifications can be made to the set after creation.
    - Does not permit `null` or duplicate elements.


### Conclusion:
- While arrays and lists are beneficial for many tasks, sometimes we need to ensure that we don't have duplicates. 
For these cases, the `Set` interface and its implementations like `HashSet` are extremely useful. As you progress 
in Java, you'll discover more advanced set implementations, such as `LinkedHashSet` and `TreeSet`, each with its unique 
properties and use cases.
- Understanding immutability is crucial when working with collections in Java. Especially with `HashSet`,
where the hashcode of elements is pivotal for its functionality, ensuring that elements are immutable or using
immutable elements provides stability and predictability in your applications.


### Recommended Resources
- [Java HashSet](https://www.w3schools.com/java/java_hashset.asp)
- [HashSet in Java](https://www.geeksforgeeks.org/hashset-in-java)
- [A Guide to HashSet in Java](https://www.baeldung.com/java-hashset)
- [Java HashSet Class](https://www.programiz.com/java-programming/hashset)
- [HashSet](https://www.scaler.com/topics/hashset-in-java)

## Tasks

<details>
  <summary>Task 1: Unique Number Finder</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Unique Number Finder
## Description:
Implement a method that receives a List of integers and returns a HashSet containing only the unique integers from the input list.

### _Inputs & Outputs:_
#### _Sample Input 1:_
[1, 2, 2, 3, 4, 4, 5]

#### _Sample Output 1:_
[1, 2, 3, 4, 5]

#### _Sample Input 2:_
[10, 10, 11, 12, 12]

#### _Sample Output 2:_
[10, 11, 12]

</pre>
</details>

---

<details>
  <summary>Task 2: Intersection of Two Sets</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Intersection of Two Sets
## Description:
Implement a method that takes two HashSets of integers and returns a new HashSet containing the common elements between the two input sets.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Set1: [1, 2, 3, 4]
Set2: [3, 4, 5, 6]

#### _Sample Output 1:_
[3, 4]

#### _Sample Input 2:_
Set1: [5, 10, 15]
Set2: [20, 25, 30]

#### _Sample Output 2:_
[]

</pre>
</details>

---

<details>
  <summary>Task 3: Remove Odd Numbers</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Remove Odd Numbers
## Description:
Create a method that removes all the odd numbers from a given HashSet of integers and returns the modified HashSet.

### _Inputs & Outputs:_
#### _Sample Input 1:_
[1, 2, 3, 4, 5]

#### _Sample Output 1:_
[2, 4]

#### _Sample Input 2:_
[11, 14, 15, 18, 19]

#### _Sample Output 2:_
[14, 18]

</pre>
</details>

---

<details>
  <summary>Task 4: Check Subset</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Check Subset
## Description:
Implement a method that accepts two HashSets and checks whether the first set is a subset of the second set.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Set1: [1, 2]
Set2: [1, 2, 3, 4]

#### _Sample Output 1:_
true

#### _Sample Input 2:_
Set1: [1, 5]
Set2: [1, 2, 3, 4]

#### _Sample Output 2:_
false

</pre>
</details>

---

<details>
  <summary>Task 5: String Length Categorizer</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# String Length Categorizer
## Description:
Implement a method that accepts a List of strings and returns a HashMap. The keys of the HashMap are integers representing string lengths, and the associated values are HashSets containing strings from the input list that have that length.

### _Inputs & Outputs:_
#### _Sample Input 1:_
["cat", "dog", "elephant", "lion", "tiger"]

#### _Sample Output 1:_
{3=["cat", "dog"], 5=["tiger", "lion"], 8=["elephant"]}

#### _Sample Input 2:_
["apple", "banana", "kiwi", "grape"]

#### _Sample Output 2:_
{5=["apple"], 6=["banana", "grape"], 4=["kiwi"]}

</pre>
</details>

---

<details>
  <summary>Task 6: Symmetric Difference Calculator</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Symmetric Difference Calculator
## Description:
Implement a method that finds the symmetric difference (elements that are in one of the sets, but not in both) between two HashSets and returns the result as a new HashSet.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Set1: [1, 2, 3]
Set2: [3, 4, 5]

#### _Sample Output 1:_
[1, 2, 4, 5]

#### _Sample Input 2:_
Set1: [1, 2, 3]
Set2: [4, 5, 6]

#### _Sample Output 2:_
[1, 2, 3, 4, 5, 6]

</pre>
</details>

---

<details>
  <summary>Task 7: First Non-Repeated Character</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# First Non-Repeated Character
## Description:
Create a method that receives a string and returns the first non-repeated character using HashSet to achieve an optimized solution.

### _Inputs & Outputs:_
#### _Sample Input 1:_
"swiss"

#### _Sample Output 1:_
'w'

#### _Sample Input 2:_
"repeater"

#### _Sample Output 2:_
'r'

</pre>
</details>

---

<details>
  <summary>Task 8: Group Anagrams</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Group Anagrams
## Description:
Write a method that takes a list of strings and groups anagrams together. Each group of anagrams should be in a separate HashSet. All these HashSets should be stored in a List and returned.

### _Inputs & Outputs:_
#### _Sample Input 1:_
["rat", "tar", "evil", "vile", "act", "cat"]

#### _Sample Output 1:_
[[rat, tar], [evil, vile], [act, cat]]

#### _Sample Input 2:_
["bat", "tap", "pat"]

#### _Sample Output 2:_
[[bat], [tap, pat]]

</pre>
</details>

---

<details>
  <summary>Task 9: Pair with Given Sum</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Pair with Given Sum
## Description:
Implement a method that identifies if there exists a pair of integers in a given HashSet which, when added together, equals a specified target sum.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Set: [1, 2, 3, 4, 5], Target Sum: 9

#### _Sample Output 1:_
true (because 4 + 5 = 9)

#### _Sample Input 2:_
Set: [1, 1, 1, 1, 1], Target Sum: 3

#### _Sample Output 2:_
false

</pre>
</details>

---

<details>
  <summary>Task 10: Distinct Substring Counter</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Distinct Substring Counter
## Description:
Develop a method that receives a string and an integer 'n' and returns the number of distinct substrings of length 'n' that can be formed from the input string.

### _Inputs & Outputs:_
#### _Sample Input 1:_
String: "banana", n: 2

#### _Sample Output 1:_
4  (["ba", "an", "na"])

#### _Sample Input 2:_
String: "computer", n: 3

#### _Sample Output 2:_
6  (["com", "omp", "mpu", "put", "ute", "ter"])

</pre>
</details>

---

<details>
  <summary>Task 11: Fraudulent Transaction Identifier</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Fraudulent Transaction Identifier
## Description:
Develop a method that accepts a list of transaction IDs and a HashSet of known fraudulent transaction IDs. The method should return a list of transaction IDs from the input list that have been identified as fraudulent.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Transaction IDs: ["T1001", "T1002", "T1003", "T1004"]
Fraudulent IDs: ["T1003", "T1002"]

#### _Sample Output 1:_
["T1002", "T1003"]

#### _Sample Input 2:_
Transaction IDs: ["T1005", "T1006", "T1007"]
Fraudulent IDs: ["T1008", "T1009"]

#### _Sample Output 2:_
[]

</pre>
</details>

---

<details>
  <summary>Task 12: Optimal Route Identifier</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Optimal Route Identifier
## Description:
Create a method that accepts two parameters: a HashSet of blocked routes and a list of all available routes between two destinations (A and B). The method should return a list of routes that are available and not blocked between A and B.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Blocked Routes: ["Route3", "Route5"]
Available Routes: ["Route1", "Route2", "Route3", "Route4", "Route5"]

#### _Sample Output 1:_
["Route1", "Route2", "Route4"]

#### _Sample Input 2:_
Blocked Routes: ["Route2"]
Available Routes: ["Route1", "Route2", "Route3"]

#### _Sample Output 2:_
["Route1", "Route3"]

</pre>
</details>

---

<details>
  <summary>Task 13: Unique Course Registration</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Unique Course Registration
## Description:
Develop a method that accepts a list of student IDs trying to register for a course and a HashSet of student IDs that have already registered. The method should add unique IDs from the list to the HashSet and return a new list of IDs that could not be registered because they were already registered earlier.

### _Inputs & Outputs:_
#### _Sample Input 1:_
New Registrations: ["S1001", "S1002", "S1003"]
Already Registered: ["S1001", "S1004", "S1005"]

#### _Sample Output 1:_
Cannot Register: ["S1001"]

#### _Sample Input 2:_
New Registrations: ["S1002", "S1003", "S1006"]
Already Registered: ["S1001", "S1002", "S1004"]

#### _Sample Output 2:_
Cannot Register: ["S1002"]

</pre>
</details>



