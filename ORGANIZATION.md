# Organization Reference

This document records the provenance of each notebook: where it came from, what it implements, why it was included, and what supporting files it needs.

## Classification Table

| Original Repository | Original File | Detected Topic | Destination Path | Classification Rationale | Required Supporting Files |
|---------------------|---------------|----------------|------------------|--------------------------|--------------------------|
| `assignment-2-ManikyaPant/` | `q2.ipynb` | K-Means Clustering (from scratch) | `probabilistic-models/kmeans/kmeans_clustering.ipynb` | Implements a complete `KMeans` class with `fit`, `predict`, `getCost`; performs elbow method and silhouette score analysis for optimal k selection | `Clustering_dataset(in).csv` |
| `assignment-2-ManikyaPant/` | `q3.ipynb` | Gaussian Mixture Model + EM (from scratch) | `probabilistic-models/gmm/gaussian_mixture_model.ipynb` | Implements a full `GMM` class with multivariate Gaussian PDF, E-step, M-step, `fit`, `predict`, log-likelihood tracking; uses BIC for model selection | `Clustering_dataset(in).csv` |
| `assignment-2-ManikyaPant/` | `q4.ipynb` | GMM Image Segmentation | `probabilistic-models/gmm/gmm_image_segmentation.ipynb` | Imports the GMM class from `q3` and applies it to satellite image segmentation; includes animated EM fitting visualization | `gaussian_mixture_model.ipynb` (cross-notebook import via `import_ipynb`), `satellite_1.png`, `satellite_2.png` |
| `assignment-2-ManikyaPant/` | `q5.ipynb` | PCA (from scratch) | `probabilistic-models/pca/pca_from_scratch.ipynb` | Implements `PCA` class with eigendecomposition, `fit`, `transform`, `inverse_transform`, `explained_variance`; demonstrated on MNIST digits | Uses `tensorflow.keras.datasets.mnist` (downloaded at runtime) |
| `assignment-5-ManikyaPant/` | `q1.ipynb` | Kernel Density Estimation (from scratch) | `probabilistic-models/kde/kernel_density_estimation.ipynb` | Implements `CustomKDE` class with Gaussian, triangular, and uniform kernels; Silverman bandwidth selection; applied to foreground detection | `kde_results.png` (pre-computed output). **Missing**: `data/Q1/back.jpg`, `data/Q1/Full.jpg` |
| `assignment-3-ManikyaPant/` | `q1.ipynb` | Neural Network Framework (from scratch) | `neural-networks/neural_network_framework.ipynb` | Complete NN framework in NumPy: ReLU/Tanh/Sigmoid activations, `Linear` layer with He init, `MSELoss`/`BCELoss`, forward/backward propagation, mini-batch SGD, gradient accumulation, early stopping; tested on XOR and border classification | `runs/` directory (training results: loss plots, saved models, predictions) |
| `assignment-3-ManikyaPant/` | `q2.ipynb` | Feature Mapping + NN Image Reconstruction | `neural-networks/feature_mapping_reconstruction.ipynb` | Self-contained NN (redefines layers, activations, losses); raw/polynomial/Fourier feature expansions for pixel-coordinate-to-color regression; animated training comparison GIFs | `cat_comparison_with_loss.gif`, `smiley_comparison_with_loss.gif`. **Missing**: `dataset/Q2/smiley.png`, `dataset/Q2/cat.jpg`, `dataset/Q2/blurred/` |
| `assignment-5-ManikyaPant/` | `q4.ipynb` | Variational Autoencoder (VAE) | `generative-models/variational_autoencoder.ipynb` | PyTorch VAE: encoder/decoder, reparameterization trick, ELBO loss; β-VAE experiments with β ∈ {0.1, 0.5, 1.0}; latent space PCA visualization; FID evaluation; generation with varying σ | `results/` directory (latent space plots, beta evolution GIF). Uses `torchvision.datasets.FashionMNIST` (downloaded at runtime) |

## Excluded Notebooks

| Original Repository | Original File | Detected Topic | Exclusion Reason |
|---------------------|---------------|----------------|------------------|
| `assignment-2-ManikyaPant/` | `q1.ipynb` | Linear/Polynomial Regression | Uses `sklearn.linear_model.LinearRegression`, `Lasso`, `Ridge` — not implemented from scratch; introductory regression exercise |
| `assignment-2-ManikyaPant/` | `q6.ipynb` | PCA + KNN Classification | Imports the from-scratch PCA, but the notebook's own contribution is using `sklearn.neighbors.KNeighborsClassifier` — no new from-scratch model |
| `assignment-2-ManikyaPant/` | `q7.ipynb` | Rotated MNIST Template Matching + Clustering | Applies PCA and K-Means to a rotated digit correction problem; interesting preprocessing but not a standalone ML model implementation |

## Cross-Notebook Dependencies

| Notebook | Import Statement | Resolution |
|----------|-----------------|------------|
| `probabilistic-models/gmm/gmm_image_segmentation.ipynb` | `from gaussian_mixture_model import GMM` (via `import_ipynb`) | Both `gaussian_mixture_model.ipynb` and `gmm_image_segmentation.ipynb` are placed in the same `gmm/` directory, preserving the relative import |

## Missing Data Files

These datasets were not present in the original repositories. The notebooks cannot be fully re-run without them, but pre-computed outputs are preserved.

| Notebook | Missing Path | Impact |
|----------|-------------|--------|
| `neural-networks/feature_mapping_reconstruction.ipynb` | `dataset/Q2/smiley.png`, `dataset/Q2/cat.jpg`, `dataset/Q2/blurred/blur_*.png` | Cannot re-run image reconstruction cells; output GIFs are preserved |
| `probabilistic-models/kde/kernel_density_estimation.ipynb` | `data/Q1/back.jpg`, `data/Q1/Full.jpg` | Cannot re-run KDE foreground detection; `kde_results.png` output is preserved |

## Notes

- `neural-networks/feature_mapping_reconstruction.ipynb` redefines its own neural network classes (`LinearLayer`, `Model`, activations, losses) — it does **not** import from `neural_network_framework.ipynb`. Both notebooks are self-contained.
- The `runs/` directory contains small training artifacts (~600 KB total): loss plots, saved weight files (`.npz`), prediction comparison images, and result JSON files.
- No notebook code was modified, rewritten, or refactored (except for fixing cross-imports between notebooks).
- No relative paths inside notebooks were changed.
