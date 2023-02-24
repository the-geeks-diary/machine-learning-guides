# Linear Programming in Python using PuLP - Part 1

In this guide we are exploring the basics of Linear Programming with a practical example using [Python](https://www.python.org/downloads/release/python-3100/) and [PuLP](https://coin-or.github.io/pulp/). 

For a step by step walkthough of the code in this guide please visit [my blog post]().

### Pre-requisites

Please make sure that you have the following pre-requisites installed

1. [Miniconda](https://docs.conda.io/en/latest/miniconda.html)
2. ```xcode-select --install``` (if you are on mac)
3. ```conda install -y jupyter```
4. ```conda deactivate```

### Environment Setup

### Setup new environment

Run the following commands

```bash
conda env create -f environment.yml -n optimization-python-pulp
conda activate optimization-python-pulp
conda deactivate
conda activate optimization-python-pulp
python -m ipykernel install --user --name optimization-python-pulp --display-name "Python 3.10 (optimization-python-pulp)"
jupyter notebook
```
