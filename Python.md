# Python

## Installing Miniconda
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```
On bash:
```
bash Miniconda3-latest-Linux-x86_64.sh
```
On zsh:
```
zsh Miniconda3-latest-Linux-x86_64.sh
```
In case if it is already installed using another shell and needs to be added to `.*rc` file:
```
<path/to/miniconda>/bin/conda init     # for bash
<path/to/miniconda>/bin/conda init zsh # for zsh
```

## Environments
Instruction: Install line by line
### Generic (materials) simulation environment
```
conda create -n sims python numpy scipy ipython matplotlib jupyterlab pandas
```
```
pip install ase
```
### For Jupyter-book
NB: Bodged; using `pip` not `conda`.
```
conda create -n website pip
```
```
pip install jupyter-book
```