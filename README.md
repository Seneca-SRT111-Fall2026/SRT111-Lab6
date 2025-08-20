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

### lab16a.py - Creating 1D Arrays
**Objective:** Learn how to create NumPy arrays from Python lists.

NumPy, provides an array object similar to a list in Python but with added functionality for numerical operations.
```Python
import numpy as np  # Step 1: Import NumPy
# Creating a 1D array using a Python list
arr1 = np.array([1, 2, 3, 4, 5])
print("1D Array:", arr1)
```

- In your lab6a.py file write code create an array with values from 20 to 49 (inclusive) using `np.arange()`. Save it in a variable called `array1`.
- Create the same array in a different way, for example either using `linspace` or a different method and save it in a variable called `array2`.
- Expected output (both arrays should look like):
  ```yaml
  [20 21 22 23 ... 49]
  ```
- Run your script using the command: `python ./lab6a.py` and verify the output.

### lab16b.py - Creating 2D Arrays
**Objective:** Learn how to create a two dimenstional NumPy arrays from Python lists.

NumPy can also create multi-dimensional arrays, which are useful for working with tabular or matrix-like data.
```Python
import numpy as np  # Step 1: Import NumPy
# Creating a 2D array (matrix) from a list of lists
arr2 = np.array([[1, 2, 3], [4, 5, 6]])
print("2D Array:\n", arr2)
```
- In your lab6b.py file create a 2D array (3 × 3) with values from 1 to 9. Save it in a variable called `array3`.
- Print your array with a descriptive message, e.g. "3x3 Array:"
- Expected output (both arrays should look like):
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
