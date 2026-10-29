<h1 align="center">SRT111 Lab 6 - Fall 2026</h1>

<p align="center">
<b>Prepared by:</b> Tiayyba Riaz<br>
<b>Total Marks:</b> 10<br>
<b>Percentage Towards Final Grade:</b> 2%
</p>

In Lab 5, your programs read from and wrote to files. But what happens when the file is missing, or a line that should hold a number contains `abc`? Python stops the program and prints a traceback. In the first part of this lab, you will learn how to **handle exceptions** with `try`, `except` and `finally`, and how to **raise** your own exceptions, so your programs recover from errors instead of crashing.

In the second part, you will work with **NumPy**, one of the most widely used Python libraries for numerical computing and data analysis. NumPy is written in C for speed and provides the **NumPy array** (`ndarray`), a grid of values that is much faster than a Python list and lets you do maths on a whole array at once, without writing loops. NumPy is the foundation for libraries such as Pandas, Matplotlib and Scikit-learn, and it is used in data analytics, machine learning, scientific computing, and cybersecurity log and network analysis. The last task brings both topics together: you will load network data from a file safely and analyse it with NumPy.

You will continue to use functions and a `main()` function to organize your programs, as practised in Labs 4 and 5.

The lab is divided into two components:

- **Part A: In-Class Lab** (must be completed during the scheduled lab period and demonstrated to the professor for grading).
- **Part B: Take-Home Lab** (can be completed independently after the scheduled class and is submitted as a link to your GitHub repository).

## Academic Integrity and Use of AI

This lab is intended to assess your individual understanding of Python programming. You may use AI tools (e.g., ChatGPT, Copilot, Gemini) to help explain concepts, syntax, or error messages. However, all submitted code must be your own work, and you must be able to explain your solution if asked by the professor.

Submitting copied, shared, or AI-generated solutions as your own work may result in a grade of zero and may be handled according to the College Academic Integrity Policy.

## Lab Objectives

By the end of this lab, you should be able to:

- Explain what an exception is and what happens when a program does not handle one.
- Use `try` and `except` to handle `ValueError`, `ZeroDivisionError` and `FileNotFoundError`.
- Use several `except` clauses, `except ... as exception`, and a `finally` clause.
- Use the `raise` statement to signal an error in your own function, and handle it in the caller.
- Import NumPy and create 1D, 2D and 3D arrays with `np.array()`, `np.linspace()`, `np.arange()`, `np.zeros()`, `np.ones()`, `np.diag()` and `np.eye()`.
- Use the array attributes `ndim`, `shape`, `size` and `dtype`.
- Perform element-wise arithmetic and broadcasting, and compute sum, mean, median, maximum and minimum.
- Index, slice and reshape arrays, and calculate row and column totals with `axis`.
- Filter data with Boolean indexing.
- Combine file reading, exception handling and NumPy in one program.

## Required Comment Header

For every script created in this lab include the following comment block at the top of the file/cell.

```python
# Author: Your Name
# Date: YYYY-MM-DD
# Purpose: Brief description of what the program does.
```

## Data Files

Some tasks read from text files. The text of every file is given in the task that uses it. Create each file with exactly that text, **in the same folder as your script or notebook**.

| File | Used in |
|---|---|
| `number.txt`, `badnumber.txt` | Task 2 |
| `packets.txt` | Task 7 |

`missing.txt` is used in Tasks 2 and 7, but you must **not** create it. Those tasks test what your program does when a file does not exist.

---

## Part A - In-Class Lab [30% of Lab Marks]

Complete all assigned in-class tasks during your scheduled lab.

**Part A Marking (3 marks):**

| Task | Marks |
|---|---|
| Task 1 - Catching Errors with try/except | 1.0 |
| Task 2 - Handling Different Exceptions When Reading a File | 1.0 |
| Task 3 - Raising Your Own Exceptions | 1.0 |
| **Total** | **3** |

- This part can be completed in Jupyter Lab or VS Code. You have a choice. I recommend using Jupyter Lab.
  - If you are using Jupyter Lab, then please create a single notebook file called `Lab6.ipynb` and complete each task in a unique cell. Create the data files in the same folder as the notebook.
  - If you are using VS Code, then just follow the instructions for each task and create `.py` files.
