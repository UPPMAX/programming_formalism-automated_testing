
Continuous Integration(CI) is a popular practice where changes to the code are
committed often and by all members of a project into a main branch branch,
possibly several times a day. Automating the process of ensuring that new code
works and does not conflict with existing, is a goal in itself. Testing is a
central part of the CI workflow. Git and GH Actions are tools that help us with
this.

!!! info "The ingredients of CI"
    
    * Version control for the entire codebase/project
    * Automated testing of the code
    * Automated building e.g. [`cmake`](https://cmake.org/) and
      [`pyproject.toml`](https://pip.pypa.io/en/stable/reference/build-system/pyproject-toml/)
    * A platform/infrastructure for automation e.g.
      [Github](https://github.com/), [GitLab](https://about.gitlab.com/) or
      [circleci](https://circleci.com)

