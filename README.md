# Teaching Python's NetworkX and Bash

Lecture  materials for teaching Python's NetworkX package and Bash scripting.


**Contents**

- [Requirements](#requirements)
- [Environment Setup](#environment-setup)
    - [Anaconda and Conda](#anaconda-and-conda)
    - [Downloading Packages](#downloading-packages)


## Requirements

To run the Jupyter notebooks, you'll need Python 3.x and to install the
appropriate packages

- Python 3.x
- NetworkX
- bash


## Environment Setup

### Anaconda and Conda

To make things as streamlined as possible, I suggest downloading Anaconda or, at
the very least, just the package manager Conda.

Miniconda and just the `conda` package manager and Python is much smaller, and
you can find the download instructions for your operating system of choice
[here][conda].

Anaconda includes many more useful packages commonly used in scientific
computing and data science. It also comes with Jupyter Notebook packages so this
might be easier route if you don't have experience with Python and see yourself
using it in the future.

[conda]: https://conda.io/miniconda.html


### Downloading Packages

Running this in your `bash` terminal should setup your environment with
everything you'll need.

```sh
# Create separate environment if you want to separate environment for this
conda create -n py3 python=3 networkx ipython notebook

# Install bash kernel for running bash commands from within the bash notebook
source activate py3  # Activate new environment first
pip install bash_kernel
python -m bash_kernel.install

# Deactivate environment
source deactivate py3
```


### Using Environment

If you use the environment created above, you'll first need to "activate" it
first before using the environment and all the packages you've installed.

Following the use of the environment and you wish to exit, you'll need to
"deactivate" your environment.

Depending on your operating system, the `source` part of the following commands
may be unnecessary e.g. Windows OS.

```sh
# Activate environment
source activate py3

# Deactivate environment
source deactivate py3
```

For more on environment management, see [here][env] for more.

[env]: https://conda.io/docs/user-guide/tasks/manage-environments.html
