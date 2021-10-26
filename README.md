# Getting started with Python on OS X

Note: if you are using an M1-based Mac, you should look out for universal binaries, or M1 builds for optimal performance.

## Setting up a Python environemnt

First, you will need to set up a Python 3 environment on your computer. The system `python` on MacOS is still Python 2.7, which is deprecated and should NOT be used. 

The three most common approaches to setting up a python environment are:

1. Install [Homebrew](https://brew.sh) and run `brew install python3`. Then use `pip install package-name` to install any Python packages you may need. 
    - Pros: `pip` is the "official" Python package manager and has the most up-to-date index (PyPI). In addition, most Python/tutorials use `pip`. 
    - Cons: YMMV if you need extremely specific build configurations for scientific computing packages, e.g., TensorFlow built against a particular version of BLAS or CUDA. 

1. If you don't want to mess with package management or virtual environments, the most straightforward option is to install [Anaconda (Individual Edition)](https://www.anaconda.com/products/individual). Anaconda comes with over 1500 scientific computing packages preinstalled. 
   - Pros: "everything and the kitchen sink." Cross-platform (Windows, Linux, MacOS)
   - Cons: installation is bloated and promotes lazy dependency/package management. 

1. Alternatively, install [Miniconda](https://docs.conda.io/en/latest/miniconda.html). Miniconda is a small, bootstrap version of Anaconda that includes only `conda`, Python, and the packages they depend on. Unlike `pip` which only installs Python packages published on PyPI, `conda` is much more powerful can install other packages _outside_ of the Python package ecosystem, such as R and CUDA. However, additional steps and knowledge are required to get the most out of `conda`. 

## Choosing an IDE 

The best choice for most use cases is [VS Code](https://code.visualstudio.com/download) with the following extensions:
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

VS Code has full support of Jupyter notebooks. In many ways the experience is superior to running Jupyter notebooks in the browser. You can directly open `.ipynb` files and VS Code will start the appropriate notebook server. See full documentation here (https://code.visualstudio.com/docs/datascience/jupyter-notebooks). 

Another great feature of VS Code is [Remote development using SSH](https://code.visualstudio.com/docs/remote/ssh), which lets you open a remote folder on any remote machine, virtual machine, or container with a running SSH server and take full advantage of VS Code's feature set. This is useful, for example, if you are on a Mac and need to run CUDA on a Linux workstation. 

## Cloud developer environments 

### [Deepnote](https://deepnote.com/)
Collaborative Jupyter Python Notebooks
![image](https://user-images.githubusercontent.com/336681/138863363-e2bd8331-5562-4f14-aea5-f50c1e1c8b99.png)


### [Google Colab](https://colab.research.google.com/notebooks/intro.ipynb)
Sharable Jupyter Python Notebooks

### [GitHub CodeSpaces](https://github.com/features/codespaces) 
Lets users run VS Code in their browser connected to powerful VMs. This is a full-fat version of VS Code running in the cloud. Extremely useful and cost-effective for developing code using thin clients or in a team setting. 

## Virtual environments

Virtual environments are extremely useful when collaborating on a project with other developers since virtualenvs allow you to specify specific versions of python and required packages for a particular peojct. However, each package manager has its own way of setting up virtual environments, and even the best solutions tend to have issues with cross platform compatibility. 

**If you are working on a solo project, you probably don't need to set up a virtual environment unless your base environment is totally broken.** However, if you plan on sharing your code, then you can always export your current environment so that others can duplicate it. Using `pip`, you can export all installed packages and their versions to a file:
```bash
$ pip freeze > requirements.txt
```
To import and install the requirements from a file, run
```bash
$ pip install -r requirements.txt
```


## Notebooks vs. scripts

Notebooks, when done well, are great for achieving what Donald Knuth called [Literate Programming](https://en.wikipedia.org/wiki/Literate_programming#:~:text=Literate%20programming%20is%20a%20programming,source%20code%20can%20be%20generated.). This is usually achieved by interleaving code cells with markdown cells, which support LaTeX markup. However, notebooks have several pitfalls:
1. Out-of-order execution can lead to inconsistent results. 
2. Writing code inside of cells makes it awkward to use abstractions such as functions, classes, or modules. This is because entire classes and functions must be contained within a single cell, which jumbles the execution order. 
3. Notebooks don't play well with version control since they have a lot of embedded binary data and create nasty merge conflicts.
5. Some forms of CPU parallelism are not supported inside of a notebook.

With VS Code, the line between scripts and notebooks are blurred. You can evaluate any part of a python script in an interactive REPL and seamlessly convert between scripts and notebook, similar to how `%%` blocks work in MATLAB. 

