# 🐍 Python Interview Preparation Guide

A curated list of **Core Python**, **OOP**, and **Internal Concept** questions — with short, easy-to-understand answers for quick revision before interviews.

---

## 🧠 Core Python Concepts

<details>
<summary><b>1. How does the Python interpreter work?</b></summary>
Python compiles your `.py` file into **bytecode** (`.pyc`), then executes it using the **Python Virtual Machine (PVM)**.  
**Steps:** Source code → Bytecode → Executed by PVM.
</details>

<details>
<summary><b>2. Is Python compiled or interpreted?</b></summary>
Python is both. It first compiles code to bytecode, then the interpreter executes that bytecode line by line.
</details>

<details>
<summary><b>3. What are Python namespaces?</b></summary>
A namespace is a mapping between names and objects. Types include Local, Global, Enclosing, and Built-in.
</details>

<details>
<summary><b>4. What is the difference between a module and a package?</b></summary>
- **Module:** A single `.py` file.  
- **Package:** A collection of modules in a directory with an `__init__.py` file.
</details>

<details>
<summary><b>5. What happens when you execute a Python file?</b></summary>
1. Parser checks syntax.  
2. Compiler converts it to bytecode.  
3. Bytecode is executed by PVM.  
4. Objects are created in heap memory.
</details>

<details>
<summary><b>6. What is the difference between shallow copy and deep copy?</b></summary>
Shallow copy creates a new object but references inner objects; deep copy recursively copies everything.
</details>

<details>
<summary><b>7. What is the Global Interpreter Lock (GIL)?</b></summary>
A lock that ensures only one thread runs Python bytecode at a time in CPython. It simplifies memory management but limits CPU parallelism.
</details>

<details>
<summary><b>8. What is Python’s memory management model?</b></summary>
Python uses a private heap, reference counting, and a garbage collector for cyclic references.
</details>

<details>
<summary><b>9. What are Python’s key data structures?</b></summary>
- **List:** Dynamic array, ordered, mutable.  
- **Tuple:** Ordered, immutable.  
- **Set:** Unordered, unique elements.  
- **Dict:** Key-value pairs using hash tables.
</details>

<details>
<summary><b>10. What is duck typing?</b></summary>
Python checks behavior, not type. If an object acts like a type, it’s accepted (e.g., has a `__len__()` method → can be used with `len()`).
</details>

<details>
<summary><b>11. What is difference between `is` and `==`?</b></summary>
`is` checks identity (same memory address), `==` checks value equality.
</details>

<details>
<summary><b>12. What are Python decorators?</b></summary>
Functions that modify other functions’ behavior without changing their source code.
</details>

<details>
<summary><b>13. What are iterators and generators?</b></summary>
- **Iterator:** Object with `__iter__()` and `__next__()` methods.  
- **Generator:** Function using `yield` that automatically creates an iterator.
</details>

<details>
<summary><b>14. What is the difference between function and method?</b></summary>
A **function** is defined outside a class; a **method** is defined inside a class and takes `self` as first argument.
</details>

<details>
<summary><b>15. What is Python’s execution model?</b></summary>
Source code → Compilation to bytecode → Execution by PVM → Managed memory allocation.
</details>

---

## 🧩 Object-Oriented Programming (OOP)

<details>
<summary><b>1. What is the difference between class and instance attributes?</b></summary>
Class attributes are shared by all objects; instance attributes are unique per instance.
</details>

<details>
<summary><b>2. What is inheritance?</b></summary>
Mechanism that allows a class to inherit attributes and methods from another class.
</details>

<details>
<summary><b>3. What is polymorphism?</b></summary>
Different objects can respond to the same method in different ways.
</details>

<details>
<summary><b>4. What is encapsulation?</b></summary>
Wrapping data and methods that operate on that data within a single unit (class). Achieved using private and protected members.
</details>

<details>
<summary><b>5. What is abstraction?</b></summary>
Hiding implementation details and exposing only essential features, using abstract base classes or interfaces.
</details>

<details>
<summary><b>6. What is method overriding?</b></summary>
Defining a method in a subclass with the same name as one in its superclass to change or extend its behavior.
</details>

