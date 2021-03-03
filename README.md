# NIDS FAIR data / BIDS



You can either run everything on your computer after following the environment setup below (recommended), or you can access the lecture Jupyter notebook simply by clicking on the "Launch Binder" badge (cf instructions below)).

# Running the lecture Jupyter notebook online on Binder

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/NIDS2020-instructor/preproc/HEAD?filepath=preproc.ipynb)

To run the lecture Jupyter notebook online on Binder:
* Click on the "Launch binder" badge above (better to right click and then open in a new tab)
* Once the notebook is ready, display a terminal by:
  * selecting on the top left `File` --> `Open...`
  * selecting on the top right of the newly displayed page `New` -->  `Terminal`
* You can follow along the notebook, and in the terminal you could type bash commands indicated in the notebook

# How to setup your own coding environment at home ?

## First part, depending on your OS

### Linux

* Install [Visual Studio Code](https://code.visualstudio.com/docs/setup/linux) (prefer deb or repository installation)
* Install [Miniconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html)
* Please indicate any problem during installation on Slack (after your very first message, please immediately hover on it and click on the chat buble to `Reply in thread` for  all your messages to be in a single thread)

### Mac
* Open a terminal and type `echo $0`. If the output does not indicate `bash` this means you need to set your default shell as `bash`. You can do it by following the instructions [here](https://www.howtogeek.com/444596/how-to-change-the-default-shell-to-bash-in-macos-catalina/#:~:text=From%20System%20Preferences&text=Hold%20the%20Ctrl%20key%2C%20click,OK%E2%80%9D%20to%20save%20your%20changes.) (see section "Using System Preferences" if you prefer using the graphical interface)
* Install `homebrew` as indicated [here](https://brew.sh/)
* Update `bash` as described [here](https://itnext.io/upgrading-bash-on-macos-7138bd1066ba)
* May be a good idea to restart ? Please let me know if you don't restart and have issues (so that i update these instructions)
* Install [Visual Studio Code](https://code.visualstudio.com/docs/setup/mac)
* Install [Miniconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/macos.html)
* Please indicate any problem during installation on Slack (after your very first message, please immediately hover on it and click on the chat buble to `Reply in thread` for  all your messages to be in a single thread)

### Windows 10
* Make sure you have installed the latest OS updates (Windows menu -> `Check for Updates`)
* Install WSL2 as indicated [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10) (you may also need info from [here](https://codefellows.github.io/setup-guide/windows/)), then install the Ubuntu 20.04 app from the Microsoft store as indicated in the first link (it is recommended to also install the Terminal app as suggested in that link)
* Install [Visual Studio Code](https://code.visualstudio.com/docs/setup/windows) 
* Start VS Code, and inside the program accept the suggestion of installing "VS Code Remote Pack" to use with WSL2 (for more information please see [these instructions](https://code.visualstudio.com/docs/remote/wsl))
* Please indicate any problem during installation on Slack (after your very first message, please immediately hover on it and click on the chat buble to `Reply in thread` for  all your messages to be in a single thread)

## Second part, OS independent (almost)

* Now on the command line in a terminal (WSL 2 for Windows):
  * Update your local environment:  
  `source ~/.bashrc`
  * Configure the conda-forge channel to be BEFORE any defaults in `~/.condarc`:  
  `conda config --prepend channels conda-forge`
  * Update your conda version to the latest:  
  `conda update -n base -c defaults conda`
  * Install Jupyter notebook in base environment (you will need to install the `ipykernel` module in each other conda python environment for Jupyter to find your environments automatically):  
  `conda install -n base nb_conda_kernels ipykernel`
  * Create a neuroimaging data science environment, for example as below:  
    ```
    conda create -n ni38 python=3.8
    conda install -n ni38 numpy cython ipython scipy scikit-learn \
                   pandas xlrd matplotlib seaborn lxml ipykernel \
                   yapf sphinx numpydoc mypy pytest imageio pylint \
                   nilearn heudiconv pybids
    ```
  * **FOR WINDOWS ONLY**
    * Make sure you are in the `base` conda environment  
    `conda activate base`
    * Generate Jupyter notebook configuration  
    `jupyter notebook --generate-config`
    * Edit `~/.jupyter/jupyter_notebook_config.py` (for example with VS Code) to make sure to have the following two configuration statements (no `#` in front) inside that file (asuming you have Chrome installed, otherwise change the path below to the location of your Internet browser executable): 
      * `c.NotebookApp.use_redirect_file = False`
      * `c.NotebookApp.browser =  u'/mnt/c/Program\ Files\ \(x86\)/Google/Chrome/Application/chrome.exe %s'`
* **For all OS**, to start a new project, you could do something like:
  * Create a new project directory `my_proj` inside a parent directory `my_projects`
    ```
    cd
    mkdir my_projects
    cd my_projects
    mkdir my_proj
    ```
  * Start Visual Studio code, create a new file, save it inside `my_proj` as a Python file (i.e. with `.py` extension, e.g. `analysis.py`)
  * In a terminal (a linux terminal but not the one provided by VS Code to keep it free), start a Jupyter notebook after making sure you are in the default `base` conda environment:
    ```
    conda activate base
    jupyter notebook
    ```
  * A page should automatically open in your internet browser. If you cannot find it or it does not happen, read the output on the terminal and copy the URL indicated inside a tab of your internet browser
  * To start a new notebook, in the Jupyter page in your browser, click in the top right on `New` and then choose the conda environment you want (the python process which will interpret your commands is called a kernel)
* **For all OS**, to run the examples from the course, you could do something like:
  * Create a directory `NIDS` then clone the python lectures inside it
    ```
    cd
    mkdir NIDS
    cd NIDS
    git clone https://github.com/NIDS2020-instructor/python-series.git
    ```
  * Start Visual Studio code, click on `File` --> `Open Folder` and then choose `python-series` (inside `NIDS`), click `OK`
  * In a terminal (a linux terminal but not the one provided by VS Code to keep it free), start a Jupyter notebook after making sure you are in the default `base` conda environment:
    ```
    cd
    cd NIDS
    cd python-series
    conda activate base
    jupyter notebook
    ```
  * A page should automatically open in your internet browser. If you cannot find it or it does not happen, read the output on the terminal and copy the URL indicated inside a tab of your internet browser
  * To start a Python lecture notebook, click on its name in the list of files which is displayed in the Jupyter page of your browser (e.g. choose `python_part3.ipynb`)
  * Then choose the right conda environment by clicking on `Kernel` -> `Change Kernel` and selecting an environment with all the required packages 

In case of any problem or if you have any question, please ask on Slack (after your very first message, please immediately hover on it and click on the chat buble to `Reply in thread` for  all your messages to be in a single thread), thank you !
