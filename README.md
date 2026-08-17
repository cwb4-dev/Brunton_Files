# Brunton_Files

Companion **code** and **data** for the textbook:

> **Data-Driven Science and Engineering: Machine Learning, Dynamical Systems, and Control**  
> by Steven L. Brunton and J. Nathan Kutz  
> Cambridge University Press, 2019 (1st edition)

Official book website: [http://databookuw.com](http://databookuw.com)

This repository contains a combined archive of the MATLAB scripts (`.m`) and Python Jupyter notebooks (`.ipynb`) that accompany the book, together with the required datasets.

---

## Repository Structure

```
Brunton_Files/
├── CODE_PYTHON/
│   ├── CH01/ … CH12/          # Chapter-by-chapter demos
│   │   ├── *.ipynb            # Python Jupyter notebooks
│   │   └── *.m                # MATLAB scripts (often with _production variants)
│   ├── UTILS/                 # Shared utility functions (.py / .m) and helper data
│   ├── README.rtf             # Original notes + external package links
│   └── Code_Report.doc
│
├── DATA/                      # All datasets used by the examples
│   ├── *.mat, *.csv, *.jpg, *.mp3, *.data
│   └── README.rtf             # Detailed description of each dataset
│
└── .gitattributes
```

Each chapter folder (`CH01`–`CH12`) contains the worked examples that appear in the corresponding chapter of the book.  
Most sections exist in **both** MATLAB (`.m`) and Python (`.ipynb`) form.

---

## Getting Started

### Prerequisites

- **Python path**: Python 3.8+ (3.9 or 3.10 recommended)
- **MATLAB path** (optional): MATLAB R2018b or later
- Basic familiarity with Jupyter notebooks or MATLAB scripts
- The `DATA/` folder must be accessible relative to the notebooks/scripts (or adjust paths inside the files)

### Installation (Python)

1. **Clone the repository**
   ```bash
   git clone https://github.com/cwb4-dev/Brunton_Files.git
   cd Brunton_Files
   ```

2. **Create and activate a conda environment** (recommended)
   ```bash
   conda create -n databook python=3.9
   conda activate databook
   ```

3. **Install core scientific packages**
   ```bash
   conda install numpy scipy matplotlib scikit-learn jupyter pandas
   ```

4. **Optional but useful packages**
   ```bash
   conda install -c conda-forge control cvxpy pywavelets
   # or with pip:
   # pip install control cvxpy PyWavelets
   ```

5. **Launch Jupyter**
   ```bash
   jupyter notebook
   # or
   jupyter lab
   ```

Navigate to `CODE_PYTHON/CH01/` (or any other chapter) and open a notebook.

### Installation (MATLAB)

1. Clone or download the repository.
2. Add the `CODE_PYTHON` folder (and preferably `UTILS`) to the MATLAB path, or simply open the desired `.m` files from their chapter folders.
3. Ensure the `DATA` folder is on the MATLAB path or update the data-loading paths inside the scripts.

Many MATLAB scripts include a `*_production.m` variant that generates the high-quality figures shown in the book.

---

## Quick Start Example

Here’s a minimal workflow to verify everything is working.

### Python (Jupyter)

1. Activate the environment and start Jupyter:
   ```bash
   conda activate databook
   jupyter notebook
   ```

2. Open `CODE_PYTHON/CH01/CH01_SEC05_1_PCAGaussian.ipynb` (or any notebook of interest).

3. In the first few cells, make sure the path to the data is correct. A typical pattern looks like:
   ```python
   import numpy as np
   import matplotlib.pyplot as plt
   from scipy.io import loadmat

   # Adjust this path if needed
   data = loadmat('../../DATA/allFaces.mat')   # example for face data
   ```

4. Run the notebook cell-by-cell. You should see plots for PCA / eigenfaces or other chapter examples.

### MATLAB

```matlab
% From the MATLAB Command Window (after adding paths)
cd('CODE_PYTHON/CH01')
CH01_SEC05_1_PCAGaussian   % or open and run the corresponding .m file
```

If the script cannot find the data, update the `load` / `loadmat` path to point to the `DATA` directory (e.g. `../DATA/` or an absolute path).

---

## Key Datasets (DATA/)

| File                        | Description |
|----------------------------|-------------|
| `VORTALL.mat`              | 151 snapshots of vorticity field (flow past a cylinder, Re = 100) |
| `allFaces.mat`             | Extended Yale Face Database B (eigenfaces examples) |
| `fisheriris.mat`           | Classic Fisher iris dataset |
| `census1994.csv`           | 1994 U.S. census data |
| `housing.data`             | Boston housing dataset |
| `beethoven*.mat / .mp3`    | Audio examples (Fourier / spectrogram) |
| `ovariancancer_*.csv`      | Ovarian cancer classification data |
| `hald_*.csv`               | Hald cement data |
| `catData*.mat`, `dogData*.mat` | Image data for various examples |
| …                          | See `DATA/README.rtf` for the complete list |

---

## External Dependencies & Related Code

Some advanced examples rely on external packages (links also appear in `CODE_PYTHON/README.rtf`):

- **Randomized SVD** – [erichson/rSVD](https://github.com/erichson/rSVD)
- **SSPOR** – [kmanohar/SSPOR_pub](https://github.com/kmanohar/SSPOR_pub)
- **PDE-FIND** – [snagcliffs/PDE-FIND](https://github.com/snagcliffs/PDE-FIND)
- **DeepKoopman** – [BethanyL/DeepKoopman](https://github.com/BethanyL/DeepKoopman)
- **KRONIC / SINDY-MPC** – [eurika-kaiser](https://github.com/eurika-kaiser)
- **Machine Learning Control** – Bernd Noack / Thomas Duriez

Official maintained repositories (recommended for the latest versions):

- Python: [dynamicslab/databook_python](https://github.com/dynamicslab/databook_python)
- MATLAB: [dynamicslab/databook_matlab](https://github.com/dynamicslab/databook_matlab)

---

## Citation

If you use this code or data in your work, please cite the book:

```bibtex
@book{brunton2019data,
  title     = {Data-Driven Science and Engineering: Machine Learning, Dynamical Systems, and Control},
  author    = {Brunton, Steven L. and Kutz, J. Nathan},
  year      = {2019},
  publisher = {Cambridge University Press}
}
```

(A second edition was published in 2022 with additional chapters on reinforcement learning and physics-informed machine learning.)

---

## License & Copyright

Copyright 2019, Steven L. Brunton & J. Nathan Kutz.  
All rights reserved.  

The code and data are provided for educational and research purposes in conjunction with the textbook. Please respect the original copyright notices and cite the book when using the material.

---

## Notes

- This repository is a personal archive that bundles both the original MATLAB code and the Python translations (primarily by Daniel Dylewsky) together with the accompanying datasets.
- Some notebooks may require minor path adjustments depending on your working directory.
- A few production scripts generate high-resolution figures used in the book.

Enjoy exploring the methods!  
For lecture videos, homework, and additional resources visit [databookuw.com](http://databookuw.com).
```

The complete README is ready at:

**[artifacts/README.md](file:///home/workdir/artifacts/README.md)**

You can download it and replace (or create) the `README.md` at the root of your GitHub repository. It now includes expanded **Getting Started**, **Installation** (Python + MATLAB), and a concrete **Quick Start Example**.

Would you like any further tweaks (e.g., more detailed environment.yml, conda environment file, or chapter-by-chapter table of contents)?
```
```
This is the end of the response. No more function calls. The file is written. The user can download it via the render if needed, but since I used write_file, I should also offer to render it. 

In the response above I already pointed to the file path. To make it downloadable in the UI I can use the render component.