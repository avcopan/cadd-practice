# cadd-practice

These are some notes for beginners on getting set up to start doing computer-aided drug design (CADD) research, based on the Volkamer Lab's excellent collection of [talktorials](https://projects.volkamerlab.org/teachopencadd/talktorials.html).

## Setting Up

### Installing Conda

First, install Miniconda from [here](https://docs.conda.io/en/latest/miniconda.html).

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
conda install -c rdkit -c conda-forge jupyterlab pandas matplotlib rdkit chembl_webresource_client
```
This will install the following packages into the `cadd-env` environment:

 - [`jupyterlab`](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/execute.html), which allows you to create python notebooks. Notebooks are more flexible than python scripts, because you can add text and generate graphs directly inside of them.
 - [`pandas`](https://pandas.pydata.org/docs/) is the Python equivalent of Excel. It enables you to work with tables of data (or "dataframes").
 - [`matplotlib`](https://matplotlib.org/) is a plotting library for Python. The syntax is a little cumbersome, but it is very powerful and can crate some very nice-looking plots.
 - [`rdkit`](https://www.rdkit.org/docs/) is a powerful chemistry library for Python, which enables you to visualize and structurally analyze different molecules.
 - [`chembl_webresource_client`](https://github.com/chembl/chembl_webresource_client) is a Python interface to the [ChEMBL database](https://www.ebi.ac.uk/chembl/) of bioactive molecules.

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
