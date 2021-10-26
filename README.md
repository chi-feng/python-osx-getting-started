# Getting started with Python on OS X

## Setting up a Python environemnt

First, you will need to set up a Python 3 environment on your computer. The system `python` on MacOS is still Python 2.7, which is deprecated and should NOT be used. 

There are three popular approaches to setting up a python environment from easiest (when it works) to most flexible:

1. If you don't want to mess with package management or virtual environments, the most straightforward option is to install [Anaconda (Individual Edition)](https://www.anaconda.com/products/individual). Anaconda comes with 1500+ of the most popular scientific computing packages compiled with sensible defaults (e.g. numpy is compiled using Intel MKL instead of OpenBLAS). 

2. Install [Homebrew](https://brew.sh) and run `brew install python3`. Then use `pip` to install any Python packages you may need. Instead of installing packages _globally_&mdash;which is the default&mdash;you can optionally use virtual environments to manage different versions of packages for portability and reproducibility. 

3. Install [Miniconda](). Miniconda is a free minimal installer for `conda`. It is a small, bootstrap version of Anaconda that includes only `conda`, Python, and the packages they depend on. Unlike `pip` which onl installs Python packages published on PyPI, `conda` is much more powerful can install other packages _outside_ of the Python package ecosystem, such as R and CUDA. However, more steps are needed to get started. 

## Choosing an IDE 

The best choice (for most use cases) is [VS Code](VS Code) with the [Python extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

VS Code has full support of Jupyter notebooks. In many ways the experience is superior to running jupyter notebooks in the browser. See https://code.visualstudio.com/docs/languages/python#_jupyter-notebooks 

Another great feature of VS Code is [Remote development using SSH](https://code.visualstudio.com/docs/remote/ssh), which lets you open a remote folder on any remote machine, virtual machine, or container with a running SSH server and take full advantage of VS Code's feature set. This is useful, for example, if you are on a Mac and need to run CUDA code on a Linux desktop. 

Another alternative IDE which is useful for _large_ projects is [PyCharm](https://www.jetbrains.com/pycharm/) but a lot of important features such as support for jupyter notebooks are only available in the Professional paid version, which is subscription only. 

## Notebooks vs. python scripts

Notebooks, when done well, are great for achieving what Donald Knuth called [Literate Programming](Literate programming). However, notebooks have several pitfalls:
1. Out-of-order execution can lead to inconsistent results. 
2. Writing code inside of cells makes it difficult to use proper software abstractions such as functions, classes, or modules (entire classes and functions must be contained within a single cell). 
3. Notebooks do not play well with version control unless you use workarounds.
5. Some forms of multiprocessing are not supported inside of a notebook.
6. Changes to code in an imported module require a kernel reset to be reflected. 

With VS Code, the lines between scripts and notebooks are blurred. You can evaluate any part of a python script in an interactive REPL and seamlessly convert between scripts and notebook, similar to `%%` blocks in MATLAB. 
