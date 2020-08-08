# SOLID Design Principle.
S.O.L.I.D stands for the first five Object-oriented design principles. It helps to write effective object-oriented code.
*  Single responsibility principle.
* Open-closed principle.
* Liskov substitution principle.
* Interface segregation principle
* Dependency inversion principle.

## 1. Single responsibility principle.
According to the single-responsibility principle, **a class should have only one responsibility**. If a class has more than one responsibility then it becomes coupled. For example 

```python
class Employee:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def name(self):
        pass

    def edit_age(self):
        pass
```
The above program will make an error because the class have two responsibility.

To solve this problem create an another class and divide the responsibilities like each class is having one responsibility.

```python
#first class
class Employee_name:

    def __init__(self, name):
        self.name = name

    def name(self):
        pass

#second class
class Employee_age:

    def __init__(self, age):
        self.age = age

    def edit_age(self, age):
        pass
```
## 2. Open-closed principle.


