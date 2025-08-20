# Lab 6
In this lab, you will create ten simple Python scripts. All scripts must be written in GitHub Codespaces. 
In this lab, you will learn how to work with NumPy and Pandas, two of the most widely used Python libraries for data analysis and scientific computing. You will begin by exploring the basics of NumPy arrays, performing mathematical operations, and manipulating array data. Then, you will transition to Pandas, where you will learn how to work with Series and DataFrames to handle, analyze, and visualize real-world datasets.
By the end of this lab, you will have a solid foundation in using these libraries for numerical computation and data analysis.

# Lab Objectives
- Understand the role of NumPy in numerical computing.
- Create and manipulate NumPy arrays.
- Perform mathematical and statistical operations on arrays.
- Understand the role of Pandas in data analysis.
- Create and manipulate Pandas Series and DataFrames.
- Perform filtering, grouping, and aggregations in Pandas.
- Apply both libraries to solve data-driven problems.# Submission Instructions

# Submission Instructions
For each task:
1. **Write the script** in Codespaces.  
2. **Run the script** from the **terminal**.  
3. **Take a screenshot** that clearly shows:  
   - Your **code** in the editor.  
   - The **terminal output**, including your **username** visible in the terminal.  
4. **Insert the screenshot** into a Word document under the heading that matches the task name:  
   - Example: **Lab6a**, **Lab6b**, **Lab6c**, etc.  
5. After completing all tasks, **convert the Word document to PDF**.  Name the PDF file using your **yoursenecausername.pdf**
6. **Submit the PDF file** as your final lab submission on Blackbaord.

## INVESTIGATION 1: CREATING AND USING ARRAYS IN NumPy

NumPy is a Python library implemented in C language for creating and manipulating data in large arrays at speed. It provides:
- Multi-dimensional arrays (ndarray) that are much more efficient than Python lists.
- Mathematical operations on entire arrays without writing loops (vectorization).
- Statistical and linear algebra functions for scientific computing.
- Tools for reshaping, slicing, and manipulating data efficiently.

NumPy is the foundation for many other libraries such as Pandas, Matplotlib, SciPy, and Scikit-learn. In the slides you saw different ways of creating arrays and initializing them. This lab deals with testing your understanding of those methods discussed in the slides.

### lab6a.py - Creating 1D Arrays
**Objective:** Learn how to create NumPy arrays from Python lists.

NumPy, provides an array object similar to a list in Python but with added functionality for numerical operations.
```Python
import numpy as np  # Step 1: Import NumPy
# Creating a 1D array using a Python list
arr1 = np.array([1, 2, 3, 4, 5])
print("1D Array:", arr1)
```
**Instructions:**
- In your lab6a.py file write code create an array with values from 20 to 49 (inclusive) using `np.arange()`. Save it in a variable called `array1`.
- Create the same array in a different way, for example either using `linspace` or a different method and save it in a variable called `array2`.
- Expected output (both arrays should look like):
  ```yaml
  [20 21 22 23 ... 49]
  ```
- Run your script using the command: `python ./lab6a.py` and verify the output.
---
### lab6b.py - Creating 2D Arrays and Array Attributes
**Objective:** Learn how to create a two dimenstional NumPy arrays from Python lists and print its attributes.

NumPy can also create multi-dimensional arrays, which are useful for working with tabular or matrix-like data.
```Python
import numpy as np  # Step 1: Import NumPy
# Creating a 2D array (matrix) from a list of lists
arr2 = np.array([[1, 2, 3], [4, 5, 6]])
print("2D Array:\n", arr2)
```
**Instructions:**
- In your lab6b.py file create a 2D array (3 × 3) with values from 1 to 9. Save it in a variable called `array3`.
- Print your array with a descriptive message, e.g. "3x3 Array:"
- Expected output of the array is:
```yaml
[[1 2 3]
 [4 5 6]
 [7 8 9]]
```
- Next print the following attributes of `array3`.
   - array3.shape → should show (3, 3)
   - array3.size → should show 9
   - array3.dtype → data type of the elements
- Run your script using the command: `python ./la6b.py` and verify the output.
---
### lab6c.py - Accessing and Modifying Elements (Indexing and Slicing)
**Objective:** Learn how to apply common slicing scenarios in 1D arrays.

NumPy arrays allow you to access and modify elements using indexing and slicing. This works similarly to Python lists, but NumPy also supports powerful multi-dimensional indexing. Look at the examples below. You may want to run this code and observe the output.
```Python
import numpy as np

arr1 = np.array([2, 4, 6, 8, 10, 12, 14])
print("Original 1D Array:", arr1)

# Indexing
print("First element:", arr1[0])
print("Last element:", arr1[-1])

# Slicing
print("Elements from index 1 to 4:", arr1[1:5])       # middle elements
print("Elements from start to index 4 (exclusive):", arr1[:4])
print("Elements from index 3 to the end:", arr1[3:])
print("Elements with a step of 2:", arr1[::2])

# Modifying values
arr1[1] = 99
print("Modified 1D Array:", arr1)

```
**Instructions:**
- Create a 1D NumPy array with values [3, 6, 9, 12, 15, 18, 21].
- Print:
   - The first element
   - The last element
   - Elements from index 2 to end
   - Elements with a step of 3
