# Python Variable Annotations

## Resources
To get the most out of this project, please review the following resources:

- [Python 3 typing documentation](https://docs.python.org/3/library/typing.html)
- [MyPy cheat sheet](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)

## Learning Objectives
By the end of this project, you will be able to:

- Explain type annotations in Python 3.
- Use type annotations to specify function signatures and variable types.
- Understand duck typing.
- Validate your code with `mypy`.

## Requirements

- **Editors**: `vi`, `vim`, `emacs`
- **OS**: Ubuntu 18.04 LTS
- **Python version**: Python 3.7
- **Code Style**: `pycodestyle` version 2.5
- **File Requirements**:
  - All files must end with a new line.
  - The first line of all files should be `#!/usr/bin/env python3`.
  - Files must be executable.
  - Files should pass `wc` length tests.
  - Modules, classes, and functions should have documentation.

## Project Tasks

### 0. Basic Annotations - `add`
Create a type-annotated function `add` that takes two floats and returns their sum.

**File**: `0-add.py`

```python
def add(a: float, b: float) -> float:
    """Add two floats and return the result."""
    return a + b
```

### 1. Basic Annotations - `concat`
Create a type-annotated function `concat` that takes two strings and returns their concatenation.

**File**: `1-concat.py`

```python
def concat(str1: str, str2: str) -> str:
    """Concatenate two strings."""
    return str1 + str2
```

### 2. Basic Annotations - `floor`
Create a type-annotated function `floor` that takes a float and returns its floor as an integer.

**File**: `2-floor.py`

```python
import math

def floor(n: float) -> int:
    """Return the floor of a float."""
    return math.floor(n)
```

### 3. Basic Annotations - `to_str`
Create a type-annotated function `to_str` that takes a float and returns its string representation.

**File**: `3-to_str.py`

```python
def to_str(n: float) -> str:
    """Convert a float to its string representation."""
    return str(n)
```

### 4. Define Variables
Define and annotate the following variables:

- `a`: integer, value 1
- `pi`: float, value 3.14
- `i_understand_annotations`: boolean, value True
- `school`: string, value "Holberton"

**File**: `4-define_variables.py`

```python
a: int = 1
pi: float = 3.14
i_understand_annotations: bool = True
school: str = "Holberton"
```

### 5. Complex Types - List of Floats
Create a type-annotated function `sum_list` that takes a list of floats and returns their sum.

**File**: `5-sum_list.py`

```python
from typing import List

def sum_list(input_list: List[float]) -> float:
    """Sum a list of floats and return the result."""
    return sum(input_list)
```

### 6. Complex Types - Mixed List
Create a type-annotated function `sum_mixed_list` that takes a list of integers and floats, and returns their sum as a float.

**File**: `6-sum_mixed_list.py`

```python
from typing import List, Union

def sum_mixed_list(mxd_lst: List[Union[int, float]]) -> float:
    """Sum a list of integers and floats and return the result as a float."""
    return sum(mxd_lst)
```

### 7. Complex Types - String and Int/Float to Tuple
Create a type-annotated function `to_kv` that takes a string and an int/float, and returns a tuple with the string and the square of the int/float.

**File**: `7-to_kv.py`

```python
from typing import Union, Tuple

def to_kv(k: str, v: Union[int, float]) -> Tuple[str, float]:
    """Return a tuple with a string and the square of an int/float."""
    return (k, float(v ** 2))
```

### 8. Complex Types - Functions
Create a type-annotated function `make_multiplier` that takes a float multiplier and returns a function that multiplies a float by the multiplier.

**File**: `8-make_multiplier.py`

```python
from typing import Callable

def make_multiplier(multiplier: float) -> Callable[[float], float]:
    """Return a function that multiplies a float by a given multiplier."""
    def multiply(n: float) -> float:
        return n * multiplier
    return multiply
```

### 9. Duck Typing - Iterable Object
Annotate the function `element_length` with the appropriate types.

**File**: `9-element_length.py`

```python
from typing import Iterable, Sequence, List, Tuple

def element_length(lst: Iterable[Sequence]) -> List[Tuple[Sequence, int]]:
    """Return a list of tuples with sequence and its length."""
    return [(i, len(i)) for i in lst]
```

### 10. Duck Typing - First Element of a Sequence
Augment the function `safe_first_element` with the correct duck-typed annotations.

**File**: `100-safe_first_element.py`

```python
from typing import Sequence, Any, Union

def safe_first_element(lst: Sequence[Any]) -> Union[Any, None]:
    """Return the first element of a sequence or None if empty."""
    if lst:
        return lst[0]
    else:
        return None
```

### 11. More Involved Type Annotations
Add type annotations to the function `safely_get_value`.

**File**: `101-safely_get_value.py`

```python
from typing import Mapping, Any, Union, TypeVar

T = TypeVar('T')

def safely_get_value(dct: Mapping[Any, Any], key: Any, default: Union[T, None] = None) -> Union[Any, T]:
    """Return the value for a key in the dictionary or a default value."""
    if key in dct:
        return dct[key]
    else:
        return default
```

### 12. Type Checking
Use `mypy` to validate and modify the following code:

**File**: `102-type_checking.py`

```python
from typing import Tuple, List

def zoom_array(lst: Tuple[int, ...], factor: int = 2) -> List[int]:
    """Return a list where each element of the tuple is repeated factor times."""
    zoomed_in: List[int] = [
        item for item in lst
        for _ in range(factor)
    ]
    return zoomed_in

array = (12, 72, 91)

zoom_2x = zoom_array(array)
zoom_3x = zoom_array(array, 3)
```

## Repository Structure

```
alx-backend-python/
├── 0x00-python_variable_annotations/
│   ├── 0-add.py
│   ├── 1-concat.py
│   ├── 2-floor.py
│   ├── 3-to_str.py
│   ├── 4-define_variables.py
│   ├── 5-sum_list.py
│   ├── 6-sum_mixed_list.py
│   ├── 7-to_kv.py
│   ├── 8-make_multiplier.py
│   ├── 9-element_length.py
│   ├── 100-safe_first_element.py
│   ├── 101-safely_get_value.py
│   └── 102-type_checking.py
├── README.md
```

## Usage
To test each script, you can run the corresponding `*-main.py` file, for example:

```sh
$ ./0-main.py
```

Ensure all scripts are executable and follow the PEP 8 style guide using `pycodestyle`.

## Validating with `mypy`
Use `mypy` to check the type correctness of your code:

```sh
$ mypy 102-type_checking.py
```

This ensures that your type annotations are correct and the code adheres to the specified types.

Happy coding!
