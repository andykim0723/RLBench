# RLBench Windows
## Purpose
This repository is to support [RLBench](https://github.com/stepjam/RLBench) in Windows, mainly to enable building rlbench tasks.


## Install

First, install CoppeliaSim and PyRep following [this repository](https://github.com/tingelst/PyRep):
```bash
# download CoppeliaSim_PyRep
Invoke-WebRequest -uri "https://github.com/tingelst/PyRep/releases/download/windows-preview/CoppeliaSim_PyRep.zip" -Method "GET"  -Outfile "CoppeliaSim_PyRep.zip"
Expand-Archive CoppeliaSim_PyRep.zip
Remove-Item CoppeliaSim_PyRep.zip

# set environment variables
$env:COPPELIASIM_ROOT='EDIT/ME/PATH/TO/COPPELIASIM/INSTALL/DIR'
$env:LD_LIBRARY_PATH='$LD_LIBRARY_PATH:$COPPELIASIM_ROOT'
$env:QT_QPA_PLATFORM_PLUGIN_PATH='$COPPELIASIM_ROOT'

# create conda env
conda create -n rlbench python=3.8
conda activate rlbench

# install pyrep
cd .\CoppeliaSim_PyRep\PyRep\
python -m pip install -e .

# install rlbench
cd ..\..\
python -m pip install -e .

# install packages
pip install -r requirements.txt

# source setup.ps1
.\setup.ps1
```


And that's it!

### Task Builder

```bash
python .\tools\task_builder.py
```

