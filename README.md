# Lab 6: NumPy Arrays
**Weight:** 2% <br>
**Work Type:** Individual <br>
Environment: GitHub Codespaces
**Submission Format:** Screenshots

----

## Introduction

In this lab, you will work with **NumPy**, one of the most widely used Python libraries for numerical computing and data analysis.

NumPy provides support for efficient numerical operations using a powerful data structure called the **NumPy array**. Unlike regular Python lists, NumPy arrays are optimized for performance and allow fast, element-wise mathematical operations.

NumPy is widely used in:
- Data analytics
- Machine learning
- Scientific computing
- Cybersecurity data processing
- Network and log analysis

In this lab, you will create and manipulate NumPy arrays, perform mathematical and statistical operations, and apply basic data analysis techniques.

By the end of this lab, you will understand how NumPy arrays work and why they are essential for modern data analysis in Python.

----

## Lab Objectives

By the end of this lab, you will be able to:

- Import and use the NumPy library in Python
- Create one-dimensional (1D) and two-dimensional (2D) NumPy arrays
- Perform element-wise mathematical operations on arrays
- Compute basic statistical measures such as sum, mean, minimum, and maximum
- Access, index, and slice array elements
- Reshape arrays using built-in NumPy functions
- Apply NumPy arrays to simple data analysis tasks

----

## Before You Begin

Before starting this lab, ensure the following:

1. Open your GitHub repository and launch GitHub Codespaces.
3. Inside the repository, create six Python files:
   - `task1.py`
   - `task2.py`
   - `task3.py`
   - `task4.py`
   - `task5.py`
   - `task6.py`

4. At the top of each Python file, add your name and date in the comment section.
5. import the NumPy library:

```python
import numpy as np
```

----

# Submission Instructions
For each task:
1. Write the script in Codespaces or your local VSCode.  
2. Run the script from the terminal.  
3. Take a screenshot that clearly shows:  
   - Your **code** in the editor.  
   - The **terminal output**, including your **username** visible in the terminal.  
4. Insert the screenshot into a Word document under the heading that matches the task name:  
   - Example: **Task 1**, **Task 2**, **Task 3**, etc.  
5. After completing all tasks, convert the Word document to PDF.  Name the PDF file using your **yoursenecausername.pdf**
6. Submit the PDF file as your final lab submission on Blackbaord.

----

## INVESTIGATION 1: CREATING AND USING ARRAYS IN NumPy

NumPy is a Python library implemented in C language for creating and manipulating data in large arrays at speed. It provides:
- Multi-dimensional arrays (ndarray) that are much more efficient than Python lists.
- Mathematical operations on entire arrays without writing loops (vectorization).
- Statistical and linear algebra functions for scientific computing.
- Tools for reshaping, slicing, and manipulating data efficiently.

NumPy is the foundation for many other libraries such as Pandas, Matplotlib, SciPy, and Scikit-learn. In the slides you saw different ways of creating arrays and initializing them. This lab deals with testing your understanding of those methods discussed in the slides.

### Task 1 - Creating 1D Arrays and Array Attributes
**Objective:** Learn how to create NumPy arrays from Python lists.

NumPy, provides an array object similar to a list in Python but with added functionality for numerical operations.
```Python
import numpy as np  # Step 1: Import NumPy
# Creating a 1D array using a Python list
arr1 = np.array([1, 2, 3, 4, 5])
print("1D Array:", arr1)
```
**Instructions:**
- In `task1.py`, create a NumPy array containing the following numbers in a variable called  `array1 `:
``` yaml
10, 20, 30, 40, 50
```
- Print the array.
- Print the type of the object `array1 ` using the attribute `.dtype`
- Print the shape of the array using using the attribute `.shape`.
- Create the same array using `linspace` and save it in a variable called `array2`. Print this array.
- Run your script using the command: `python ./task1.py` and verify the output.

---

### Task2 - Array Arithmetic (Vectorized Operations, Broadcasting)
**Objective:** To practice performing element-wise arithmetic operations onNumPy arrays.

NumPy allows element-wise arithmetic on arrays, which is much faster and more concise than using Python loops. Broadcasting lets you perform operations on arrays of different shapes in a consistent way. Look at the example given below:
```Python
import numpy as np

# Create two 1D arrays
a = np.array([1, 2, 3])
b = np.array([10, 20, 30])

# Example of addition
print("Addition:", a + b)  # [11 22 33]

# Broadcasting example: adding a scalar to an array
print("Add 5 to each element:", a + 5)  # [6 7 8]

```
**Instructions:**
- In your task2.py file, create the following 1D arrays:
```Python
arr1 = np.array([2, 4, 6, 8])
arr2 = np.array([1, 3, 5, 7])
```
- Perform all of the following operations and print the results:
   - Addition using `arr1 + arr2`
   - Subtraction  `arr1 - arr2`
   - Multiplicationn `arr1 * arr2`
- Add 10 to each element of `arr1` using broadcasting and print print the updated array.
- Multiply each element of `arr2` by 2, and print the updated array.
- Run your script with the command: `python ./task2.py` and verify the output.
- In 2-4 sentences write down your reflections of these operations, why you did not have to use loops with Numpy arrays.

