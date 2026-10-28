# PCA Lab (`tp_pca.ipynb`)

A step-by-step implementation of **Principal Component Analysis (PCA)**, first from scratch with NumPy, then with scikit-learn, to check that both give the same result.

## Dataset

Grades of 6 students (S1 to S6) in 4 subjects: **Mathematics, Statistics, Programming, Algorithms**.

## Steps

**1. PCA from scratch (NumPy)**
1. Build the dataset and look at it with `describe()`
2. Standardize the data (mean 0, std 1)
3. Compute the covariance matrix of the standardized data
4. Compute the eigenvalues and eigenvectors with `np.linalg.eig`, sorted from largest to smallest
5. Keep the 2 eigenvectors with the largest eigenvalues (PC1, PC2)
6. Project the standardized data onto them
7. Compute the explained variance ratio and the cumulative variance

**2. PCA with scikit-learn**
1. `StandardScaler` to standardize
2. `PCA(n_components=2)` to fit and transform
3. Compare components, projections, and explained variance with the manual results

**3. Visualization**
Scatter plots of the data before and after PCA.

## Results

| Component | Explained variance | Cumulative |
|-----------|-------------------|------------|
| PC1 | ~93% | ~93% |
| PC2 | ~6% | ~99% |

- The 4 subjects are strongly correlated (correlation ≥ 0.77).
- **PC1** has roughly equal weights on all subjects, so it is the students' overall level.
- **PC2** contrasts Statistics against Programming.
- Two components keep about **99% of the information**, so the 4 columns can be reduced to 2.

## Manual vs sklearn

The principal components are identical. The projected values differ slightly (about 0.1 to 0.3) because the manual version standardizes with `data.std()` (divides by n−1), while `StandardScaler` divides by n.
