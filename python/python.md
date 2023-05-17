# Python

## Python on Window using Vscode

- To check python version use: `py -3 --version` on CL (i.e. in terminal)

- Note: by starting VS Code in a folder, that folder becomes your "workspace".

- `py` on CL will enter in python's repl mode (with prompt ">>>" ) and show information about the installed python (version etc.).

- To exit the repl mode either ctrl-Z and Enter or write exit()/quit() and Enter

- to run a python file in terminal: enter `py hello.py`

### The most used pip commands:

- `pip list`: to check the pre-installed packages in the current virtual environment

- `py -m pip install matplotlib`: to instal "matplotlib" in current environment

- `pip freeze > requirements.txt` to create a list of packages in current environment

- To install the project dependencies using the requirements.txt file: `pip install -r requirements.txt`

### Python Environments

- An "environment" in Python is the context in which a Python program runs and consists of an interpreter and any number of installed packages.

- in programming, we use virtual environments to isolate package dependencies used in different projects so that they don't conflict with each other.

#### Global environments

By default, any Python interpreter installed runs in its own global environment. For example, if you just run python, python3, or py at a new terminal (depending on how you installed Python), you're running in that interpreter's global environment. Any packages that you install or uninstall affect the global environment and all programs that you run within it.

Do note that if you install packages into your global environment, though, in time it will become crowded with potentially unrelated or unexpected packages and make it difficult to properly test an application. You typically want to create an environment for each workspace.

#### Local environments

There are two types of environments that you can create for your workspace: virtual and conda environments. Both types of environment allow you to install packages without affecting other environments. This lets you isolate what packages you install for your workspace so that they don't interfere with your needs in another workspace.

##### Virtual environments

- A Python virtual environment consists of two essential components: the Python interpreter that the virtual environment runs on and a folder containing third-party libraries installed in the virtual environment.

- Python virtual environments create isolated contexts to keep dependencies required by different projects separate so they don't interfere with other projects or system-wide packages.

- Basically, setting up virtual environments is the best way to isolate different Python projects, especially if these projects have different and conflicting dependencies.

Always set up a separate virtual environment for each Python project, and install all the required dependencies inside it — never install packages globally.

A "virtual" environment is a built-in way to create an environment to isolate the packages you install per workspace. A virtual environment creates a folder that contains a copy (or symlink) to a specific interpreter. When you install packages into a virtual environment it will end up in this new folder so that they are not interspersed with other packages used or needed by other workspaces.

Note: While it's possible to open a virtual environment folder as a workspace, doing so is not recommended and might cause issues with using the Python extension.

- To create a virtual environment: `python -m venv venvname`

- To activate a virtual environment named "venvname": `source venvname/Scripts/activate`

- usually venvname should start by a a dot ('.') making it hidden. It is recommended not to modify the venvname folder

##### Virtual environment directory (folder) structure

```js
venv\
│
├── Include\
│
├── Lib\
│ │
│ └── site-packages\
│ │
│ ├── \_distutils_hack\
│ │
│ ├── pip\
│ │
│ ├── pip-22.0.4.dist-info\
│ │
│ ├── pkg_resources\
│ │
│ ├── setuptools\
│ │
│ ├── setuptools-58.1.0.dist-info\
│ │
│ └── distutils-precedence.pth
│
│
├── Scripts\
│ ├── Activate.ps1
│ ├── activate
│ ├── activate.bat
│ ├── deactivate.bat
│ ├── pip.exe
│ ├── pip3.10.exe
│ ├── pip3.exe
│ ├── python.exe
│ └── pythonw.exe
│
└── pyvenv.cfg

```

##### Conda environments

A "conda" environment is a Python environment that's managed using the conda package manager (see Getting started with conda). Whether to use a conda environment or a virtual one will depend on your packaging needs, what your team has standardized on, etc.

#### Python environment tools

- `pip`: the Python "package manager" that installs and updates packages. It's installed with Python 3.9+ by default.

- `venv`: allows you to manage separate package installations for different projects and is installed with Python 3 by default.

- `conda`: installed with "Miniconda" (or Anaconda). It can be used to manage both packages and virtual environments. Generally used for data science projects.

## Miscelleneous

- IPython (short for Interactive Python) was started in 2001 by Fernando Perez as an enhanced Python interpreter, and has since grown into a project aiming to provide, in Perez's words, "Tools for the entire life cycle of research computing." If Python is the engine of our data science task, you might think of IPython as the interactive control panel.

- A package manager is a tool that is used to download, install, manage, and even remove packages from your computer. The package manager tool also keeps an accurate track of package versions, and dependencies. Just as is the case with Python distributions, you can choose between several package managers. A good number of the package managers available today feature a simple command structure and function pretty much the same.

