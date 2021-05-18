# Python Installation

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
conda activate sims # activate the environment
pip install ase
```
### For Jupyter-book
NB: Bodged; using `pip` not `conda`.
```
conda create -n website pip
```
```
conda activate website # activate the environment
pip install jupyter-book sphinx-sitemap
```

## Using Minconda installation on windows
### Installation
Download [miniconda](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe).

See also [instructions to add entries to Windows Terminal](WinTerm.md).