- Demonstrate your completed work to the professor before leaving the lab.
- The professor may ask you to explain portions of your code.
- No submission is required for Part A unless otherwise instructed.

<details markdown="1">

<summary><b>Quick Reference: Exceptions and try/except</b></summary>

<br>

An **exception** is an error that happens while the program is running (a **run-time error**). If nothing handles it, Python prints a traceback and **stops** the program.

| Code | Exception raised | Why |
|---|---|---|
| `int("ten")` | `ValueError` | The string is not a whole number |
| `10 / 0` | `ZeroDivisionError` | You cannot divide by zero |
| `open("missing.txt", "r")` | `FileNotFoundError` | The file does not exist |
| `[1, 2, 3][5]` | `IndexError` | The index is outside the list |

**Handling an exception**

```python
try:
    # code that MIGHT cause an error
    age = int(input("Enter your age: "))
    print("Next year you will be", age + 1)
except ValueError:
    # runs ONLY if a ValueError happens in the try block
    print("Please enter a whole number.")
print("The program keeps going.")
```

- If no error happens, the `except` block is skipped.
- If an error happens, the rest of the `try` block is **skipped** and Python jumps to the matching `except` block. After it, the program continues normally.
- Name the exception you expect, such as `except ValueError:`. A bare `except:` hides every error, including mistakes in your own code.

**Asking again until the input is valid** (the user-friendly way to handle an error):

```python
while True:
    try:
        value = int(input("Enter a number: "))
        break                  # only reached if int() worked
    except ValueError:
        print("Not a number. Try again.")
```

A `return` inside the `try` block works the same way as `break`: it leaves the loop and the function.

</details>

### Task 1 - Catching Errors with try/except

**Objective:** Practice catching a `ValueError` and a `ZeroDivisionError`, and asking the user to correct their input instead of letting the program crash.

**Instructions:**

- Create a file named `task1.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header:

  ```python
  def get_integer(prompt):
      # 1. Use a while True loop
      # 2. Inside the loop, use try to convert input(prompt) to an int and return it
      # 3. If a ValueError happens, print: That is not a whole number. Please try again.
      pass


  def divide(a, b):
      # 1. Use try to calculate a / b and return the result
      # 2. If a ZeroDivisionError happens, print: Error: you cannot divide by zero.
      #    and return None
      pass


  def main():
      numerator = get_integer("Enter the numerator: ")
      denominator = get_integer("Enter the denominator: ")
      result = divide(numerator, denominator)
      if result is not None:
          print(numerator, "/", denominator, "=", result)
      print("Program finished normally.")


  main()
  ```

- Complete the two functions by following the numbered comments inside each one. Do not change `main()`.
- Run your script twice, typing the input shown in the two sample runs below.

**Expected Output (Run 1, the user types `ten`, then `10`, then `4`):**

```text
Enter the numerator: ten
That is not a whole number. Please try again.
Enter the numerator: 10
Enter the denominator: 4
10 / 4 = 2.5
Program finished normally.
```

**Expected Output (Run 2, the user types `10`, then `0`):**

```text
Enter the numerator: 10
Enter the denominator: 0
Error: you cannot divide by zero.
Program finished normally.
```

> **Think about it:** Temporarily remove the `try` and `except` lines from `divide()` (keep `return a / b`) and run it again with `0` as the denominator. Read the last line of the traceback. The name it shows, `ZeroDivisionError`, is exactly the name you write after `except`. Put your code back before you demonstrate your work.

<details markdown="1">

<summary><b>Quick Reference: Several except Clauses, "as", and finally</b></summary>

<br>

One `try` block can have several `except` clauses, one for each kind of error. Python runs the **first** one that matches.

```python
try:
    infile = open(filename, "r")       # open() can raise FileNotFoundError
    line = infile.readline()
    infile.close()
    value = int(line.strip())          # int() can raise ValueError
except FileNotFoundError:
    print("Error: file not found.")
except ValueError as exception:        # 'as' saves the exception in a variable
    print("Error:", str(exception))    # str() gives Python's own error message
finally:
    print("Done.")                     # ALWAYS runs, error or not
