# ML Models — Implementations and Experiments

A collection of machine-learning models and algorithms implemented as part of coursework in statistical learning, neural networks, and generative modeling.

## Repository Structure

```
ml-models-from-scratch/
├── probabilistic-models/   # Clustering, density estimation, dimensionality reduction
├── neural-networks/         # Neural network framework and image reconstruction
├── generative-models/       # Variational Autoencoder experiments
├── ORGANIZATION.md          # Detailed provenance and classification of each notebook
└── requirements.txt         # Python dependencies
```

## Included Models

### Probabilistic Models

| Model | Notebook | Description |
|-------|----------|-------------|
| **K-Means Clustering** | [`probabilistic-models/kmeans/kmeans_clustering.ipynb`](probabilistic-models/kmeans/kmeans_clustering.ipynb) | K-Means implementation with elbow method and silhouette analysis for optimal cluster selection. Applied to a customer segmentation dataset. Achieved clustering performance on par with the scikit-learn equivalent. |
| **Gaussian Mixture Model (GMM)** | [`probabilistic-models/gmm/gaussian_mixture_model.ipynb`](probabilistic-models/gmm/gaussian_mixture_model.ipynb) | Full GMM with Expectation-Maximization: multivariate Gaussian PDF, E-step (responsibilities), M-step (parameter updates), log-likelihood tracking, and BIC-based model selection. Validated against scikit-learn's `GaussianMixture` and achieved identical clustering accuracy and likelihood scores. |
| **GMM Image Segmentation** | [`probabilistic-models/gmm/gmm_image_segmentation.ipynb`](probabilistic-models/gmm/gmm_image_segmentation.ipynb) | Applies the GMM implementation to satellite image segmentation, including animated visualization of the EM fitting process. |
| **Principal Component Analysis (PCA)** | [`probabilistic-models/pca/pca_from_scratch.ipynb`](probabilistic-models/pca/pca_from_scratch.ipynb) | PCA via eigendecomposition of the covariance matrix, with fit/transform/inverse-transform and explained variance computation. Demonstrated on MNIST. Produced matching explained variance ratios and reconstructed images as scikit-learn's PCA. |
| **Kernel Density Estimation (KDE)** | [`probabilistic-models/kde/kernel_density_estimation.ipynb`](probabilistic-models/kde/kernel_density_estimation.ipynb) | Custom KDE class supporting Gaussian, triangular, and uniform product kernels with Silverman bandwidth selection. Applied to foreground detection in images. |

### Neural Networks

| Model | Notebook | Description |
|-------|----------|-------------|
| **Neural Network Framework** | [`neural-networks/neural_network_framework.ipynb`](neural-networks/neural_network_framework.ipynb) | Modular neural network built with NumPy: activation functions (ReLU, Tanh, Sigmoid), fully connected layers with He initialization, MSE and BCE loss functions, forward/backward propagation, mini-batch gradient descent, and early stopping. Evaluated on XOR and border classification tasks, matching the convergence speed and accuracy of standard frameworks. |
| **Feature Mapping + Image Reconstruction** | [`neural-networks/feature_mapping_reconstruction.ipynb`](neural-networks/feature_mapping_reconstruction.ipynb) | Neural network for image reconstruction using raw, polynomial, and Fourier feature expansions of pixel coordinates. Compares reconstruction quality across feature mappings with animated training GIFs. |

### Generative Models

| Model | Notebook | Description |
|-------|----------|-------------|
| **Variational Autoencoder (VAE)** | [`generative-models/variational_autoencoder.ipynb`](generative-models/variational_autoencoder.ipynb) | VAE with encoder, reparameterization trick, and decoder built in PyTorch. Trained on FashionMNIST with ELBO loss (reconstruction + KL divergence). Achieved comparable ELBO scores and generation quality as standard benchmark models. Includes β-VAE experiments, latent space visualization, FID score evaluation, and generation with varying sampling variance. |

## Requirements

See [`requirements.txt`](requirements.txt) for the full list of Python dependencies.
