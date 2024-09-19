# Python String Formatting Cheat Sheet Using `{}`

Python offers several ways to format strings using curly braces `{}`. The two primary methods are the `.format()` function and **f-strings** (formatted string literals). This cheat sheet covers both methods, including various formatting options.

---

## Table of Contents

1. [Basic Formatting with `.format()`](#1-basic-formatting-with-format)
2. [Formatting with F-Strings (Python 3.6+)](#2-formatting-with-f-strings-python-36)
3. [Number Formatting](#3-number-formatting)
    - [Decimal Places](#a-decimal-places)
    - [Thousand Separators](#b-thousand-separators)
    - [Percentage](#c-percentage)
4. [Alignment and Padding](#4-alignment-and-padding)
    - [Align Text](#a-align-text)
    - [Padding with Characters](#b-padding-with-characters)
5. [Number Bases](#5-number-bases)
    - [Binary, Octal, Hexadecimal](#a-binary-octal-hexadecimal)
    - [Adding Prefixes](#b-adding-prefixes)
6. [Sign Formatting](#6-sign-formatting)
7. [String Truncation and Precision](#7-string-truncation-and-precision)
8. [Combining Multiple Format Specifications](#8-combining-multiple-format-specifications)
9. [Date and Time Formatting](#9-date-and-time-formatting)
10. [Escaping Braces](#10-escaping-braces)
11. [Accessing Attributes and Items](#11-accessing-attributes-and-items)
    - [Attributes](#a-attributes)
    - [Dictionary Items](#b-dictionary-items)
12. [Nested Formatting](#12-nested-formatting)
13. [Custom Object Formatting](#13-custom-object-formatting)
14. [Locale-Aware Formatting](#14-locale-aware-formatting)
15. [Formatting Class Instances with `__str__` and `__repr__`](#15-formatting-class-instances-with-__str__-and-__repr__)
16. [Summary of Format Specifiers](#16-summary-of-format-specifiers)

---

## 1. Basic Formatting with `.format()`

```python
# Using positional arguments
print("Hello, {}!".format("Alice"))
# Output: Hello, Alice!

# Using indexed positional arguments
print("Hello, {0}! You are {1} years old.".format("Bob", 30))
# Output: Hello, Bob! You are 30 years old.

# Using keyword arguments
print("Hello, {name}! You are {age} years old.".format(name="Charlie", age=25))
# Output: Hello, Charlie! You are 25 years old.
```

---

## 2. Formatting with F-Strings (Python 3.6+)

```python
name = "Diana"
age = 28
print(f"Hello, {name}! You are {age} years old.")
# Output: Hello, Diana! You are 28 years old.
```

---

## 3. Number Formatting

### a. Decimal Places

```python
number = 3.14159
print("Pi is approximately {:.2f}".format(number))
# Output: Pi is approximately 3.14

# Using f-strings
print(f"Pi is approximately {number:.2f}")
# Output: Pi is approximately 3.14
```

### b. Thousand Separators

```python
number = 1234567.89
print("Number: {:,}".format(number))
# Output: Number: 1,234,567.89

# Using f-strings
print(f"Number: {number:,}")
# Output: Number: 1,234,567.89
```

### c. Percentage

```python
ratio = 0.75
print("Completion: {:.0%}".format(ratio))
# Output: Completion: 75%

# Using f-strings
print(f"Completion: {ratio:.0%}")
# Output: Completion: 75%
```

---

## 4. Alignment and Padding

### a. Align Text

```python
text = "Align me"
print("|{:<10}|{:^10}|{:>10}|".format(text, text, text))
# Output: |Align me  |  Align me |  Align me|

# Using f-strings
print(f"|{text:<10}|{text:^10}|{text:>10}|")
# Output: |Align me  |  Align me |  Align me|
```

- `<` : Left-align
- `^` : Center-align
- `>` : Right-align

### b. Padding with Characters

```python
number = 42
print("{:0>5}".format(number))
# Output: 00042

# Using f-strings
print(f"{number:0>5}")
# Output: 00042
```

---

## 5. Number Bases

### a. Binary, Octal, Hexadecimal

```python
number = 255
print("Binary: {0:b}, Octal: {0:o}, Hex: {0:x}".format(number))
# Output: Binary: 11111111, Octal: 377, Hex: ff

# Using f-strings
print(f"Binary: {number:b}, Octal: {number:o}, Hex: {number:x}")
# Output: Binary: 11111111, Octal: 377, Hex: ff
```

### b. Adding Prefixes

```python
print("Hex with prefix: {0:#x}".format(number))
# Output: Hex with prefix: 0xff

# Using f-strings
print(f"Hex with prefix: {number:#x}")
# Output: Hex with prefix: 0xff
```

---

## 6. Sign Formatting

```python
positive = 42
negative = -42

print("{:+}".format(positive))
# Output: +42

print("{:+}".format(negative))
# Output: -42

# Using f-strings
print(f"{positive:+}")
# Output: +42

print(f"{negative:+}")
# Output: -42
```

- `'+'` : Use a plus sign for positive numbers and a minus sign for negative numbers.
- `'-'` : Use only a minus sign for negative numbers (default behavior).
- `' '` : Use a leading space for positive numbers and a minus sign for negative numbers.

---

## 7. String Truncation and Precision

```python
text = "Hello, World!"
print("{:.5}".format(text))
# Output: Hello

# Using f-strings
print(f"{text:.5}")
# Output: Hello
```

---

## 8. Combining Multiple Format Specifications

```python
number = 1234.56789
print("{:*>10.2f}".format(number))
# Output: ****1234.57

# Using f-strings
print(f"{number:*>10.2f}")
# Output: ****1234.57
```

---

## 9. Date and Time Formatting

For date and time objects, you can use the `datetime` module with formatting codes.

```python
from datetime import datetime

now = datetime.now()
print("{:%Y-%m-%d %H:%M:%S}".format(now))
# Output: e.g., 2023-09-18 15:30:45

# Using f-strings
print(f"{now:%Y-%m-%d %H:%M:%S}")
# Output: e.g., 2023-09-18 15:30:45
```

---

## 10. Escaping Braces

To include literal curly braces `{}` in your string, double them:

```python
print("Use {{}} to escape braces in {}.".format("format strings"))
# Output: Use {} to escape braces in format strings.

# Using f-strings
print(f"Use {{}} to escape braces in f-strings.")
# Output: Use {} to escape braces in f-strings.
```

---

## 11. Accessing Attributes and Items

### a. Attributes

```python
class Person:
    def __init__(self, name):
        self.name = name

p = Person("Eve")
print("Name: {0.name}".format(p))
# Output: Name: Eve

# Using f-strings
print(f"Name: {p.name}")
# Output: Name: Eve
```

### b. Dictionary Items

```python
data = {'key': 'value'}
print("Value: {0[key]}".format(data))
# Output: Value: value

# Using f-strings
print(f"Value: {data['key']}")
# Output: Value: value
```

---

## 12. Nested Formatting

```python
for i in range(5):
    print("{:{width}}".format(i, width=i+1))

# Output:
# 0
#  1
#   2
#    3
#     4
```

---

## 13. Custom Object Formatting

You can define how your custom objects are formatted by implementing the `__format__` method.

```python
class Currency:
    def __init__(self, amount):
        self.amount = amount

    def __format__(self, format_spec):
        return "${:,.2f}".format(self.amount)

price = Currency(1234.5)
print("Price: {}".format(price))
# Output: Price: $1,234.50

# Using f-strings
print(f"Price: {price}")
# Output: Price: $1,234.50
```

---

## 14. Locale-Aware Formatting

For locale-aware formatting (e.g., using commas or periods according to locale), use the `locale` module.

```python
import locale
locale.setlocale(locale.LC_ALL, '')  # Set to user's default locale

number = 1234567.89
print("{:n}".format(number))
# Output may vary based on locale, e.g., 1,234,567.89

# Using f-strings
print(f"{number:n}")
# Output may vary based on locale
```

---

## 15. Formatting Class Instances with `__str__` and `__repr__`

```python
class Person:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"Person named {self.name}"

    def __repr__(self):
        return f"Person('{self.name}')"

p = Person("Frank")

print("Using str: {}".format(p))
# Output: Using str: Person named Frank

print("Using repr: {!r}".format(p))
# Output: Using repr: Person('Frank')

# Using f-strings
print(f"Using str: {p}")
# Output: Using str: Person named Frank

print(f"Using repr: {p!r}")
# Output: Using repr: Person('Frank')
```

- `{}` or `{:s}` calls `str()` on the object.
- `{!r}` or `{:r}` calls `repr()` on the object.

---

## 16. Summary of Format Specifiers

Format: `{field_name: [fill][align][sign][#][0][width][,][.precision][type]}`

- **fill** : Any character (default is space)
- **align** :
  - `<` : Left-align
  - `^` : Center-align
  - `>` : Right-align
  - `=` : Forces the padding to be placed after the sign (numeric types only)
- **sign** :
  - `+` : Use a plus sign for positive numbers
  - `-` : Use a minus sign only for negative numbers (default)
  - `' '` : Use a space for positive numbers
- `#` : Use alternate form (e.g., `0b` for binary, `0x` for hex)
- `0` : Pad with zeros
- **width** : Minimum field width
- `,` : Use comma as thousand separator
- **.precision** : For floating-point numbers, number of digits after the decimal point
- **type** :
  - `d` : Decimal integer
  - `b` : Binary
  - `o` : Octal
  - `x` : Hexadecimal (lowercase)
  - `X` : Hexadecimal (uppercase)
  - `e` : Exponential notation (lowercase)
  - `E` : Exponential notation (uppercase)
  - `f` : Fixed-point
  - `F` : Fixed-point (uppercase)
  - `g` : General format
  - `G` : General format (uppercase)
  - `n` : Number (uses current locale)
  - `%` : Percentage (multiplies by 100 and adds '%')

---

By mastering these formatting options, you can display strings and numbers in a wide variety of ways to suit your needs.

