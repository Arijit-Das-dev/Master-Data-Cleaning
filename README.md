<div align="center">

# 🧹Master Data Cleaning

**A hands-on, well-documented reference for cleaning real-world datasets with Python**

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)](https://numpy.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?logo=scipy&logoColor=white)](https://scipy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?logo=plotly&logoColor=white)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0)](https://seaborn.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

</div>

---

## 📖 About

**Data Cleaning Tutorial** is a personal knowledge base that documents every method, technique, and concept I use to take a messy, real-world dataset and turn it into an analysis-ready one. Instead of scattering notes across notebooks, this repo organizes each cleaning technique into its own short, focused markdown doc — with an explanation of *why* it matters, the *steps* to follow, and *ready-to-use* Python code.

It's built to be two things at once:
- 📓 **A personal reference** I can return to whenever I clean a new dataset.
- 🎓 **A learning resource** for anyone starting out with data cleaning and exploratory data analysis (EDA) in Python.

---

## 📑 Table of Contents

- [About](#-about)
- [Repository Structure](#-repository-structure)
- [Libraries Used](#-libraries-used)
- [What's Covered](#-whats-covered)
- [Datasets](#-datasets)
- [Getting Started](#-getting-started)
- [Learning Resources](#-learning-resources)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [Author](#-author)

---

## 📂 Repository Structure

```
Data-Cleaning-Tutorial/
│
├── docs/                            # Core reference — one concept per file
│   ├── 1_import_libraries.md
│   ├── 2_explore_dataset.md
│   ├── 4_save_data.md
│   └── cleaning_methods/
│       ├── fixing_column_names.md
│       ├── fixing_individual_cols.md
│       ├── fixing_duplicates.md
│       ├── fixing_outliers.md
│       └── fixing_nulls/
│           ├── integer_type.md      # Strategy for numeric (int/float) nulls
│           └── object_type.md       # Strategy for text/categorical nulls
│
├── notebooks/                       # Full, applied walkthroughs
│   ├── airbnb_dataset.ipynb         # End-to-end cleaning of Airbnb listings data
│   └── marketing_dataset.ipynb      # End-to-end cleaning of a messy marketing dataset
│
├── data/
│   └── cleaned_airbnb.csv           # Output of the Airbnb cleaning notebook
│
├── LICENSE
└── README.md
```

The `docs/` folder is the heart of the repo — each file is self-contained, so you can jump straight to the technique you need. The `notebooks/` folder shows those same techniques applied end-to-end on real datasets.

---

## 🛠 Libraries Used

| Library | Purpose |
|---|---|
| **NumPy** | Numerical operations, handling `NaN` values, array-based logic |
| **Pandas** | Loading, exploring, transforming, and cleaning tabular data |
| **Statistics** | Core statistical measures (mean, median, mode) |
| **SciPy** | Statistical tests and distribution-based outlier/skewness checks |
| **Matplotlib** | Base plotting for distributions and visual QA |
| **Seaborn** | Boxplots, distribution plots, and visual outlier detection |

```python
import numpy as np
import pandas as pd
import statistics as stats
import scipy.stats as scipy_stats
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## ✅ What's Covered

- [x] **Importing & setting up** the essential data analysis libraries
- [x] **Exploring a dataset** — shape, `info()`, dtypes, `describe()`, missing values, duplicates, uniques
- [x] **Fixing column names** — case, whitespace, special characters, renaming
- [x] **Fixing individual columns** — detecting/removing unwanted characters, digits, spacing, casing issues
- [x] **Handling missing values**
  - Numeric (`int64` / `float64`) columns — mean vs. median strategy based on outlier presence
  - Object columns — mode imputation vs. `"unknown"` placeholder, based on missing %
- [x] **Detecting & fixing duplicates**
- [x] **Detecting & fixing outliers** — using the IQR (Interquartile Range) method
- [x] **Saving the cleaned dataset** back to CSV

Each doc follows the same simple pattern: **why it matters → steps to follow → code you can copy directly into your own project.**

---

## 📊 Datasets

The techniques above are applied end-to-end in the `notebooks/` folder using two real, messy datasets:

| Dataset | Notebook | Focus |
|---|---|---|
| **Airbnb Open Data** | `airbnb_dataset.ipynb` | Full pipeline — nulls, duplicates, outliers, column & text cleanup |
| **Marketing Campaign Data** | `marketing_dataset.ipynb` | Column/text cleanup and exploratory checks on a messy campaign dataset |

> 💡 The cleaned Airbnb output is saved in `data/cleaned_airbnb.csv` as a reference for what a fully cleaned dataset looks like.

---

## 🚀 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/Arijit-Das-dev/Data-Cleaning-Tutorial.git
   cd Data-Cleaning-Tutorial
   ```

2. **Install the required libraries**
   ```bash
   pip install numpy pandas scipy matplotlib seaborn
   ```

3. **Start exploring**
   - Read through `docs/` in order (1 → 2 → cleaning methods → save) for the concept-by-concept walkthrough.
   - Open the notebooks in `notebooks/` to see the same techniques applied to real datasets.

---

## 🎥 Learning Resources

These are the YouTube videos I personally learned from while building this repo — sharing them here so anyone following along has the same starting point:

1. 📺 [Data Cleaning Tutorial — Part 1](https://youtu.be/NeJKaolLQqU)
2. 📺 [Data Cleaning Tutorial — Part 2](https://youtu.be/P6D__CqOfqQ)
3. 📺 [Data Cleaning Tutorial — Part 3](https://youtu.be/WFaE-5zYHGo)
4. 📺 [Data Cleaning Tutorial — Part 4](https://youtu.be/ZX8vmcSTCrc)
5. 📺 [Data Cleaning Tutorial — Part 5](https://youtu.be/Y_s3hndYbB0)

> Watch them in order alongside the `docs/` folder for the best learning experience — theory in the videos, quick-reference code here.

---

## 🗺 Roadmap

- [ ] Add a dedicated doc for **skewness detection & treatment**
- [ ] Add a doc for **data type conversion best practices**
- [ ] Add a `requirements.txt` for one-command environment setup
- [ ] Add more real-world messy datasets and notebooks

---

## 🤝 Contributing

This repo is primarily a personal learning log, but suggestions, corrections, and improvements are always welcome:

1. Fork the repository
2. Create a new branch (`git checkout -b improve-outlier-doc`)
3. Commit your changes
4. Open a Pull Request

If you spot an error or have a cleaner way to explain a concept, feel free to open an issue too.

---

## 👤 Author

**Arijit Das**
, Data Analytics professional focused on data-driven problem solving and analytical solutions.

[![GitHub](https://img.shields.io/badge/GitHub-Arijit--Das--dev-181717?logo=github&logoColor=white)](https://github.com/Arijit-Das-dev)

---

<div align="center">

⭐ If this repo helped you understand data cleaning better, consider giving it a star!

</div>