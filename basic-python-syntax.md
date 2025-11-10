# 🐍 Basic Python Syntax & Code Q&A

A quick revision guide for Python syntax, commonly asked short code snippets, and behavior-based questions — perfect for warm-up interview rounds.

---

## 🧩 Variables & Data Types

<details>
<summary><b>1. How do you declare a variable in Python?</b></summary>
Python uses dynamic typing — you can assign directly:
```python
x = 10
y = "Hello"
z = 3.14
```
</details>

<details>
<summary><b>2. How to check the type of a variable?</b></summary>
Use the built-in `type()` function:
```python
print(type(x))
```
</details>

<details>
<summary><b>3. How to convert between types?</b></summary>
```python
int('10')    # to integer
float('3.5') # to float
str(100)     # to string
list('abc')  # to list ['a', 'b', 'c']
```
</details>

<details>
<summary><b>4. What are Python’s numeric types?</b></summary>
`int`, `float`, `complex`, and `bool`.
</details>

---

## 🧮 Operators

<details>
<summary><b>1. What are the basic arithmetic operators?</b></summary>
`+`, `-`, `*`, `/`, `//`, `%`, `**`
</details>

<details>
<summary><b>2. What is the difference between '/' and '//'?</b></summary>
`/` performs floating-point division, `//` performs floor division.
</details>

<details>
<summary><b>3. What is operator precedence?</b></summary>
Order in which operations are evaluated. Example:
```python
print(2 + 3 * 5)  # 17, because * has higher precedence
```
</details>

---

## 🔁 Control Flow

<details>
<summary><b>1. How do you write an if-else statement?</b></summary>
```python
x = 10
if x > 0:
    print("Positive")
else:
    print("Non-positive")
```
</details>

<details>
<summary><b>2. How does Python handle indentation?</b></summary>
Indentation (spaces or tabs) defines blocks — no curly braces.
</details>

<details>
<summary><b>3. How to write a one-line conditional?</b></summary>
```python
result = "Even" if x % 2 == 0 else "Odd"
```
</details>

---

## 🔁 Loops

<details>
<summary><b>1. How does a for loop work in Python?</b></summary>
```python
for i in range(5):
    print(i)
```
</details>

<details>
<summary><b>2. How does a while loop work?</b></summary>
```python
count = 0
while count < 5:
    print(count)
    count += 1
```
</details>

<details>
<summary><b>3. How do you break or continue in a loop?</b></summary>
```python
for i in range(5):
    if i == 2:
        continue  # skip iteration
    if i == 4:
        break     # exit loop
```
</details>

<details>
<summary><b>4. What is the use of 'else' with loops?</b></summary>
The `else` part executes only if the loop completes normally (no break).
```python
for i in range(3):
    print(i)
else:
    print("Done")
```
</details>

---

## 🧰 Functions

<details>
<summary><b>1. How to define a function in Python?</b></summary>
```python
def greet(name):
    return f"Hello, {name}!"
```
</details>

<details>
<summary><b>2. What are default arguments?</b></summary>
```python
def power(base, exp=2):
    return base ** exp
```
</details>

<details>
<summary><b>3. What are *args and **kwargs?</b></summary>
They allow variable arguments:
```python
def func(*args, **kwargs):
    print(args, kwargs)
```
</details>

<details>
<summary><b>4. What is a lambda function?</b></summary>
Anonymous single-line function:
```python
square = lambda x: x**2
```
</details>

<details>
<summary><b>5. What are docstrings?</b></summary>
Used to document functions:
```python
def add(a, b):
    """Returns the sum of a and b."""
    return a + b
```
</details>

---

## 📦 Collections

<details>
<summary><b>1. How to create a list, tuple, set, and dictionary?</b></summary>
```python
lst = [1, 2, 3]
tpl = (1, 2, 3)
st = {1, 2, 3}
dct = {'a': 1, 'b': 2}
```
</details>

<details>
<summary><b>2. How to iterate over a dictionary?</b></summary>
```python
for k, v in dct.items():
    print(k, v)
```
</details>

<details>
<summary><b>3. How to perform list comprehension?</b></summary>
```python
squares = [x*x for x in range(5)]
```
</details>

<details>
<summary><b>4. How to merge two dictionaries?</b></summary>
```python
a = {'x': 1}
b = {'y': 2}
merged = {**a, **b}
```
</details>

---

## 🧾 Strings

<details>
<summary><b>1. How to reverse a string?</b></summary>
```python
s = "Python"
print(s[::-1])
```
</details>

<details>
<summary><b>2. How to check for substring?</b></summary>
```python
"th" in "Python"  # True
```
</details>

<details>
<summary><b>3. How to split and join strings?</b></summary>
```python
text = "Hello World"
words = text.split()        # ['Hello', 'World']
joined = '-'.join(words)    # 'Hello-World'
```
</details>

<details>
<summary><b>4. How to format strings?</b></summary>
```python
name = 'Sakshi'
print(f"Hello, {name}!")
```
</details>

---

## 🧮 List Tricks

<details>
<summary><b>1. How to remove duplicates from a list?</b></summary>
```python
lst = [1, 2, 2, 3]
unique = list(set(lst))
```
</details>

<details>
<summary><b>2. How to flatten a nested list?</b></summary>
```python
nested = [[1, 2], [3, 4]]
flat = [x for sub in nested for x in sub]
```
</details>

<details>
<summary><b>3. How to sort a list of tuples by second element?</b></summary>
```python
data = [(1, 3), (2, 1), (4, 2)]
data.sort(key=lambda x: x[1])
```
</details>

---

## ⚡ Miscellaneous

<details>
<summary><b>1. How to swap two variables?</b></summary>
```python
a, b = b, a
```
</details>

<details>
<summary><b>2. How to handle exceptions?</b></summary>
```python
try:
    x = 1 / 0
except ZeroDivisionError:
    print("Can't divide by zero")
```
</details>

<details>
<summary><b>3. What is the difference between del, remove, and pop?</b></summary>
- `del` deletes by index or key.  
- `remove()` deletes by value.  
- `pop()` deletes by index and returns the element.
</details>

<details>
<summary><b>4. How to check memory address of a variable?</b></summary>
```python
id(x)
```
</details>

<details>
<summary><b>5. How to check Python version?</b></summary>
```python
import sys
print(sys.version)
```
</details>

---

## 🧠 Quick Syntax Facts

* Indentation replaces braces `{}`.
* Everything is an object.
* Semicolons are optional.
* No variable declaration keyword.
* Strings are immutable.

---

### ✅ Summary

This file includes quick syntax-based questions, small coding snippets, and language behavior — great for warm-up or coding screening rounds.

---

**Author:** Sakshi Agarwal
✨ Backend Developer | Python | AWS | Data Engineering
