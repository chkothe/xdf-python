[![Latest PyPI Release](https://img.shields.io/pypi/v/pyxdf)](https://pypi.org/project/pyxdf/)
[![Latest Conda Release](https://img.shields.io/conda/vn/conda-forge/pyxdf)](https://anaconda.org/conda-forge/pyxdf)
![Python 3.5+](https://img.shields.io/badge/python-3.5+-green.svg)
![License](https://img.shields.io/github/license/xdf-modules/xdf-python)

pyXDF
=====

pyXDF is a Python importer for [XDF](https://github.com/sccn/xdf) files.

## Sample usage

```
import pyxdf
import matplotlib.pyplot as plt
import numpy as np

data, header = pyxdf.load_xdf('test.xdf')
for stream in data: 
	y = stream['time_series'] 
	if isinstance(y, list): 
		for ts, marker in zip(stream['time_stamps'], y): 
			plt.axvline(x=ts, label=marker) 
	elif isinstance(y, np.ndarray): 
		plt.plot(stream['time_stamps'], y) 
	else: 
		raise RuntimeError('Unknown stream format') 
```

pyxdf.load

## Installation

The latest stable version can be installed with `pip install pyxdf`.

For the latest development version, use `pip install git+https://github.com/xdf-modules/xdf-Python.git`.

## For maintainers

A new release is automatically uploaded to PyPI. Therefore, as soon as a new release is created on GitHub (using a tag labeled e.g. `v1.16.2`), a PyPI package is created with the version number matching the release tag.
