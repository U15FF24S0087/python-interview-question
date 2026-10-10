# Day 3 – Python Interview Preparation

## 1. What is the difference between local and global variables in Python?

A **local variable** is created inside a function and can normally be used only there. A **global variable** is defined outside functions and can be read throughout the module.

```python
count = 0  # global

def update():
    message = "Hello"  # local
    print(count)        # can read the global variable
```

To assign to a global variable inside a function, declare it with `global`:

```python
count = 0

def update():
    global count
    count += 1
```

Without `global`, assigning to `count` inside `update` creates a local variable instead.

## 2. What is the difference between positional, keyword, and default arguments?

- **Positional arguments** are matched to parameters by their order.
- **Keyword arguments** are matched by parameter name.
- **Default arguments** have a value used when the caller does not provide one.

```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Maya")                      # positional; uses the default greeting
greet(name="Maya")                 # keyword; uses the default greeting
greet(name="Maya", greeting="Hi")   # keyword; overrides the default
```

Positional arguments must come before keyword arguments in a call.

## 3. `*args` and `**kwargs`: What are they, and when do we use them?

They let a function accept a variable number of arguments:

- `*args` collects extra **positional** arguments into a tuple.
- `**kwargs` collects extra **keyword** arguments into a dictionary.

```python
def describe(*args, **kwargs):
    print(args)
    print(kwargs)

describe("Python", "interviews", level="beginner")
# args: ("Python", "interviews")
# kwargs: {"level": "beginner"}
```

Use them when a function needs to accept a flexible set of arguments, such as a wrapper that passes arguments to another function.

## 4. What is the difference between `return` and `print()` in Python?

`print()` displays a value for a person to see. `return` sends a value back to the code that called the function, where it can be stored or used in another calculation.

```python
def add_and_print(a, b):
    print(a + b)  # displays the result

def add_and_return(a, b):
    return a + b  # gives the result back

result = add_and_return(2, 3)
print(result * 2)  # 10
```

A function that does not explicitly `return` a value returns `None`.

## 5. What is a lambda function in Python, and how is it different from a normal function?

A **lambda** is a small, anonymous function written as a single expression. It implicitly returns the expression's result.

```python
double = lambda number: number * 2
print(double(4))  # 8
```

The equivalent normal function is:

```python
def double(number):
    return number * 2
```

Lambdas are useful for short, simple operations, often when passing a function to another function. Use `def` when the function needs multiple statements, a descriptive name, or more complex logic.
