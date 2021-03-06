# <div align="left"><img src="img/rapids_logo.png" width="90px"/>&nbsp;cuML - GPU Machine Learning Algorithms</div>

**NOTE:** For the latest stable [README.md](https://github.com/rapidsai/cuml/blob/master/README.md) ensure you are on the `master` branch.

cuML is a suite of libraries that implement machine learning algorithms and mathematical primitives functions that share compatible APIs with other [RAPIDS](https://rapids.ai/) projects.

cuML enables data scientists, researchers, and software engineers to run
traditional tabular ML tasks on GPUs without going into the details of CUDA
programming. In most cases, cuML's Python API matches the API from
[scikit-learn](https://scikit-learn.org).

For large datasets, these GPU-based implementations can complete 10-50x faster
than their CPU equivalents. For details on performance, see the [cuML Benchmarks
Notebook](https://github.com/rapidsai/notebooks-extended/blob/master/intermediate_notebooks/benchmarks/cuml_benchmarks.ipynb).

As an example, the following Python snippet loads input and computes DBSCAN clusters, all on GPU:
```python
import cudf
from cuml.cluster import DBSCAN

# Create and populate a GPU DataFrame
gdf_float = cudf.DataFrame()
gdf_float['0'] = [1.0, 2.0, 5.0]
gdf_float['1'] = [4.0, 2.0, 1.0]
gdf_float['2'] = [4.0, 2.0, 1.0]

# Setup and fit clusters
dbscan_float = DBSCAN(eps=1.0, min_samples=1)
dbscan_float.fit(gdf_float)

print(dbscan_float.labels_)
```

Output:
```
0    0
1    1
2    2
dtype: int32
```

For additional examples, browse our complete [API
documentation](https://docs.rapids.ai/api/cuml/stable/), or check out our
introductory [walkthrough
notebooks](https://github.com/rapidsai/notebooks/tree/master/cuml). Finally, you
can find complete end-to-end examples in the [notebooks-extended
repo](https://github.com/rapidsai/notebooks-extended).


### Supported Algorithms
| Category | Algorithm | Notes |
| --- | --- | --- |
| **Clustering** |  Density-Based Spatial Clustering of Applications with Noise (DBSCAN) | |
|  | K-Means | |
| **Dimensionality Reduction** | Principal Components Analysis (PCA) | |
| | Truncated Singular Value Decomposition (tSVD) | Multi-GPU version available (CUDA 10 only) |
| | Uniform Manifold Approximation and Projection (UMAP) | |
| | Random Projection | |
| **Linear Models for Regression or Classification** | Linear Regression (OLS) | Multi-GPU available in conda CUDA 10 package and [dask-cuml](http://github.com/rapidsai/dask-cuml) |
| | Linear Regression with Lasso or Ridge Regularization | |
| | ElasticNet Regression | |
| | Logistic Regression | |
| | Stochastic Gradient Descent (SGD), Coordinate Descent (CD), and Quasi-Newton (QN) (including L-BFGS and OWL-QN) solvers for linear models  | |
| **Nonlinear Models for Regression or Classification** | Random Forest (RF) Classification | Initial preview version in cuML 0.8 | 
|  | K-Nearest Neighbors (KNN) | Multi-GPU with [dask-cuml](http://github.com/rapidsai/dask-cuml) <br> Uses [Faiss](https://github.com/facebookresearch/faiss) |
| **Time Series** | Linear Kalman Filter | |
---

More ML algorithms in cuML and more ML primitives in ml-prims are planned for
future releases, including: T-SNE, spectral embedding, spectral clustering,
support vector machines, and additional time series methods. Future releases
will also expand support for multi-node, multi-GPU algorithms.

## Installation

See [the RAPIDS Release
Selector](https://rapids.ai/start.html#rapids-release-selector) for the command
line to install either nightly or official release cuML packages via Conda or
Docker.

## Build/Install from Source
See the build [guide](BUILD.md).

## Contributing

Please see our [guide for contributing to cuML](CONTRIBUTING.md).

## Contact

Find out more details on the [RAPIDS site](https://rapids.ai/community.html)

## <div align="left"><img src="img/rapids_logo.png" width="265px"/></div> Open GPU Data Science

The RAPIDS suite of open source software libraries aim to enable execution of end-to-end data science and analytics pipelines entirely on GPUs. It relies on NVIDIA® CUDA® primitives for low-level compute optimization, but exposing that GPU parallelism and high-bandwidth memory speed through user-friendly Python interfaces.

<p align="center"><img src="img/rapids_arrow.png" width="80%"/></p>
