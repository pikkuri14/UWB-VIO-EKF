# Localization

## Introduction

This library is based out of [kamalshadi/Localization](https://github.com/kamalshadi/Localization).

This fork has the same 2D/3D implementations but aim (not done yet) to provide a 2.5D implementation with one or more axis fixed.

## Installation

The package has been tested with python2.7 and python3.6. Use pip to install the package:

```bash
# required libraries:
pip install numpy scipy
pip install multilateration
# or before being published on Pypi;
sudo -H python setup.py install
# or for development
pip install -e .
```

## Usage

```python
import multilateration
from math import sqrt

P=multilateration.Project(goal=[None, None, 2.0]) # To fix that the resulting height should be 2 meters
# P=multilateration.Project() # for 3D, simply do not set a goal
P.add_anchor('anchor_A',(1,0,1))
P.add_anchor('anchor_B',(-1,0,1))
P.add_anchor('anchor_C',(1,1,1))

P.add_measure_id('anchor_A',sqrt(2))
P.add_measure_id('anchor_B',sqrt(2))
P.add_measure_id('anchor_C',sqrt(3))
print(P.solve())
```

## Changes from the [original library](https://github.com/kamalshadi/Localization)

The library has been cleaned:

- Remove unused dependencies
- Keep only the LSE method
- Removed all models and changed the usage. It will only be in 3D, with values we can fix with the goal, to allow 2.5D.
