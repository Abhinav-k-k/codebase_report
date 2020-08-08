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
Software entities(Classes, modules, functions) should be open for extension, not modification. 

Means While developing a new feature doesn't modify the classes, functions. Instead of that extend the entities. For example, Let's imagine you have a shop and you want to give a 40% discount to your favorite customers using this class: When you decide to give a 20% discount to normal customers. You may modify the class like this:
```python
class Discount:

  def __init__(self, customer, price):
      self.customer = customer
      self.price = price

  def give_discount(self):
      if self.customer == 'fav':
          return self.price * 0.4
      if self.customer == 'normal':
          return self.price * 0.2
```
Don't do this, Because it fails the OCP principle. Instead of this make an another class.
```python
class Discount:

    def __init__(self, customer, price):
      self.customer = customer
      self.price = price

    def get_discount(self):
      return self.price * 0.2

class fav_discount(Discount):
    def get_discount(self):
      return super().get_discount() * 2
```
## 3. Liskov substitution principle.
This principle states that every subclass/derived class should acts as a substitute to their base/parent class. 

For Example

A rectangle’s height can be any value and width can be any value.  A square is a rectangle with equal width and height. So we can extend the properties of the rectangle class into square class. In order to do that you need to swap the child (square) class with parent (rectangle) class to fit the definition of a square having four equal sides but a derived class does not affect the behavior of the parent class so if you will do that it will violate the Liskov Substitution Principle.
## 4. Interface segregation principle

A client should not be forced to depend upon interfaces and methods that they do not use.

For example
```python

class IShape:
    def draw(self):
        raise NotImplementedError

class Circle(IShape):
    def draw(self):
        pass

class Square(IShape):
    def draw(self):
        pass

class Rectangle(IShape):
    def draw(self):
        pass
```
A single class can implement several interfaces if needed. So we can provide a single implementation for all the common methodes between the interfaces. The segregated interfaces will also force us to think of our code more from the client’s point of view.

## 5. Dependency inversion principle.

Depend on Abstractions not on concretions.

That means,
1. High-level modules should not depend upon low-level modules. Both should depend upon abstractions.
2. Abstractions should not depend on details. Details should depend upon abstractions.

when our app will be largely composed of modules, we have to clear things up by using dependency injection. High-level components depending on low-level components to function. To create specific behavior you can use techniques like inheritance or interfaces.
