## Introduction to `TreeSet` in Java

`TreeSet` is a member of the Java Collections Framework and implements the `Set` and `NavigableSet` interfaces. 
It's backed by a Red-Black Tree (a type of self-balancing binary search tree). The elements are ordered using their 
natural ordering, or by a comparator provided at set creation time, depending on which constructor is used.

### Features:
1. **Ordered**: Elements are stored in ascending order.
2. **No duplicates**: Just like any other set, it doesn’t allow duplicates.
3. **Non-synchronized**: Operations on `TreeSet` are not synchronized.
4. **Performance**: Operations like add, remove, and search take O(log n) time.
5. **Allows null initially**: However, if you try to add another null, it will throw an exception.

### Basic Operations:
#### 1. Adding Elements
```java
TreeSet<Integer> numbers = new TreeSet<>();
numbers.add(10);
numbers.add(5);
numbers.add(15);
System.out.println(numbers); // Outputs: [5, 10, 15]
```

#### 2. Removing Elements
```java
numbers.remove(10);
System.out.println(numbers); // Outputs: [5, 15]
```

#### 3. Checking if a Set Contains a Value
```java
boolean hasValueFive = numbers.contains(5); // true
```

### NavigableSet Methods:
Since `TreeSet` implements `NavigableSet`, it provides some powerful navigation methods:

1. `first()`: Returns the first (lowest) element.
2. `last()`: Returns the last (highest) element.
3. `ceiling(E e)`: Returns the least element that is greater than or equal to the given element.
4. `floor(E e)`: Returns the greatest element that is less than or equal to the given element.
5. `higher(E e)`: Returns the least element that is strictly greater than the given element.
6. `lower(E e)`: Returns the greatest element that is strictly less than the given element.

```java
System.out.println(numbers.ceiling(7));  // Outputs: 15
System.out.println(numbers.floor(7));   // Outputs: 5
```

### Custom Ordering:
You can define a custom ordering for the elements in the `TreeSet` by providing a comparator.

```java
TreeSet<String> names = new TreeSet<>(Comparator.reverseOrder());
names.add("Alice");
names.add("Bob");
names.add("Charlie");
System.out.println(names);  // Outputs: [Charlie, Bob, Alice]
```

### Limitations:
1. All elements that are added to a `TreeSet` must implement the `Comparable` interface, unless you provide a custom comparator. This is because the `TreeSet` needs to know how to order the elements.
2. Adding null to a `TreeSet` which has already some elements will throw `NullPointerException`.

### Conclusion:
`TreeSet` is a powerful collection class in Java, which not only ensures no duplicates but also maintains the 
elements in a sorted order. This makes it a good choice when you want to store unique values in a sorted manner. 
Whether it's navigating the set in a particular order, or maintaining a custom sort order, `TreeSet` provides the 
necessary methods to make these tasks easy.

### Recommended Resources
- [A Guide to TreeSet in Java](https://www.baeldung.com/java-tree-set)
- [TreeSet in Java](https://www.geeksforgeeks.org/treeset-in-java-with-examples)
- [Java TreeSet](https://www.programiz.com/java-programming/treeset#google_vignette)

## Tasks

<details>
  <summary>Task 1: Create and Display</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Create and Display
## Description:
Create a TreeSet, add some integers to it and then display them.

### _Inputs & Outputs:_
#### _Sample Input 1:_
5, 3, 8, 1

#### _Sample Output 1:_
1, 3, 5, 8

#### _Sample Input 2:_
10, 7, 12, 5

#### _Sample Output 2:_
5, 7, 10, 12

</pre>
</details>

---

<details>
  <summary>Task 2: Remove Element</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Remove Element
## Description:
Given a TreeSet and an integer, remove that integer from the TreeSet and display the resultant TreeSet.

### _Inputs & Outputs:_
#### _Sample Input 1:_
TreeSet: [2, 4, 6, 8, 10]
Remove: 6

#### _Sample Output 1:_
2, 4, 8, 10

#### _Sample Input 2:_
TreeSet: [5, 10, 15, 20]
Remove: 5

#### _Sample Output 2:_
10, 15, 20

</pre>
</details>

---

<details>
  <summary>Task 3: Retrieve Ceiling and Floor</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Retrieve Ceiling and Floor
## Description:
Given a TreeSet and an integer, retrieve and display the ceiling and floor of that integer from the TreeSet.

### _Inputs & Outputs:_
#### _Sample Input 1:_
TreeSet: [5, 10, 15, 20, 25]
Integer: 18

#### _Sample Output 1:_
Ceiling: 20
Floor: 15

#### _Sample Input 2:_
TreeSet: [10, 30, 50, 70, 90]
Integer: 45

#### _Sample Output 2:_
Ceiling: 50
Floor: 30

</pre>
</details>

---

<details>
  <summary>Task 4: Custom Ordering with Strings</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Custom Ordering with Strings
## Description:
Create a TreeSet with a custom comparator to store strings in reverse alphabetical order. Add some strings to it and then display them.

### _Inputs & Outputs:_
#### _Sample Input 1:_
"Apple", "Banana", "Cherry"

#### _Sample Output 1:_
Cherry, Banana, Apple

#### _Sample Input 2:_
"Mango", "Peach", "Kiwi"

#### _Sample Output 2:_
Peach, Mango, Kiwi

</pre>
</details>

---

<details>
  <summary>Task 5: First and Last Elements</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# First and Last Elements
## Description:
Given a TreeSet, retrieve and display the first and last elements from it.

### _Inputs & Outputs:_
#### _Sample Input 1:_
TreeSet: [5, 10, 15, 20, 25]

#### _Sample Output 1:_
First: 5
Last: 25

#### _Sample Input 2:_
TreeSet: [10, 30, 50, 70, 90]

#### _Sample Output 2:_
First: 10
Last: 90

</pre>
</details>

