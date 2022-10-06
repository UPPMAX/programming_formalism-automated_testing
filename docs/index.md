# Course Overview 

This module is intended to give an introduction to test driven development (TDD) in
practice. Because it is impossible to completely separate this from a
programming language, we will be using `Python` for this part of the course.
However, the workflow presented here generalizes to other languages and we we
will provide links to common testing tools/resources for other programming
languages. We will also be using `git` for version control and `Github` actions
for continuous integration testing.

# Learning Outcomes

* Learn about tools like `pytest` and Github actions commonly used in TDD.
* Be able to apply the tools on simple examples.
* Introduction to more and advanced topics and where to go from here. 


# Schedule

| Time  | Topic   | 
|-------------- | -------------- |
| 13:00-13:30    | Introduction to testing in Python | 
| 13:30-14:00    | Automated testing using Github actions | 
| 14:00-14:15    | Break | 
| 14:15-15:00    | Putting it all together - code along | 
| 15:00-15:30    | Exercises | 
| 15:30-16:00    | Advanced Topics | 

# Prerequisites

To follow the code-along and complete the exercises you should have the
following things prepared before the class:

* A working `Python 3.7` or above version with `pip` installed
* A [Github](https://github.com/) account that is setup so you can push changes
  to a remote repository 
* `Git`
* Follow the steps listed below 



## Verify you are set to go

To verify that you are all set for participating in the module, you should follow
the steps listed here. This will simultaneously give you a first introduction
to the tools we will be working with.

### 1. Fork the testing template repository

Go to the [testing template](https://github.com/MatPiq/testing_template) and
make a fork of the repository. You can read all about forking
[here](https://docs.github.com/en/get-started/quickstart/fork-a-repo). This
repository will serve as a minimal template for trying out TDD and will used
throughout the this TDD module. 

### 2. Make a local clone of the repository

Once you have forked the repository, you can make a local clone on your
computer. Remember to change the username accordingly. 

``` bash
# If you are using https 
git clone https://github.com/'your-username'/testing_template.git

# If you are using SSH
git clone git@github.com:'your-username'/testing_template.git

# Enter the template
cd testing_template
```

!!! info "Setting up Github for pushing to remote" 
    If you want to be able to push changes to a remote Github repository (which
    you want), your normal password used to login is not enough. You need
    either a personal access token (PAT) or generate an SSH keypair and add the
    public key to your github account. Please see this
    [link](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls)
    for more information.

### 3. Install the necessary requirements 

We now install the necessary requirements for the project. This includes the
testing library [`pytest`](https://docs.pytest.org/en/7.1.x/) and
[`NumPy`](https://numpy.org/) that will be used for several examples. It is
recommended to setup a virtual environment for the project using
[`venv`](https://docs.python.org/3/library/venv.html) or
[`conda`](https://docs.conda.io/en/latest/) to not clutter your system `Python`
with packages. 

!!! tip "Setup virtual environment (optional but recommended)"

    **Using `venv`**
    ``` bash
    # From root of the project directory
    python3 -m venv testing-env

    # source it
    source testing-env/bin/activate
    ```
    **Using `conda`**
    ``` bash
    # Create the environment
    conda create --name testing-env 
    
    # Activate the environment
    conda activate testing-env
    ```

After having activated the virtual environment, installing dependencies is as
easy as:

``` bash
pip install .[test]
```
Make sure that you are standing at the root of the directory when running the
command. The output form a successful installation should end with something similar to

``` bash
Successfully built testlib
Installing collected packages: numpy, testlib, pytest
Successfully installed numpy-1.23.3 pytest-7.1.3 testlib-0.0.1
```

!!! note "`pyproject.toml`"
    We are using `pyproject.toml` to define and install dependencies
    instead of a basic `requirements.txt` file. This is the prefered
    way to build and distribute packages according to [PEP
    621](https://peps.python.org/pep-0621/) and facilitates TDD workflows. This
    also means that the project will be installed as a module called `testlib`
    in your virtual environment. Below you can see how the project is defined

    ``` toml title="pyproject.toml"
    [project]
    name = "testlib"
    version = "0.0.1"
    description = "Minimal template for continous integration testing with Python using Github actions and pytest"
    authors = [{ name = "Matias Piqueras", email = "matias.piqueras@uppmax.uu.se" }]
    requires-python = ">=3.7"
    dependencies = ["numpy>=1.23.0"]

    [project.optional-dependencies]
    test = [
      "pytest>=7.1.3"
    ]
    ```

### 5. Run `pytest` and make the test pass

You should now be able to run your first test! To do so, simply run the command 

``` bash
pytest
```

from your terminal.


``` py
================================================= test session starts ==================================================
platform darwin -- Python 3.10.6, pytest-7.1.3, pluggy-1.0.0
rootdir: /Users/matpi832/Projects/programming-formalism/testing_template
collected 1 item

tests/test_math.py F                                                                                             [100%]

======================================================= FAILURES =======================================================
_______________________________________________________ test_add _______________________________________________________

    def test_add():
>       assert math_funcs.add(1, 1) == 2
E       assert 0 == 2
E        +  where 0 = <function add at 0x105814820>(1, 1)
E        +    where <function add at 0x105814820> = math_funcs.add

tests/test_math.py:5: AssertionError
=============================================== short test summary info ================================================
FAILED tests/test_math.py::test_add - assert 0 == 2
================================================== 1 failed in 0.02s ===================================================
```

### 6. Commit and push your changes to Github

# Credits
