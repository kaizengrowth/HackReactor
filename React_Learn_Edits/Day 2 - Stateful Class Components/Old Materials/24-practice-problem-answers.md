---
Type: Instructor
UID: 158c0362-9b0f-42b3-9e27-59f4b05c34d2
---

# Solutions

Solutions for today's practice problems

All of today's problems solve the same problem:

Given an array/list of strings, return a new list which
contains the upper-cased version of each string in the
input list.

For example, given this input:

```python
input = [
    "arrays in JavaScript, lists in Python",
    "objects in JavaScript, dictionaries in Python"
]
```

all of the practice problems should produce:

```python
output = [
    'ARRAYS IN JAVASCRIPT, LISTS IN PYTHON',
    'OBJECTS IN JAVASCRIPT, DICTIONARIES IN PYTHON'
]
```

## Problem 1 : Python for-in loop

```py
def uppercase_all(strings):
    result = []
    for string in strings:
        result.append(string.upper())
    return result
```

## Problem 2 : Python list comprehension

```python
def uppercase_all2(strings):
    return [string.upper() for string in strings]
```

## Problem 3 : JavaScript for-of loop

```javascript
const uppercaseAll = function (strings) {
    const result = [];
    for(const string of strings) {
        result.push(string.toUpperCase());
    }
    return result;
}
```

## Problem 4 : JavaScript map function

```javascript
const uppercaseAll2 = function (strings) {
    return strings.map(string => string.toUpperCase());
}

const uppercaseAll2 = strings => strings.map(string => string.toUpperCase();
```
