---
Type: Checkpoint
UID: 71f23181-650c-4581-8ac3-0e3d6684a855
DefaultVisibility: hidden
TimeLimit: 30
Autoscore: true
---

# Practice Problems
<!-- markdownlint-disable MD013 -->

All of today's problems solve the same problem:

Given an array/list of strings, return a new list that
contains the uppercase version of each string in the
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

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
### !challenge

* type: code-snippet
* language: python3.6
* id: 7df7b148-435d-472a-9be3-b94532ecae12
* title: Python, `for ... in`

##### !question

Implement the function `uppercase_all(strings)` in Python
using a `for ... in` loop.

##### !end-question

##### !placeholder

```py
def uppercase_all(strings):
    result = []

    # your for...in loop here

    return result
```

##### !end-placeholder

##### !tests

```py
import unittest
from main import uppercase_all

class TestPython1(unittest.TestCase):
    def test_one(self):
        expected = ['SEMICOLONS IN JAVASCRIPT, NOT IN PYTHON', 'SNAKES']
        actual = uppercase_all(["semicolons in javascript, not in python", "snakes"])
        self.assertEqual(expected, actual)
```

##### !end-tests

##### !explanation-incorrect:

```py
def uppercase_all(strings):
    result = []
    for string in strings:
        result.append(string.upper())
    return result
```

##### !end-explanation

##### !explanation-correct:

```py
def uppercase_all(strings):
    result = []
    for string in strings:
        result.append(string.upper())
    return result
```

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->
<!-- ---------------------------------------------------------------------- -->
<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->

### !challenge

* type: code-snippet
* language: python3.6
* id: 0536bfbb-c7dd-4498-82d0-262b770d97ea
* title: Python list comprehension

##### !question

Implement the function `uppercase_all(strings)` in Python,
but this time use a list comprehension to do it.

Recall that a list comprehension is shorthand way to do common
list operations. In the following code, the loop at the top and
the list comprehension at the bottom perform the same task:

```python
# loop
result = []
for number in numbers:
    result.append(number * number)

# list comprehension
result = [number * number for number in numbers]

```

##### !end-question

##### !placeholder

```python
def uppercase_all2(strings):
    # return [... for ... in ...]
```

##### !end-placeholder

##### !tests

```py
import unittest
from main import uppercase_all2

class TestPython2(unittest.TestCase):
    def test_two(self):
        expected = ['SEMICOLONS IN JAVASCRIPT, NOT IN PYTHON', 'SNAKES']
        actual = uppercase_all2(["semicolons in javascript, not in python", "snakes"])
        self.assertEqual(expected, actual)
```

##### !end-tests

##### !explanation-incorrect:

```python
def uppercase_all2(strings):
    return [string.upper() for string in strings]
```

##### !end-explanation

##### !explanation-correct:

```python
def uppercase_all2(strings):
    return [string.upper() for string in strings]
```

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->
<!-- ---------------------------------------------------------------------- -->
<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->

### !challenge

* type: code-snippet
* language: javascript
* id: c6623814-5b37-4858-9254-efffd3e154ac
* title: JavaScript `for ... of`

##### !question

Implement the function `uppercaseAll(strings)` in JavaScript
using a `for ... of` loop.

##### !end-question

##### !placeholder

```javascript
const uppercaseAll = function (strings) {
    const result = [];

    // your for...of loop here

    return result;
}
```

##### !end-placeholder

##### !tests

```javascript
describe('uppercaseAll', function() {
    it("does what it is supposed to do", function() {
        const expected = ['SEMICOLONS IN JAVASCRIPT, NOT IN PYTHON', 'SNAKES']
        const actual = uppercaseAll(["semicolons in javascript, not in python", "snakes"])
        expect(actual, "Error message").to.deep.eq(expected)
    });
});
```

##### !end-tests

##### !explanation-incorrect:

```javascript
const uppercaseAll = function (strings) {
    const result = [];
    for(const string of strings) {
        result.push(string.toUpperCase());
    }
    return result;
}
```

##### !end-explanation

##### !explanation-correct:

```javascript
const uppercaseAll = function (strings) {
    const result = [];
    for(const string of strings) {
        result.push(string.toUpperCase());
    }
    return result;
}
```

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->
<!-- ---------------------------------------------------------------------- -->
<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->

### !challenge

* type: code-snippet
* language: javascript
* id: f0c259a8-4316-46ff-92ae-c6092df564b6
* title: JavaScript with `map`

##### !question

JavaScript doesn't have comprehensions like Python, but like many
other languages, it has a `map` function that serves a similar purpose,
which is to create a new list that has one item for each item in
the input list.

Below is the "square" example from problem 2, but in JavaScript
using the `map` function:

```javascript
// with for loop
const result = [];
for(const number of numbers) {
    result.push(number * number);
}

// with the map function
const result = numbers.map(function(number) {
    return number * number;
});

// with the map function and arrow-function notation
const result = numbers.map(number => number * number);
```

Implement the function `uppercaseAll(strings)` in javascript
using the `map` function.

##### !end-question

##### !placeholder

```javascript
const uppercaseAll2 = function (strings) {
    // use map
}
```

##### !end-placeholder

##### !tests

```javascript
describe('uppercaseAll2', function() {
    it("does what it is supposed to do", function() {
        const expected = ['SEMICOLONS IN JAVASCRIPT, NOT IN PYTHON', 'SNAKES']
        const actual = uppercaseAll2(["semicolons in javascript, not in python", "snakes"])
        expect(actual, "Error message").to.deep.eq(expected)
    });
});
```

##### !end-tests

##### !explanation-incorrect:

```javascript
const uppercaseAll2 = function (strings) {
    return strings.map(string => string.toUpperCase());
}

const uppercaseAll2 = strings => strings.map(string => string.toUpperCase();
```

##### !end-explanation

##### !explanation-correct:

```javascript
const uppercaseAll2 = function (strings) {
    return strings.map(string => string.toUpperCase());
}

// or, more succinctly ...

const uppercaseAll2 = strings => strings.map(string => string.toUpperCase();
```

##### !end-explanation

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->
