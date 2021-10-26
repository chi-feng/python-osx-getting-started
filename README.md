# Getting started with Python on OS X

Note: if you are using an M1-based Mac, you should look out for universal binaries, or M1 builds for optimal performance.

## Setting up a Python environemnt

First, you will need to set up a Python 3 environment on your computer. The system `python` on MacOS is still Python 2.7, which is deprecated and should NOT be used. 

There are three popular approaches to setting up a python environment from easiest (when it works) to most flexible:

1. If you don't want to mess with package management or virtual environments, the most straightforward option is to install [Anaconda (Individual Edition)](https://www.anaconda.com/products/individual). Anaconda comes with 1500+ of the most popular scientific computing packages compiled with sensible defaults (e.g. numpy is compiled using Intel MKL instead of OpenBLAS). 

2. Install [Homebrew](https://brew.sh) and run `brew install python3`. Then use `pip` to install any Python packages you may need. Instead of installing packages _globally_&mdash;which is the default&mdash;you can optionally use virtual environments to manage different versions of packages for portability and reproducibility. 

3. Install [Miniconda](https://docs.conda.io/en/latest/miniconda.html). Miniconda is a free minimal installer for `conda`. It is a small, bootstrap version of Anaconda that includes only `conda`, Python, and the packages they depend on. Unlike `pip` which only installs Python packages published on PyPI, `conda` is much more powerful can install other packages _outside_ of the Python package ecosystem, such as R and CUDA. However, additional steps and knowledge are required to get the most out of `conda`. 

## Choosing an IDE 

The best choice (for most use cases) is [VS Code](https://code.visualstudio.com/download) with the following extensions installed:
1. [Python extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-python.python). 
   - IntelliSense: Edit your code with auto-completion, code navigation, syntax checking and more
   - Linting: Get additional code analysis with Pylint, Flake8 and more
   - Code formatting: Format your code with black, autopep or yapf
   - Debugging: Debug your Python scripts, web apps, remote or multi-threaded processes
   - Testing: Run and debug tests through the Test Explorer with unittest or pytest.
   - Jupyter Notebooks: Create and edit Jupyter Notebooks, add and run code cells, render plots, visualize variables through the variable explorer, visualize dataframes with the data viewer, and more
   - Environments: Automatically activate and switch between virtualenv, venv, pipenv, conda and pyenv environments
   - Refactoring: Restructure your Python code with variable extraction, method extraction and import sorting
2. [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance) (type checking, static code analysis, auto-imports, semantic highlighting, etc.)

VS Code has full support of Jupyter notebooks. In many ways the experience is superior to running Jupyter notebooks in the browser. See https://code.visualstudio.com/docs/languages/python#_jupyter-notebooks. Some notebook features that are only available in VS Code but not in the browser-based notebook editor are:
1. Table of contents
2. IntelliSense support in the Jupyter Notebook Editor
3. Variable explorer and Data Viewer
4. Custom notebook diffing 
5. Debugging using the Python language server debugger. 

See full documentation here (https://code.visualstudio.com/docs/datascience/jupyter-notebooks#_table-of-contents)

Another great feature of VS Code is [Remote development using SSH](https://code.visualstudio.com/docs/remote/ssh), which lets you open a remote folder on any remote machine, virtual machine, or container with a running SSH server and take full advantage of VS Code's feature set. This is useful, for example, if you are on a Mac and need to run CUDA code on a Linux desktop. 

Another alternative IDE which is useful for _large_ projects is [PyCharm](https://www.jetbrains.com/pycharm/) but a lot of important features such as support for jupyter notebooks are only available in the Professional paid version, which is subscription only. 

## Notebooks vs. scripts

Notebooks, when done well, are great for achieving what Donald Knuth called [Literate Programming](Literate programming). This is usually achieved by interleaving code cells with markdown cells, which support LaTeX markup. However, notebooks have several pitfalls:
1. Out-of-order execution can lead to inconsistent results. 
2. Writing code inside of cells makes it difficult to use proper software abstractions such as functions, classes, or modules. This is because entire classes and functions must be contained within a single cell, which exacerbates out-of-order execution issue when updating functions or classes. Furthermore, changes to code in an imported module require resetting the kernel to take effect.
3. Notebooks do not play well with version control unless you use certain workarounds like converting notebooks into python scripts before committing changes.
5. Some forms of multiprocessing are not supported inside of a notebook.

With VS Code, the lines between scripts and notebooks are blurred. You can evaluate any part of a python script in an interactive REPL and seamlessly convert between scripts and notebook, similar to how `%%` blocks work in MATLAB. 
