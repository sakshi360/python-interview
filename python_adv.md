# 🧠 Advanced Python Theoretical & Conceptual Q&A (Interview Ready)

This document extends the **Core Python Interview Guide** with advanced, conceptual, and often asked theoretical questions related to **memory, threading, performance, profiling, and internals**.

---

## ⚙️ Exception Handling

<details>
<summary><b>1. What is the difference between Exception and Error?</b></summary>
`Error` usually represents issues that occur at runtime (e.g., ZeroDivisionError), while `Exception` is the base class for all built-in exceptions. Custom ones inherit from it.
</details>

<details>
<summary><b>2. What is the flow of try-except-else-finally?</b></summary>
- `try`: Contains code that might raise an exception.
- `except`: Handles specific exceptions.
- `else`: Runs if no exception occurs.
- `finally`: Always runs, even if an exception is raised or caught.
</details>

<details>
<summary><b>3. How to raise custom exceptions?</b></summary>
You can create your own exception class by inheriting from `Exception`.
```python
class MyError(Exception):
    pass
raise MyError("Something went wrong!")
```
</details>

<details>
<summary><b>4. What is exception chaining?</b></summary>
`raise ... from ...` allows linking two exceptions to show the original cause of the new error.
</details>

---

## 📄 File Handling & Context Managers

<details>
<summary><b>1. What happens internally with 'with open()'?</b></summary>
It calls the file object's `__enter__()` method at the start and `__exit__()` method when done, ensuring automatic cleanup.
</details>

<details>
<summary><b>2. What are file modes in Python?</b></summary>
`r` - read, `w` - write, `a` - append, `b` - binary, `+` - read & write.
</details>

<details>
<summary><b>3. What is file buffering?</b></summary>
It temporarily stores data in memory before writing to disk to improve I/O performance.
</details>

---

## 🧮 Memory Management & Performance

<details>
<summary><b>1. How does Python reuse small objects?</b></summary>
Small integers (-5 to 256) and short strings are **interned** and reused from memory to save space.
</details>

<details>
<summary><b>2. How to check object size in Python?</b></summary>
Use `sys.getsizeof(obj)` to check memory used by an object.
</details>

<details>
<summary><b>3. How to profile memory usage?</b></summary>
Use the `tracemalloc` module to track memory allocation.
```python
import tracemalloc
tracemalloc.start()
# code
print(tracemalloc.get_traced_memory())
```
</details>

<details>
<summary><b>4. What makes tuples faster than lists?</b></summary>
Tuples are immutable, so they have a fixed size and lower memory overhead.
</details>

<details>
<summary><b>5. What is lazy evaluation?</b></summary>
Expressions or objects are evaluated only when needed, e.g., generators.
</details>

---

## 🔀 Multi-threading, Multiprocessing & AsyncIO

<details>
<summary><b>1. Difference between threading and multiprocessing?</b></summary>
Threads share memory space (affected by GIL), while processes run in separate memory spaces (no GIL issue).
</details>

<details>
<summary><b>2. What is asyncio used for?</b></summary>
For asynchronous, non-blocking I/O operations using coroutines and event loops.
</details>

<details>
<summary><b>3. When to use multiprocessing over threading?</b></summary>
Use **multiprocessing** for CPU-bound tasks and **threading** for I/O-bound tasks.
</details>

<details>
<summary><b>4. How to share data between threads/processes?</b></summary>
- Threads: Use `Queue` or `Lock`.
- Processes: Use `multiprocessing.Manager()` or `Queue`.
</details>

---

## 🧩 Data Structures & Internals

<details>
<summary><b>1. How are dictionaries implemented internally?</b></summary>
Dictionaries use a **hash table** to map keys to values, using open addressing to resolve collisions.
</details>

<details>
<summary><b>2. Why are dicts insertion-ordered?</b></summary>
Since Python 3.7, dictionaries preserve insertion order by maintaining a compact array of key-value pairs.
</details>

<details>
<summary><b>3. Why are tuples hashable but lists are not?</b></summary>
Tuples are immutable, so their hash value doesn't change; lists can change, so they are unhashable.
</details>

<details>
<summary><b>4. How does list resizing work internally?</b></summary>
Lists over-allocate extra space to minimize the need for frequent memory reallocation when appending.
</details>

