---
title: Python | Programacion
description: Cosas basicas para aprender a programar python
date: 2026-01-17 10:00:0 +0000
categories: [Programming, Python]
tags: [Python, Programming]
pin: false
mermaid: true
---
# Python Basics — What You Should Know

This is a simple guide to the basic Python concepts.

---

## 1. What is Python?

Python is a **high-level, interpreted, general-purpose programming language**.

- **High-level** → Python syntax is relatively easy for humans to read.
- **Interpreted** → Python code is executed by the Python interpreter.
- **General-purpose** → It can be used for web development, automation, cybersecurity, data analysis, scripting, and more.

Example:

```python
print("Hello World")
```

---

# 2. Variables and Data Types

## What is a variable?

A variable is a **name that refers to a value**.

Python does not require you to declare the type of a variable. Python determines the type automatically.

```python
name = "Isaac"
age = 27
height = 1.75
is_student = True
```

## Main Data Types

| Type | Example | Meaning |
|---|---|---|
| `str` | `"hello"` | Text |
| `int` | `10` | Whole number |
| `float` | `3.14` | Decimal number |
| `bool` | `True` / `False` | True or false |
| `list` | `[1, 2, 3]` | Ordered and changeable collection |
| `tuple` | `(1, 2, 3)` | Ordered and unchangeable collection |
| `set` | `{1, 2, 3}` | Collection without duplicates |
| `dict` | `{"name": "Isaac"}` | Key-value pairs |

You can use `type()` to check the type of a value.

```python
name = "Isaac"
age = 27

print(type(name))
print(type(age))
```

### Say it like this

> "In Python, variables don't need a fixed type. Python determines the type automatically based on the value."

---

# 3. Type Casting

## What is Type Casting?

**Type Casting** is the process of **converting a value from one data type to another**.

Common functions:

- `int()` → converts to integer
- `float()` → converts to decimal
- `str()` → converts to string
- `bool()` → converts to boolean

```python
number = "10"

number = int(number)

print(number)
print(type(number))
```

Another example:

```python
number = 10

decimal = float(number)
text = str(number)

print(decimal)
print(text)
```

### `input()` and Type Casting

`input()` always returns a **string**.

```python
age = input("Enter your age: ")

print(type(age))
```

If we need an integer:

```python
age = int(input("Enter your age: "))

print(type(age))
```

> "Type casting allows me to convert data from one type to another, for example converting user input from a string to an integer."

---

# 4. Operators

## What are operators?

Operators are symbols or keywords used to **perform operations on values**.

---

## Arithmetic Operators

| Operator | Meaning | Example |
|---|---|---|
| `+` | Addition | `5 + 3` |
| `-` | Subtraction | `5 - 3` |
| `*` | Multiplication | `5 * 3` |
| `/` | Division | `5 / 3` |
| `//` | Floor division | `5 // 3` |
| `%` | Remainder | `5 % 3` |
| `**` | Power | `5 ** 2` |

Example:

```python
sum_result = 5 + 3
sub_result = 5 - 3
mult_result = 5 * 3
div_result = 5 / 3
mod_result = 5 % 3

print(sum_result)
print(sub_result)
print(mult_result)
print(div_result)
print(mod_result)
```

---

## Comparison Operators

Comparison operators compare values and return `True` or `False`.

| Operator | Meaning |
|---|---|
| `==` | Equal |
| `!=` | Not equal |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal |
| `<=` | Less than or equal |

```python
print(5 > 3)
print(5 == 3)
print(5 != 3)
print(10 >= 10)
```

---

## Logical Operators

Logical operators allow us to combine conditions.

### `and`

Both conditions must be `True`.

```python
age = 20
has_id = True

if age >= 18 and has_id:
    print("Access allowed")
```

### `or`

At least one condition must be `True`.

```python
is_admin = False
is_manager = True

if is_admin or is_manager:
    print("Access allowed")
```

### `not`

Reverses a boolean value.

```python
is_blocked = False

if not is_blocked:
    print("User is allowed")
```



> "`and` requires both conditions to be true, `or` requires at least one, and `not` reverses the condition."

---

# 5. Strings

## What is a String?

A **string (`str`)** is a sequence of characters used to represent text.

```python
text = "Hello World"

print(text)
print(type(text))
```

Strings are **immutable**, which means their individual characters cannot be changed directly.

```python
text = "Python"

# text[0] = "J"  # Error
```

---

## Useful String Methods

### `lower()`

Converts text to lowercase.

```python
text = "HELLO"

print(text.lower())
```

### `upper()`

Converts text to uppercase.

