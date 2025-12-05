---
title: Python Basic
date: 2025-12-03 16:08:00 +0800
categories: [Python, Basic]
tags: [notes] # TAG names should always be lowercase
author: zora
description: "Python Learning Notes"
toc: true
comments: false
---

## Data Types
>
> Number, String, Boolean, None, List, Dictionary, Tuple, Set.  
> *Mutable*: List, Dictionary, Set
{: .prompt-info }

1. Number - `int`, `float`, `complex`  

   | Type      | Typical literal         |                                                                                                    Key Traits |
   | :-------- | :---------------------- | ------------------------------------------------------------------------------------------------------------: |
   | `int`     | `42`, `0xFF`            | Whole numbers that can be as large as your memory allows; supports binary `0b`, octal `0o`, hex `0x` literals |
   | `float`   | `3.14`, `1.2e3`         |                                   Numbers with decimal points; may have small rounding errors in calculations |
   | `complex` | `2+3j`, `complex(a, b)` |               Numbers with real and imaginary parts (used in advanced math); `.real`, `.imag`, `.conjugate()` |

2. String - `str`  

   ```python
   # Creating Strings
   name = "Alice"
   message = "Hello World"
   long_text = """This is a
   multi-line string"""

   # Basic Operations
   greeting = "Hello, " + name  # "Hello, Alice"
   repeated = "Ha" * 3          # "HaHaHa"
   length = len(message)        # 11


    # Useful methods
    text = "  Python Programming  "

    clean_text = text.strip()           # "Python Programming"
    words = clean_text.split()          # ["Python", "Programming"]
    joined = "-".join(words)            # "Python-Programming"
    upper_text = clean_text.upper()     # "PYTHON PROGRAMMING"
    replaced = clean_text.replace("Python", "Java")  # "Java Programming"

    # Checking content
    starts_with_p = clean_text.startswith("Python")  # True
    has_gram = "gram" in clean_text                  # True

    # Modern formatting (recommended)
    age = 25
    formatted = f"I am {age} years old"  # "I am 25 years old"
   ```

3. Boolean - `bool` : True, False  

   ```python
   # Simple boolean values
   is_student = True
   is_graduated = False

   # Boolean operations
   has_degree = is_student or is_graduated
   ready_to_work = is_graduated and not is_student


   # Python treats many values as True or False in conditions:
   # These are "truthy" (act like True)
   if "hello":     # non-empty strings
   if [1, 2, 3]:   # non-empty lists
   if 42:          # non-zero numbers

   # These are "falsy" (act like False)
   if "":          # empty string
   if []:          # empty list
   if 0:           # zero
   if None:        # None value
   ```

4. None - `None Type`: nothing or no value
   > always use `is` and `is not` when comparing with `None`, not `==`

5. List - `list`: multiple items in order in a single variable by square bracket

   ```python
   # Creating lists
   fruits = ["apple", "banana", "orange"]
   numbers = [1, 2, 3, 4, 5]
   mixed = ["hello", 42, True, None]  # Lists can hold different types
   empty = []

   # Accessing items (starts at index 0)
   first_fruit = fruits[0]      # "apple"
   last_fruit = fruits[-1]      # "orange"
   

   # Common operations
   shopping_list = ["milk", "bread"]

   # Adding items
   shopping_list.append("eggs")             # ["milk", "bread", "eggs"]
   shopping_list.insert(0, "butter")        # ["butter", "milk", "bread", "eggs"]
   shipping_list.extend(["cheese", "ham"])  # Add multiple items

   # Removing items
   shopping_list.remove("milk")         # Remove first occurrence
   last_item = shopping_list.pop()      # Remove and return last item
   first_item = shopping_list.pop(0)    # Remove and return first item
   
   # Useful operations
   length = len(shopping_list)
   has_bread = "bread" in shopping_list
   ```

6. Dictionary - `dict`: store data as key-value pairs `{key: value pairs}`

   ```python
   # Creating dictionaries
   person = {"name": "Alice", "age": 30, "city": "New York"}
   grades = {"math": 85, "english": 92, "science": 78}
   empty = {}

   # Accessing values
   name = person["name"]        # "Alice"
   age = person.get("age")      # 30 (safer way)
   height = person.get("height", "unknown")  # "unknown" if key doesn't exist
  
   student = {"name": "Bob", "grade": 85}

   # Adding/updating values
   student["age"] = 20           # Add new key-value pair
   student["grade"] = 90         # Update existing value

   # Useful methods
   keys = student.keys()         # dict_keys(['name', 'grade', 'age'])
   values = student.values()     # dict_values(['Bob', 90, 20])
   items = student.items()       # dict_items([('name', 'Bob'), ...])

   # Checking for keys
   if "name" in student:
      print(f"Student name: {student['name']}")

   # Removing items
   age = student.pop("age")      # Remove and return value
   student.pop("height", None)   # Safe removal (no error if key missing)
   ```

7. Tuple - `tuple`: multiple items in a single variable by parantheses `(element 1, element 2)`

   ```python
   # Creating tuples
   coordinates = (10, 20)
   rgb_color = (255, 0, 128)
   single_item = (42,)    # Note the comma for single-item tuples
   empty = ()

   # Parentheses are often optional
   point = 5, 10          # Same as (5, 10)
   name_age = "Alice", 25 # Same as ("Alice", 25)

   # Accessing items (same as lists)
   x = coordinates[0]     # 10
   y = coordinates[1]     # 20

   # Unpacking is very useful
   point = (100, 200)
   x, y = point          # x=100, y=200

   # Swapping values
   a = 5
   b = 10
   a, b = b, a           # Now a=10, b=5

   # Function returning multiple values
   def get_name_age():
      return "Bob", 25

   name, age = get_name_age()

   ```

