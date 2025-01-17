# typedclasses
Python classes with types validation at runtime. ***(Experimental & Under Development)***

## Installation
You can install this library using Python's favorite, `pip` package manager.

```sh
pip install -U typedclasses
```

## How it works
Using typedclasses, you can create classes in `dataclasses`-like manner i.e using type annotations and library will enforce types for
that class at runtime. Here's an example:

```py
import typing
from typedclasses import TypedClass

class User(TypedClass):
  id: int
  name: str
  email: typing.Optional[str] = None
```

Parameters will be validated when initialising above class. Since `email` has a default value set, It is optional to pass
it as a parameter while instansiating:

```py
>>> User(id=1, name="foobar") # runs fine
>>> User(id="1", name="foobar")
TypeError: Parameter 'id' must be an instance of <class 'int'>, <class 'str'> is unsupported.
```

This library also provides validation for *various* generic types from `typing` module:

```py
class Foo(TypedClass):
  x: typing.Union[int, float]

Foo(x=1) # ok
Foo(x=1.0) # ok
Foo(x="1") # invalid
```

List of all types supported from `typing` module can be found in the [documentation](https://github.com/nerdguyahmad/typedclasses/wiki).

## Contribute
You can contribute to the library in two ways:

- Directly contributing to code using pull requests.
- Suggest features or report bugs via issues.

We welcome all contributions! 👍

When using issues, Please be descriptive about your issue and for pull requests, Try to be consistent with current design.
