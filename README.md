
# Advanced Object-Oriented Programming in Python
A Comprehensive Guide with Real-World Examples

## Table of Contents
- [Advanced Object-Oriented Programming in Python](#advanced-object-oriented-programming-in-python)
  - [Table of Contents](#table-of-contents)
  - [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Setup](#setup)
  - [Core Concepts](#core-concepts)
    - [Introduction to OOP](#introduction-to-oop)
      - [Example:](#example)
    - [Classes and Objects](#classes-and-objects)
      - [Example:](#example-1)
    - [Constructor and Instance Variables](#constructor-and-instance-variables)
      - [Example:](#example-2)
    - [Inheritance](#inheritance)
      - [Example:](#example-3)
    - [Encapsulation](#encapsulation)
      - [Example:](#example-4)
    - [Polymorphism](#polymorphism)
      - [Example:](#example-5)
    - [Abstract Classes and Interfaces](#abstract-classes-and-interfaces)
      - [Example:](#example-6)
    - [Properties and Decorators](#properties-and-decorators)
      - [Example:](#example-7)
    - [Design Patterns](#design-patterns)
      - [Singleton Pattern](#singleton-pattern)
      - [Factory Pattern](#factory-pattern)
  - [Best Practices](#best-practices)
    - [Code Organization](#code-organization)
    - [Documentation](#documentation)
  - [Implementation Examples](#implementation-examples)
    - [Library Management System](#library-management-system)
    - [Testing Guidelines](#testing-guidelines)
  - [Resources and Contributing](#resources-and-contributing)
    - [Contact](#contact)

---

## Getting Started

### Prerequisites
To follow along with this guide, ensure you have the following:
- Python 3.8 or newer installed on your system.
- Familiarity with basic Python syntax.
- A text editor or integrated development environment (IDE) such as Visual Studio Code or PyCharm.
- The `pip` package manager to install dependencies.

### Setup
Use the commands below to set up the environment:
```bash
# Clone the repository
git clone https://github.com/shahinabdi/python-oop-guide.git

# Create virtual environment
python -m venv venv

# Activate virtual environment
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

---

## Core Concepts

### Introduction to OOP
Object-Oriented Programming organizes code into reusable components called **classes**. Classes define blueprints, and objects are their instances.

#### Example:
```python
class Book:
    def __init__(self, title: str, author: str):
        self.title = title
        self.author = author
    
    def get_info(self) -> str:
        return f"{self.title} by {self.author}"

# Usage
book = Book("Python OOP", "Shahin Abdi")
print(book.get_info())  # Output: Python OOP by Shahin Abdi
```
In this example, the `Book` class defines a template with a `title` and `author`. Each `book` object can represent a specific book.

---

### Classes and Objects
Classes act as templates for objects, encapsulating data and behavior.

#### Example:
```python
class Car:
    def __init__(self, brand: str, model: str, year: int):
        self.brand = brand
        self.model = model
        self.year = year
        self.speed = 0
    
    def accelerate(self, speed_increase: int) -> str:
        self.speed += speed_increase
        return f"Current speed: {self.speed} km/h"
    
    def brake(self, speed_decrease: int) -> str:
        self.speed = max(0, self.speed - speed_decrease)
        return f"Current speed: {self.speed} km/h"

# Usage
my_car = Car("Tesla", "Model 3", 2023)
print(my_car.accelerate(20))  # Output: Current speed: 20 km/h
```
**Explanation:** The `Car` class includes attributes like `brand`, `model`, and methods like `accelerate`. Objects like `my_car` represent individual cars with these features.

---

### Constructor and Instance Variables
Constructors (`__init__`) initialize objects with attributes called instance variables.

#### Example:
```python
class Student:
    def __init__(self, name: str, student_id: str):
        self.name = name  # Instance variable
        self.student_id = student_id  # Instance variable
        self.courses = []  # Default empty list
    
    def enroll(self, course: str) -> str:
        if course not in self.courses:
            self.courses.append(course)
            return f"Enrolled in {course}"
        return f"Already enrolled in {course}"
```
**Explanation:** The `Student` class uses a constructor to initialize `name`, `student_id`, and `courses`.

---

### Inheritance
Inheritance enables a class to derive properties and methods from another class.

#### Example:
```python
class Animal:
    def __init__(self, name: str):
        self.name = name
    
    def speak(self) -> str:
        return "Unknown sound"

class Dog(Animal):
    def speak(self) -> str:
        return "Woof!"

class Cat(Animal):
    def speak(self) -> str:
        return "Meow!"
```
**Explanation:** The `Dog` and `Cat` classes inherit from `Animal`, but override the `speak` method to provide unique behavior.

---

### Encapsulation
Encapsulation hides internal details of an object, exposing only necessary parts.

#### Example:
```python
class BankAccount:
    def __init__(self, owner: str):
        self.__balance = 0  # Private variable
        self.owner = owner
    
    def deposit(self, amount: float):
        if amount > 0:
            self.__balance += amount
    
    def get_balance(self) -> float:
        return self.__balance
```
**Explanation:** The `__balance` variable is private and can only be accessed through methods.

---

### Polymorphism
Polymorphism allows different classes to define the same method differently.

#### Example:
```python
class Shape:
    def area(self) -> float:
        pass

class Rectangle(Shape):
    def __init__(self, width: float, height: float):
        self.width = width
        self.height = height
    
    def area(self) -> float:
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius: float):
        self.radius = radius
    
    def area(self) -> float:
        return 3.14 * self.radius ** 2
```
**Explanation:** Both `Rectangle` and `Circle` implement the `area` method differently.

---

### Abstract Classes and Interfaces
Abstract classes define a template, ensuring subclasses implement required methods.

#### Example:
```python
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def connect(self) -> bool:
        pass

class PostgreSQL(Database):
    def connect(self) -> bool:
        return True
```
---

### Properties and Decorators
Properties control access to attributes.

#### Example:
```python
class Temperature:
    def __init__(self, celsius: float):
        self._celsius = celsius
    
    @property
    def celsius(self) -> float:
        return self._celsius
    
    @celsius.setter
    def celsius(self, value: float):
        if value < -273.15:
            raise ValueError("Below absolute zero!")
        self._celsius = value
```
---

### Design Patterns

#### Singleton Pattern
Restricts a class to a single instance.

#### Factory Pattern
Creates objects without exposing instantiation logic.

---

## Best Practices
### Code Organization
- Use meaningful names.
- Follow the Single Responsibility Principle.

### Documentation
Comment classes and methods thoroughly.

---

## Implementation Examples

### Library Management System
A practical OOP implementation of a library.

### Testing Guidelines
Use tools like `pytest`.

---

## Resources and Contributing

For further learning, refer to resources like [Real Python](https://realpython.com).

### Contact
Connect via [GitHub](https://github.com/shahinabdi).
