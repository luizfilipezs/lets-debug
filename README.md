# lets-debug

[![Build Status](https://img.shields.io/pypi/v/lets-debug.svg)](https://pypi.org/project/lets-debug/)


## Introduction

This package allows you to debug your Python code using terminal tools.

## Installation

`pip install lets-debug`

### Imports

```python
from lets_debug import terminal, DecoratorTools
```

## Reference

### `terminal`

These are the available methods from `terminal`:

#### `log(*args)`

Prints every element passed in `*args` using blue color.

#### `warn(*args)`

Prints every element passed in `*args` using orange color.

#### `error(*args)`

Prints every element passed in `*args` using red color.

#### `success(*args)`

Prints every element passed in `*args` using green color.

#### `clear()`

Clear terminal or command prompt screen.

#### `count(name='counter')`

Counts number of times that `name` was called using this method. It is useful for couting number of times that a function is called. See the example bellow:

```python
def greet():
    terminal.log('Welcome!')
    terminal.count('greet')

greet()
greet()
```

The output will be:

```bash
greet: 1
greet: 2
```

#### `check_bool(boolean: bool, callback: Any)`

Prints `callback` if `boolean` is `False`.

#### `table(dictionary_list: List[Dict])`

Prints `dictionary_list` as table.

### `DecoratorTools`

These are the available methods from `DecoratorTools` class (all methods are static):

#### `log(*args, type='log')`

Prints every element passed in `*args` using custom color. `type` argument defines the color. The available types are `'log'`, `'warn'`, `'error'`, and `'success'`. 

#### `count(*args)`

Counts number of times that a function was called.

#### `stopwatch(*args)`

Counts how long a function takes to run.

#### `override(*args, **kwargs)`

Check if the current method exists in its parent object. See the example bellow:

```python
from lets_debug import DecoratorTools as debug

class Human:

    def walk(self):
        terminal.log('Human is walking...')

class Person(Human):

    @debug.override
    def walk(self):
        terminal.log('Person is walking...')
```

This code is OK. But if you remove `walk()` from `Human` class, an error message will appear in the output.

If you want the program to stop in this situations, set `get_error` option to `True`:

```python
@debug.override(get_error=True)
def walk(self):
```

## Contributions

Feel free to use this package and to contribute on this repository with your ideas!