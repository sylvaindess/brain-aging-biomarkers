# Brain Aging Biomarkers

## Project Overview

This repository contains code and data processing pipelines focused on identifying and analyzing biomarkers related to brain aging and neurodegenerative diseases such as Alzheimer's. The primary dataset used is the [OASIS MRI dataset](https://sites.wustl.edu/oasisbrains/), alongside metadata from ADNI and other sources.

The goal is to extract meaningful imaging biomarkers—such as hippocampal volume—and explore their correlations with aging and cognitive decline. This project combines neuroimaging analysis with machine learning to support early detection and a deeper understanding of neurodegeneration.

## Contents
- Data preprocessing scripts using nibabel and nilearn  
- Biomarker extraction pipelines  
- Statistical and visualization analyses correlating biomarkers with age  
- Initial machine learning classification models on imaging data  
- Documentation and blog posts related to project progress  

## Getting Started

- Clone the repository  
- Set up the Python environment with required libraries:

### Option 1 – venv + pip

```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### Option 2 – Conda (recommended for scientific workflows)
```bash
conda env create -f environment.yml
conda activate brain-age

```

- Download the OASIS MRI dataset (link in documentation)  
- Follow the preprocessing and analysis notebooks

### Requirements
|Package|Purpose|
|-|-|
|numpy, pandas|	Core data manipulation|
|matplotlib, seaborn|	Visualizations and plots|
|scikit-learn|	ML models, stats, preprocessing|
|nibabel, nilearn|	Neuroimaging: reading & analyzing .nii files|
|jupyter|	For running notebooks cleanly|

## 🔐 Data Access

This repository contains **code only**.

To run the full pipeline, you must first request access to the [OASIS dataset](https://www.oasis-brains.org/)

Please ensure you follow the terms of their Data Use Agreement.  
No raw data or subject-level outputs are provided or distributed here.

### On Datasets

Our main study uses the OASIS-3 dataset. However, to begin development and testing, we are starting with:

**OASIS-1:**

1. Demographic and Clinical Data  
Includes a CSV file with demographic and clinical information — essential for linking imaging data to subjects’ age, diagnosis, cognitive scores, etc.
Optionally, the Cross-sectional Fact Sheet provides an overview of the dataset.

2. Raw Image Data  
The files oasis_cross-sectional_disc1.tar.gz through oasis_cross-sectional_disc12.tar.gz contain the raw T1-weighted MRI scans needed for analysis.
You do not need to download all files at once; starting with discs 1 and 2 is usually sufficient to obtain a representative sample.

3. FreeSurfer Data (optional)  
These are processed outputs containing structural segmentations and volumetric measurements (including hippocampus volumes).
Each file is large (~9.5 GB), but can save preprocessing time if you want to work with ready-to-use segmentations.
If you prefer to build your pipeline starting from raw scans, focus on downloading the raw image data first. FreeSurfer data can be downloaded later for validation or alternative analysis.

### Loading Datasets

Your notebook will need to access the data by referencing the full absolute path on your drive.

I recommend to use an environment variable for the data base path, so the code stays portable and config-free in the repo.

Example:

```
import os

base_data_path = os.getenv('OASIS_DATA_PATH')
nii_path = os.path.join(base_data_path, '<OASIS_DISC_FOLDER>', '<DISC_SUBFOLDER>', '<SUBJECT_FOLDER>', 'RAW', '<FILENAME>.hdr')

img = nib.load(nii_path)
```

Then, set that env var on your machine before running the notebook:

```bash
# Linux/macOS shells (like Bash or Zsh).
export OASIS_DATA_PATH=/mnt/external_drive/oasis_raw
```

```powershell
# PowerShell
$Env:OASIS_DATA_PATH="D:\path\to\data"
```

You could also use a config file (like `config.json` or `.env`) that you will put in .gitignore and which stores local paths.

```python
import os
import nibabel as nib

base_path = os.getenv('OASIS_DATA_PATH')
if not base_path:
    raise EnvironmentError('Please set the OASIS_DATA_PATH environment variable')

hdr_file = os.path.join(base_path, 'oasis_cross-sectional_disc1', 'disc1', 'OAS1_0001_MR1', 'RAW', 'your_file.hdr')
img = nib.load(hdr_file)
print(img.shape)
```

## Future Work

- Expand biomarker extraction methods
- Integrate additional datasets (e.g., ADNI)
- Develop machine learning models for early cognitive decline prediction
- Incorporate NLP analysis for clinical text mining

## License

This project is for personal research and portfolio development. No license granted for commercial use.