<details>
<summary><b>5. How are sets implemented?</b></summary>
Sets are also backed by a **hash table**, but only store keys (no values).
</details>

---

## 🧱 Functions & Closures

<details>
<summary><b>1. What are closures?</b></summary>
A closure is a function that remembers variables from its enclosing scope even after that scope has finished executing.
</details>

<details>
<summary><b>2. What is the late binding issue in closures?</b></summary>
Inner functions capture variables by reference, not value, leading to unexpected results in loops.
</details>

<details>
<summary><b>3. What is the difference between lambda and def?</b></summary>
`lambda` creates anonymous functions with a single expression; `def` defines full functions with multiple statements.
</details>

<details>
<summary><b>4. What are function annotations?</b></summary>
Annotations are optional metadata or type hints provided in function signatures, accessible via `__annotations__`.
</details>

<details>
<summary><b>5. What is the mutable default argument problem?</b></summary>
Default arguments are evaluated once at definition time; using mutable defaults (like lists) can cause data leakage between calls.
</details>

---

## ⚡ Advanced Internals

<details>
<summary><b>1. What is the __pycache__ folder?</b></summary>
Python stores compiled bytecode files (`.pyc`) in this folder to speed up module loading.
</details>

<details>
<summary><b>2. How does the import system work?</b></summary>
1. Checks `sys.modules` cache.  
2. Searches `sys.path`.  
3. Compiles and executes if not loaded.  
4. Caches result in `sys.modules`.
</details>

<details>
<summary><b>3. What is the purpose of __all__?</b></summary>
Defines the list of names to import when using `from module import *`.
</details>

<details>
<summary><b>4. What is hashability?</b></summary>
An object is hashable if it has a fixed hash value during its lifetime and supports equality comparison.
</details>

<details>
<summary><b>5. What is the difference between __str__ and __repr__?</b></summary>
- `__str__`: Readable representation for users.  
- `__repr__`: Unambiguous representation for developers/debugging.
</details>

---

## 📊 Profiling & Optimization

<details>
<summary><b>1. How to profile code performance?</b></summary>
Use the built-in `cProfile` module:
```python
import cProfile
cProfile.run('main()')
```
</details>

<details>
<summary><b>2. How to find slow parts of code?</b></summary>
Use `timeit` for small snippets or `line_profiler` for detailed line-level performance.
</details>

<details>
<summary><b>3. How to reduce memory usage?</b></summary>
- Use generators instead of lists.  
- Prefer tuples over lists.  
- Use `__slots__` to avoid `__dict__`.  
- Use lazy evaluation.
</details>

<details>
<summary><b>4. What is Just-In-Time (JIT) compilation?</b></summary>
Used by PyPy to compile bytecode into machine code during runtime, improving speed.
</details>

<details>
<summary><b>5. What are common performance bottlenecks in Python?</b></summary>
- GIL for CPU-bound threads  
- Repeated string concatenation  
- Large loops with interpreted code  
- Excessive I/O blocking
</details>

---

## 🧾 Miscellaneous Theoretical

<details>
<summary><b>1. Why is Python slower than C?</b></summary>
Because Python code is interpreted at runtime and uses dynamic typing, causing extra overhead.
</details>

<details>
<summary><b>2. Why does Python limit recursion depth?</b></summary>
To prevent stack overflow errors. Default is around 1000 (`sys.getrecursionlimit()`).
</details>

<details>
<summary><b>3. Why are all values in Python objects?</b></summary>
Everything in Python (even functions, modules, types) is an object derived from the base `object` class.
</details>

<details>
<summary><b>4. What are function objects?</b></summary>
Functions are first-class objects — they can be assigned to variables, passed as arguments, or returned from other functions.
</details>

<details>
<summary><b>5. What is reflection in Python?</b></summary>
Inspecting and modifying program structure at runtime using `getattr()`, `setattr()`, and `dir()`.
</details>

---

## 🧠 Summary

This file completes your **interview-ready theory revision** with in-depth coverage of Python internals, performance profiling, memory handling, and advanced conceptual topics.

Use this with your **Core Python Q&A README** for complete preparation.

---

## ✍️ Author

**Sakshi Agarwal**
🚀 Passionate about Python, AWS, and performance optimization.
