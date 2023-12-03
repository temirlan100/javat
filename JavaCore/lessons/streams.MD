### Overview of Java Streams
1. **Definition**: A stream represents a sequence of elements and supports different kinds of operations to perform computations on those elements.
2. **Source**: Streams take Collections, Arrays, or I/O channels as input sources.
3. **Operations**:
    - **Intermediate Operations**: Transform the stream into another stream, e.g., `filter`, `map`, `sorted`.
    - **Terminal Operations**: Produce a result or side-effect, e.g., `forEach`, `reduce`, `collect`.

### Key Concepts
- **Laziness**: Many stream operations are lazy, meaning computation on the source data is only performed when necessary.
- **Non-interference**: The data source should not be modified while it is being used by a stream pipeline.
- **Statelessness**: Stream operations should not depend on any state outside the operation.

### Examples
#### 1. Filtering and Mapping
```java
List<String> myList = Arrays.asList("a1", "a2", "b1", "c2", "c1");

myList.stream()
      .filter(s -> s.startsWith("c"))
      .map(String::toUpperCase)
      .sorted()
      .forEach(System.out::println);
// Output: C1, C2
```

#### 2. Reduction
```java
List<Integer> numbers = Arrays.asList(3, 7, 8, 1, 5, 9);

int sum = numbers.stream()
                 .reduce(0, Integer::sum);
System.out.println("Sum: " + sum);
// Output: Sum: 33
```

#### 3. Collectors
```java
List<String> givenList = Arrays.asList("a", "bb", "ccc", "dd");

Map<Integer, Set<String>> result = givenList.stream()
    .collect(Collectors.groupingBy(String::length, Collectors.toSet()));
System.out.println(result);
// Output: {1=[a], 2=[bb, dd], 3=[ccc]}
```

### Advanced Concepts in Java Streams

1. **Stream Builders**: Apart from collections, arrays, or I/O channels, streams can also be built from functions (e.g., `Stream.iterate` and `Stream.generate`) for creating infinite streams.
   Example:
   ```java
   Stream<Integer> infiniteStream = Stream.iterate(0, n -> n + 2);
   infiniteStream.limit(5).forEach(System.out::println); // Output: 0, 2, 4, 6, 8
   ```

2. **Parallel Streams**: For performance improvement, especially in large data sets, streams can be processed in parallel. However, ensure that the operations are stateless and non-interfering.
   Example:
   ```java
   List<Integer> numberList = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
   int sumOfSquares = numberList.parallelStream()
                               .map(n -> n * n)
                               .reduce(0, Integer::sum);
   System.out.println(sumOfSquares); // Output: Sum of squares
   ```

3. **Short-circuiting Operations**: Operations that do not need to process the entire stream to produce a result, e.g., `findFirst`, `anyMatch`.
   Example:
   ```java
   List<String> stringList = Arrays.asList("abc", "def", "ghi");
   Optional<String> result = stringList.stream()
                                       .filter(s -> s.startsWith("d"))
                                       .findFirst();
   result.ifPresent(System.out::println); // Output: def
   ```

4. **Stream Concatenation**: Combining two or more streams into one.
   Example:
   ```java
   Stream<String> stream1 = Stream.of("A", "B", "C");
   Stream<String> stream2 = Stream.of("D", "E", "F");
   Stream<String> resultingStream = Stream.concat(stream1, stream2);
   resultingStream.forEach(System.out::println); // Output: A, B, C, D, E, F
   ```

5. **Advanced Collectors**: Beyond basic collectors like `toList`, `toSet`, and `toMap`, there are more complex ones like `joining`, `groupingBy`, `partitioningBy`.
   Example:
   ```java
   List<String> items = Arrays.asList("apple", "banana", "lemon", "orange");
   String result = items.stream()
                        .collect(Collectors.joining(", ", "[", "]"));
   System.out.println(result); // Output: [apple, banana, lemon, orange]
   ```

### Custom Class Example
Let's define a simple class, `Person`, with a few attributes:

```java
public class Person {
    private String name;
    private int age;
    private String city;

    public Person(String name, int age, String city) {
        this.name = name;
        this.age = age;
        this.city = city;
    }

    // Getters and setters for name, age, and city
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public int getAge() { return age; }
    public void setAge(int age) { this.age = age; }
    public String getCity() { return city; }
    public void setCity(String city) { this.city = city; }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + ", city='" + city + "'}";
    }
}
```

