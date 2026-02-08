# 🧠 SAINT Protocol – fMRI-Guided DLPFC Targeting Pipeline

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)

This Jupyter Notebook implements the **SAINT (Stanford Accelerated Intelligent Neuromodulation Therapy)** protocol to identify an optimal left dorsolateral prefrontal cortex (DLPFC) target for transcranial magnetic stimulation (TMS), based on individual resting-state fMRI connectivity with the subgenual anterior cingulate cortex (sgACC).

The pipeline is **modular, reproducible**, and supports multiple correlation metrics (e.g., Pearson, Spearman, Kendall’s tau). All documentation, code, and visualizations are contained within this notebook.

➡️ **Open [`sanit.ipynb`](sanit.ipynb) to explore the full pipeline.**

---

## 🔢 Pipeline Overview

| Step | Name | Purpose |
|------|------|--------|
| **🧱 Step 0** | Environment Setup | Installs missing dependencies (`nibabel`, `plotly`, `kaleido`, etc.) |
| **🔬 Step 1** | Functional Parcellation | Parcellates left DLPFC and bilateral sgACC into functional subunits using hierarchical agglomerative clustering (HAC) |
| **🔍 Step 2** | Optimal Subunit Selection | Ranks DLPFC subunits by anticorrelation strength, spatial concentration, and cluster size |
| **🖼️ Step 3** | 3D Visualization | Renders the top DLPFC subunit as a smooth 3D mesh overlaid on anatomical context |

> ⚠️ **Execution Order Matters**:  
> Run **Step 1 → Step 2 → Step 3** in sequence. Each step depends on outputs from the previous one.

---

## 📂 Required Data Structure

Your data must be organized as follows:

your_base_directory/
└── Subjects/
├── sub1/
│ ├── filtered_func_data.nii.gz
│ ├── l_DLPFC_bin.nii.gz (or l_DLPFC_func.nii.gz)
│ └── sgACC_bin.nii.gz (or sgACC_func.nii.gz)
├── sub2/
│ ├── filtered_func_data.nii.gz
│ ├── l_DLPFC_bin.nii.gz
│ └── sgACC_bin.nii.gz
└── ...