----

## Task 3 – Statistical Operations with NumPy
**Objective:** Learn how to use built-in NumPy functions to calculate basic statistical values from numerical data.

NumPy provides built-in functions that allow you to quickly compute statistical measures without writing loops.

In this task, you will use the following functions:

- `np.sum()` → Calculates the total of all values in an array  
- `np.mean()` → Calculates the average value  
- `np.max()` → Returns the largest value  
- `np.min()` → Returns the smallest value  

These functions are efficient and commonly used in data analysis and cybersecurity log analysis.

**Instructions:**
- In task3.py, create a NumPy array representing daily login attempts:
```yaml
15, 22, 13, 40, 30, 27, 18
```
Then calculate and print:
- The total number of login attempts.
- The average number of login attempts.
- The maximum number of login attempts.
- The minimum number of login attempts.
- Print clear labels with your output.
- Run your script with the command: `python ./task3.py` and verify the output.
- In 2-4 sentences, explain how NumPy arrays can be useful in Cybersecurity.

----

### Task4 - 2D Arrays (Matrix Form)
**Objective:** Learn how to create a two dimenstional NumPy arrays from Python lists and print its attributes.

NumPy can also create multi-dimensional arrays, which are useful for working with tabular or matrix-like data.
```Python
import numpy as np  # Step 1: Import NumPy
# Creating a 2D array (matrix) from a list of lists
arr2 = np.array([[1, 2, 3], [4, 5, 6]])
print("2D Array:\n", arr2)
```
**Instructions:**
- In task4.py, write code to create a 2D array (3 × 3) with values from 1 to 9. Save it in a variable called `array3`.
   ```yaml
   1  2  3
   4  5  6
   7  8  9
   ```
- Print the full matrix with a descriptive message, e.g. "3x3 Array:"
- Print the shape and size of array.
- Add 5 to each elements of array.
- Print the second row of array (Numpy arrays follow the same indiexing and slicing operations as Python lists).
- Print the third column of array.
- Run your script using the command: `python ./task4.py` and verify the output.
  
---

### Task 5 - Reshaping Arrays in NumPy
**Objective:** Learn how to change the shape of 1D arrays into 2D or 3D arrays using NumPy’s reshape() method, without modifying the array data.

Sometimes, you may need to change the shape of an array to make it suitable for certain calculations or to match the shape of other arrays. NumPy’s reshape() method allows you to transform 1D arrays into 2D or 3D arrays without changing the data. This is a key skill when working with numerical data in matrices.
```Python
import numpy as np

# Create a 1D array of 12 elements
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])
print("Original 1D Array:\n", arr)

# Reshape to a 3x4 2D array
arr2d = arr.reshape(3, 4)
print("\nReshaped to 3x4 Array:\n", arr2d)

# Reshape to 2x2x3 3D array
arr3d = arr.reshape(2, 2, 3)
print("\nReshaped to 2x2x3 Array:\n", arr3d)
```
**Instructions:**
- In your task5.py file, Create a 1D array with values from 1 to 12.
- Reshape it into a 3×4 matrix using `np.arange()` and print it.
- Reshape the same array into a 2×2×3 matrix using `.reshape()`and print it.
- Verify that the total number of elements is the same in all shapes.
- Run your script with the command: `python ./task5.py` and verify the output.

----

## Task 6 – Mini Data Analysis Challenge (Boolean Indexing)

**Objective:** Learn how to use Boolean indexing in NumPy to filter and analyze data based on conditions.

In data analytics and cybersecurity, we often need to filter data that meets specific conditions.  
NumPy allows this using **Boolean indexing**, which lets you select values from an array based on logical comparisons.

For example:
- `data > 1000` creates a Boolean array (True/False values)
- `data[data > 1000]` returns only the values that meet the condition

This technique is widely used in log analysis, anomaly detection, and traffic monitoring.

**Instructions:**

- You are given the following network packet sizes (in bytes):
```yaml
500, 1500, 800, 2000, 750, 1200, 3000
````
- In the file `task6.py`,cCreate a NumPy array with these values.
- Calculate the average packet size.
- Extract all packet sizes greater than 1000 bytes, use Boolean indexing (no loops allowed).
- Count how many packets are greater than 1000 bytes.
- Print clear and labeled output.
- Run your script with the command: `python ./task5.py` and verify the output.

----

## Lab 6 Sign-Off
- Submit a PDF on Blackboard, named using your Seneca username (e.g., **yoursenecausername.pdf**).
- The PDF must include screenshots of the following scripts and their terminal output, clearly showing your GitHub username.
    - task1.py
    - task2.py
    - task3.py
    - task4.py
    - task5.py
    - task6.py
- Ensure the code and output are clearly readable. Screenshots should be high-resolution (minimum 800x600) and not blurry.
- Blurry or unreadable submissions will be returned for redo. Resubmissions will only be graded as Satisfactory with a grade of 0, provided the work is satisfactory.
