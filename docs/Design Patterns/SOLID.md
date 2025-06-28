## S - Single Responsibility Principle (SRP)

A class should have **one and only one reason to change**. Each class should do one thing only.

```python
class Journal:
    def __init__(self):
        self.entries = []
        self.count = 0

    def add_entry(self, text):
        self.entries.append(f"{self.count}: {text}")
        self.count += 1

    def remove_entry(self, pos):
        del self.entries[pos]

    def __str__(self):
        return "\n".join(self.entries)

    # break SRP
    def save(self, filename):
        file = open(filename, "w")
        file.write(str(self))
        file.close()

    def load(self, filename):
        pass

    def load_from_web(self, uri):
        pass


class PersistenceManager:
    def save_to_file(journal, filename):
        file = open(filename, "w")
        file.write(str(journal))
        file.close()


j = Journal()
j.add_entry("I cried today.")
j.add_entry("I ate a bug.")
print(f"Journal entries:\n{j}\n")

p = PersistenceManager()
file = r'c:\temp\journal.txt'
p.save_to_file(j, file)

# verify!
with open(file) as fh:
    print(fh.read())

```



## O - Open/Closed Principle (OCP)

Software entities should be **open for extension, but closed for modification**. New behavior should be added via extension rather than altering existing code.

Benefits:

- Avoids touching stable, tested code
- Reduces the risk of introducing bugs when adding features
- Encourages use of **polymorphism**, **abstraction**, and **inheritance** or **composition**

Problem Example (Violates OCP). Here, every time you add a new shape type, you must modify `AreaCalculator`, violating OCP.

```python
class Shape:
    def __init__(self, type):
        self.type = type

class AreaCalculator:
    def calculate(self, shapes):
        for shape in shapes:
            if shape.type == 'circle':
                # calculate circle area
            elif shape.type == 'square':
                # calculate square area
```

OCP-Compliant Example (Using Polymorphism)

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self): pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2

class Square(Shape):
    def __init__(self, side):
        self.side = side

    def area(self):
        return self.side ** 2

class AreaCalculator:
    def calculate(self, shapes):
        return sum(shape.area() for shape in shapes)

```

When to Apply

- When a module is **stable** but requires **new features**

- When you want to reduce the impact of future changes

- In plugin architectures, rule engines, or strategy-based designs

  ```python
  from enum import Enum
  
  
  class Color(Enum):
      RED = 1
      GREEN = 2
      BLUE = 3
  
  
  class Size(Enum):
      SMALL = 1
      MEDIUM = 2
      LARGE = 3
  
  
  class Product:
      def __init__(self, name, color, size):
          self.name = name
          self.color = color
          self.size = size
  
  
  class ProductFilter:
      def filter_by_color(self, products, color):
          for p in products:
              if p.color == color:
                  yield p
  
      def filter_by_size(self, products, size):
          for p in products:
              if p.size == size:
                  yield p
  
      def filter_by_size_and_color(self, products, size, color):
          for p in products:
              if p.color == color and p.size == size:
                  yield p
  
      # state space explosion
      # 3 criteria
      # c s w cs sw cw csw = 7 methods
  
      # OCP = open for extension, closed for modification
  
  
  class Specification:
      def is_satisfied(self, item):
          pass
  
      # and operator makes life easier
      def __and__(self, other):
          return AndSpecification(self, other)
  
  
  class Filter:
      def filter(self, items, spec):
          pass
  
  
  class ColorSpecification(Specification):
      def __init__(self, color):
          self.color = color
  
      def is_satisfied(self, item):
          return item.color == self.color
  
  
  class SizeSpecification(Specification):
      def __init__(self, size):
          self.size = size
  
      def is_satisfied(self, item):
          return item.size == self.size
  
  
  # class AndSpecification(Specification):
  #     def __init__(self, spec1, spec2):
  #         self.spec2 = spec2
  #         self.spec1 = spec1
  #
  #     def is_satisfied(self, item):
  #         return self.spec1.is_satisfied(item) and \
  #                self.spec2.is_satisfied(item)
  
  
  class AndSpecification(Specification):
      def __init__(self, *args):
          self.args = args
  
      def is_satisfied(self, item):
          return all(map(lambda spec: spec.is_satisfied(item), self.args))
  
  
  class BetterFilter(Filter):
      def filter(self, items, spec):
          for item in items:
              if spec.is_satisfied(item):
                  yield item
  
  
  apple = Product("Apple", Color.GREEN, Size.SMALL)
  tree = Product("Tree", Color.GREEN, Size.LARGE)
  house = Product("House", Color.BLUE, Size.LARGE)
  
  products = [apple, tree, house]
  
  pf = ProductFilter()
  print("Green products (old):")
  for p in pf.filter_by_color(products, Color.GREEN):
      print(f" - {p.name} is green")
  
  # ^ BEFORE
  
  # v AFTER
  bf = BetterFilter()
  
  print("Green products (new):")
  green = ColorSpecification(Color.GREEN)
  for p in bf.filter(products, green):
      print(f" - {p.name} is green")
  
  print("Large products:")
  large = SizeSpecification(Size.LARGE)
  for p in bf.filter(products, large):
      print(f" - {p.name} is large")
  
  print("Large blue items:")
  # large_blue = AndSpecification(large, ColorSpecification(Color.BLUE))
  large_blue = large & ColorSpecification(Color.BLUE)
  for p in bf.filter(products, large_blue):
      print(f" - {p.name} is large and blue")
  
  ```

  

## L - Liskov Substitution Principle (LSP)



## I - Interface Segregation Principle (ISP)

## D - Dependency Inversion Principle (DIP)