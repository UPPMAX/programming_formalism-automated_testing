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

# Prerequisites

To follow the code-along and complete the exercises you should have the
following things prepared before the class:

* `Python 3.7` or above as well as a package manager - either `pip` or `conda`
  to install `pytest` and `NumPy`. 
* A [Github](https://github.com/) account with SSH setup so that you can push
  changes to a remote repository from your local branch. See Github's ssh
  [guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys)
  for how to set it up.
* Git



## Verify you are set to go

To verify that you are all set for participating in the module, you can follow
the steps listed below. This will simultaneously give you a first introduction
to the tools we will be working with. 

### 1. Fork the testing template repository

### 2. Make a local clone of the repository

### 3. Install the necessary requirements 

!!! note
    We will be using `pyproject.toml` to define and install dependencies
    instead of a basic `requirements.txt` file. This is the prefered
    way to build and distribute packages according to [PEP
    621](https://peps.python.org/pep-0621/) and will facilitate testing. This
    also means that `testing_template` will be installed as a module in your
    virtual environment. 

### 5. Run `pytest` and make the test pass

### 6. Commit and push your changes to Github

# Credits
