### Introduction to Two-Dimensional Arrays
A two-dimensional array is an array that has other arrays as its elements. You can visualize it as a table with rows 
and columns. For instance, if you want to store a 3x3 matrix, you'd use a two-dimensional array.

### Declaring a Two-Dimensional Array
Syntax:
```java
dataType[][] arrayName = new dataType[numberOfRows][numberOfColumns];
```

Example:
```java
int[][] matrix = new int[3][3];
```

### Initializing a Two-Dimensional Array
There are multiple ways to initialize a 2D array:

1. At the time of declaration:
```java
int[][] matrix = { {1, 2, 3}, {4, 5, 6}, {7, 8, 9} };
```

2. After declaration:
```java
int[][] matrix = new int[3][3];
matrix[0][0] = 1;
matrix[0][1] = 2;
// ... and so on
```

### Looping through a Two-Dimensional Array
To loop through a 2D array, you would generally use nested loops:

```java
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println(); // Move to the next line after printing a row
}
```

### Practical Example: Matrix Transposition

Let's transpose a 3x3 matrix (swap rows with columns):

```java
public class MatrixTranspose {
    public static void main(String[] args) {
        int[][] matrix = { {1, 2, 3}, {4, 5, 6}, {7, 8, 9} };
        int[][] transposed = new int[3][3];

        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                transposed[j][i] = matrix[i][j];
            }
        }

        // Print the transposed matrix
        for (int[] ints : transposed) {
            for (int anInt : ints) {
                System.out.print(anInt + " ");
            }
            System.out.println(); // Move to the next line after printing a row
        }
    }
}
```

### Points to Remember:
1. A two-dimensional array is essentially an array of arrays.
2. Each row in a two-dimensional array can, technically, have a different number of columns, though it's common to see matrices with uniform columns.
3. Always ensure you are not accessing an index outside the array bounds to avoid `ArrayIndexOutOfBoundsException`.