<details>
<summary><b>7. What is method overloading in Python?</b></summary>
Python doesn’t support true method overloading. It uses default arguments or variable-length arguments to simulate it.
</details>

<details>
<summary><b>8. What is a metaclass?</b></summary>
A class that defines how other classes behave. `type` is the default metaclass.
</details>

<details>
<summary><b>9. What are `__slots__`?</b></summary>
Used to restrict attribute creation and reduce memory by preventing a per-instance `__dict__`.
</details>

<details>
<summary><b>10. What is operator overloading?</b></summary>
Customizing operators using dunder methods like `__add__`, `__eq__`, etc.
</details>

---

## ⚙️ Python Internals & Concepts

<details>
<summary><b>1. What is the difference between process and thread?</b></summary>
Threads share the same memory, while processes have separate memory spaces.
</details>

<details>
<summary><b>2. What is Python’s memory allocator?</b></summary>
Uses PyMalloc for small objects and system malloc for larger allocations.
</details>

<details>
<summary><b>3. What are reference counts?</b></summary>
Each object maintains a counter of how many references point to it. When count = 0, object is deleted.
</details>

<details>
<summary><b>4. What are weak references?</b></summary>
References that do not increase an object’s reference count. Defined in the `weakref` module.
</details>

<details>
<summary><b>5. What is interning?</b></summary>
Python stores small integers (-5 to 256) and short strings in memory to reuse them and improve performance.
</details>

<details>
<summary><b>6. What are Python’s execution modes?</b></summary>
- **Interactive mode:** Runs commands directly in the interpreter.  
- **Script mode:** Executes code from a `.py` file.
</details>

<details>
<summary><b>7. What is the role of the `__main__` block?</b></summary>
Used to execute code only when the file is run directly, not imported.
```python
if __name__ == '__main__':
    main()
```
</details>

<details>
<summary><b>8. What are Python’s common built-in functions for introspection?</b></summary>
`type()`, `id()`, `dir()`, `vars()`, `callable()`, `help()`
</details>

<details>
<summary><b>9. What are descriptors?</b></summary>
Objects that define custom behavior for attribute access using `__get__`, `__set__`, and `__delete__` methods.
</details>

<details>
<summary><b>10. What are context managers?</b></summary>
They handle resource management automatically with `__enter__` and `__exit__` methods (used with `with`).
</details>

---

## 💡 Additional Conceptual Questions

<details>
<summary><b>1. What is dynamic typing?</b></summary>
Variables do not have fixed types; the type is determined at runtime.
</details>

<details>
<summary><b>2. What is strong typing?</b></summary>
Python doesn’t implicitly convert types; you can’t add a string and integer without explicit conversion.
</details>

<details>
<summary><b>3. What is monkey patching?</b></summary>
Changing a class or module behavior at runtime, usually for testing or quick fixes.
</details>

<details>
<summary><b>4. What is the difference between deep copy and assignment?</b></summary>
Assignment creates a new reference; deep copy creates a completely new object with copied data.
</details>

<details>
<summary><b>5. What is pickling and unpickling?</b></summary>
Pickling converts Python objects to byte streams. Unpickling restores them. Done using `pickle` module.
</details>

<details>
<summary><b>6. What is the use of `__del__`?</b></summary>
It’s a destructor called when an object is deleted or goes out of scope.
</details>

<details>
<summary><b>7. What are Python’s optimization techniques?</b></summary>
Interning, caching small integers, using generators instead of lists, and lazy imports.
</details>

<details>
<summary><b>8. What is lazy evaluation?</b></summary>
Expressions are evaluated only when needed, improving performance.
</details>

<details>
<summary><b>9. What is the difference between compile-time and runtime in Python?</b></summary>
Python does minimal compile-time checks; most errors are caught at runtime due to its dynamic nature.
</details>

<details>
<summary><b>10. What is the difference between shallow and deep equality?</b></summary>
`==` checks shallow equality (values), `is` checks deep equality (identity).
</details>

---

## 📘 Author

**Sakshi Agarwal**
✨ Passionate about Python, AWS, and backend engineering.

---

## 🏷️ License

This project is licensed under the MIT License — free to use and share.
