# TBW

[![PyPI](https://img.shields.io/pypi/v/TBW)](https://pypi.org/project/TBW/)
[![Publish to PyPI](https://github.com/ramyamounir/TBW/actions/workflows/pypi_publish.yaml/badge.svg)](https://github.com/ramyamounir/TBW/actions/workflows/pypi_publish.yaml)

A wrapper to facilitate Tensorboard logging.

---

## Overview

### Documentation

Checkout the [documentation](https://ramymounir.com/docs/tbw/) of TBW to learn more details about how to use our codebase.

### Installation

```bash
pip install tbw # with pip from PyPI
pip install git+'https://github.com/ramyamounir/TBW' # with GitHub
```

### Usage

> Note: More examples available in the documentations

```python
import torch
from tbw import TBWrapper

wrapper = TBWrapper('logs') # path to logging directory
loss_writer = wrapper('scalar', 'loss')

for _ in range(10):
    loss_writer(torch.randn(1))

del wrapper
```

