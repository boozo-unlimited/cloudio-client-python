# Development

[Home](../README.md)

This section contains information for developers. In case you want to improve, debug, 
extend the project you may find here some useful information.

## Set up Development Environment
You need to have Python 3.x and `pipenv` installed:
```bash
# Install pipenv using pip
$ pip install pipenv
```
Install the needed packages for development (using pipenv):
```bash
$ pipenv install
```

## Generate and Upload Distribution Package
Prior to upload a new Python package be sure to create first a new release
of the project:
 - Increment version number
 - Update changelog file
 - Push to master branch

```bash
$ cd <into project>

# Install package needed for deployment (build, twine) 
$ pipenv install --dev

# Build the package
$ pipenv run python -m build

# Optional: Send to test server
$ pipenv run twine upload --repository testpypi dist/*

# Upload to official server
$ pipenv run twine upload --repository pypi dist/{<project-name>-x.y.z}*.whl
$ pipenv run twine upload --repository pypi dist/{<project-name>-x.y.z}.tar.gz
```

## Link to Local Package
If you want to use for example the `cloudio-common-python` package from your locally cloned 
git repository, use a command similar like:
```bash
$ pipenv install --dev -e ../cloudio-common-python
```
If it does not work with a relative path, try with an absolute path. The folder you are 
referencing must contain a `setup.cfg` or `setup.py` file.