```

- `except ValueError as exception:` lets you print the message that Python created, such as `invalid literal for int() with base 10: 'abc'`.
- The `finally` clause runs whether or not an exception happened. It is used for clean-up that must always happen, such as closing a file.
- The `with` statement is a shortcut for `try`/`finally` when working with files: it closes the file even if an error happens.

</details>

### Task 2 - Handling Different Exceptions When Reading a File

**Objective:** Practice handling two different exceptions with two `except` clauses, printing Python's error message with `as`, and using `finally`.

**Instructions:**

- Create a file named `number.txt` in the same folder as your script, containing this single line:

  ```text
  25
  ```

- Create a file named `badnumber.txt` containing this single line:

  ```text
  twenty five
  ```

- Do **not** create a file named `missing.txt`.
- Create a file named `task2.py` and add the required comment header.
- Write a function named `read_first_number` that:
  - Takes a file name, `filename`, as a parameter.
  - Inside a `try` block:
    - Opens the file in read mode, reads the first line with `readline()`, and closes the file.
    - Converts the line to an integer with `int()`. Use `strip()` first, so the `\n` is removed.
    - Prints `The first number in <filename> is <value>`.
  - Has an `except FileNotFoundError:` clause that prints `Error: the file <filename> was not found.`
  - Has an `except ValueError as exception:` clause that prints `Error:` followed by `str(exception)`.
  - Has a `finally:` clause that prints `Finished checking <filename>`.
- Write a `main()` function that calls `read_first_number()` three times, with `"number.txt"`, `"missing.txt"` and `"badnumber.txt"`, in that order.
- Add a call to the `main()` function.
- Run your script to test it.

**Expected Output:**

```text
The first number in number.txt is 25
Finished checking number.txt
Error: the file missing.txt was not found.
Finished checking missing.txt
Error: invalid literal for int() with base 10: 'twenty five'
Finished checking badnumber.txt
```

> **Note:** `Finished checking ...` appears after every file, including the two that failed. That is what `finally` is for. The program also keeps running after each error, so all three files are checked.

<details markdown="1">

<summary><b>Quick Reference: Raising an Exception</b></summary>

<br>

Built-in functions such as `int()` and `open()` raise exceptions when something is wrong. Your own functions can do the same with the `raise` statement:

```python
def set_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")   # stops the function here
    return age