### Recommended Resources
- [Matrix Programs in Java](https://www.digitalocean.com/community/tutorials/matrix-programs-in-java)
- [Java Multidimensional Arrays](https://www.programiz.com/java-programming/multidimensional-array)


## Tasks

<details>
  <summary>Task 1: Matrix Sum</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Matrix Sum**
## **Description:**
Write a program that accepts an NxN matrix from the user and calculates the sum of its elements. The user will first input N, followed by the elements of the matrix.

### _Inputs & Outputs:_

#### _Sample Input 1:_
Size of matrix (N): 2  
Enter element [0][0]: 1  
Enter element [0][1]: 2  
Enter element [1][0]: 3  
Enter element [1][1]: 4

#### _Sample Output 1:_
The sum of the matrix elements is: 10.

#### _Sample Input 2:_
Size of matrix (N): 3  
Enter element [0][0]: 1  
Enter element [0][1]: 2  
Enter element [0][2]: 3  
Enter element [1][0]: 4  
Enter element [1][1]: 5  
Enter element [1][2]: 6  
Enter element [2][0]: 7  
Enter element [2][1]: 8  
Enter element [2][2]: 9

#### _Sample Output 2:_
The sum of the matrix elements is: 45.

#### _Sample Input 3:_
Size of matrix (N): 4  
Enter element [0][0]: 1  
Enter element [0][1]: 2  
Enter element [0][2]: 3  
Enter element [0][3]: 4  
Enter element [1][0]: 5  
Enter element [1][1]: 6  
Enter element [1][2]: 7  
Enter element [1][3]: 8  
Enter element [2][0]: 9  
Enter element [2][1]: 10  
Enter element [2][2]: 11  
Enter element [2][3]: 12  
Enter element [3][0]: 13  
Enter element [3][1]: 14  
Enter element [3][2]: 15  
Enter element [3][3]: 16

#### _Sample Output 3:_
The sum of the matrix elements is: 136.

</pre>
</details>

---

<details>
  <summary>Task 2: Diagonal Elements</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Diagonal Elements**
## **Description:**
Write a program that reads a 3x3 matrix and prints the elements of both the main diagonal and the secondary diagonal.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter element [0][0]: 1  
Enter element [0][1]: 2  
Enter element [0][2]: 3  
Enter element [1][0]: 4  
Enter element [1][1]: 5  
Enter element [1][2]: 6  
Enter element [2][0]: 7  
Enter element [2][1]: 8  
Enter element [2][2]: 9

#### _Sample Output 1:_
Main Diagonal: 1, 5, 9  
Secondary Diagonal: 3, 5, 7

</pre>
</details>

---

<details>
  <summary>Task 3: Matrix Transpose</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Matrix Transpose**
## **Description:**
Given a 2x3 matrix, write a program to transpose it into a 3x2 matrix.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter element [0][0]: 1  
Enter element [0][1]: 2  
Enter element [0][2]: 3  
Enter element [1][0]: 4  
Enter element [1][1]: 5  
Enter element [1][2]: 6

#### _Sample Output 1:_
Transposed Matrix:  
1 4  
2 5  
3 6

</pre>
</details>

---

<details>
  <summary>Task 4: Matrix Multiplication</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Matrix Multiplication**
## **Description:**
Write a program to multiply two 2x2 matrices entered by the user.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter matrix A elements:  
Enter element [0][0]: 1  
Enter element [0][1]: 2  
Enter element [1][0]: 3  
Enter element [1][1]: 4

Enter matrix B elements:  
Enter element [0][0]: 2  
Enter element [0][1]: 0  
Enter element [1][0]: 1  
Enter element [1][1]: 3

#### _Sample Output 1:_
Resultant Matrix:  
4 6  
10 12

</pre>
</details>

---

<details>
  <summary>Task 5: Find the Highest Average</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Matrix Explorer**
## **Description:**
Write a program that takes scores of students in multiple subjects and finds the student with the highest average score.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Number of students: 3  
Number of subjects: 2  
Enter scores for student 1:  
Math: 85  
Science: 90

Enter scores for student 2:  
Math: 78  
Science: 82

Enter scores for student 3:  
Math: 92  
Science: 88

#### _Sample Output 1:_
Student 3 has the highest average score of 90.0

</pre>
</details>

---

<details>
  <summary>Task 6: Pattern Recognition</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Pattern Hunter**
## **Description:**
Write a program that recognizes if the given 3x3 matrix is symmetric around its main diagonal.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter element [0][0]: 1  
Enter element [0][1]: 2  
Enter element [0][2]: 3  
Enter element [1][0]: 2  
Enter element [1][1]: 4  
Enter element [1][2]: 5  
Enter element [2][0]: 3  
Enter element [2][1]: 5  
Enter element [2][2]: 6

#### _Sample Output 1:_
The matrix is symmetric around its main diagonal.

</pre>
</details>

---

<details>
  <summary>Task 7: Boundary Elements</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Border Keeper**
## **Description:**
Write a program that accepts a 4x4 matrix and prints the boundary elements.

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter element [0][0]: 1  
...  
Enter element [3][3]: 16

#### _Sample Output 1:_
Boundary Elements: 1, 2, 3, 4, 8, 12, 16, 15, 14, 13, 9, 5

</pre>
</details>

---

<details>
  <summary>Task 8: Anti-Diagonal Elements</summary>
<pre style="background-color: #333; color: lime; padding: 10px; border-radius: 5px;">

# **Reverse Diagonal Inspector**
## **Description:**
Given a 4x4 matrix, write a program to print the elements of the anti-diagonal (from bottom-left to top-right).

### _Inputs & Outputs:_
#### _Sample Input 1:_
Enter element [0][0]: 1  
...  
Enter element [3][3]: 16

#### _Sample Output 1:_
Anti-Diagonal Elements: 13, 10, 7, 4

</pre>
</details>


