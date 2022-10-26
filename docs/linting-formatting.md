We are now going to see other parts of the development that be automated using
GH Actions in order improve the quality of the code base. We will continue with
Python and look at some modern and common tools used popular projects.

## Formatting with `black`

How your code is formatted matters for the readability. This is a hot topic and
people have different styles and preferences. When working together however, it
is often more important that the style is coherent than which exact style
use. 

In Python some of the most popular formatters are:

* [`Black`](https://github.com/psf/black)
* [`autopep8`](https://github.com/hhatto/autopep8)
* [`YAPF`](https://github.com/google/yapf)

We will be looking using `Black` since this is the mostly commonly used

!!! quote "Black - The Uncompromising Code Formatter"
    Black is the uncompromising Python code formatter. By using it, you agree
    to cede control over minutiae of hand-formatting. In return, Black gives
    you speed, determinism, and freedom from pycodestyle nagging about
    formatting. You will save time and mental energy for more important
    matters.

Let us create a module `formatting.py` 

``` python title="formatting.py"
import numpy as np
def the_abc_func(a,                    b,           c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z, a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z):
    pass

a_short_list = [
"an element"
]

a_long_list = ["an element",  "an element",    "an element"  "an element",  "an element",  "an element", "an element",  "an element"]





```

Now we format at see what happens

``` bash
black formatting.py
```

### Adding `black` to workflow

To add `black` to the workflow we need to add it to the packages being
`pip`-installed as well as create a new new *step*.

``` yaml title="python-app.yml"
    # This workflow will install Python dependencies, run tests and lint with a single version of Python
    # For more information see: https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-python

    name: Python application

    on:
      push:
        branches: [ "main" ]
      pull_request:
        branches: [ "main" ]

    permissions:
      contents: read

    jobs:
      build:

        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v3
        - name: Set up Python 3.10
          uses: actions/setup-python@v3
          with:
            python-version: "3.10"
        - name: Install dependencies
          run: |
            python -m pip install --upgrade pip
            pip install pytest black 
            if [ -f requirements.txt ]; then pip install -r requirements.txt; fi
        - name: Test with pytest
          run: |
            pytest .
        - name: Formatting with black
          run: |
            black formatting.py --check --diff
```

!!! note "Formatting on push"
    It is also possible to setup for your code to be automatically formatted
    when pushed to the repository. You can read more about that [here](https://github.com/marketplace/actions/run-black-formatter).


## Linting with `flake8`

Linting is a form of static code analysis that looks for and warns about code
smells, possible errors and bad style in your code. You have probably seen this
already if you are using a modern IDE like vscode or Pycharm with a built-in
language server. 


A popular *linter* for Python that can be used directly from the command line
(It can also be integrated into an IDE) is
[`Flake8`](https://flake8.pycqa.org/en/latest/#). Let us create a new file
called `linting.py` in the same directory we used for automated testing. You
can find all the error/violation codes
[here](https://flake8.pycqa.org/en/latest/user/error-codes.html)

``` bash
touch linting.py
```

``` python title="linting.py"
import numpy as np # F401
from math import * # F403

if True == False: #
    x = sqrt(9)
    break # F701
```

## Static type-checking with `mypy`

Python is an interpreted language, however, as of [PEP
484](https://peps.python.org/pep-0484/) it supports *Type Hints*. Some very
popular packages like [`pydantic`](https://pydantic-docs.helpmanual.io/) even
use type hints to evaluate input at runtime. 


``` python title="type_checking.py"
def reverse_string(s: str) -> str:
    return s.reverse()
```

We can now evaluate if there are any type errors using `mypy`. 

``` bash
mypy type_checking.py
```

!!! note "Benefits of Type Hints"
    * Improves readability (I think)
    * Easier to spot bugs and maintain project
    * Forces you to think
    * Better autocomplete if using language server


??? tip "Final workflow"
    ``` yaml title="python-app.yml"
    # This workflow will install Python dependencies, run tests and lint with a single version of Python
    # For more information see: https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-python

    name: Python application

    on:
      push:
        branches: [ "main" ]
      pull_request:
        branches: [ "main" ]

    permissions:
      contents: read

    jobs:
      build:

        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v3
        - name: Set up Python 3.10
          uses: actions/setup-python@v3
          with:
            python-version: "3.10"
        - name: Install dependencies
          run: |
            python -m pip install --upgrade pip
            pip install flake8 pytest black mypy
            if [ -f requirements.txt ]; then pip install -r requirements.txt; fi
        - name: Test with pytest
          run: |
            pytest .
        - name: Formatting with black
          run: |
            black formatting.py --check --diff
        - name: Linting with flake8
          run: |
            flake8 linting.py
        - name: Type checking with mypy
          run: |
            mypy type_checking.py

    ```



## Automated refactoring with `sourcery` (Bonus)

`sourcery` is a new and interesting tool that is able to refactor the code to
make it more *pythonic*. Since it requires that you sign up for an account, I
will just quickly show its functionality. However, it can be added as a GitHub
action and just like with `black` it can be used to automatically refactor the
when you push. You can read more about this [here](https://docs.sourcery.ai/Guides/Getting-Started/GitHub/).

``` python title="refactoring.py"
# assign-if-exp
condition = True
if condition:
    x = 1
else:
    x = 2


# Augmented assign
count = 2
other_value = 2
count = count + other_value


# Chain compares
b = 2
if 1 < b and b < 3:
    print("b is between 1 and 3")


# convert-any-to-in
hats = ["basker", "cap", "bowler"]
if any(hat == "bowler" for hat in hats):
    print("I have a bowler hat!")
```

We can check if any refactoring can be done using `sourcery`

``` bash 
sourcery review refactoring.py
```
Or if we want to directly perform the refactoring in-place

``` bash 
sourcery review --in-place refactoring.py
```

!!! tip "Where to go from here"
    If you are interested in learning more tools and ways to improve the
    quality of your project, a really good place to start is looking at
    cookicutter templates. Two great ones for `Python` are:

    * <https://cookiecutter-hypermodern-python.readthedocs.io/en/2022.6.3.post1/>
    * <https://scikit-hep.org/developer>
