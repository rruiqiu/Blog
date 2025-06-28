## Chain of Responsibility


The Chain of Responsibility pattern allows multiple objects the chance to handle a request without the sender needing to know which one will handle it. The request is passed along a chain until an object handles it or the chain ends.

### Motivation

In real-world scenarios, responsibilities often flow up a hierarchy. For example, in a company, if an employee behaves unethically, the blame may fall on the employee, their manager, or even the CEO—depending on the severity and source of the behavior. This layered delegation is an example of a **chain of responsibility**.

Similarly, in UI applications, when a user clicks a button, the button may handle the event. If it doesn’t, the event bubbles up to the parent component (like a group box), and then possibly to the window itself. Each element in the hierarchy gets a chance to handle the event.

Another example is a card game where a creature’s stats (like attack and defense) can be modified by multiple other cards. Each modifier can be seen as a handler in the chain that alters the request.

In all these cases, the idea is to:

- Pass a request through a chain of handlers
- Let each handler decide to process or forward it
- Allow optional early termination of the chain

This pattern is ideal for building flexible, decoupled systems where multiple parties might act on a single input.

### Method Chain

```python
class Creature:
    def __init__(self, name, attack, defense):
        self.defense = defense
        self.attack = attack
        self.name = name

    def __str__(self):
        return f'{self.name} ({self.attack}/{self.defense})'


class CreatureModifier:
    def __init__(self, creature):
        self.creature = creature
        self.next_modifier = None

    def add_modifier(self, modifier):
        if self.next_modifier:
            self.next_modifier.add_modifier(modifier)
        else:
            self.next_modifier = modifier

    def handle(self):
        if self.next_modifier:
            self.next_modifier.handle()


class NoBonusesModifier(CreatureModifier):
    def handle(self):
        print('No bonuses for you!')


class DoubleAttackModifier(CreatureModifier):
    def handle(self): # in Python, if no init called, the init will get inherited automatically
        print(f'Doubling {self.creature.name}''s attack')
        self.creature.attack *= 2
        super().handle()


class IncreaseDefenseModifier(CreatureModifier):
    def handle(self):
        if self.creature.attack <= 2:
            print(f'Increasing {self.creature.name}''s defense')
            self.creature.defense += 1
        super().handle()


if __name__ == '__main__':
    goblin = Creature('Goblin', 1, 1)
    print(goblin)

    root = CreatureModifier(goblin)

    root.add_modifier(NoBonusesModifier(goblin))

    root.add_modifier(DoubleAttackModifier(goblin))
    root.add_modifier(DoubleAttackModifier(goblin))

    # no effect
    root.add_modifier(IncreaseDefenseModifier(goblin))

    root.handle()  # apply modifiers
    print(goblin)
```

### Command Query Separation

- **Command** = asking for an action or change (e.g., please set your attack value to 2).
- **Query** = asking for information (e.g., please give me your attack value).
- **CQS** = having separate means of sending commands and queries to e.g., direct field access.

### Broker Chain

