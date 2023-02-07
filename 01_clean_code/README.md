# Clean Code

People who write code are often not the same people who maintain it. Trying to understand an unfamiliar codebase to fix a bug in production is already stressful enough, but trying to understand _badly written_ code is even worse.

![Reading bad code can be quite the adventure](../images/67178102e022f9ea214baf9f58f0e44fcdef9a123c64e3abf70cee8ba00bc511.png)  

Code is read more often than it is written, so we should should always our code thinking about the person who will eventually read it - even when that person turns out to be you. Being able to return to previously written code and understand what it does is key, especially in the software development world.

This module focuses on the principles of clean code, and how to apply them to your own code.

## Uncle Bob - Clean code lesson 1 (1:48)

![Uncle Bob - Clean code lesson 1](../images/27c5bc65a8bfeb5ac8d50003f71ca50734341593f7a243670e6c8e34ec4789b3.png)

[Link to video](https://www.youtube.com/watch?v=7EmboKQH8lM)

Robert "Uncle Bob" Martin is one of the icons of the industry and one of the authors of the Agile Manifesto. In this first part of the "Coding Better World Together", he explain what is clean code, why it matters, and establishes the bases to achieve it.

After this lesson you should:

- Understand what clean code is,
- Learn how to start refactoring your current codebase,
- Antipatterns to avoid.

### NOTES:
- Fast coding is coding well
- Smaller codes (small functions)
- Let readers know what a function does clearly and easily (small codes)
- Exctract functions until their maximum (functions on functions on functions) - Question: how small should they be? Should they be in the same file or another file? 2-4 lines of code usually, maybe 6 sometimes?
- Smallness also implies:
  * functiosn should not be large enough to hold nested structures
  * indent level of a function should not be higher than two
- Not many arguments (3-4) - create objects/data structures as arguments
- No boolean arguments. If it is needed for an if/else, separate this into two different functions [Video](https://youtu.be/7EmboKQH8lM?t=4394)
- Use exceptions
- Don't duplicate code

## Uncle Bob - Clean code lesson 2 (1:06)

[Link to video](https://www.youtube.com/watch?v=2a_ytyt9sf8)

In the second part of the "Coding Better World Together", Uncle Bob focuses on the clean code rules for comments and rules to write names.

After this lesson you should:

- Understand what kinds of comments to write,
- Know about _lying comments_ and when _not_ to write comments,
- Be able to reveal your intent while naming things.

### Notes:
- Use comments when the code does not explain itself
- Have a good name for functions instead of having comments
- Warning comments of consequences
- No redundant comments (i.e. explaining simple things that do not need to be explained or are already explained by the code itself)
- Use explanatory code
- Don't check in commented code
- Lines usually 30-40 characters, max max 120
- The name of a variable should tell its significance
- No number series in variables
- Destinguish names clearly
- Reviewing code should take roughly the same time as writing it

## Python Type Checking (Guide) (1:40)

![RealPython cover](../images/4b3cc00ea7b463fb46c2dfbe07beab3d6e708384e6938b82cc3e4f65767da9e2.png)  

[Link to RealPython guide](https://realpython.com/python-type-checking/)

This is a very complete guide on Python type hints from _RealPython_. It's a comprehensive guide that covers a lot of ground and a good piece to keep for future reference.
Type hints are optional in Python, but using them will allow you to catch bugs before they happen, and allow readers to understand your classes and functions just by looking at their signatures.

After this lesson you should:

- Learn how to add type hints to your code,
- Be able to create type aliases,
- Know how to run a static type checker like `mypy`.

### Notes:
* def headline(text: str, align: bool = True) -> str:
  - The text: str syntax says that the text argument should be of type str. Similarly, the optional align argument should have type bool with the default value True. Finally, the -> str notation specifies that headline() will return a string. In terms of style, PEP 8 recommends the following:
    - Use normal rules for colons, that is, no space before and one space after a colon: text: str.
    - Use spaces around the = sign when combining an argument annotation with a default value: align: bool = True.
    - Use spaces around the -> arrow: def headline(...) -> str.
  - Adding type hints like this has no runtime effect: they are only hints and are not enforced on their own. For instance, if we use a wrong type for the (admittedly badly named) align argument, the code still runs without any problems or warnings
 
* A few rules of thumb on whether to add types to your project are:
  - If you are just beginning to learn Python, you can safely wait with type hints until you have more experience.
  - Type hints add little value in short throw-away scripts.
  - In libraries that will be used by others, especially ones published on PyPI, type hints add a lot of value. Other code using your libraries need these type hints to be properly type checked itself. For examples of projects using type hints see cursive_re, black, our own Real Python Reader, and Mypy itself.
  - In bigger projects, type hints help you understand how types flow through your code, and are highly recommended. Even more so in projects where you cooperate with others.
  - In his excellent article The State of Type Hints in Python Bernát Gábor recommends that “type hints should be used whenever unit tests are worth writing.”

* Annotations:
```
>>> nothing: str
>>> nothing
NameError: name 'nothing' is not defined

>>> __annotations__
{'nothing': <class 'str'>}
``` 

* Pyhon types - Part 1:

´´´
>>> from typing import Dict, List, Tuple

>>> names: List[str] = ["Guido", "Jukka", "Ivan"]
>>> version: Tuple[int, int, int] = (3, 7, 1)
>>> options: Dict[str, bool] = {"centered": False, "capitalize": True}
´´´

´´´
def create_deck(shuffle: bool = False) -> List[Tuple[str, str]]:

    """Create a new deck of 52 cards"""

    deck = [(s, r) for r in RANKS for s in SUITS]

    if shuffle:

        random.shuffle(deck)

    return deck
´´´

## 7 Python Code Smells (0:22)

![Arjan Codes YouTube cover](../images/186f8c6d5b3ee296613d84f8b1b5a304ca39034a513d79bcd09688ef91f8b6cb.png)

[Link to video](https://www.youtube.com/watch?v=LrtnLEkOwFE)

This video shows 7 code smells that point to poor design decisions, as well as how to fix them. It's a very practical video, that uses actual Python code and a good way to close this module.

After this lesson you should:

- Have a better idea of things to look out for when reviewing other people' codes. But we will cover more ground in the following modules.
