# ⚙️ Advanced Python Code Q&A — Decorators, Generators, Iterators, and Beyond

A practical collection of **interview-focused advanced Python code examples** and explanations — including decorators, generators, iterators, context managers, and functional programming.

---

## 🧩 Decorators

### 1. What is a decorator?

A decorator is a function that takes another function as input and modifies or extends its behavior without changing its code.

```python
def my_decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@my_decorator
def greet():
    print("Hello!")

greet()
```

**Output:**

```
Before function call
Hello!
After function call
```

---

### 2. How to create a decorator that takes arguments?

```python
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(3)
def say_hi():
    print("Hi!")

say_hi()
```

---

### 3. How to preserve function metadata in decorators?

Use `functools.wraps` to copy the original function’s metadata.

```python
from functools import wraps

def deco(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)
    return wrapper
```

---

### 4. What are class decorators?

Decorators can also modify class behavior.

```python
def add_repr(cls):
    cls.__repr__ = lambda self: f"{cls.__name__}({self.__dict__})"
    return cls

@add_repr
class Point:
    def __init__(self, x, y):
        self.x, self.y = x, y

p = Point(1, 2)
print(p)
```

**Output:**

```
Point({'x': 1, 'y': 2})
```

---

## ⚙️ Generators — Deep Dive

### 1. What is a generator function?

A function that yields one item at a time instead of returning all results at once.

```python
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

for num in count_up_to(5):
    print(num)
```

---

### 2. Difference between `return` and `yield`

* `return` terminates the function.
* `yield` pauses the function and resumes later, remembering state.

---

### 3. Sending values into a generator

```python
def greeter():
    name = yield "Hello! What's your name?"
    yield f"Hi {name}!"

g = greeter()
print(next(g))      # Starts the generator
print(g.send("Sakshi"))  # Sends a value into generator
```

**Output:**

```
Hello! What's your name?
Hi Sakshi!
```

---

### 4. Using `yield from`

Delegates part of a generator’s operation to another generator.

```python
def sub_gen():
    yield from range(3)

def main_gen():
    yield from sub_gen()
    yield 100

for val in main_gen():
    print(val)
```

**Output:**

```
0
1
2
100
```

---

### 5. Closing a generator

```python
def my_gen():
    try:
        yield 1
        yield 2
    except GeneratorExit:
        print("Generator closed")

g = my_gen()
print(next(g))
g.close()
```

**Output:**

```
1
Generator closed
```

---

### 6. Throwing exceptions inside generators

```python
def my_gen():
    try:
        yield 1
    except ValueError:
        print("ValueError caught inside generator")

g = my_gen()
print(next(g))
g.throw(ValueError)
```

**Output:**

```
1
ValueError caught inside generator
```

---

### 7. Generator pipelines (chaining generators)

```python
def read_lines(lines):
    for line in lines:
        yield line.strip()

def filter_nonempty(lines):
    for line in lines:
        if line:
            yield line

lines = ["Python", "", "AWS"]
for line in filter_nonempty(read_lines(lines)):
    print(line)
```

**Output:**

```
Python
AWS
```

---

### 8. Reading large files lazily

```python
def read_file_in_chunks(filename, chunk_size=1024):
    with open(filename, 'r') as f:
        while True:
            data = f.read(chunk_size)
            if not data:
                break
            yield data

for chunk in read_file_in_chunks('bigdata.txt'):
    process(chunk)
```

---

### 9. Generators + Decorators

```python
from functools import wraps

def log_gen(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print(f"Starting generator {func.__name__}")
        for value in func(*args, **kwargs):
            print(f"Yielded: {value}")
            yield value
        print(f"Generator {func.__name__} finished")
    return wrapper

@log_gen
def squares(n):
    for i in range(n):
        yield i*i

for num in squares(3):
    pass
```

**Output:**

```
Starting generator squares
Yielded: 0
Yielded: 1
Yielded: 4
Generator squares finished
```

---

## 🔁 Iterators

### 1. What makes an object iterable?

An object implementing `__iter__()` and returning an iterator object with `__next__()`.

### 2. Creating a custom iterator

```python
class Counter:
    def __init__(self, start, end):
        self.current = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.current > self.end:
            raise StopIteration
        self.current += 1
        return self.current - 1

for i in Counter(1, 3):
    print(i)
```

---

## 🧠 Context Managers

### 1. Basic context manager

```python
class FileManager:
    def __init__(self, filename, mode):
        self.filename, self.mode = filename, mode
    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file
    def __exit__(self, exc_type, exc_val, exc_tb):
        self.file.close()

with FileManager('demo.txt', 'w') as f:
    f.write('Hello')
```

### 2. Using @contextmanager

```python
from contextlib import contextmanager

@contextmanager
def open_file(name, mode):
    f = open(name, mode)
    try:
        yield f
    finally:
        f.close()

with open_file('demo.txt', 'w') as f:
    f.write('Hello')
```

---

## 🧰 Functional Programming

### 1. map, filter, reduce

```python
from functools import reduce
nums = [1, 2, 3, 4]
print(list(map(lambda x: x*2, nums)))      # [2, 4, 6, 8]
print(list(filter(lambda x: x%2==0, nums))) # [2, 4]
print(reduce(lambda a,b: a+b, nums))        # 10
```

### 2. Partial function application

```python
from functools import partial

def power(base, exp):
    return base ** exp

square = partial(power, exp=2)
print(square(5))  # 25
```

### 3. Higher-order functions

Functions that take other functions as arguments or return them.

---

## ⚡ Advanced Tricks & Idioms

### 1. Memoization with caching

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)

print(fib(10))
```

### 2. Chaining multiple iterables

```python
from itertools import chain
for i in chain([1,2], [3,4]):
    print(i)
```

### 3. Grouping data using itertools.groupby

```python
from itertools import groupby
nums = [1,1,2,2,3,3]
for k, g in groupby(nums):
    print(k, list(g))
```

### 4. Infinite iterators

```python
from itertools import count, cycle
for i in count(1):
    if i > 3:
        break
    print(i)
```

---

## 🧾 Summary

This file now includes **fully formatted, interview-ready Python code examples** — covering decorators, iterators, and **complete generator internals** (`yield from`, `.send()`, `.throw()`, `.close()`, pipelines, and lazy evaluation) — along with functional programming and best practices.

---

**Author:** Sakshi Agarwal
🚀 Advanced Python | AWS | Backend Engineering