8. Sets - `set`: store unique items with no duplicates and no particular order. Great for membership testing and removing duplicates.

   ``` python
   # Creating sets
   colors = {"red", "green", "blue"}
   numbers = {1, 2, 3, 4, 5}
   empty = set()  # Note: {} creates an empty dict, not set!

   # From lists (removes duplicates)
   mixed_list = [1, 2, 2, 3, 3, 3]
   unique_numbers = set(mixed_list)  # {1, 2, 3}

   tags = {"python", "programming", "beginner"}

   # Adding items
   tags.add("tutorial")
   tags.update(["coding", "learning"])  # Add multiple items

   # Removing items
   tags.remove("beginner")     # Error if item doesn't exist
   tags.discard("advanced")    # No error if item doesn't exist

   # Membership testing (very fast!)
   if "python" in tags:
      print("This is about Python!")

   # Set operations
   set1 = {1, 2, 3}
   set2 = {3, 4, 5}
   union = set1 | set2         # {1, 2, 3, 4, 5}
   intersection = set1 & set2   # {3}
   difference = set1 - set2     # {1, 2}
   ```

## Control Flow

### if, elif, else Statements

```python
if 1 < 2:
  print("Yep!")

if 1 < 2:
  print('first')
elif: 
  print('last')

if 1 == 2:
  print('first')
elif 3 == 3:
  print('middle')
else:
  print('last')

if True:
  print('always true')
```

### for loop

- A foor loop iterates through each of the items in a collection type, or any other type of object which is "iterable".
  > `for <item> in <collection>`
- if `<collection>` is a **list** or **tuple**, then the loop steps through each element of the sequence
- if `<collection>` is a **string**, then the loop steps through each character of the string
- if `<collection>` is a **dictionary**, then the loop steps through each key of the dictionary
  
#### Loop over a list

```python
seq = [1, 2, 3, 4, 5]

for i in seq:
   print(i, end="")
# 12345

for item in seq:
  print('Yep ', end="")
# Yep Yep Yep Yep Yep

for jelly in seq:
  print(jelly + jelly, end="")
# 246810
```

- To loop through a set of code a specified number of times, we can use the range(start, end, interval) function.
  > range(x) function creates a sequence of numbers from 0 to x-1
  {: .prompt-tip}

  ```python
  my_list = []

  for i in range(10):
    my_list.append(i)

  print(my_list) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

  # specify interval
  my_list_2 = []

  for i in range(1, 10, 2):
    my_list.append(i)

  print(my_list_2) # [1, 3, 5, 7, 9]
  ```
  
#### Loop over nested list

```python
house = [["hallway", 11.25], 
         ["kitchen", 18.0], 
         ["living room", 20.0], 
         ["bedroom", 10.75], 
         ["bathroom", 9.50]]

for a in house:
  print("the {} is {} sqm".format(a[0], a[1]))

# the hallway is 11.25 sqm
# the kitchen is 18.0 sqm
# the living room is 20.0 sqm
# the bedroom is 10.75 sqm
# the bathroom is 9.5 sqm
```

#### Loop over dictionary

```python
europe = {'spain':'madrid', 
          'france':'paris', 
          'germany':'berlin',
          'norway':'oslo', 
          'italy':'rome', 
          'poland':'warsaw', 
          'austria':'vienna' }

europe.items() 
# dict_items([('spain', 'madrid'), ('france', 'paris'), ('germany', 'berlin'), ('norway', 'oslo'), ('italy', 'rome'), ('poland', 'warsaw'), ('austria', 'vienna')])

for key, value in europe.items():
  print("the capital of {} is {}".format(key, value))

# the capital of spain is madrid
# the capital of france is paris
# the capital of germany is berlin
# the capital of norway is oslo
# the capital of italy is rome
# the capital of poland is warsaw
# the capital of austria is vienna
```

## Functions

- Function is a piece of reusable code and solves a particular task
- There are many built-in functions in Python for standard task like `len()`, `print()`, `type()`, `sort()`  

```python
fam = [1.73, 1.68, 1.71, 1.89]

max(fam) # 1.89
```

### Create own function

- `def` creates a function and assigns it a name
- `return` sends a result back to the caller
- *arguments*(参数) are passed by the assignment
- arguments and return types are not declared  
  
```python
def my_fumc(param1='default'):
  print(param1)

my_func('new param')  # new param
my_func()             # default


def square(x):
  return x**2

out = square(2)
print(out) # 4
```

### Inline function

`lambda x: expression`

- **lambda** - indicates the start of a lambda (or anonymous) function
- **x** - represents the input parameter or argument to the labmbda function
- **expression** - represents the operation or calculation that the labmbda function will execute and return  
  
``` python
my_inline_square = lambda x: x**2
my_inline_square(2)  # 4

inline_add = lambda x, y: x + y
inline_add(1, 2)  # 3


cars = ['Ford', 'Mitsubishi', 'BMW', 'VW']

# sort by the length of each element, in descending order
cars.sort(
  reverse = True,
  key = lambda element: len(element)
)

print(cars)  # ['Mitsubishi', 'Ford', 'BMW', 'VW']
```