```python
text = "hello"

print(text.upper())
```

### `split()`

Splits a string into a list.

```python
text = "Hello World"

print(text.split(" "))
```

### `replace()`

Replaces part of a string.

```python
text = "Hello World"

print(text.replace("World", "Python"))
```

### `len()`

Returns the number of characters.

```python
text = "Python"

print(len(text))
```

### `in`

Checks if text exists inside another string.

```python
text = "Hello Python"

print("Python" in text)
```

---

# 6. String Formatting

## What is String Formatting?

String formatting allows us to **insert variables or values into text**.

---

## f-strings

The recommended and easiest way.

```python
name = "Isaac"
age = 27

print(f"My name is {name} and I am {age} years old.")
```

You can also perform operations:

```python
number = 5

print(f"Double: {number * 2}")
```

---

## `format()`

Another way to insert values into strings.

```python
name = "Isaac"
age = 27

print("My name is {} and I am {} years old.".format(name, age))
```

---

## `%` Formatting

An older way of formatting strings.

```python
name = "Isaac"

print("My name is %s" % name)
```

> "I normally use f-strings because they are simple and easy to read."

---

# 7. Lists

## What is a List?

A **list** is a data structure used to store **multiple values in one variable**.

Lists are:

- Ordered
- Mutable
- Able to contain duplicate values
- Able to contain different data types

```python
numbers = [10, 20, 30]

print(numbers)
```

---

## Accessing List Elements

Python indexes start at `0`.

```python
numbers = [10, 20, 30]

print(numbers[0])
print(numbers[1])
print(numbers[2])
```

Output:

```text
10
20
30
```

---

## Adding Elements

### `append()`

Adds one element to the end.

```python
numbers = [10, 20, 30]

numbers.append(40)

print(numbers)
```

### `extend()`

Adds multiple elements.

```python
numbers = [10, 20, 30]

numbers.extend([40, 50])

print(numbers)
```

---

## Removing Elements

### `remove()`

Removes a specific value.

```python
numbers = [10, 20, 30]

numbers.remove(20)

print(numbers)
```

### `pop()`

Removes an element using its index. Without an index, it removes the last element.

```python
numbers = [10, 20, 30]

numbers.pop()

print(numbers)
```

---

## Sorting

```python
numbers = [30, 10, 20]

numbers.sort()

print(numbers)
```

---

## List Length

`len()` returns the number of elements.

```python
numbers = [10, 20, 30]

print(len(numbers))
```

---

## List Slicing

**Slicing** allows us to obtain part of a list.

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[0:3])
```

Output:

```text
[10, 20, 30]
```

Other examples:

```python
print(numbers[:3])   # First 3 elements
print(numbers[2:])   # From index 2
print(numbers[-1])   # Last element
```

> "A list is useful when I need an ordered collection of values that I may need to modify."

---

# 8. Tuples

## What is a Tuple?

A **tuple** is an ordered collection of values that **cannot be changed after creation**.

```python
coordinates = (10, 20)

print(coordinates[0])
```

Trying to modify it causes an error:

```python
coordinates[0] = 50
```

### List vs Tuple

| List | Tuple |
|---|---|
| Mutable | Immutable |
| `[1, 2, 3]` | `(1, 2, 3)` |
| Can be modified | Cannot be modified |

---

# 9. Sets

## What is a Set?

A **set** is a collection that does **not allow duplicate values**.

```python
ports = {22, 80, 443, 80}

print(ports)
```

The duplicated `80` is stored only once.

Sets are useful when you need **unique values**.

```python
numbers = [1, 2, 2, 3, 3, 4]

unique_numbers = set(numbers)

print(unique_numbers)
```

---

# 10. Dictionaries

## What is a Dictionary?

A **dictionary (`dict`)** stores data as **key-value pairs**.

```python
user = {
    "name": "Isaac",
    "age": 27,
    "role": "student"
}
```

Here:

- `"name"` → key
- `"Isaac"` → value

---

## Accessing Values

```python
print(user["name"])
```

---

## Updating Values

```python
user["age"] = 28

print(user)
```

---

## Adding Values

```python
user["city"] = "San Jose"

print(user)
```

---

## Useful Dictionary Methods

### `keys()`

Returns the keys.

```python
print(user.keys())
```

### `values()`

Returns the values.

```python
print(user.values())
```

### `items()`

Returns key-value pairs.

```python
print(user.items())
```

### `get()`

Gets a value safely.

```python
print(user.get("name"))
```

If the key does not exist:

```python
print(user.get("email"))
```

It returns `None` instead of immediately causing a `KeyError`.


> "A dictionary is useful when I need to associate a value with a key, such as a username, ID, or configuration."

---

# 11. Conditionals

## What are Conditionals?

Conditionals allow a program to **make decisions based on conditions**.

Python uses:

- `if`
- `elif`
- `else`

```python
age = 20

