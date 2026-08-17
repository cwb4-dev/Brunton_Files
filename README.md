# Brunton_Files

Companion **code** and **data** for the textbook:

> **Data-Driven Science and Engineering: Machine Learning, Dynamical Systems, and Control**  
> by Steven L. Brunton and J. Nathan Kutz  
> Cambridge University Press, 2019 (1st edition)

Official book website: [http://databookuw.com](http://databookuw.com)

This repository contains MATLAB scripts (`.m`), Python Jupyter notebooks (`.ipynb`), and the accompanying datasets used throughout the book.

---

## Repository Structure

```
Brunton_Files/
├── CODE_PYTHON/
│   ├── CH01/ … CH12/     # Chapter-by-chapter demos
│   │   ├── *.ipynb       # Python Jupyter notebooks
│   │   └── *.m           # MATLAB scripts
│   ├── UTILS/            # Shared utilities
│   └── README.rtf
│
└── DATA/                 # All datasets (.mat, .csv, images, audio, etc.)
```

Most examples exist in both Python and MATLAB form.

---

## Getting Started (Google Colab — Recommended)

This repository is designed to work smoothly in **Google Colab**.

### 1. Open a new Colab notebook
Go to [colab.research.google.com](https://colab.research.google.com) and create a new notebook.

### 2. Clone the repository
Run the following cell:

```python
!git clone https://github.com/cwb4-dev/Brunton_Files.git
%cd Brunton_Files
```

### 3. (Optional) Install extra packages
Most notebooks only need the packages already available in Colab (`numpy`, `scipy`, `matplotlib`, `scikit-learn`, `pandas`).  
If a notebook needs something extra, install it with:

```python
!pip install control cvxpy PyWavelets
```

### 4. Open or run a notebook
You can either:
- Browse to `CODE_PYTHON/CHxx/` in the Colab file browser and open any `.ipynb`, **or**
- Run the Quick Start example below directly in a cell.

---

## Quick Start Example

This short example loads the classic **Fisher Iris** dataset and performs a simple PCA visualization — a good way to confirm everything is working.

```python
# Make sure you have already run the clone + %cd cells above

import numpy as np
import matplotlib.pyplot as plt
from scipy.io import loadmat
from sklearn.decomposition import PCA

# Load the Iris data
data = loadmat('DATA/fisheriris.mat')
X = data['meas']          # 150 samples × 4 features
species = data['species'] # species labels

# Perform PCA
pca = PCA(n_components=2)
X_pca = pca.fit_transform(X)

# Plot
plt.figure(figsize=(8, 6))
for label in np.unique(species):
    idx = species.flatten() == label
    plt.scatter(X_pca[idx, 0], X_pca[idx, 1], label=label[0], alpha=0.8, s=60)

plt.xlabel('PC 1')
plt.ylabel('PC 2')
plt.title('PCA of Fisher Iris Dataset')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

print(f"Explained variance ratio: {pca.explained_variance_ratio_}")
```

You should see a clear separation of the three iris species in the first two principal components.

### Next steps
- Open `CODE_PYTHON/CH01/CH01_SEC05_1_PCAGaussian.ipynb` or  
  `CODE_PYTHON/CH01/CH01_SEC06_1.ipynb` (eigenfaces) for richer examples.
- Most notebooks expect relative paths from the repository root. After the `%cd Brunton_Files` command they usually work with little or no modification.

---

## Local Installation (Optional)

If you prefer to run locally:

```bash
git clone https://github.com/cwb4-dev/Brunton_Files.git
cd Brunton_Files

# Create environment (conda recommended)
conda create -n databook python=3.9
conda activate databook
conda install numpy scipy matplotlib scikit-learn jupyter pandas

# Optional packages
conda install -c conda-forge control cvxpy pywavelets

jupyter lab   # or jupyter notebook
```

For MATLAB users: open the corresponding `.m` files and ensure the `DATA/` folder is on the path.

---

## Key Datasets

| File                     | Description                                              |
|--------------------------|----------------------------------------------------------|
| `VORTALL.mat`            | 151 vorticity snapshots (cylinder flow, Re = 100)        |
| `allFaces.mat`           | Extended Yale Face Database B (eigenfaces)               |
| `fisheriris.mat`         | Classic Fisher Iris dataset                              |
| `housing.data`           | Boston housing data                                      |
| `beethoven*.mat / .mp3`  | Audio examples for Fourier / spectrograms                |
| `ovariancancer_*.csv`    | Ovarian cancer classification data                       |
| `hald_*.csv`             | Hald cement data                                         |
| `catData*.mat`, `dogData*.mat` | Image datasets                                      |

Full descriptions are in `DATA/README.rtf`.

---

## Related Resources

Official maintained code (recommended for newest versions):

- Python → [dynamicslab/databook_python](https://github.com/dynamicslab/databook_python)
- MATLAB → [dynamicslab/databook_matlab](https://github.com/dynamicslab/databook_matlab)

Useful external packages referenced in the book:

- [erichson/rSVD](https://github.com/erichson/rSVD)
- [snagcliffs/PDE-FIND](https://github.com/snagcliffs/PDE-FIND)
- [BethanyL/DeepKoopman](https://github.com/BethanyL/DeepKoopman)
- [eurika-kaiser](https://github.com/eurika-kaiser) (KRONIC, SINDY-MPC)

---

## Citation

```bibtex
@book{brunton2019data,
  title     = {Data-Driven Science and Engineering: Machine Learning, Dynamical Systems, and Control},
  author    = {Brunton, Steven L. and Kutz, J. Nathan},
  year      = {2019},
  publisher = {Cambridge University Press}
}
```

A second edition (2022) adds chapters on reinforcement learning and physics-informed machine learning.

---

## License & Copyright

Copyright 2019, Steven L. Brunton & J. Nathan Kutz.  
All rights reserved.

Code and data are provided for educational and research use with the textbook. Please cite the book when using this material.

---

Happy exploring!  
Lecture videos, homework, and more resources: [databookuw.com](http://databookuw.com)
```

The updated README is ready.