```python
# 1) event broker
# 2) command-query separation (cqs)
# 3) observer
from abc import ABC
from enum import Enum


class Event(list):
    def __call__(self, *args, **kwargs):
        for item in self:
            item(*args, **kwargs)


class WhatToQuery(Enum):
    ATTACK = 1
    DEFENSE = 2


class Query:
    def __init__(self, creature_name, what_to_query, default_value):
        self.value = default_value  # bidirectional
        self.what_to_query = what_to_query
        self.creature_name = creature_name


class Game:
    def __init__(self):
        self.queries = Event()

    def perform_query(self, sender, query):
        self.queries(sender, query)


class Creature:
    def __init__(self, game, name, attack, defense):
        self.initial_defense = defense
        self.initial_attack = attack
        self.name = name
        self.game = game

    @property
    def attack(self):
        q = Query(self.name, WhatToQuery.ATTACK, self.initial_attack)
        self.game.perform_query(self, q)
        return q.value

    @property
    def defense(self):
        q = Query(self.name, WhatToQuery.DEFENSE, self.initial_attack)
        self.game.perform_query(self, q)
        return q.value

    def __str__(self):
        return f'{self.name} ({self.attack}/{self.defense})'


class CreatureModifier(ABC):
    def __init__(self, game, creature):
        self.creature = creature
        self.game = game
        self.game.queries.append(self.handle)

    def handle(self, sender, query):
        pass

    def __enter__(self):
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.game.queries.remove(self.handle)


class DoubleAttackModifier(CreatureModifier):
    def handle(self, sender, query):
        if (sender.name == self.creature.name and
                query.what_to_query == WhatToQuery.ATTACK):
            query.value *= 2


class IncreaseDefenseModifier(CreatureModifier):
    def handle(self, sender, query):
        if (sender.name == self.creature.name and
                query.what_to_query == WhatToQuery.DEFENSE):
            query.value += 3


if __name__ == '__main__':
    game = Game()
    goblin = Creature(game, 'Strong Goblin', 2, 2)
    print(goblin)

    with DoubleAttackModifier(game, goblin):
        print(goblin)
        with IncreaseDefenseModifier(game, goblin):
            print(goblin)

    print(goblin)

```

### Exercise

```python
import unittest
from abc import ABC
from enum import Enum

# creature removal (unsubscription) ignored in this exercise solution

class Creature(ABC):
    def __init__(self, game, attack, defense):
        self.initial_defense = defense
        self.initial_attack = attack
        self.game = game

    @property
    def attack(self): pass

    @property
    def defense(self): pass

    def query(self, source, query): pass


class WhatToQuery(Enum):
    ATTACK = 1
    DEFENSE = 2


class Goblin(Creature):

    def __init__(self, game, attack=1, defense=1):
        super().__init__(game, attack, defense)

    @property
    def attack(self):
        q = Query(self.initial_attack, WhatToQuery.ATTACK)
        for c in self.game.creatures:
            c.query(self, q)
        return q.value

    @property
    def defense(self):
        q = Query(self.initial_defense, WhatToQuery.DEFENSE)
        for c in self.game.creatures:
            c.query(self, q)
        return q.value

    def query(self, source, query):
        if self != source and query.what_to_query == WhatToQuery.DEFENSE:
            query.value += 1


class GoblinKing(Goblin):

    def __init__(self, game):
        super().__init__(game, 3, 3)

    def query(self, source, query):
        if self != source and query.what_to_query == WhatToQuery.ATTACK:
            query.value += 1
        else:
            super().query(source, query)


class Query:
    def __init__(self, initial_value, what_to_query):
        self.what_to_query = what_to_query
        self.value = initial_value

class Game:
    def __init__(self):
        self.creatures = []


class FirstTestSuite(unittest.TestCase):
    def test(self):
        game = Game()
        goblin = Goblin(game)
        game.creatures.append(goblin)

        self.assertEqual(1, goblin.attack)
        self.assertEqual(1, goblin.defense)

        goblin2 = Goblin(game)
        game.creatures.append(goblin2)

        self.assertEqual(1, goblin.attack)
        self.assertEqual(2, goblin.defense)

        goblin3 = GoblinKing(game)
        game.creatures.append(goblin3)

        self.assertEqual(2, goblin.attack)
        self.assertEqual(3, goblin.defense)
```

### Summary

The **Chain of Responsibility** pattern enables a sequence of handlers to process a request. Each handler in the chain can choose to act on the request, pass it along, or halt further processing entirely.

There are two common implementations:

- A **linked chain of handlers**, where each object holds a reference to the next
- A **centralized dispatcher** (e.g., event broker) that maintains a list of handlers and invokes them in order

Key characteristics:

- Handlers are organized into a **chain**, and the request flows through them sequentially
- Each handler can **modify**, **act on**, or **terminate** the flow
- Handler order can be managed explicitly to establish priority
- Handlers can be dynamically **added**, **removed**, or **self-unregistered**

This pattern promotes flexibility and decoupling by allowing multiple objects the opportunity to handle a request without tightly coupling the sender to any specific receiver.