if age < 18:
    print("You are a minor.")
elif age < 65:
    print("You are an adult.")
else:
    print("You are a senior.")
```

### Meaning

- `if` → checks the first condition.
- `elif` → checks another condition if the previous one was false.
- `else` → runs when none of the conditions are true.


> "`if` checks a condition. `elif` checks another condition if the first one was false. `else` runs when none of the conditions are true."

---

# 12. Loops

## What is a Loop?

A **loop** repeats a block of code.

Python mainly uses:

- `for`
- `while`

---

## What is an Iterable?

An **iterable** is an object that can be traversed element by element.

Examples:

```python
names = ["Isaac", "Maria", "David"]

text = "Python"

numbers = range(5)
```

These can be used with a `for` loop.

---

## `for` Loop

A `for` loop is used to **iterate over the elements of an iterable**.

```python
fruits = ["apple", "banana", "orange"]

for fruit in fruits:
    print(fruit)
```

---

## `range()`

`range()` generates a sequence of numbers.

```python
for i in range(5):
    print(i)
```

Output:

```text
0
1
2
3
4
```

 `range(5)` stops before `5`.

---

## `while` Loop

A `while` loop repeats while a condition is `True`.

```python
count = 0

while count < 3:
    print(count)
    count += 1
```

---

# 13. break, continue and pass

## `break`

Stops the loop completely.

```python
for number in range(10):

    if number == 5:
        break

    print(number)
```

---

## `continue`

Skips the current iteration and continues with the next one.

```python
for number in range(5):

    if number == 2:
        continue

    print(number)
```

---

## `pass`

Does nothing. It is useful as a placeholder when code will be added later.

```python
def future_function():
    pass
```

---

# 14. Functions

## What is a Function?

A **function** is a reusable block of code designed to perform a specific task.

Functions help us:

- Avoid repeating code
- Organize the program
- Make code easier to read
- Make code easier to maintain

Functions are created using `def`.

```python
def greet():
    print("Hello")
```

To execute the function:

```python
greet()
```

---

## Parameters

A **parameter** is a variable that receives a value when the function is called.

```python
def greet(name):
    print(f"Hello {name}")

greet("Isaac")
```

Here, `name` is the parameter.

---

## Arguments

An **argument** is the actual value passed to a function.

```python
greet("Isaac")
```

`"Isaac"` is the argument.

---

## `return`

`return` sends a value back from the function.

```python
def add(a, b):
    return a + b

result = add(5, 3)

print(result)
```

### `print()` vs `return`

`print()` displays something:

```python
def add(a, b):
    print(a + b)
```

`return` gives the value back so it can be stored or used later:

```python
def add(a, b):
    return a + b

result = add(5, 3)
```

---

## Default Parameters

A parameter can have a default value.

```python
def add_numbers(a, b=0):
    return a + b

print(add_numbers(5, 3))
print(add_numbers(5))
```

In the second call, `b` uses the default value `0`.


> "Functions help me avoid repeating code. I can write the logic once and call it many times with different values."

---

# 15. Scope

## What is Scope?

**Scope** defines **where a variable exists and where it can be used**.

The two basic scopes are:

- Local
- Global

---

## Local Variable

A local variable is created inside a function and normally can only be used inside that function.

```python
def test():
    message = "Local variable"
    print(message)

test()
```

This will cause an error:

```python
print(message)
```

because `message` only exists inside `test()`.

---

## Global Variable

A global variable is created outside a function.

```python
message = "Global variable"

def test():
    print(message)

test()
```

The function can read the global variable.

### Local vs Global

```python
message = "Global"

def test():
    message = "Local"
    print(message)

test()

print(message)
```

Output:

```text
Local
Global
```

They are different variables even though they have the same name.


> "Scope defines where a variable can be accessed. A local variable belongs to a function, while a global variable is defined outside functions."

---

# 16. Lambda Functions

## What is a Lambda Function?

A **lambda function** is a small, anonymous function usually written in one line.

It is useful for simple operations.

### Structure

```python
lambda arguments: expression
```

Example:

```python
square = lambda x: x ** 2

print(square(5))
```

Lambda with two parameters:

```python
add = lambda x, y: x + y

print(add(5, 3))
```

📌 For complex logic, a normal function using `def` is usually clearer.

---

# 17. List Comprehensions

## What is a List Comprehension?

A **list comprehension** is a short way to create a list from an iterable.

Normal approach:

```python
numbers = [1, 2, 3, 4]

