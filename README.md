# cadd-practice

These are some notes for beginners on getting set up to start doing computer-aided drug design (CADD) research, based on the Volkamer Lab's excellent collection of [talktorials](https://projects.volkamerlab.org/teachopencadd/talktorials.html).

## Note to self

The installation has changed. It is necessary now to use `mamba` to install the environment.

To install mamba, use
```
conda install mamba -n base -c conda-forge
```
Then create an environment for the dependencies in `teachopencadd` and `opencadd`. Currently, the links for these environments are:

- [https://raw.githubusercontent.com/volkamerlab/teachopencadd/master/devtools/test_env.yml]
- [https://raw.githubusercontent.com/volkamerlab/opencadd/master/devtools/conda-envs/user_env.yaml]

Once you have the environment file set up, use
```
mamba env create -f env.yml
```

## Setting Up

### Starting from Windows

If you are starting on a Windows machine, you will need to install a separate Linux operating system called "Ubuntu" onto it.
Most of the software we will be using is designed to run on a Linux OS, because these operating systems are open-source (freely available) and are widely used in scientific computing.

Start by following [these instructions](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) to install the Ubuntu OS as a Windows Subsystem.

Once you have the "Ubuntu" app installed, open it.
Upon opening the newly installed Ubuntu app, you will be prompted to create a username and password. You will need this password to run any commands requiring "superuser" permissions (commands starding with "sudo").

Before moving forward, you should change one setting:
1. Click the orange Ubuntu icon in the upper left corner of your terminal window.
2. Click "Properties"
3. Check the box that says "Ctrl+Shift+C/V as Copy/Paste".

This will enable you to copy and paste in your terminal window (more on that momentarily).

Some context on what you have just installed:
Ubuntu is the most popular instance of the broader family Linux operating systems.
The Ubuntu "app" that you are installing is sort of like a separate computer within your computer.
You will interact with this Linux "subsystem" through a [terminal](https://en.wikipedia.org/wiki/Computer_terminal) window, which is just a window that allows you to enter operating system commands.
In a moment, we will show some simple commands to do things like print to the screen, move from one folder (or "directory") to another, tell you which directory you are in, list contents of a given directory, download a file from the internet, etc.

Different terminals have different languages that are used to enter terminal commands. This one uses the [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) command language.
As a first attempt, let's use the `echo` command to print a message to our screen:
```
echo "HELLO WORLD"
```
You should see that it prints `HELLO WORLD` to your screen.

Your Ubuntu OS has its own file system. To figure out where you are in your file system, use the "print working directory" command:
```
pwd
```
If you ever need to, you can access your Windows file system as a "mounted drive" by navigating to `/mnt/c/Users/<your username>`.
You can do so with the "change directory" command.
```
cd /mnt/c/Users/<your username>
```
If you aren't sure what your user name is, you can start typing and press tab to see the available options along the way.

To see what's in the directory you navigated to, you can use the "list" command:
```
ls
```
If you need to, you can learn more terminal commands from [this tutorial](https://linuxjourney.com/lesson/the-shell).

I will give you all of the commands you need here to install the necessary software, so you can wait to learn more unless you are interested.

### Installing Conda

[Conda](https://en.wikipedia.org/wiki/Conda_(package_manager)) is a powerful package-manager for scientific computing.
You can think of it like an "app store".

If you are on a Linux machine or using a Linux terminal on Windows, you can download the install script for conda to your current directory as follows using the "web get" command:
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```
This installer script is written in the Bash language.
You can run it as follows:
```
bash Miniconda3-latest-Linux-x86_64.sh
```
You will be prompted to accept the licensing terms along with two questions:
 - The first question will ask you where you want it installed. Instead of `/home/<username>/miniconda3`, set the install location to `/home/<username>/conda`.
 - The second question will ask you you want to initialize conda. Answer `yes` here. (If you miss this step and type "no", it should give you instructions at the end for running the initialization command.)

Then restart your terminal.
When you restart, you should see the word "base" in parentheses next to your terminal prompt.
This indicates that you are in Conda's "base environment".
All of your software for this project will be installed into an environment that is specific to this work.
If you do more coding in the future, you would create new environments with the necessary software.

To check that it worked, try the following command to update conda:
```
conda update conda
```
There seem to be some recent issues with allowing conda permissions on a Windows subsystem.
If you get an HTTP Error like I did, the following should fix it for you:
```
chmod -R 777 /home/<username>/conda
```
after which you can try the update command again.

Once the update command is working, you should be good to go.

### Creating Your Environment

Next, we will create a conda environment called `cadd-env`, which is where you will install all of your software for this project.
You can create this environment as follows:
```
conda create -n cadd-env python=3
```
This creates an environment called `cadd-env` that uses version 3 of the [Python programming language](https://docs.python.org/3/).

To activate the environment you just created, you will then use:
```
conda activate cadd-env
```
When this environment is active, your terminal window will say `(cadd-env)` to the left of the terminal prompt.

### Installing Packages Into Your Environment

Inside the `cadd-env` environment, run this command:
```
conda install -c rdkit -c conda-forge jupyterlab pandas matplotlib rdkit chembl_webresource_client tqdm ipywidgets
```
This will install the following packages into the `cadd-env` environment:

 - [`jupyterlab`](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/execute.html), which allows you to create python notebooks. Notebooks are more flexible than python scripts, because you can add text and generate graphs directly inside of them.
 - [`pandas`](https://pandas.pydata.org/docs/) is the Python equivalent of Excel. It enables you to work with tables of data (or "dataframes").
 - [`matplotlib`](https://matplotlib.org/) is a plotting library for Python. The syntax is a little cumbersome, but it is very powerful and can create some very nice-looking plots.
 - [`rdkit`](https://www.rdkit.org/docs/) is a powerful chemistry library for Python, which enables you to visualize and structurally analyze different molecules.
 - [`chembl_webresource_client`](https://github.com/chembl/chembl_webresource_client) is a Python interface to the [ChEMBL database](https://www.ebi.ac.uk/chembl/) of bioactive molecules.

Additional minor packages included in the install command here are: `tqdm` for visualizing progress bars with long downloads; `ipywidgets` for making `tqdm` work in a Jupyter notebook.
You may also need to run the following command to enable widgets in Jupyter:
```
jupyter nbextension enable --py widgetsnbextension
```

Note that these packages are only available to you inside of your `cadd-env` environment.
You will need to activate it anytime you want to use them.


### Starting A Jupyter Notebook Session

To start a new Jupyter notebook session, simply type
```
jupyter notebook
```
This will open the Jupyterlab interface in your browser, where you can create new notebooks and run them.

To start a new Python 3 notebook, click "New" in the upper right and select "Notebook: > Python 3".

## Getting Started

To get started with the TeachOpenCADD tutorials, go [here](https://projects.volkamerlab.org/teachopencadd/talktorials.html).

You can find my notes and code for the tutorials in this repository, labeled `T001...ipynb`, `T002...ipynb`, etc.

I have also added the data for those tutorials to the `data` directory in this repository.

For those who are unfamiliar with Python, I would recommend going through the following tutorials alongside the TeachOpenCADD talktorials, to help you get caught up on what the Python is doing:

- [Python Data and Scripting for Biochemists](https://education.molssi.org/python-scripting-biochemistry/chapters/setup.html)
- [Scientific Data Visualization Using Python](https://education.molssi.org/python-visualization/chapters/setup.html)

If you want more, the MolSSI Institute has several good tutorials [here](http://education.molssi.org/resources.html), but the two above are the most directly relevant to CADD.