```

- When `raise` runs, the function stops immediately. The next line does **not** run, and nothing is returned.
- Control jumps to the `except` block of the code that **called** the function:

  ```python
  try:
      age = set_age(-5)
      print("Age set to", age)          # skipped, because set_age() raised
  except ValueError as exception:
      print("Problem:", str(exception)) # Problem: Age cannot be negative
  ```

- The function **detects** the error. The caller decides how to **handle** it.

</details>

### Task 3 - Raising Your Own Exceptions

**Objective:** Practice detecting an error with `raise` inside a function, and handling it with `try`/`except` in the caller.

A bank must not let a customer withdraw more money than they have, or withdraw a negative amount. The `withdraw()` function will detect these problems and raise an exception. `main()` will handle it, so one bad withdrawal does not stop the others.

**Instructions:**

- Create a file named `task3.py` and add the required comment header.
- Write a function named `withdraw` that:
  - Takes two parameters: `balance` and `amount`.
  - Raises a `ValueError` with the message `Amount must be greater than zero` if `amount` is zero or less.
  - Raises a `ValueError` with the message `Amount exceeds balance` if `amount` is greater than `balance`.
  - Otherwise, returns the new balance (`balance - amount`).
  - Does **not** use `print()` or `try`/`except`. It only raises.
- Write a `main()` function that:
  - Sets `balance` to `500` and creates the list `withdrawals = [100, 600, -50, 250]`.
  - Prints `Starting balance: 500`.
  - Uses a `for` loop over `withdrawals`. For each amount, inside a `try` block, it calls `withdraw()`, stores the result in `balance`, and prints `Withdrew <amount> - new balance: <balance>`.
  - If a `ValueError` is raised, prints `Withdrawal of <amount> failed: <message>`.
  - After the loop, prints `Final balance: <balance>`.
- Add a call to the `main()` function.
- Run your script to test it.

**Expected Output:**

```text
Starting balance: 500
Withdrew 100 - new balance: 400
Withdrawal of 600 failed: Amount exceeds balance
Withdrawal of -50 failed: Amount must be greater than zero
Withdrew 250 - new balance: 150
Final balance: 150
```

> **Think about it:** Why does the balance stay at `400` after the failed withdrawal of `600`? Look at what happens to the line `balance = withdraw(balance, amount)` when `withdraw()` raises an exception.

---

## Part B - Take-Home Lab [70% of Lab Marks]

Complete the following tasks independently after the scheduled lab using VS Code.

**Part B Marking (7 marks):**

| Task | Marks |
|---|---|
| Task 4 - Creating NumPy Arrays and Their Attributes | 1.5 |
| Task 5 - Array Arithmetic and Statistics | 1.5 |
| Task 6 - Indexing, Slicing and Reshaping 2D Arrays | 2.0 |
| Task 7 - Safe Packet Analysis (Files + Exceptions + NumPy) | 2.0 |
| Submission requirements (exact repo, folder and file names, comment headers, code pushed to GitHub) | up to 100% deduction may apply |
| **Total** | **7** |

> Marks are awarded only when the required functions and methods are used as instructed. Correct output alone is not enough.

**Before You Begin:**

- Open your local Git repository `SRT111F2026` on your computer.
- Create a new folder named `Lab06` inside the repository (capital `L`, then a zero: `Lab06`).
- Open the `Lab06` folder in VS Code.
- Create all Part B files inside the `Lab06` folder. Use these names **exactly**, all in lower case:
  - `task4.py`, `task5.py`, `task6.py`, `task7.py`
  - `packets.txt`
- Make sure NumPy is installed. In the VS Code terminal, run:

  ```text
  python -m pip install numpy
  ```

  On a Mac, use `python3` instead of `python` if `python` is not found.

**For each task:**

- Run the script using the VS Code terminal and compare your output with the expected output.
- Some tasks ask you to answer a question in a **comment** at the bottom of your script. These answers are marked, so do not skip them.
- No screenshots or PDF are required for this lab. Your code in GitHub is your submission.

<details markdown="1">

<summary><b>Quick Reference: Creating NumPy Arrays</b></summary>

<br>

**Import NumPy once, at the top of the script.** By convention it is given the short name `np`:

```python
import numpy as np
```

**Creating arrays**

| Code | Result | What it does |
|---|---|---|
| `np.array([1, 2, 3])` | `[1 2 3]` | 1D array from a list |
| `np.array([[1, 2], [3, 4]])` | `[[1 2]` <br> ` [3 4]]` | 2D array from a list of lists (one inner list per row) |
| `np.arange(0, 10, 2)` | `[0 2 4 6 8]` | Start, stop (**not** included), step, like `range()` |
| `np.linspace(0, 1, 5)` | `[0.   0.25 0.5  0.75 1.  ]` | 5 evenly spaced values from start to stop (**included**) |
| `np.zeros([2, 3])` | 2 rows, 3 columns of `0.` | Array filled with zeros |
| `np.ones(4)` | `[1. 1. 1. 1.]` | Array filled with ones |
| `np.diag((4, 6, 1))` | 3x3 with `4, 6, 1` on the diagonal | Diagonal matrix, every other value is 0 |
| `np.eye(3)` | 3x3 with `1.` on the diagonal | Identity (unity) matrix |

**Array attributes** (no brackets, because they are attributes, not methods)

| Attribute | Meaning | For `np.array([[1, 2, 3], [4, 5, 6]])` |
|---|---|---|
| `arr.ndim` | Number of dimensions | `2` |
| `arr.shape` | Size of each dimension, as a tuple | `(2, 3)` (2 rows, 3 columns) |
| `arr.size` | Total number of elements | `6` |
| `arr.dtype` | Type of every element | `int64` |

- Every element of a NumPy array has the **same type**. The `.` after a number, as in `1.`, means it is a float.
- A 1D shape is written with a comma, such as `(5,)`, because it is a tuple with one value.

</details>

### Task 4 - Creating NumPy Arrays and Their Attributes

**Objective:** Practice creating arrays in different ways and inspecting them with `ndim`, `shape`, `size` and `dtype`.

**Instructions:**

- In your `Lab06` folder, create the file `task4.py`, add the required comment header, and import NumPy as `np`.
- Write a function named `print_info` that:
  - Takes two parameters: a text `label` and a NumPy array `arr`.
  - Prints the label, then the array.
  - Prints the four attributes on one line in this format: `ndim: <ndim> | shape: <shape> | size: <size> | dtype: <dtype>`
  - Prints an empty line.
- Write a function named `create_arrays` that creates the following arrays and calls `print_info()` for each one, using the labels shown in the expected output:
  - `array1`: the values `10, 20, 30, 40, 50, 60, 70, 80, 90, 100`, created with `np.array()`.
  - `array2`: the same ten values, created with `np.linspace()`.
  - `array3`: the same ten values, created with `np.arange()`.
  - `array4`: a 2D array with the rows `1, 2, 3` and `4, 5, 6`, created with `np.array()`.
- Write a function named `create_special_arrays` that calls `print_info()` for each of these arrays:
  - A 2x4 array of zeros, created with `np.zeros()`.
  - A 1D array of five ones, created with `np.ones()`.
  - A 4x4 diagonal matrix with `4, 6, 1, 3` on the diagonal, created with `np.diag()`.
  - A 3x3 identity matrix, created with `np.eye()`.
- Write a `main()` function that prints `=== Creating arrays ===`, calls `create_arrays()`, prints `=== Special arrays ===`, and calls `create_special_arrays()`.
- Add a call to the `main()` function.
- Run your script with `python task4.py` and verify the output.

**Expected Output:**

```text
=== Creating arrays ===
array1 (np.array):
[ 10  20  30  40  50  60  70  80  90 100]
ndim: 1 | shape: (10,) | size: 10 | dtype: int64