squares = []

for number in numbers:
    squares.append(number ** 2)

print(squares)
```

Using list comprehension:

```python
numbers = [1, 2, 3, 4]

squares = [number ** 2 for number in numbers]

print(squares)
```

It produces:

```text
[1, 4, 9, 16]
```

---

# 18. enumerate(), zip(), map() and filter()

## `enumerate()`

`enumerate()` gives us both the **index and the value**.

```python
names = ["Isaac", "Maria", "David"]

for index, name in enumerate(names):
    print(index, name)
```

---

## `zip()`

`zip()` combines elements from two or more iterables.

```python
names = ["Isaac", "Maria"]
ages = [27, 25]

for name, age in zip(names, ages):
    print(name, age)
```

---

## `map()`

`map()` applies a function to every element.

```python
numbers = [1, 2, 3, 4]

squares = list(map(lambda x: x ** 2, numbers))

print(squares)
```

---

## `filter()`

`filter()` keeps only the elements that satisfy a condition.

```python
numbers = [1, 2, 3, 4, 5]

even_numbers = list(
    filter(lambda x: x % 2 == 0, numbers)
)

print(even_numbers)
```

---

# 19. Error Handling

## What is an Error?

An error occurs when something goes wrong in a program.

Example:

```python
number = 10 / 0
```

This produces a `ZeroDivisionError`.

---

## What is an Exception?

An **exception** is an event that occurs during program execution that interrupts the normal flow of the program.

Python allows us to **handle exceptions** instead of allowing the program to stop unexpectedly.

---

## `try`

Contains the code that might cause an exception.

## `except`

Handles the exception.

## `else`

Runs if no exception occurs.

## `finally`

Runs whether an exception occurs or not.

Example:

```python
try:
    number = int(input("Enter a number: "))
    result = 10 / number

except ValueError:
    print("That is not a valid number.")

except ZeroDivisionError:
    print("You cannot divide by zero.")

else:
    print("Result:", result)

finally:
    print("This always runs.")
```

> "`try` contains the code I want to test. `except` handles an error. `else` runs if there is no error, and `finally` always runs."

---

# 20. raise

## What is `raise`?

`raise` is used to **manually create an exception**.

```python
age = -5

if age < 0:
    raise ValueError("Age cannot be negative")
```

This is useful when we want to validate data.

---

# 21. Working with Files

## What is File Handling?

File handling allows a program to **read, create, modify, and write files**.

---

## Writing to a File

```python
with open("data.txt", "w") as file:
    file.write("Hello, this is a test.")
```

`"w"` means **write**.

---

## Reading a File

```python
with open("data.txt", "r") as file:
    content = file.read()

print(content)
```

`"r"` means **read**.

---

## Why use `with`?

`with` automatically closes the file after we finish using it.

```python
with open("data.txt", "r") as file:
    content = file.read()
```

> "I use `with open()` because Python automatically closes the file when the block finishes, even if an error occurs."

---

# 22. Modules and Imports

## What is a Module?

A **module** is a Python file that contains reusable code such as functions, classes, or variables.

We can import modules into our program.

```python
import math

print(math.sqrt(16))
```

---

## Useful Python Modules

### `os`

Used to interact with the operating system.

```python
import os

print(os.getcwd())
```

---

### `re`

Used for **Regular Expressions**, which allow us to search for patterns in text.

```python
import re

text = "IP: 192.168.1.10"

match = re.search(r"\d+\.\d+\.\d+\.\d+", text)

print(match.group())
```

---

### `json`

Used to work with JSON data.

```python
import json

data = '{"name": "Isaac", "age": 27}'

user = json.loads(data)

print(user["name"])
```

---

### `subprocess`

Used to execute system commands from Python.

```python
import subprocess

result = subprocess.run(
    ["whoami"],
    capture_output=True,
    text=True
)

print(result.stdout)
```

📌 `subprocess` is especially useful for **automation and system scripting**.

---

# 23. if __name__ == "__main__"

## What does it mean?

This is one of the concepts that can be confusing at first.

```python
if __name__ == "__main__":
```

It checks whether the Python file is being **executed directly** or **imported as a module**.

Python automatically gives the variable `__name__` a value.

When the file is executed directly:

```text
__name__ == "__main__"
```

When the file is imported:

```text
__name__ != "__main__"
```

---

## Example

```python
def scan_ports():
    print("Scanning ports...")


if __name__ == "__main__":
    scan_ports()
