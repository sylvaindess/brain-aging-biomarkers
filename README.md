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

```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
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

## Future Work

- Expand biomarker extraction methods
- Integrate additional datasets (e.g., ADNI)
- Develop machine learning models for early cognitive decline prediction
- Incorporate NLP analysis for clinical text mining

## License

This project is for personal research and portfolio development. No license granted for commercial use.