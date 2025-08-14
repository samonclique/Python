# Python
A comprehensive guide to learning Python
# Python Programming Learning Guide

Welcome to your comprehensive journey into Python programming! This guide will take you from complete beginner to proficient Python developer.

## Table of Contents

1. [Getting Started](#getting-started)
2. [Python Basics](#python-basics)
3. [Control Structures](#control-structures)
4. [Functions](#functions)
5. [Data Structures](#data-structures)
6. [Object-Oriented Programming](#object-oriented-programming)
7. [File Handling](#file-handling)
8. [Error Handling](#error-handling)
9. [Modules and Packages](#modules-and-packages)
10. [Advanced Topics](#advanced-topics)
11. [Popular Libraries](#popular-libraries)
12. [Best Practices](#best-practices)
13. [Project Ideas](#project-ideas)
14. [Resources](#resources)

## Getting Started

### Installation

**Windows:**
- Download Python from [python.org](https://python.org)
- Check "Add Python to PATH" during installation
- Verify: `python --version` in Command Prompt

**macOS:**
- Install via Homebrew: `brew install python`
- Or download from python.org
- Verify: `python3 --version` in Terminal

**Linux:**
- Ubuntu/Debian: `sudo apt update && sudo apt install python3 python3-pip`
- CentOS/RHEL: `sudo yum install python3 python3-pip`
- Verify: `python3 --version`

### Development Environment

**Recommended IDEs:**
- **PyCharm** (Professional/Community)
- **VS Code** with Python extension
- **Jupyter Notebook** for data science
- **IDLE** (comes with Python)

**Essential Tools:**
- **pip**: Package installer
- **venv**: Virtual environment manager
- **Git**: Version control

### Your First Python Program

```python
# hello_world.py
print("Hello, World!")
print("Welcome to Python programming!")
```

Run with: `python hello_world.py`

## Python Basics

### Variables and Data Types

```python
# Variables (no declaration needed)
name = "Alice"
age = 25
height = 5.6
is_student = True

# Basic data types
text = "Hello"           # str
number = 42             # int
decimal = 3.14          # float
flag = True             # bool
nothing = None          # NoneType

# Type checking
print(type(name))       # <class 'str'>
print(isinstance(age, int))  # True
```

### Basic Operations

```python
# Arithmetic operators
a, b = 10, 3
print(a + b)    # Addition: 13
print(a - b)    # Subtraction: 7
print(a * b)    # Multiplication: 30
print(a / b)    # Division: 3.333...
print(a // b)   # Floor division: 3
print(a % b)    # Modulus: 1
print(a ** b)   # Exponentiation: 1000

# Comparison operators
print(a > b)    # True
print(a == b)   # False
print(a != b)   # True

# Logical operators
x, y = True, False
print(x and y)  # False
print(x or y)   # True
print(not x)    # False
```

### String Manipulation

```python
text = "Python Programming"

# String methods
print(text.lower())         # python programming
print(text.upper())         # PYTHON PROGRAMMING
print(text.title())         # Python Programming
print(text.replace("Python", "Java"))  # Java Programming

# String formatting
name = "Bob"
age = 30
print(f"My name is {name} and I'm {age} years old")  # f-strings (Python 3.6+)
print("My name is {} and I'm {} years old".format(name, age))  # .format()
print("My name is %s and I'm %d years old" % (name, age))  # % formatting

# String slicing
text = "Hello, World!"
print(text[0])      # H
print(text[-1])     # !
print(text[0:5])    # Hello
print(text[7:])     # World!
print(text[::-1])   # !dlroW ,olleH (reverse)
```

## Control Structures

### Conditional Statements

```python
# if-elif-else
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Your grade is: {grade}")

# Ternary operator
status = "Pass" if score >= 60 else "Fail"
```

### Loops

```python
# for loop
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
    print(f"I like {fruit}")

# for loop with range
for i in range(5):          # 0 to 4
    print(i)

for i in range(1, 6):       # 1 to 5
    print(i)

for i in range(0, 10, 2):   # 0, 2, 4, 6, 8
    print(i)

# while loop
count = 0
while count < 5:
    print(f"Count: {count}")
    count += 1

# Loop control
for i in range(10):
    if i == 3:
        continue    # Skip this iteration
    if i == 7:
        break      # Exit the loop
    print(i)

# enumerate and zip
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 35]

for index, name in enumerate(names):
    print(f"{index}: {name}")

for name, age in zip(names, ages):
    print(f"{name} is {age} years old")
```

## Functions

### Function Basics

```python
# Basic function
def greet(name):
    """Greet a person with their name."""
    return f"Hello, {name}!"

message = greet("Alice")
print(message)

# Function with default parameters
def introduce(name, age=25, city="Unknown"):
    return f"Hi, I'm {name}, {age} years old, from {city}"

print(introduce("Bob"))
print(introduce("Charlie", 30))
print(introduce("Diana", 28, "New York"))

# Variable-length arguments
def calculate_sum(*args):
    """Calculate sum of any number of arguments."""
    return sum(args)

print(calculate_sum(1, 2, 3, 4, 5))  # 15

# Keyword arguments
def create_profile(**kwargs):
    """Create a user profile from keyword arguments."""
    profile = {}
    for key, value in kwargs.items():
        profile[key] = value
    return profile

user = create_profile(name="Alice", age=30, city="Boston", job="Engineer")
print(user)

# Lambda functions (anonymous functions)
square = lambda x: x ** 2
print(square(5))  # 25

numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # [1, 4, 9, 16, 25]
```

### Advanced Function Concepts

```python
# Decorators
def timer_decorator(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timer_decorator
def slow_function():
    import time
    time.sleep(1)
    return "Done!"

slow_function()

# Generator functions
def fibonacci_generator(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

fib = fibonacci_generator(10)
for num in fib:
    print(num, end=" ")
```

## Data Structures

### Lists

```python
# Creating lists
fruits = ["apple", "banana", "orange"]
numbers = [1, 2, 3, 4, 5]
mixed = ["hello", 42, 3.14, True]

# List methods
fruits.append("grape")          # Add to end
fruits.insert(1, "kiwi")        # Insert at index
fruits.remove("banana")         # Remove first occurrence
popped = fruits.pop()           # Remove and return last item
fruits.extend(["mango", "peach"])  # Add multiple items

# List comprehensions
squares = [x**2 for x in range(10)]
even_squares = [x**2 for x in range(10) if x % 2 == 0]
```

### Dictionaries

```python
# Creating dictionaries
person = {
    "name": "Alice",
    "age": 30,
    "city": "Boston"
}

# Dictionary methods
person["job"] = "Engineer"      # Add new key-value pair
name = person.get("name", "Unknown")  # Safe access with default
keys = person.keys()            # Get all keys
values = person.values()        # Get all values
items = person.items()          # Get key-value pairs

# Dictionary comprehension
squares_dict = {x: x**2 for x in range(5)}
```

### Tuples and Sets

```python
# Tuples (immutable)
coordinates = (10, 20)
rgb_color = (255, 128, 0)

# Tuple unpacking
x, y = coordinates
r, g, b = rgb_color

# Sets (unique elements)
unique_numbers = {1, 2, 3, 4, 5}
unique_numbers.add(6)
unique_numbers.discard(3)

# Set operations
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}
print(set1.union(set2))         # {1, 2, 3, 4, 5, 6}
print(set1.intersection(set2))  # {3, 4}
print(set1.difference(set2))    # {1, 2}
```

## Object-Oriented Programming

### Classes and Objects

```python
class Person:
    """A simple Person class."""
    
    # Class variable (shared by all instances)
    species = "Homo sapiens"
    
    def __init__(self, name, age):
        """Initialize a new Person instance."""
        self.name = name        # Instance variable
        self.age = age          # Instance variable
    
    def introduce(self):
        """Return a self-introduction."""
        return f"Hi, I'm {self.name} and I'm {self.age} years old"
    
    def have_birthday(self):
        """Increment age by 1."""
        self.age += 1
        print(f"Happy birthday! {self.name} is now {self.age}")
    
    def __str__(self):
        """String representation of the object."""
        return f"Person(name='{self.name}', age={self.age})"

# Creating objects
alice = Person("Alice", 25)
bob = Person("Bob", 30)

print(alice.introduce())
alice.have_birthday()
print(alice)
```

### Inheritance

```python
class Employee(Person):
    """Employee class that inherits from Person."""
    
    def __init__(self, name, age, job_title, salary):
        super().__init__(name, age)  # Call parent constructor
        self.job_title = job_title
        self.salary = salary
    
    def introduce(self):
        """Override parent method."""
        return f"Hi, I'm {self.name}, a {self.job_title}"
    
    def get_raise(self, amount):
        """Increase salary."""
        self.salary += amount
        print(f"{self.name} got a raise! New salary: ${self.salary}")

class Manager(Employee):
    """Manager class that inherits from Employee."""
    
    def __init__(self, name, age, salary, team_size):
        super().__init__(name, age, "Manager", salary)
        self.team_size = team_size
    
    def introduce(self):
        return f"Hi, I'm {self.name}, a Manager of {self.team_size} people"

# Using inheritance
emp = Employee("Charlie", 28, "Developer", 70000)
mgr = Manager("Diana", 35, 90000, 5)

print(emp.introduce())
print(mgr.introduce())
```

### Advanced OOP Concepts

```python
class BankAccount:
    """Demonstration of encapsulation and properties."""
    
    def __init__(self, account_number, initial_balance=0):
        self.account_number = account_number
        self._balance = initial_balance  # Protected attribute
    
    @property
    def balance(self):
        """Getter for balance."""
        return self._balance
    
    @balance.setter
    def balance(self, value):
        """Setter for balance with validation."""
        if value < 0:
            raise ValueError("Balance cannot be negative")
        self._balance = value
    
    def deposit(self, amount):
        """Deposit money to account."""
        if amount > 0:
            self._balance += amount
            return True
        return False
    
    def withdraw(self, amount):
        """Withdraw money from account."""
        if 0 < amount <= self._balance:
            self._balance -= amount
            return True
        return False
    
    def __str__(self):
        return f"Account {self.account_number}: ${self._balance:.2f}"

account = BankAccount("12345", 1000)
print(account.balance)  # Using property getter
account.deposit(500)
print(account)
```

## File Handling

### Reading and Writing Files

```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is a test file.\n")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# Reading line by line
with open("example.txt", "r") as file:
    for line_number, line in enumerate(file, 1):
        print(f"Line {line_number}: {line.strip()}")

# Appending to a file
with open("example.txt", "a") as file:
    file.write("This line was appended.\n")

# Working with CSV files
import csv

# Writing CSV
data = [
    ["Name", "Age", "City"],
    ["Alice", 25, "Boston"],
    ["Bob", 30, "New York"],
    ["Charlie", 35, "Chicago"]
]

with open("people.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(data)

# Reading CSV
with open("people.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

# Working with JSON
import json

# Writing JSON
person_data = {
    "name": "Alice",
    "age": 25,
    "hobbies": ["reading", "swimming", "coding"]
}

with open("person.json", "w") as file:
    json.dump(person_data, file, indent=2)

# Reading JSON
with open("person.json", "r") as file:
    loaded_data = json.load(file)
    print(loaded_data)
```

## Error Handling

### Exception Handling

```python
# Basic try-except
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple exceptions
try:
    number = int(input("Enter a number: "))
    result = 10 / number
    print(f"Result: {result}")
except ValueError:
    print("Please enter a valid number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")
except Exception as e:
    print(f"An unexpected error occurred: {e}")

# Try-except-else-finally
try:
    file = open("data.txt", "r")
except FileNotFoundError:
    print("File not found!")
else:
    # Executed if no exception occurs
    content = file.read()
    print("File read successfully!")
finally:
    # Always executed
    if 'file' in locals():
        file.close()
        print("File closed.")

# Custom exceptions
class CustomError(Exception):
    """Custom exception class."""
    pass

def validate_age(age):
    if age < 0:
        raise CustomError("Age cannot be negative")
    if age > 150:
        raise CustomError("Age seems unrealistic")
    return True

try:
    validate_age(-5)
except CustomError as e:
    print(f"Validation error: {e}")
```

## Modules and Packages

### Working with Modules

```python
# math_utils.py - Custom module
def add(a, b):
    """Add two numbers."""
    return a + b

def multiply(a, b):
    """Multiply two numbers."""
    return a * b

PI = 3.14159

# Using the custom module
# In another file:
import math_utils

result = math_utils.add(5, 3)
print(f"5 + 3 = {result}")
print(f"PI = {math_utils.PI}")

# Alternative import methods
from math_utils import add, PI
from math_utils import multiply as mult
import math_utils as mu

# Built-in modules
import datetime
import random
import os
import sys

# Current date and time
now = datetime.datetime.now()
print(f"Current time: {now}")

# Random numbers
print(f"Random number: {random.randint(1, 100)}")

# File system operations
current_dir = os.getcwd()
files = os.listdir(".")
print(f"Current directory: {current_dir}")
print(f"Files: {files}")

# System information
print(f"Python version: {sys.version}")
print(f"Platform: {sys.platform}")
```

### Package Structure

```
my_project/
│
├── main.py
└── utils/
    ├── __init__.py
    ├── math_operations.py
    └── string_operations.py
```

```python
# utils/__init__.py
from .math_operations import add, subtract
from .string_operations import capitalize_words

# utils/math_operations.py
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

# utils/string_operations.py
def capitalize_words(text):
    return text.title()

# main.py
from utils import add, capitalize_words

result = add(5, 3)
text = capitalize_words("hello world")
```

## Advanced Topics

### List Comprehensions and Generators

```python
# List comprehensions
squares = [x**2 for x in range(10)]
even_squares = [x**2 for x in range(10) if x % 2 == 0]

# Nested list comprehensions
matrix = [[i*j for j in range(3)] for i in range(3)]

# Dictionary comprehensions
word_lengths = {word: len(word) for word in ["hello", "world", "python"]}

# Set comprehensions
unique_lengths = {len(word) for word in ["hello", "world", "python", "hi"]}

# Generator expressions
squares_gen = (x**2 for x in range(10))
print(sum(squares_gen))  # Generators are memory efficient

# Generator functions
def countdown(n):
    while n > 0:
        yield n
        n -= 1

for num in countdown(5):
    print(num)
```

### Context Managers

```python
# Using context managers
with open("file.txt", "w") as f:
    f.write("Hello, World!")
# File is automatically closed

# Creating custom context managers
class DatabaseConnection:
    def __enter__(self):
        print("Opening database connection")
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Closing database connection")
        if exc_type:
            print(f"Exception occurred: {exc_val}")
        return False  # Don't suppress exceptions

with DatabaseConnection() as db:
    print("Working with database")

# Context manager using contextlib
from contextlib import contextmanager

@contextmanager
def timer():
    import time
    start = time.time()
    try:
        yield
    finally:
        end = time.time()
        print(f"Elapsed time: {end - start:.4f} seconds")

with timer():
    # Some time-consuming operation
    sum(range(1000000))
```

### Regular Expressions

```python
import re

text = "Contact us at info@example.com or support@company.org"

# Basic pattern matching
pattern = r'\b\w+@\w+\.\w+\b'
emails = re.findall(pattern, text)
print(f"Found emails: {emails}")

# Using groups
pattern = r'(\w+)@(\w+)\.(\w+)'
matches = re.findall(pattern, text)
for match in matches:
    username, domain, extension = match
    print(f"Username: {username}, Domain: {domain}, Extension: {extension}")

# Substitution
censored = re.sub(r'\b\w+@\w+\.\w+\b', '[EMAIL]', text)
print(f"Censored: {censored}")

# Validation
def validate_email(email):
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return bool(re.match(pattern, email))

print(validate_email("user@example.com"))  # True
print(validate_email("invalid.email"))     # False
```

## Popular Libraries

### Data Science Libraries

```python
# NumPy - Numerical computing
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
print(f"Array: {arr}")
print(f"Mean: {np.mean(arr)}")
print(f"Sum: {np.sum(arr)}")

# Pandas - Data manipulation
import pandas as pd

data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['Boston', 'New York', 'Chicago']
}

df = pd.DataFrame(data)
print(df)
print(df.describe())  # Statistical summary

# Matplotlib - Data visualization
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

plt.plot(x, y, marker='o')
plt.title('Simple Line Plot')
plt.xlabel('X values')
plt.ylabel('Y values')
plt.show()
```

### Web Development

```python
# Flask - Web framework
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def home():
    return '<h1>Hello, Flask!</h1>'

@app.route('/user/<name>')
def user_profile(name):
    return f'<h1>Welcome, {name}!</h1>'

@app.route('/form', methods=['GET', 'POST'])
def form_handler():
    if request.method == 'POST':
        name = request.form['name']
        return f'Hello, {name}!'
    return '''
        <form method="post">
            <input type="text" name="name" placeholder="Your name">
            <input type="submit" value="Submit">
        </form>
    '''

if __name__ == '__main__':
    app.run(debug=True)

# Requests - HTTP library
import requests

response = requests.get('https://api.github.com/users/octocat')
if response.status_code == 200:
    user_data = response.json()
    print(f"GitHub user: {user_data['name']}")
else:
    print(f"Error: {response.status_code}")
```

## Best Practices

### Code Style and Documentation

```python
"""
Module docstring: Brief description of what this module does.

This module demonstrates Python best practices including:
- Proper naming conventions
- Documentation
- Error handling
- Type hints
"""

from typing import List, Dict, Optional
import logging

# Configure logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

class StudentManager:
    """Manages student records with proper error handling and documentation."""
    
    def __init__(self) -> None:
        """Initialize empty student database."""
        self._students: Dict[str, Dict] = {}
        logger.info("StudentManager initialized")
    
    def add_student(self, student_id: str, name: str, age: int, 
                   grades: Optional[List[float]] = None) -> bool:
        """
        Add a new student to the database.
        
        Args:
            student_id: Unique identifier for the student
            name: Student's full name
            age: Student's age in years
            grades: Optional list of grades
            
        Returns:
            True if student was added successfully, False otherwise
            
        Raises:
            ValueError: If age is negative or student_id already exists
        """
        if age < 0:
            raise ValueError("Age cannot be negative")
        
        if student_id in self._students:
            logger.warning(f"Student {student_id} already exists")
            return False
        
        self._students[student_id] = {
            'name': name,
            'age': age,
            'grades': grades or []
        }
        
        logger.info(f"Added student: {name} ({student_id})")
        return True
    
    def get_student_average(self, student_id: str) -> Optional[float]:
        """Calculate and return student's grade average."""
        if student_id not in self._students:
            return None
        
        grades = self._students[student_id]['grades']
        return sum(grades) / len(grades) if grades else 0.0

# Constants
DEFAULT_GRADE = 0.0
MAX_STUDENTS = 1000

# Example usage with error handling
def main() -> None:
    """Main function demonstrating best practices."""
    manager = StudentManager()
    
    try:
        manager.add_student("001", "Alice Johnson", 20, [85.5, 92.0, 78.5])
        average = manager.get_student_average("001")
        print(f"Alice's average: {average:.2f}")
    
    except ValueError as e:
        logger.error(f"Invalid input: {e}")
    except Exception as e:
        logger.error(f"Unexpected error: {e}")

if __name__ == "__main__":
    main()
```

### Virtual Environments and Requirements

```bash
# Create virtual environment
python -m venv myproject_env

# Activate virtual environment
# Windows:
myproject_env\Scripts\activate
# macOS/Linux:
source myproject_env/bin/activate

# Install packages
pip install requests pandas matplotlib

# Generate requirements file
pip freeze > requirements.txt

# Install from requirements
pip install -r requirements.txt

# Deactivate virtual environment
deactivate
```

## Project Ideas

### Beginner Projects
1. **Calculator**: Build a command-line calculator with basic operations
2. **To-Do List**: Create a task management system with file persistence
3. **Number Guessing Game**: Interactive game with difficulty levels
4. **Password Generator**: Generate secure passwords with customizable criteria
5. **Unit Converter**: Convert between different units (temperature, weight, etc.)

### Intermediate Projects
1. **Web Scraper**: Extract data from websites using requests and BeautifulSoup
2. **Weather App**: Fetch weather data from API and display formatted results
3. **Expense Tracker**: Track personal finances with data visualization
4. **Quiz Application**: Interactive quiz with score tracking and statistics
5. **File Organizer**: Automatically organize files in directories by type/date

### Advanced Projects
1. **Web Application**: Full-stack web app using Flask/Django with database
2. **Data Analysis Dashboard**: Interactive data visualization with Plotly/Dash
3. **Machine Learning Model**: Predict outcomes using scikit-learn
4. **API Service**: RESTful API with authentication and database integration
5. **Desktop GUI Application**: Cross-platform app using tkinter or PyQt

## Resources

### Official Documentation
- [Python.org](https://python.org) - Official Python website
- [Python Documentation](https://docs.python.org/3/) - Comprehensive language reference
- [PEP 8](https://pep8.org/) - Style Guide for Python Code

### Learning Platforms
- [Real Python](https://realpython.com/) - High-quality Python tutorials
- [Python.org Tutorial](https://docs.python.org/3/tutorial/) - Official tutorial
- [Automate the Boring Stuff](https://automatetheboringstuff.com/) - Free practical Python book
- [Python Crash Course](https://nostarch.com/pythoncrashcourse2e) - Beginner-friendly book

### Practice Platforms
- [LeetCode](https://leetcode.com/) - Coding interview preparation
- [HackerRank](https://hackerrank.com/) - Programming challenges
- [Codewars](https://codewars.com/) - Coding kata and challenges
- [Project Euler](https://projecteuler.net/) - Mathematical programming problems

### Community and Help
- [Stack Overflow](https://stackoverflow.com/questions/tagged/python) - Q&A community
- [r/Python](https://reddit.com/r/python) - Reddit Python community
- [Python Discord](https://discord.gg/python) - Real-time chat and help
- [GitHub](https://github.com/topics/python) - Open source Python projects

### Development Tools
- **Package Index**: [PyPI](https://pypi.org/) - Python Package Index
- **Code Formatting**: [Black](https://black.readthedocs.io/) - Code formatter
- **Linting**: [Pylint](https://pylint.org/) - Code analysis tool
- **Testing**: [pytest](https://pytest.org/) - Testing framework

## Next Steps

1. **Start Small**: Begin with basic syntax and simple programs
2. **Practice Daily**: Consistency is key to learning programming
3. **Build Projects**: Apply your knowledge to real-world problems
4. **Read Code**: Study well-written Python code on GitHub
5. **Join Communities**: Engage with other Python developers
6. **Keep Learning**: Python has a rich ecosystem - explore libraries relevant to your interests

Remember: Programming is a skill that improves with practice. Don't be discouraged by challenges - they're part of the learning process. Focus on understanding concepts rather than memorizing syntax, and always strive to write clean, readable code.

Happy coding! 🐍