```

If we execute:

```text
python scanner.py
```

Python sees:

```text
__name__ == "__main__"
```

So it executes:

```python
scan_ports()
```

But if another file does:

```python
import scanner
```

then `scan_ports()` is not automatically executed.

### Why is this useful?

It allows us to create files that can work as both:

- A standalone script
- A reusable module


> "`if __name__ == '__main__'` makes sure that some code only runs when the file is executed directly, not when the file is imported."

---

# 24. Object-Oriented Programming (OOP)

## What is OOP?

**Object-Oriented Programming** is a programming style based on **classes and objects**.

You do not need deep OOP knowledge for basic Python, but you should understand the concept.

---

## What is a Class?

A **class** is like a template used to create objects.

```python
class User:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hi, my name is {self.name}"
```

Creating an object:

```python
user1 = User("Isaac", 27)

print(user1.greet())
```

---

## `__init__`

`__init__` is a special method that runs when an object is created.

It is commonly used to initialize the object's data.

---

## `self`

`self` refers to the **current object**.

```python
self.name = name
```

This means that the object stores the value in its own `name` attribute.


> "A class is a template used to create objects. `__init__` initializes the object, and `self` refers to the current object."

---

# 25. Regular Expressions (Regex)

## What is Regex?

**Regex (Regular Expression)** is a pattern used to **search, match, or validate text**.

It is very useful for automation, log analysis, and cybersecurity.

Example:

```python
import re

text = "User logged in from 192.168.1.10"

pattern = r"\d+\.\d+\.\d+\.\d+"

match = re.search(pattern, text)

if match:
    print("IP found:", match.group())
```

Output:

```text
IP found: 192.168.1.10
```

📌 Regex can be used to find IP addresses, emails, usernames, dates, log entries, and other patterns.

---

# 26. Useful Python Libraries for Automation

These libraries are useful to know

| Library | Main use |
|---|---|
| `os` | Operating system interaction |
| `sys` | Python interpreter and program arguments |
| `subprocess` | Execute system commands |
| `re` | Regular expressions |
| `json` | JSON data |
| `requests` | HTTP requests |
| `pathlib` | Files and directories |
| `datetime` | Dates and times |
| `math` | Mathematical operations |

Example:

```python
import os
import re
import json
```

You do not need to memorize every function in these libraries.

The important thing is to understand **what each library is used for** and know how to look up its documentation when needed.

---

# 27. Python Naming Conventions

## What are Naming Conventions?

Naming conventions are **recommended rules for naming variables, functions, classes, and constants**.

### `snake_case`

Used for variables and functions.

```python
user_name = "Isaac"

def check_connection():
    pass
```

### `PascalCase`

Used for classes.

```python
class NetworkScanner:
    pass
```

### `SCREAMING_SNAKE_CASE`

Usually used for constants.

```python
MAX_CONNECTIONS = 100
API_VERSION = 1
```

Python follows style recommendations described in **PEP 8**.

---

# 29. Quick Reference

| Concept | Simple meaning |
|---|---|
| Variable | Name that refers to a value |
| `str` | Text |
| `int` | Whole number |
| `float` | Decimal number |
| `bool` | True or False |
| List | Ordered, changeable collection |
| Tuple | Ordered, unchangeable collection |
| Set | Collection without duplicates |
| Dictionary | Key-value collection |
| Type Casting | Converting one type to another |
| Operator | Performs an operation |
| Conditional | Makes a decision |
| Loop | Repeats code |
| Function | Reusable block of code |
| Parameter | Variable received by a function |
| Argument | Value passed to a function |
| `return` | Sends a value back |
| Scope | Where a variable can be accessed |
| Lambda | Small anonymous function |
| Exception | Runtime problem that can be handled |
| `raise` | Manually creates an exception |
| Module | Python file with reusable code |
| Class | Template for creating objects |
| Object | Instance of a class |
| Regex | Pattern used to search text |
| Iterable | Object that can be traversed |

---

# Final Goal

For a basic Python level, you should be able to:

- Create variables
- Identify basic data types
- Convert between data types
- Use operators
- Work with strings
- Work with lists, tuples, sets, and dictionaries
- Use `if`, `elif`, and `else`
- Use `for` and `while`
- Use `break`, `continue`, and `pass`
- Create functions
- Use parameters and `return`
- Understand local and global scope
- Use lambda functions
- Create list comprehensions
- Use `enumerate()`, `zip()`, `map()`, and `filter()`
- Handle exceptions with `try` and `except`
- Read and write files
- Import modules
- Understand `if __name__ == "__main__"`
- Understand basic OOP
- Know what Regex is
- Know the purpose of common Python libraries
