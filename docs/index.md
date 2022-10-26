# Overview

This short module is intended to introduce how testing can be automated using
Github(GH) Actions. We will also look into other common usages of GH Actions
like formatting, linting and type checking. 

## Learning Outcomes

* Understand the value of continuous development (CI)
* Practical experience about how Github actions can be used to automate
  testing
* Understand how code quality can be improved by automating type checking,
  linting and code formatting

## Schedule

| Time  | Topic   | 
|-------------- | -------------- |
| 14:30-14:45    | Continuous integration and Intro to Github Actions |
| 14:45-15:05    | Automated (py)testing with GH Actions (code along)  | 
| 15:05-15:15    | Break | 
| 15:15-15:45    | Exercise in pairs of two | 
| 15:45-16:00    | Automated type checking, linting and formatting | 

## Prerequisites

To follow the code-along and complete the exercises you should have the
following things prepared before the class:


* Git
* Github: It must be configured so that you can push to a remote repository.
  Revisit the install instructions if needed:
  <https://github.com/UPPMAX/programming_formalism/blob/main/setup.md>.
* Miniconda (Optional): We will be using Python and the packages `pytest`,
  `black`, `flake8` and `mypy` all of which can be installed in a conda
  environment. However, everything we do will be run by a virtual machine
  through Github actions so you only need this if you want to also test things
  locally.

!!! tip "Get environment ready"
    ``` bash
    conda activate my-env # Activate environment
    conda install black flake8 mypy pytest # Install necessary packages
    ```