array2 (np.linspace):
[ 10.  20.  30.  40.  50.  60.  70.  80.  90. 100.]
ndim: 1 | shape: (10,) | size: 10 | dtype: float64

array3 (np.arange):
[ 10  20  30  40  50  60  70  80  90 100]
ndim: 1 | shape: (10,) | size: 10 | dtype: int64

array4 (2D):
[[1 2 3]
 [4 5 6]]
ndim: 2 | shape: (2, 3) | size: 6 | dtype: int64

=== Special arrays ===
Zeros 2x4:
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]]
ndim: 2 | shape: (2, 4) | size: 8 | dtype: float64

Ones 1D:
[1. 1. 1. 1. 1.]
ndim: 1 | shape: (5,) | size: 5 | dtype: float64

Diagonal:
[[4 0 0 0]
 [0 6 0 0]
 [0 0 1 0]
 [0 0 0 3]]
ndim: 2 | shape: (4, 4) | size: 16 | dtype: int64

Identity 3x3:
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
ndim: 2 | shape: (3, 3) | size: 9 | dtype: float64

```

<details markdown="1">

<summary><b>Quick Reference: Array Arithmetic and Statistics</b></summary>

<br>

**Element-wise arithmetic (vectorization).** An operator between two arrays of the same shape works on matching elements, with no loop:

```python
a = np.array([1, 2, 3])
b = np.array([10, 20, 30])
print(a + b)     # [11 22 33]
print(a * b)     # [10 40 90]
print(a ** 2)    # [1 4 9]   element-wise power
```

**Broadcasting.** An operator between an array and a single number applies the number to **every** element:

```python
print(a + 5)     # [6 7 8]
print(a * 2)     # [2 4 6]
```

Compare this with a Python list: `[1, 2, 3] * 2` gives `[1, 2, 3, 1, 2, 3]`, not `[2, 4, 6]`.

**Statistical functions**

| Function | Returns |
|---|---|
| `np.sum(arr)` | Total of all values |
| `np.mean(arr)` | Average |
| `np.median(arr)` | Middle value after sorting |
| `np.max(arr)` / `np.min(arr)` | Largest / smallest value |

Use `round(value, 2)` to round a result to two decimal places.

</details>

### Task 5 - Array Arithmetic and Statistics

**Objective:** Practice element-wise arithmetic, broadcasting, and NumPy's statistical functions.

**Instructions:**

- Create the file `task5.py`, add the required comment header, and import NumPy as `np`.
- Write a function named `array_arithmetic` that takes two arrays, `arr1` and `arr2`, as parameters and prints, with the labels shown in the expected output:
  - Both arrays.
  - `arr1 + arr2`, `arr1 - arr2` and `arr1 * arr2`.
  - `arr1 ** 2` (each element of `arr1` squared).
  - `arr1 + 10` and `arr2 * 2` (broadcasting).
- Write a function named `print_statistics` that takes one array, `data`, as a parameter and prints its total, average (rounded to 2 decimal places), median, maximum and minimum. Use the NumPy functions from the Quick Reference, **not** loops.
- Write a `main()` function that:
  - Prints `=== Array arithmetic ===`.
  - Creates `arr1 = np.array([2, 4, 6, 8])` and `arr2 = np.array([1, 3, 5, 7])` and passes them to `array_arithmetic()`.
  - Prints an empty line, then `=== Daily login attempts ===`.
  - Creates an array named `logins` with the daily login attempts `15, 22, 13, 40, 30, 27, 18` and passes it to `print_statistics()`.
- Add a call to the `main()` function.
- At the **bottom** of `task5.py`, answer the following in a comment of 2-4 sentences: *Why did you not need a loop to add 10 to every element of `arr1`?*
- Run your script with `python task5.py` and verify the output.

**Expected Output:**

```text
=== Array arithmetic ===
arr1: [2 4 6 8]
arr2: [1 3 5 7]
arr1 + arr2: [ 3  7 11 15]
arr1 - arr2: [1 1 1 1]
arr1 * arr2: [ 2 12 30 56]
arr1 ** 2: [ 4 16 36 64]
arr1 + 10: [12 14 16 18]
arr2 * 2: [ 2  6 10 14]

