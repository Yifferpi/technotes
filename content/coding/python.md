+++
chapter = false
title = "Python"
weight = 5
+++


## Virtual Environments
venv for python

allows to install Python packages and a Python Interpreter in an
isolated location from the rest of the system instead of installing
globally

Reasons:
- preventing version conflict

Isolation could be separate PC, separate VM, a docker container or a venv

How to set up:
`python -m` select a module from sys.path to run as a script

- for pythn3.4 and above, there is the baked-in package `venv`
- for versions below, use `virtualenv` (might need systemwide install first)

For python3.4 and above:
- `python -m venv <directory>` to create a virtual environment in <directory>
- `source <directory>/bin/activate` to activate the environment
- `deactivate` to deactivate the environment
- if created with `python -m venv`, simply remove the directory to delete env

the environment is active on the entire system. internally, it works by
modifying the head of the path variable.

[Resource](https://python.land/virtual-environments/virtualenv)

## General Resources
[Python Tutorials](https://scicomp.ethz.ch/wiki/Python/Manual/3.6.0)
[Advanced Python Webscraping](https://www.codementor.io/blog/python-web-scraping-63l2v9sf2q)

