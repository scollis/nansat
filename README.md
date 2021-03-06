[![Build Status](https://travis-ci.org/nansencenter/nansat.svg?branch=master)](https://travis-ci.org/nansencenter/nansat)
[![Coverage Status](https://coveralls.io/repos/nansencenter/nansat/badge.svg?branch=master)](https://coveralls.io/r/nansencenter/nansat)
[![DOI](https://zenodo.org/badge/20132/nansencenter/nansat.svg)](https://zenodo.org/badge/latestdoi/20132/nansencenter/nansat)

![NANSAT](http://nansencenter.github.io/nansat/images/nansat_logo.png)

**Nansat** is a scientist friendly Python toolbox for processing 2D satellite earth observation data.

The main **goal** of Nansat is to facilitate:

* easy development and testing of scientific algorithms,
* easy analysis of geospatial data, and
* efficient operational processing.

We appreciate acknowledments of Nansat. Please add "The image analysis was performed with
the open-source NanSat (https://github.com/nansencenter/nansat) python package" (or equivalent)
if you use Nansat in scientific publications.

## Easy to install
The easiest way to install Nansat on a Linux machine is to use [anaconda](http://docs.continuum.io/anaconda/index)
```
# download the latest version of miniconda
wget http://repo.continuum.io/miniconda/Miniconda-latest-Linux-x86_64.sh -O miniconda.sh

# make it executable
chmod +x miniconda.sh

# install miniconda virtual environment
./miniconda.sh -b -f -p $HOME/miniconda

# deactivate existing packages
export PYTHONPATH=

# activate the environment
export PATH=$HOME/miniconda/bin/:$PATH

# install some requirements from common repositories
conda install -q --yes numpy scipy matplotlib nose pillow basemap netcdf4 proj.4

#install some requirements from NERSC repository
conda install -q --yes -c https://conda.anaconda.org/nersc nansat-gdal

# configure environment
export GDAL_DATA=$HOME/miniconda/share/gdal/
export GEOS_DIR=$HOME/miniconda/

# finally install Nansat
pip install https://github.com/nansencenter/nansat/archive/master.tar.gz

# run tests
nosetests nansat
```
Fore more information see [Install-Nansat](https://github.com/nansencenter/nansat/wiki/Install-Nansat) section or
use pre-configure virtual machines as explained on [Nansat-lectures](https://github.com/nansencenter/nansat-lectures)

## Easy to use
```Python
# download a test file
!wget https://github.com/nansencenter/nansat/raw/develop/nansat/tests/data/stere.tif

# import main file opener
from nansat import Nansat

# open a test file
n = Nansat('stere.tif')

# see file content
print n

# view file footpring
n.write_map('stere.footpring.png')

# create RGB with auto-stretched histogram
n.write_figure('stere_rgb.png', [1,2,3], clim='hist')
```
Fore more information see [Tutorial](https://github.com/nansencenter/nansat/wiki/Tutorial) or notebooks for [Nansat lectures](https://github.com/nansencenter/nansat-lectures/tree/master/notebooks)

### Acknowledgements
Development is supported by the Research Council of Norway as a part of [NORMAP](https://normap.nersc.no/) project (grant no. 195397/V30).
