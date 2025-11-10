# ⚙️ Advanced Python Code Q&A — Decorators, Generators, Iterators, and Beyond

A practical collection of **interview-focused advanced Python code examples** and explanations on decorators, generators, context managers, and functional programming.

---

## 🧩 Decorators

<details>
<summary><b>1. What is a decorator?</b></summary>
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

Output:

```
Before function call
Hello!
After function call
```

</details>

<details>
<summary><b>2. How to create a decorator that takes arguments?</b></summary>
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

````
</details>

<details>
<summary><b>3. How to preserve function metadata with decorators?</b></summary>
Use `functools.wraps` to copy name and docstring.
```python
from functools import wraps

def deco(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)
    return wrapper
````

</details>

<details>
<summary><b>4. What are class decorators?</b></summary>
A decorator applied to a class instead of a function.
```python
def add_repr(cls):
    cls.__repr__ = lambda self: f"{cls.__name__}({self.__dict__})"
    return cls

@add_repr
class Point:
def **init**(self, x, y):
self.x, self.y = x, y

p = Point(1, 2)
print(p)

````
</details>

---

## ⚙️ Generators

<details>
<summary><b>1. What is a generator function?</b></summary>
A function that uses `yield` to return an iterator one value at a time.
```python
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

for num in count_up_to(5):
    print(num)
````

</details>

<details>
<summary><b>2. How is a generator different from a normal function?</b></summary>
- Uses `yield` instead of `return`.
- Remembers state between calls.
- Consumes less memory (lazy evaluation).
</details>

<details>
<summary><b>3. How to send values into a generator?</b></summary>
```python
def greeter():
    name = yield "Hello"
    yield f"Hi {name}"

g = greeter()
print(next(g))
print(g.send("Sakshi"))

````
</details>

<details>
<summary><b>4. What is a generator expression?</b></summary>
Similar to list comprehension but lazy.
```python
gen = (x*x for x in range(5))
print(next(gen))
````

</details>

---

## 🔁 Iterators

<details>
<summary><b>1. What makes an object iterable?</b></summary>
An object implementing `__iter__()` returning an iterator object that has `__next__()`.
</details>

<details>
<summary><b>2. How to create a custom iterator?</b></summary>
```python
class Counter:
    def __init__(self, start, end):
        self.current = start
        self.end = end

```
def __iter__(self):
    return self

def __next__(self):
    if self.current > self.end:
        raise StopIteration
    self.current += 1
    return self.current - 1
```

for i in Counter(1, 3):
print(i)

````
</details>

---

## 🧠 Context Managers

<details>
<summary><b>1. What are context managers?</b></summary>
They handle setup and teardown logic using `__enter__()` and `__exit__()`.
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
````

</details>

<details>
<summary><b>2. How to create context managers using decorators?</b></summary>
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

````
</details>

---

## 🧰 Functional Programming

<details>
<summary><b>1. What are map, filter, and reduce?</b></summary>
```python
from functools import reduce
nums = [1, 2, 3, 4]
print(list(map(lambda x: x*2, nums)))      # [2, 4, 6, 8]
print(list(filter(lambda x: x%2==0, nums))) # [2, 4]
print(reduce(lambda a,b: a+b, nums))        # 10
````

</details>

<details>
<summary><b>2. What is partial function application?</b></summary>
```python
from functools import partial

def power(base, exp):
return base ** exp

square = partial(power, exp=2)
print(square(5))  # 25

````
</details>

<details>
<summary><b>3. What are higher-order functions?</b></summary>
Functions that take other functions as arguments or return them.
</details>

---

## ⚡ Advanced Tricks & Idioms

<details>
<summary><b>1. What is memoization (caching)?</b></summary>
```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)

print(fib(10))
````

</details>

<details>
<summary><b>2. How to chain multiple iterables?</b></summary>
```python
from itertools import chain
for i in chain([1,2], [3,4]):
    print(i)
```
</details>

<details>
<summary><b>3. How to group data using itertools.groupby?</b></summary>
```python
from itertools import groupby
nums = [1,1,2,2,3,3]
for k, g in groupby(nums):
    print(k, list(g))
```
</details>

<details>
<summary><b>4. How to create infinite iterators?</b></summary>
```python
from itertools import count, cycle
for i in count(1):
    if i > 3:
        break
    print(i)
```
</details>

---

## 🧾 Summary

This file includes **hands-on code snippets** for mastering advanced Python concepts — decorators, generators, iterators, context managers, functional programming, and performance tricks.

---

**Author:** Sakshi Agarwal
🚀 Advanced Python | AWS | Backend Engineering
