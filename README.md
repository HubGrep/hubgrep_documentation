# HubGrep Documentation

## building the docs locally

### Cloning hubgrep_search

`hubgrep_search` is added as a submodule to this repo.
To clone it, run

    git submodule update --init --recursive

(yea, working with submodules is a bit ugly, but readthedocs will do it automatically...)

### Installing the requirements

When you have the submodule, make a new virtualenvironment (eg. with `python venv env`),
and install the documentation requirements and the projects requirements.
(This is needed, because all modules are actually imported to get their docstrings)

    pip install -r requirements.txt
    pip install -r hubgrep_search/requirements.txt


### Running a build

If you just want a single local build, just run `make html`. 

To start a watcher updating when something changes, run

    sphinx-autobuild source build/html

this will start a webserver at <http://localhost:8000>