=== Daily login attempts ===
Total: 165
Average: 23.57
Median: 22.0
Maximum: 40
Minimum: 13
```

<details markdown="1">

<summary><b>Quick Reference: Indexing, Slicing, axis and Reshaping</b></summary>

<br>

Suppose `m = np.array([[1, 2, 3], [4, 5, 6]])`.

**Indexing and slicing.** A 2D array takes two indices, `[row, column]`. Indices start at 0, and slices work like list slices (the stop is not included).

| Code | Result | Meaning |
|---|---|---|
| `m[1, 2]` | `6` | Row 1, column 2 (2nd row, 3rd column) |
| `m[0]` | `[1 2 3]` | The whole first row |
| `m[:, 1]` | `[2 5]` | The whole second column (`:` means "every row") |
| `m[0:2, 0:2]` | `[[1 2]` <br> ` [4 5]]` | Rows 0-1, columns 0-1 |

**Totals per row or per column** with the `axis` argument:

| Code | Result | Meaning |
|---|---|---|
| `np.sum(m)` | `21` | Total of every element |
| `np.sum(m, axis=1)` | `[ 6 15]` | One total **per row** (adds across the columns) |
| `np.sum(m, axis=0)` | `[5 7 9]` | One total **per column** (adds down the rows) |

**Reshaping** changes the shape without changing the data. The total number of elements must stay the same:

```python
a = np.arange(1, 7)      # [1 2 3 4 5 6], size 6
print(a.reshape(2, 3))   # 2 rows x 3 columns = 6, works
print(a.reshape(3, 2))   # 3 x 2 = 6, works
a.reshape(4, 2)          # 4 x 2 = 8, raises ValueError
```

`reshape()` accepts the new shape either as separate numbers, `reshape(2, 3)`, or as a tuple, `reshape((2, 3))`.

</details>

### Task 6 - Indexing, Slicing and Reshaping 2D Arrays

**Objective:** Practice accessing parts of a 2D array, totalling rows and columns with `axis`, and reshaping, including handling the error when a reshape is impossible.

The array below holds the number of failed logins recorded on **3 servers** over **4 hours**. Each row is a server and each column is an hour.

**Instructions:**

- Create the file `task6.py`, add the required comment header, and import NumPy as `np`.
- Write a function named `explore_matrix` that takes a 2D array, `matrix`, as a parameter and prints, with the labels shown in the expected output:
  - The whole matrix, then its shape and size on one line.
  - The value for server 2, hour 3 (one element).
  - The first row (server 1).
  - The last column (hour 4).
  - The sub-matrix for servers 1-2 and hours 1-2, using slicing.
  - The total for each server, using `np.sum()` with the correct `axis`.
  - The total for each hour, using `np.sum()` with the correct `axis`.
- Write a function named `try_reshape` that:
  - Takes two parameters: an array `arr` and a tuple `shape`.
  - Inside a `try` block, reshapes `arr` to `shape`, then prints `Reshaped to <shape>` and the reshaped array.
  - Has an `except ValueError as exception:` clause that prints `Error:` followed by `str(exception)`.
- Write a `main()` function that:
  - Creates a 1D array named `logins` with the values `15, 22, 13, 40, 30, 27, 18, 25, 11, 35, 20, 16`.
  - Reshapes `logins` into a 3x4 array named `matrix` and passes it to `explore_matrix()`.
  - Prints an empty line, then `=== Reshaping ===`.
  - Calls `try_reshape()` three times on `logins`, with the shapes `(4, 3)`, `(2, 2, 3)` and `(5, 3)`.
- Add a call to the `main()` function.
- At the **bottom** of `task6.py`, answer the following in a comment of 2-3 sentences: *Why did the reshape to `(5, 3)` fail, when `(4, 3)` and `(2, 2, 3)` worked?*
- Run your script with `python task6.py` and verify the output.

**Expected Output:**

```text
Failed logins (3 servers x 4 hours):
[[15 22 13 40]
 [30 27 18 25]
 [11 35 20 16]]