- Modify the second element (index 1) to 99 and print the updated array.
- Run your script with the command: `python ./lab6c.py` and verify the output.
---
### lab6d.py - Indexing and Slicing on 2D Array
**Objective:** Learn how to apply common slicing scenarios in 2D arrays.
You are given some examples below, you may want to run this code and observe the output.
```Python
import numpy as np

# Create a 2D array with 3 rows and 4 columns
arr2d = np.array([[1, 2, 3, 4],
                  [5, 6, 7, 8],
                  [9, 10, 11, 12]])

print("Original 2D Array:\n", arr2d)

# Access a single element: row 0, column 2
print("Element at row 0, col 2:", arr2d[0, 2])  # Output: 3

# Access a full row: row 1 (second row)
print("Second row:", arr2d[1, :])  # Output: [5 6 7 8]

# Access a full column: column 3 (fourth column)
print("Fourth column:", arr2d[:, 3])  # Output: [ 4  8 12]

# Slice a subarray: first 2 rows and first 3 columns
print("Subarray (first 2 rows, first 3 columns):\n", arr2d[0:2, 0:3])
# Output:
# [[1 2 3]
#  [5 6 7]]
```
**Instructions:**
- Create a 2D array with values 1–12 arranged in 3 rows × 4 columns. Save it in `array2`.
- Print the following using indexing and slicing::
   - Element at row 1, column 2
   - First row
   - Third column
   - Subarray of the first 2 rows and first 2 columns
- Run your script with the command: `python ./lab6d.py` and verify the output.
---
### lab6e.py - Arithmetic Operations and Broadcasting in NumPy
**Objective:** To practice performing element-wise arithmetic operations on 1D and 2D NumPy arrays.

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
- In your lab6e.py file, create the following 1D arrays:
```Python
arr1 = np.array([2, 4, 6, 8])
arr2 = np.array([1, 3, 5, 7])
```
- Perform all of the following operations and print the results:
   - Addition
   - Subtraction
   - Multiplication
- Add 10 to each element of `arr1` using broadcasting and print print the updated array.
- Multiply each element of `arr2` by 2, and print the updated array
- Create a 2D array of your choice of elements.
- Add 5 to all elements and print your array.
- Run your script with the command: `python ./lab6e.py` and verify the output.
---
### lab6f.py - Reshaping Arrays in NumPy
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
- Create a 1D array with values from 1 to 12.
- Reshape it into a 3×4 2D array and print it.
- Reshape the same array into a 2×2×3 3D array and print it.
- Verify that the total number of elements is the same in all shapes.
- Run your script with the command: `python ./lab6f.py` and verify the output.

## INVESTIGATION 2: CREATING AND USING SERIES AND DATA FRAMES FROM Pandas
Pandas is a Python library used for data manipulation and analysis. It provides two main data structures:
- Series – a one-dimensional labeled array, similar to a column in a spreadsheet or a 1D NumPy array with labels.
- DataFrame – a two-dimensional labeled data structure, like a table with rows and columns.
Why use Pandas:
- Easily handle tabular data.
- Perform filtering, grouping, and aggregation.
- Combine multiple datasets efficiently.

### lab6g.py - Reshaping Arrays in NumPy
**Objective:** Learn how to create Pandas Series with values, index labels, and a name, and access elements by position or label.

A Pandas Series is like a single column of data with labels (index) for each element. It can also have a name, similar to a column title in a spreadsheet. Series can be created from lists, NumPy arrays, or dictionaries.
Look at the example given below:
```Python
import pandas as pd
import numpy as np

# Series from a list
series_list = pd.Series([10, 20, 30, 40], name="Scores")
print("Series from list:\n", series_list)

# Series from a NumPy array
arr = np.array([1, 2, 3, 4])
series_array = pd.Series(arr)
print("\nSeries from NumPy array:\n", series_array)
```
**Instructions:**
- In the file Lab6g.py, create a numeric series from a Python list: [5, 10, 15, 20] and name it `Numbers`.
- Create a numeric series from a NumPy array [2, 4, 6, 8] and name it `Evens`.
- Create a numeric series from a dictionary: {'Alice': 25, 'Bob': 30, 'Charlie': 35} and name it `Ages`.
- Create a string Series for grades and name st `Grades`:
   - Values: ["<50", "50-59", "60-69", "70-79", "80-89", "90-100"]
   - Index labels: ["F", "D", "C", "B", "A", "A+"]
- Print all Series.
- Print the first and last elements of `Numbers`, `Evens`.
- Print the value for "Bob" from series_ages (use label-based indexing)
- Print the values for indices "C" and "A+" from `Grades`.
- Print the value "60-69" directly without the index.
- Run your script with the command: `python ./lab6g.py` and verify the output.
---


## Lab 6 Sign-Off
- Submit a PDF on Blackboard, named using your Seneca username (e.g., **yoursenecausername.pdf**).
- The PDF must include screenshots of the following scripts and their terminal output, clearly showing your GitHub username.
    - lab6a.py
    - lab6b.py
    - lab6c.py
    - lab6d.py
    - lab6e.py
    - lab6f.py
    - lab6g.py
    - lab6h.py
    - lab6i.py
    - lab6j.py