- `pip` is a recursive acronym "Python installs Packages" or "Python installs Python"

- `pypi`: Python Package Index (PyPI) is a repository of software for the Python programming language.

- `pypi` and `pip` combination provides functionality similar to that is provided by `npm` in Nodejs .

- A Python "distribution" bundles the core programing language to several other packages, and libraries that are designed to address a particular problem domain. For instance, a distribution may be specifically designed to tackle data development or Data Analytics.

- The standard Python distribution is available at the Python official website, and features the Python standard library, and Pip as the package manager. There are two other Python distributions that you need to be aware of, namely Anaconda and Miniconda.

### Diffenece between pip and conda

- `conda` is both a package manager and an environment manager. It is a cross platform package manager that may be used to install, and manage Conda packages, especially from Anaconda repository. Cross-plateform means that it can install other than python packages such as C/C++ packages. `pip` mainly install only python packages.

- `pip` is a package manager that is specifically designed to install Python packages exclusively. In contrast, Conda is an open-source installer and package-management tool that can also handle both Python and non-Python library dependencies.

- `conda` offers virtual environment capabilities and can run on multiple operating systems like Windows, Linux, and macOS. With Conda, you will be able to create, load, save, and switch between different environments.

#### Features of cons

- conda works with any distribution of Python.

- conda is an open source project and package that is 100% independent of Anaconda, Inc. and the Anaconda distribution of Python.

- conda is widely supported by a much broader software engineering community than each of the (too) many pip-based environment managers which have poor maintenance history, overlapping functionality, poor documentation, and confusing instructions.

- conda is a more general-purpose environment manager because it is inherently language-agnostic with multi-language support. pipenv, venv, pyenv, poetry and others are Python only.

- conda's environment integrity-checker is the most important feature that pipenv, venv, pyenv, and (too) many others do not do well (if at all). It guarantees that packages will be added in such a way that all pre-existing package dependencies will be met in that environment, or the build will fail and be rolled back.

- pip uses a greedy algorithm that installs (and downgrades) what it needs for the current package being installed without respecting the dependencies of the rest of the packages in the environment. pip can break existing environments and not inform users until it is too late. I have had to reinstall complete Python distributions several times because pip breaks things.

- you should prefer to use one tools that takes care of the environment and all the packages within it. And it is conda

- The biggest problem with conda is that (too) many developers are lazy and don't want to take the time to build a conda package before they distribute it. So there are many packages not available in conda package format or with a conda wrapper.

- Currently automatic conversion of pip packages to conda formats are being incorporated in conda.

### Python vs Anaconda

- Python is a multi-purpose programming language used in everything from from machine learning to web design. It uses `pip` (a recursive acronym for "Pip Installs Packages" or "Pip Installs Python") as its package manager to automate installation, update, and package removal.

- Anaconda is a distribution (a bundle) of Python, R, and other languages, as well as tools tailored for data science (i.e., Jupyter Notebook and RStudio). It also provides an alternative package manager called `conda`.

- So, when you install Python, you get a python interpreter (`py`) and `pip` (available in Python 3.4+ and Python 2.7.9+), which enables a user to install additional packages available on Python Package Index (or PyPi).

- In contrast, with Anaconda you get Python, R, 250+ pre-installed packages, data science tools, and the graphical user interface Anaconda Navigator.

- Thus, the main difference between Python and Anaconda is that the former is a programming language and the latter is software to install and manage Python and other programming languages (such as R).

#### Anaconda vs Miniconda

- Anaconda is an open-source python distribution. It is purpose-built for such applications as machine learning, data science, and large-scale data processing. This distribution includes the core Python language, along with more than 200 packages, and a package management tool (conda).

- Miniconda is a slimmed-down distribution version of Anaconda. It has all the components of the Anaconda distribution, except the 200+ pre-installed data science applications. With the various Miniconda installers, you will get the core Python language, and a package manager tool (Conda). Then
  you can use the command line to install the packages you need individually. As such, Miniconda offers all the benefits of the Anaconda distribution with minimal space requirements. Owing to the smaller file size and reduced disk space requirements, Miniconda is relatively faster to install as compared to the Anaconda distribution.

### Package.json equivalent in Python!

- First install all dependency packages, then create a requirements.txt file through below command at your local,

`pip freeze > requirements.txt`

- Then in production environment, install those packages through,

`pip install -r requirements.txt`

If there is anything you used in local, then remove those packages manually from that file. This way you can manage your dependencies as package.json
