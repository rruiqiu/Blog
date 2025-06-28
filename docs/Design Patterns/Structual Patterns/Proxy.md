## Proxy

The Proxy pattern provides a placeholder or surrogate for another object to control access to it. It allows additional behavior (e.g., access control, logging, or lazy loading) while keeping the client interface unchanged.

### Motivation

In distributed or modular systems, an object like `Foo` may be relocated to a different process or environment over time. Instead of rewriting all code that interacts with `Foo`, a **proxy** class can maintain the same interface while handling the new complexity (e.g., inter-process communication, remote calls).

A **proxy **Structure:

- Implements the same interface as the target object.
- Delegates requests to the real object (optionally adding behavior before or after the call).

Common Use Cases

- **Remote Proxy (Communication Proxy)**: Manages communication with an object in a different address space or process.
- **Virtual Proxy**: Delays the creation of an expensive object until it’s needed.
- **Logging Proxy**: Logs method calls and arguments.
- **Protection (Guard) Proxy**: Controls access based on authorization.

### Protection Proxy

Use for access control.

```python
class Car:
    def __init__(self, driver):
        self.driver = driver

    def drive(self):
        print(f'Car being driven by {self.driver.name}')

class CarProxy:
    def __init__(self, driver):
        self.driver = driver
        self.car = Car(driver)

    def drive(self):
        if self.driver.age >= 16:
            self.car.drive()
        else:
            print('Driver too young')


class Driver:
    def __init__(self, name, age):
        self.name = name
        self.age = age


if __name__ == '__main__':
    car = CarProxy(Driver('John', 12))
    car.drive()
```

### Virtual Proxy

The issue is if we initiate the Bitmap object but not drawing the image, it will call the init function which will load image from filename. And also by adding the virtual proxy, it ensures the real object is constructed only on first use, making systems more efficient without changing the public interface.

```python
class Bitmap:
    def __init__(self, filename):
        self.filename = filename
        print(f'Loading image from {filename}')

    def draw(self):
        print(f'Drawing image {self.filename}')


class LazyBitmap:
    def __init__(self, filename):
        self.filename = filename
        self.bitmap = None

    def draw(self):
        if not self.bitmap:
            self.bitmap = Bitmap(self.filename)
        self.bitmap.draw()

def draw_image(image):
    print('About to draw image')
    image.draw()
    print('Done drawing image')

if __name__ == '__main__':
    bmp = LazyBitmap('facepalm.jpg')  # Bitmap
    draw_image(bmp)

```

### Proxy vs Decorator

Both Proxy and Decorator patterns involve an object wrapping another, but they serve different design goals. Below is a structured comparison to clarify their purposes and behaviors.

- **Proxy**: Controls access to an object. It may:
  - Delay creation (lazy loading)
  - Add logging, security checks, or communication boundaries
  - Operate **before the real object exists**
- **Decorator**: Adds functionality **around** an existing object. It enhances behavior without altering the object's core structure.

Think of **Proxy** as a *transparent stand-in* that may control object creation, and **Decorator** as a *behavior enhancer* that wraps and extends functionality.

### Exercise

```python
from unittest import TestCase


class Person:
  def __init__(self, age):
    self.age = age

  def drink(self):
    return 'drinking'

  def drive(self):
    return 'driving'

  def drink_and_drive(self):
    return 'driving while drunk'

class ResponsiblePerson:
  def __init__(self, person):
    self.person = person

  @property
  def age(self):
    return self.person.age

  @age.setter
  def age(self, value):
    self.person.age = value

  def drink(self):
    if self.age >= 18:
      return self.person.drink()
    return 'too young'

  def drive(self):
    if self.age >= 16:
      return self.person.drive()
    return 'too young'

  def drink_and_drive(self):
    return 'dead'

class Evaluate(TestCase):
  def test_exercise(self):
    p = Person(10)
    rp = ResponsiblePerson(p)

    self.assertEqual('too young', rp.drive())
    self.assertEqual('too young', rp.drink())
    self.assertEqual('dead', rp.drink_and_drive())

    rp.age = 20

    self.assertEqual('driving', rp.drive())
    self.assertEqual('drinking', rp.drink())
    self.assertEqual('dead', rp.drink_and_drive())
```

### Summary

The **Proxy Pattern** is a structural design pattern that acts as a stand-in or interface to control access to another object. It maintains the same interface as the original object, allowing clients to interact with the proxy transparently while adding additional behavior like access control, logging, or lazy instantiation.

Key proxy types include:

- **Virtual Proxy** – Delays expensive object creation until first use.
- **Protection Proxy** – Restricts access based on permissions or conditions.
- **Remote Proxy** – Handles interaction across different processes or machines.
- **Logging Proxy** – Adds logging or auditing behavior around method calls.

Proxy is often compared to the **Decorator Pattern**, but unlike decorators, proxies are used to **control access** or **defer operations**, not just enhance behavior. Decorators always work with an existing object, whereas proxies may create or represent an object lazily.

Use the Proxy pattern when:

- The real object is expensive or unnecessary to initialize upfront
- Access to the object needs to be controlled or monitored
- Remote access or security checks are involved