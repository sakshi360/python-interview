# python-interview

# 🐍 Python Interview Preparation Guide

A curated list of **Core Python**, **OOP**, and **Internal Concept** questions — with short, easy-to-understand answers for quick revision before interviews.

---

## 🧠 Core Python Concepts

<details>
<summary><b>1. How does the Python interpreter work?</b></summary>

Python first compiles your `.py` file into **bytecode** (`.pyc`), then executes it using the **Python Virtual Machine (PVM)**.
**Steps:** Source code → Bytecode → Executed by PVM.

</details>

---

<details>
<summary><b>2. Is Python compiled or interpreted?</b></summary>

Both! Python compiles to bytecode, and then the interpreter executes that bytecode line by line at runtime.

</details>

---

<details>
<summary><b>3. What is CPython, PyPy, Jython, IronPython?</b></summary>

| Implementation | Language | Description                     |
| -------------- | -------- | ------------------------------- |
| CPython        | C        | Default & most used interpreter |
| PyPy           | RPython  | JIT compiled → faster           |
| Jython         | Java     | Runs on JVM                     |
| IronPython     | C#       | Runs on .NET CLR                |

</details>

---

<details>
<summary><b>4. What is the Global Interpreter Lock (GIL)?</b></summary>

A mutex that ensures **only one thread executes Python bytecode** at a time, simplifying memory management but limiting CPU-bound multithreading.

</details>

---

<details>
<summary><b>5. What are namespaces in Python?</b></summary>

A namespace is a mapping between names and objects.
Types: **Local**, **Enclosing**, **Global**, and **Built-in** (LEGB rule).

</details>

---

<details>
<summary><b>6. What are scopes in Python?</b></summary>

Python searches variables using the **LEGB rule** → Local → Enclosing → Global → Built-in.

</details>

---

<details>
<summary><b>7. What is the Python Virtual Machine (PVM)?</b></summary>

The **runtime engine** that executes bytecode line by line. It’s part of the Python interpreter.

</details>

---

<details>
<summary><b>8. How does Python manage memory?</b></summary>

* **Reference Counting**
* **Garbage Collector** for cyclic references
* **Private Heap** managed internally

</details>

---

<details>
<summary><b>9. What is the difference between mutable and immutable?</b></summary>

| Type      | Mutable | Example         |
| --------- | ------- | --------------- |
| Mutable   | ✅       | list, dict, set |
| Immutable | ❌       | str, int, tuple |

</details>

---

<details>
<summary><b>10. What is a decorator?</b></summary>

A **function that modifies another function** without changing its code.

```python
@decorator
def hello():
    print("Hello!")
```

</details>

---

## 🧩 Object-Oriented Programming (OOP)

<details>
<summary><b>1. What are class and instance attributes?</b></summary>

* **Class attribute:** Shared by all instances
* **Instance attribute:** Unique per object

</details>

---

<details>
<summary><b>2. What is the difference between __init__ and __new__?</b></summary>

`__new__` creates a new instance, `__init__` initializes it.

</details>

---

<details>
<summary><b>3. What is MRO (Method Resolution Order)?</b></summary>

Defines the order of inheritance lookup.
Follows **C3 Linearization**.
Check with `ClassName.__mro__`.

</details>

---

<details>
<summary><b>4. What is polymorphism in Python?</b></summary>

Same method name → different behavior depending on object type.

</details>

---

<details>
<summary><b>5. What are abstract base classes (ABCs)?</b></summary>

Used to define **common interfaces** and enforce subclass implementation using `abc` module.

</details>

---

## ⚙️ Python Internals

<details>
<summary><b>1. What is bytecode?</b></summary>

Intermediate instructions executed by the Python Virtual Machine.

</details>

---

<details>
<summary><b>2. How does Python handle imports?</b></summary>

1. Checks `sys.modules`
2. Searches `sys.path`
3. Compiles & executes
4. Stores module in memory

</details>

---

<details>
<summary><b>3. How does garbage collection work?</b></summary>

Uses **reference counting** and **cyclic garbage collection (generational GC)**.

</details>

---

<details>
<summary><b>4. What is the difference between process and thread?</b></summary>

| Type    | Memory   | Affected by GIL? |
| ------- | -------- | ---------------- |
| Thread  | Shared   | ✅ Yes            |
| Process | Separate | ❌ No             |

</details>

---

<details>
<summary><b>5. What is Python’s memory allocator?</b></summary>

Uses **PyMalloc** for small objects (<512 bytes).
Large objects use system malloc.

</details>

---

## 🧩 Miscellaneous Quick Q&A

* **eval()** → Evaluates expression
* **exec()** → Executes code block
* **compile()** → Compiles to bytecode
* ****slots**** → Restricts dynamic attributes, saves memory
* **Descriptors** → Custom attribute behavior using `__get__`, `__set__`, `__delete__`
* **Context Managers** → Manage setup/cleanup with `__enter__` and `__exit__`
* **@property** → Access method as attribute

---

## 💡 Summary

Python is an **interpreted**, **dynamically typed**, **object-oriented** language.
It compiles source to **bytecode**, runs it in the **PVM**, and manages memory automatically using **reference counting + garbage collection**.

---

## 📚 Author

**Sakshi Agarwal**
🌟 Passionate about Python, AWS, and backend engineering.

---

## 🏷️ License

This project is licensed under the MIT License — free to use and share.
