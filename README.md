# cadd-practice

These are some notes for beginners on getting set up to start doing computer-aided drug design (CADD) research, based on the Volkamer Lab's excellent collection of [talktorials](https://projects.volkamerlab.org/teachopencadd/talktorials.html).

## Setting Up

### Starting from Windows

Starting from a Windows machine, you will need to follow [these instructions](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) to get a working Linux terminal. Follow the instructions to install the "Ubuntu" app and then open it. This will open an [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu)-flavored [Linux](https://en.wikipedia.org/wiki/Linux_distribution) terminal, which is where you will do all of your work.

Upon opening the newly installed Ubuntu app, you will be prompted to create a username and password. You will need this password to run any commands requiring "superuser" permissions (commands starding with "sudo").

What you have just installed is an Ubuntu operating system -- sort of like a separate computer within your computer -- which you are accessing through a Linux (also known by the broader term "Unix") [terminal](https://en.wikipedia.org/wiki/Computer_terminal). Different terminals have different languages that are used to enter terminal commands. This one uses the [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) command language.

Before moving forward, you should change one setting in order to enable copy-pasting in your terminal:
1. Click the orange Ubuntu icon in the upper left corner of your terminal window.
2. Click "Properties"
3. Check the box that says "Ctrl+Shift+C/V as Copy/Paste".

To get started, enter the following Bash terminal command:
```
echo "HELLO WORLD"
```
You should see that it prints `"HELLO WORLD"` to your screen. You can learn more terminal commands from [this tutorial](https://linuxjourney.com/lesson/the-shell).

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

### Installing Conda

You can find the appropriate installer [here](https://docs.conda.io/en/latest/miniconda.html).

### Creating Your Environment

Then create an environment called `cadd-env`, which is where you will install all of your software.
You can create this environment as follows:
```
conda create -n cadd-env python=3
```
This creates an environment called `cadd-env` that uses version 3 of the [Python programming language](https://docs.python.org/3/).

To activate the environment you just created, you will then use:
```
conda activate cadd-env
```

### Installing Packages Into Your Environment

Inside the `cadd-env` environment, run this command:
```
conda install -c rdkit -c conda-forge jupyterlab pandas matplotlib rdkit chembl_webresource_client tqdm ipywidgets
```
This will install the following packages into the `cadd-env` environment:

 - [`jupyterlab`](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/execute.html), which allows you to create python notebooks. Notebooks are more flexible than python scripts, because you can add text and generate graphs directly inside of them.
 - [`pandas`](https://pandas.pydata.org/docs/) is the Python equivalent of Excel. It enables you to work with tables of data (or "dataframes").
 - [`matplotlib`](https://matplotlib.org/) is a plotting library for Python. The syntax is a little cumbersome, but it is very powerful and can crate some very nice-looking plots.
 - [`rdkit`](https://www.rdkit.org/docs/) is a powerful chemistry library for Python, which enables you to visualize and structurally analyze different molecules.
 - [`chembl_webresource_client`](https://github.com/chembl/chembl_webresource_client) is a Python interface to the [ChEMBL database](https://www.ebi.ac.uk/chembl/) of bioactive molecules.

Additional minor packages included in the install command here are: `tqdm` for visualizing progress bars with long downloads; `ipywidgets` for making `tqdm` work in a Jupyter notebook.
You will also need to run the following command to enable widgets in Jupyter:
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
