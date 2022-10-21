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
| 14:30-14:45    | Continuous integration | 
| 14:45-15:00    | Introduction to Github Actions (code along) | 
| 15:00-15:10    | Break | 
| 15:10-15:30    | Automated (py)testing with GH Actions (code along)  | 
| 15:30-15:45    | Automated type checking, linting and formatting | 
| 15:45-16:00    | Exercise | 

# Prerequisites

To follow the code-along and complete the exercises you should have the
following things prepared before the class:


* Git
* Github: It must be configured so that you can push to a remote repository.
  Revisit the install instructions if needed:
  https://github.com/UPPMAX/programming_formalism/blob/main/setup.mdLinks to an
  external site.
* Miniconda (Optional): We will be using Python and the package pytest, black,
  flake8 and pylint all of which can be installed in a conda environment.
  However, everything we do will be run by a virtual machine through Github
  actions so you only need this if you want to also test things locally.