### Using Streams with the `Person` Class
Now, let's use this class with Java Streams to perform various operations:

1. **Creating a List and Filtering**:
   - Create a list of `Person` objects.
   - Use a stream to filter out persons who are under 25 years old.

   ```java
   List<Person> people = Arrays.asList(
       new Person("Alice", 23, "London"),
       new Person("Bob", 30, "New York"),
       new Person("Charlie", 27, "Paris")
   );

   List<Person> youngPeople = people.stream()
                                    .filter(p -> p.getAge() < 25)
                                    .collect(Collectors.toList());
   System.out.println(youngPeople);
   ```

2. **Mapping and Collecting**:
   - Map each `Person` to their name.
   - Collect the names into a list.

   ```java
   List<String> names = people.stream()
                              .map(Person::getName)
                              .collect(Collectors.toList());
   System.out.println(names);
   ```

3. **Grouping by a Property**:
   - Group `Person` objects by city.

   ```java
   Map<String, List<Person>> peopleByCity = people.stream()
                                                   .collect(Collectors.groupingBy(Person::getCity));
   System.out.println(peopleByCity);
   ```

4. **Finding an Element**:
   - Use `findFirst` to get the first person in the list who lives in "Paris".

   ```java
   Optional<Person> personInParis = people.stream()
                                          .filter(p -> "Paris".equals(p.getCity()))
                                          .findFirst();
   personInParis.ifPresent(System.out::println);
   ```

5. **Sorting**:
   - Sort people by age.

   ```java
   List<Person> sortedByAge = people.stream()
                                    .sorted(Comparator.comparingInt(Person::getAge))
                                    .collect(Collectors.toList());
   System.out.println(sortedByAge);
   ```

### Conclusion
In this example, we've seen how streams can be used to process collections of objects in a clear and functional way. 
Operations like filtering, mapping, grouping, sorting, and finding elements become much more intuitive and concise 
with streams. This example can be a practical part of your course, showing how streams are applied to real-world 
scenarios using custom classes.


### Best Practices for Using Java Streams
1. **Understand the Characteristics of the Data Source**: Before applying stream operations, consider the characteristics of the data source. For instance, some sources like `List` are more efficient with certain operations (like `filter`) than others (like `HashSet`).
2. **Choose the Right Operations**: Understand the difference between intermediate and terminal operations. Intermediate operations are lazy and only executed when a terminal operation is invoked. Use them efficiently to avoid unnecessary computations.
3. **Use Method References Where Possible**: Method references, e.g., `System.out::println` instead of `x -> System.out.println(x)`, make your stream operations more readable and can be more performance-efficient.
4. **Limit the Use of Parallel Streams**: While `parallelStream()` can offer performance benefits, it's not always the best choice. Parallel streams have overhead and are beneficial only for large data sets and computationally intensive operations. Use them judiciously after profiling the performance for your specific use case.
5. **Beware of Side Effects**: Avoid using operations that change the state of other objects or variables outside the stream’s pipeline (known as side effects). Streams are designed for "functional-style operations" where each step is a pure function.
6. **Ordering Matters**: Be aware that some operations like `sorted`, `limit`, or `distinct` can be costly in terms of performance. Also, the order of operations can have a significant impact on performance. For instance, applying a `filter` before `map` can reduce the number of elements to be processed.
7. **Take Advantage of Short-circuiting Operations**: Operations like `anyMatch`, `findFirst`, and `allMatch` can greatly reduce the processing time as they do not need to process the whole stream.
8. **Avoid Using Streams for Simple Tasks**: For simple tasks, traditional iterations might be more readable and efficient. Use streams when they provide a clear advantage in terms of readability or performance.
9. **Consider Collectors**: Understand the various `Collectors` available, and how they can be combined. For example, `Collectors.groupingBy` and `Collectors.joining` can be powerful tools for data manipulation and aggregation.
10. **Handling Exceptions**: Be cautious with exceptions in stream operations. Since lambda expressions do not allow checked exceptions without wrapping, consider the impact on your design and error handling.
11. **Reuse Stream Pipelines**: Design your stream operations in a way that they can be reused across different parts of your application. This not only improves the readability of your code but also helps in maintaining consistency.
12. **Test Stream Operations**: Ensure that your stream operations are covered by unit tests, especially when they involve complex data transformations or business logic.


