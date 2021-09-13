# cadd-practice

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

Inside the `cadd-env` environment, run this command to install several packages into it:
```
conda install -c rdkit -c conda-forge jupyterlab pandas matplotlib rdkit chembl_webresource_client
```
This will install the following:

 - `jupyterlab`, which allows you to create python notebooks. Notebooks are more flexible than python scripts, because you can add text and generate graphs directly inside of them.
 - [`pandas`](https://pandas.pydata.org/docs/) is the Python equivalent of Excel. It enables you to work with tables of data (or "dataframes").
 - [`matplotlib`](https://matplotlib.org/) is a plotting library for Python. The syntax is a little cumbersome, but it is very powerful and can crate some very nice-looking plots.
 - [rdkit](https://www.rdkit.org/docs/) is a powerful chemistry library for Python, which enables you to visualize and structurally analyze different molecules.
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