Shape: (3, 4) | Size: 12
Server 2, hour 3: 18
Server 1 (first row): [15 22 13 40]
Hour 4 (last column): [40 25 16]
Servers 1-2, hours 1-2:
[[15 22]
 [30 27]]
Total per server: [ 90 100  82]
Total per hour: [56 84 51 81]

=== Reshaping ===
Reshaped to (4, 3)
[[15 22 13]
 [40 30 27]
 [18 25 11]
 [35 20 16]]
Reshaped to (2, 2, 3)
[[[15 22 13]
  [40 30 27]]

 [[18 25 11]
  [35 20 16]]]
Error: cannot reshape array of size 12 into shape (5,3)
```

> **Note:** "Server 2, hour 3" is `matrix[1, 2]`, not `matrix[2, 3]`, because indices start at 0. The error message in the last line is created by NumPy. Your program prints it and keeps running, just like the `int()` error in Task 2.

<details markdown="1">

<summary><b>Quick Reference: Boolean Indexing</b></summary>

<br>

A comparison between an array and a number gives an array of `True`/`False` values, one per element. Putting that inside square brackets keeps only the elements that are `True`:

```python
data = np.array([300, 1200, 800, 2500])
print(data > 1000)          # [False  True False  True]
print(data[data > 1000])    # [1200 2500]
print(data[data > 1000].size)   # 2, how many values matched
```

This is how analysts filter large logs and network captures quickly, with no loop.

**Building an array from a file.** Read the values into a Python list first, then convert the whole list at once:

```python
values = []
values.append(500)
values.append(1500)
packets = np.array(values)  # [ 500 1500]
```

`np.array([])` creates an **empty** array. Its `size` is `0`.

</details>

### Task 7 - Safe Packet Analysis (Files + Exceptions + NumPy)

**Objective:** Bring everything together: read data from a file, use exception handling to survive a missing file and bad lines, raise an exception for empty data, and analyse the data with NumPy and Boolean indexing.

A network monitoring tool saved the size, in bytes, of each packet it captured to a text file. Two lines were corrupted, so they do not contain numbers. Your program must skip the bad lines, report them, and analyse the rest.

**Instructions:**

- In your `Lab06` folder, create the file `packets.txt` with the following text, one value per line:

  ```text
  500
  1500
  800
  abc
  2000
  750
  N/A
  1200
  3000
  ```

- Create the file `task7.py`, add the required comment header, and import NumPy as `np`.
- Write a function named `load_packets` that:
  - Takes a file name, `filename`, as a parameter.
  - Creates an empty list named `values`.
  - In an **outer** `try` block, opens the file with a `with` statement and uses a `for` loop to read it line by line, counting the line numbers. For each line:
    - Removes whitespace with `strip()`.
    - In an **inner** `try` block, converts the text to an integer with `int()` and appends it to `values`.
    - If a `ValueError` happens, prints `Skipping line <line number> - not a number: <text>` and continues with the next line.
  - Has an outer `except FileNotFoundError:` clause that prints `Error: the file <filename> was not found.`
  - Converts `values` to a NumPy array with `np.array()` and **returns** it (this happens whether or not the file was found).
- Write a function named `analyse_packets` that:
  - Takes two parameters: a NumPy array `packets` and a number `threshold`.
  - **Raises** a `ValueError` with the message `No packet data to analyse` if the array is empty (its `size` is `0`).
  - Otherwise, prints, with the labels shown in the expected output: the array, the number of packets, the average size (rounded to 2 decimal places), the largest and smallest packet, the packets larger than `threshold` (using **Boolean indexing**, no loops), and how many packets are larger than `threshold`.
- Write a `main()` function that uses a `for` loop over the list `["packets.txt", "missing.txt"]`. For each file name, it:
  - Prints `=== Analysing <filename> ===`.
  - Calls `load_packets()` and stores the returned array.
  - Inside a `try` block, calls `analyse_packets()` with the array and a threshold of `1000`.
  - If a `ValueError` is raised, prints `Error:` followed by `str(exception)`.
  - Prints an empty line.
- Add a call to the `main()` function.
- Run your script with `python task7.py` and verify the output.

**Expected Output:**

```text
=== Analysing packets.txt ===
Skipping line 4 - not a number: abc
Skipping line 7 - not a number: N/A
Packets loaded: [ 500 1500  800 2000  750 1200 3000]
Number of packets: 7
Average size: 1392.86
Largest packet: 3000
Smallest packet: 500
Packets larger than 1000 bytes: [1500 2000 1200 3000]
Count of large packets: 4

