# arfpy: Adversarial random forests <a href='https://bips-hb.github.io/arfpy/'><img src='docs/figures/logo.png' align="right" height="139" /></a>


## Introduction
This is a python implementation of adversarial random forests (ARFs) for density estimation and generative modelling. Adversarial random forests (ARFs) recursively partition data into fully factorized leaves, where features are jointly independent. The procedure is iterative, with alternating rounds of generation and discrimination. Data become increasingly realistic at each round, until original and synthetic samples can no longer be reliably distinguished. This is useful for several unsupervised learning tasks, such as density estimation and data synthesis. Methods for both are implemented in this package. ARFs naturally handle unstructured data with mixed continuous and categorical covariates. They inherit many of the benefits of RFs, including speed, flexibility, and solid performance with default parameters. 


## Installation
The `arfpy` package is available on [PyPI](https://pypi.org/project/arfpy/):
```bash
$ pip install arfpy
```
To install the development version from GitHub, run:
```bash
git clone https://bips-hb.github.io/arfpy/
python setup.py install
```
We recommend to use `python>=3.8` with `pandas==1.4.0, numpy==1.21.0, scikit-learn==0.24.0` and `scipy==1.7.1`, see [requirements.txt](https://github.com/bips-hb/arfpy/blob/master/requirements.txt) for more details. 

## Usage
Using Fisher's iris dataset, we train an ARF, estimate distribution parameters and generate new data:

```python

from sklearn.datasets import load_iris
from arfpy import arf
import pandas as pd

# Load data
iris = load_iris() 
df = pd.DataFrame(iris['data'], columns=iris['feature_names'])

# Train the ARF
my_arf = arf.arf(x = df)

# Get density estimates
my_arf.forde()

# Generate data
my_arf.forge(n = 10)

```
For a detailed documentation on `arfpy`'s functionalities, please have a look at this [website](https://bips-hb.github.io/arfpy/). 

## Other distributions
An R implementation of ARF is available on [CRAN](https://cran.r-project.org/web/packages/arf/index.html). For the development version, see [here](https://github.com/bips-hb/arf/).

## Contributing
If you'd like to contribute,  please open an issue or submit a pull request. For further questions, please don't hesitate to write an email to Kristin Blesch (blesch@leibniz-bips.de). 

## References
* Watson, D. S., Blesch, K., Kapar, J. & Wright, M. N. (2023). Adversarial random forests for density estimation and generative modeling. In *Proceedings of the 26th International Conference on Artificial Intelligence and Statistics*. Link [here](https://proceedings.mlr.press/v206/watson23a.html).