### Recommended Resources
- [A Guide to Java Streams in Java: In-Depth Tutorial With Examples](https://stackify.com/streams-guide-java-8)
- [The Java 8 Stream API Tutorial](https://www.baeldung.com/java-8-streams)
- [Java 8 Stream Tutorial](https://www.geeksforgeeks.org/java-8-stream-tutorial)
- [Java 8 Stream - Java Stream](https://www.digitalocean.com/community/tutorials/java-8-stream)
- [Aggregate Operations](https://docs.oracle.com/javase/tutorial/collections/streams/index.html)


## Tasks

<details>
  <summary>Task 1: Stream Filtering and Mapping</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Stream Filtering and Mapping
## Description:
Using a list of integers, use a stream to filter out odd numbers and then map each remaining number to its square.

### _Inputs & Outputs:_
#### _Sample Input 1:_
[1, 2, 3, 4, 5]

#### _Sample Output 1:_
[4, 16]

#### _Sample Input 2:_
[6, 7, 8, 9, 10]

#### _Sample Output 2:_
[36, 64, 100]

</pre>
</details>

---

<details>
  <summary>Task 2: Stream Reduction</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Stream Reduction
## Description:
Given a list of strings, use a stream to concatenate them into a single string, separating each original string with a comma.

### _Inputs & Outputs:_
#### _Sample Input 1:_
["Java", "Streams", "Are", "Cool"]

#### _Sample Output 1:_
"Java,Streams,Are,Cool"

#### _Sample Input 2:_
["Hello", "World"]

#### _Sample Output 2:_
"Hello,World"

</pre>
</details>

---

<details>
  <summary>Task 3: Advanced Grouping with Streams</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Advanced Grouping with Streams
## Description:
Create a stream from a list of `Person` objects. Group them by city and then find the average age of people in each city.

### _Inputs & Outputs:_
#### _Sample Input 1:_
[Person("Alice", 23, "London"), Person("Bob", 30, "London"), Person("Charlie", 35, "New York")]

#### _Sample Output 1:_
{"London": 26.5, "New York": 35.0}

</pre>
</details>

---

<details>
  <summary>Task 4: Stream of Random Numbers</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Stream of Random Numbers
## Description:
Generate an infinite stream of random integers. Use this stream to find the first number greater than 100 that is also divisible by 5.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Random stream of integers

#### _Sample Output 1:_
A single integer (e.g., 105) - Note: Output will vary each time the program is run.

</pre>
</details>

---

<details>
  <summary>Task 5: Employee Management System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Employee Management System
## Description:
In an employee management system, create a class `Employee` with properties `id`, `name`, `department`, and `salary`. Use Java Streams to generate a report that lists the average salary in each department.

### Custom Class:
```java
public class Employee {
    private int id;
    private String name;
    private String department;
    private double salary;

    // Constructor, getters, and setters
}
```

### _Inputs & Outputs:_
#### _Sample Input 1:_
List of employees (e.g., [Employee(1, "Alice", "IT", 70000), Employee(2, "Bob", "Sales", 55000)])

#### _Sample Output 1:_
{"IT": 70000.0, "Sales": 55000.0}

#### _Sample Input 2:_
List of employees (e.g., [Employee(1, "Charlie", "IT", 60000), Employee(2, "David", "Sales", 65000), Employee(3, "Eve", "IT", 75000)])

#### _Sample Output 2:_
{"IT": 67500.0, "Sales": 65000.0}

</pre>
</details>

---

<details>
  <summary>Task 6: Product Inventory System</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# Product Inventory System
## Description:
In a product inventory system, create a class `Product` with properties `id`, `name`, `category`, and `price`. Use Java Streams to find the total value of all products in a specific category.

### Custom Class:
```java
public class Product {
    private int id;
    private String name;
    private String category;
    private double price;

    // Constructor, getters, and setters
}
```

### _Inputs & Outputs:_
#### _Sample Input 1:_
List of products (e.g., [Product(1, "Laptop", "Electronics", 1200), Product(2, "Smartphone", "Electronics", 800)])

#### _Sample Output 1:_
2000.0 (Total value of Electronics)

#### _Sample Input 2:_
List of products (e.g., [Product(1, "Chair", "Furniture", 150), Product(2, "Desk", "Furniture", 300)])

#### _Sample Output 2:_
450.0 (Total value of Furniture)

</pre>
</details>