=== Analysing missing.txt ===
Error: the file missing.txt was not found.
Error: No packet data to analyse

```

> **Think about it:** For `missing.txt`, two different errors are reported. Which function printed each one, and why did the program not crash even though `analyse_packets()` raised an exception?

## Part B Submission

Part B is graded **directly from your GitHub repository**. The structure below must match **exactly**, including upper and lower case. A file with the wrong name or in the wrong folder is treated as missing.

```text
SRT111F2026/              <- your repository, with exactly this name
└── Lab06/                <- capital L, zero, six
    ├── task4.py
    ├── task5.py
    ├── task6.py
    ├── task7.py
    └── packets.txt
```

- Do **not** rename the repository, and do not put the files in a sub-folder of `Lab06` or at the top level of the repository.
- Part A files (`task1.py` to `task3.py`, `number.txt`, `badnumber.txt`) are graded in class. You may also push them to `Lab06`; they will not affect your Part B grade.
- Do not create or push a file named `missing.txt`.
- Commit and push the `Lab06` folder to GitHub. Open your repository on github.com in a browser and confirm that all five files are inside `Lab06`.
- On Blackboard, submit **only the link** to your repository, for example: `https://github.com/yourgithubusername/SRT111F2026`
- No screenshots and no PDF are required.

### Part B Grading Checklist

Your repository will be checked against the following list. Use it to check your own work before you submit.

| # | Check |
|---|---|
| 1 | The repository is named `SRT111F2026` and contains a folder named `Lab06`. |
| 2 | `Lab06` contains `task4.py`, `task5.py`, `task6.py`, `task7.py` and `packets.txt`, with these exact names. |
| 3 | Every `.py` file starts with the required comment header (Author, Date, Purpose). |
| 4 | Every script imports NumPy as `np`, defines the required functions with the required names, has a `main()` function, and calls `main()`. |
| 5 | Each script runs from the `Lab06` folder without errors and produces the expected output. |
| 6 | Task 4 uses `np.array()`, `np.linspace()`, `np.arange()`, `np.zeros()`, `np.ones()`, `np.diag()` and `np.eye()`, and prints `ndim`, `shape`, `size` and `dtype`. |
| 7 | Task 5 uses array operators and broadcasting (no loops) and `np.sum()`, `np.mean()`, `np.median()`, `np.max()`, `np.min()`, and has the reflection comment at the bottom. |
| 8 | Task 6 uses `[row, column]` indexing, slicing, `np.sum()` with `axis`, `reshape()`, and `try`/`except ValueError` in `try_reshape()`, and has the reflection comment at the bottom. |
| 9 | Task 7 uses nested `try`/`except` (`FileNotFoundError` and `ValueError`), a `with` statement, `raise ValueError` in `analyse_packets()`, and Boolean indexing (no loops) to find the large packets. |
| 10 | The repository link was submitted on Blackboard. |
