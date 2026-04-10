# ToFSIMS-depth-profiling-of-PSCs

![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue)
![License: MIT](https://img.shields.io/badge/license-MIT-green)
![Code: Publication-Ready](https://img.shields.io/badge/code-publication--ready-brightgreen)

## Overview

This repository contains the exported data and reproducible code for the manuscript:

> **Disentangling ion migration from artifacts in high-fidelity ToF-SIMS depth profiling of perovskite solar cells**
>
> *Nico Fransaert\*, Jean V. Manca, Shabnam Ahadzadeh, Bart Ruttens, Jan D'Haen, Dirk Valkenborg, Bart Cleuren, Bart Vermang, and Aslihan H. Babayigit\**
>
> *Joule* (2026)

### Research Summary

Time-of-flight secondary ion mass spectrometry (ToF-SIMS) is widely used for depth profiling in perovskite solar cell research, yet prone to misinterpretation. This work:

- Reveals **overlooked artifacts** that mimic ion migration in multilayer devices
- Establishes a **statistically validated framework** for high-fidelity depth profiling
- Uncovers **genuine interfacial chemistry** including self-assembled monolayer (SAM) redistribution
- Sets new standards for **nanoscale characterization** of hybrid semiconductors

The repository enables **complete reproduction** of all figures (main manuscript + supplemental) from exported ToF-SIMS depth profile data.

---

## What's Included

```
.
├── notebooks/
│   └── depth_profile_analysis.ipynb           ← Main analysis notebook
├── data/
│   ├── main/                                  ← Core ToF-SIMS exported measurements
│   │   ├── MAPI-stack/
│   │   ├── FACSPI-stack/
│   │   ├── MAPI-Au-peeling/
│   │   ├── MAPI-2PACz-dip-aging/
│   │   └── FACSPI-PbI2-treatment/
│   └── supplemental/                          ← Device architecture variants & controls
│       ├── MAPI-in-FACSPI-stack/
│       ├── FACSPI-in-MAPI-stack/
│       ├── MAPI-MeO-2PACz-add/
│       ├── varying-fluences-per-scan/
│       ├── frames-versus-seconds/
│       ├── shifted-maxima/
│       ├── cluster-sizes/
│       ├── reference-PCBM/
│       └── reference-spiro/
├── output/
│   └── figures/                               ← Generated outputs
│       ├── main/                              ← Figures 1-6
│       ├── supplemental/                      ← Figures S1-S14
│       └── misc/                              ← Additional analysis
├── misc/
│   └── representations/                       ← Supporting images (peeling diagram)
├── requirements.txt                           ← Python dependencies
└── README.md                                  ← This file
```

### Data Files

All ToF-SIMS data are provided as `.txt` files (tab-separated, one file per measurement). These are **exported from SurfaceLab 7.3** and include:
- **Header rows**: Signal names and mass-to-charge ratios (m/z)
- **Data rows**: Sputter time, ion dose, fluence, and intensity for 100+ ion signals
- **Measurements**: 50+ individual profiles across 10+ sample types

**Format**: Plain text

---

## Quick Start

### Option 1: Run in Google Colab (Easiest - No Setup!)

**For users without Python experience**: This option requires no installation. Everything runs in your browser.

1. **Click this link** (opens notebook in Colab):
   ```
   https://colab.research.google.com/github/X-LAB-UHasselt/ToFSIMS-depth-profiling-of-PSCs/blob/main/notebooks/depth_profile_analysis.ipynb
   ```

2. **In the notebook**, find cell 1 (titled "Google Colab Setup") and:
   - Change `RUN_COLAB_SETUP = False` → `RUN_COLAB_SETUP = True`
   - Click **Run cell** (▶ button on the left)
   - Wait for setup to complete and follow instructions

3. **Then simply run all remaining cells** (Ctrl+F9 or Runtime → Run all)

4. **View results**: Figures appear inline in the notebook; download if desired

---

### Option 2: Run Locally (For Development & Reproduction)

**Requirements**:
- Python 3.10 or higher
- Git (for cloning)
- <1 GB disk space (code + data)
- 5-10 minutes for first run (figures generation)

#### Step 1: Clone Repository

```bash
# Via HTTPS (no credentials needed)
git clone https://github.com/X-LAB-UHasselt/ToFSIMS-depth-profiling-of-PSCs.git
cd ToFSIMS-depth-profiling-of-PSCs

# Or via SSH (if you have SSH key configured)
git clone git@github.com:X-LAB-UHasselt/ToFSIMS-depth-profiling-of-PSCs.git
cd ToFSIMS-depth-profiling-of-PSCs
```

#### Step 2: Create Python Environment

We strongly recommend using a dedicated virtual environment to avoid dependency conflicts.

**Option A: Using venv (Python standard)**
```bash
# Create environment
python3 -m venv tof-sims-depth-profile

# Activate (macOS/Linux)
source tof-sims-depth-profile/bin/activate

# Activate (Windows)
tof-sims-depth-profile\Scripts\activate
```

**Option B: Using Conda** (if you have Anaconda installed)
```bash
conda create --name tof-sims-depth-profile python=3.10
conda activate tof-sims-depth-profile
```

**Option C: Using pyenv** (matches this repo's setup)
```bash
# Create version 3.10.5 in pyenv
pyenv install 3.10.5

# Create virtual environment
pyenv virtualenv 3.10.5 tof-sims-depth-profile

# Activate
pyenv activate tof-sims-depth-profile
```

#### Step 3: Install Dependencies

```bash
# Install all required packages
pip install -r requirements.txt

# Verify installation (optional)
pip list | grep -E "matplotlib|numpy|scipy"
```

#### Step 4: Open & Run Notebook

**Using Jupyter (installed via requirements.txt)**:
```bash
jupyter notebook notebooks/depth_profile_analysis.ipynb
```

**Using VS Code** (if you have it):
- Open folder in VS Code
- Click on the `.ipynb` file
- Select kernel (should auto-detect your venv)
- Click **Run All** or run cells individually

#### Step 5: View Results

- **Figures appear inline** in the notebook as you run cells
- **Saved outputs**: `output/figures/main/`, `/supplemental/`, `/misc/`
- **Execution time**: ~5-10 minutes for full notebook (depends on CPU)

---

## Notebook Structure

### `depth_profile_analysis.ipynb` (Main)

**Setup, Analysis and Figures**:

#### **Setup & Configuration**
- Environment initialization
- Google Colab setup (optional; enables browser-based execution)
- Imports (matplotlib, scipy, numpy)
- Matplotlib configuration
- Data loading utility function

#### **Main Figures**
| Figure | Description |
|--------|---------|
| **Figure 1** | ToF-SIMS foundational principle and PVK device architectures |
| **Figure 2** | MAPI Stack: archetypal n–i–p device architecture |
| **Figure 3** | FACSPI Stack: tin-lead p–i–n device architecture |
| **Figure 4** | MAPI/Au mechanical peeling experiment validates artifact source |
| **Figure 5** | Replicate analysis and statistical assessment: Control vs. PbI2-treated samples |
| **Figure 6** | SAM aging under ambient conditions |

#### **Supplemental Figures**
Analysis of special cases and validation:
| Figure | Description |
|--------|---------|
| **Figure S1** | Varying analysis and sputter fluences |
| **Figure S2** | Sputter-time-controlled depth profiling artifacts |
| **Figure S3** | Normalized profiles show displaced maxima |
| **Figure S4** | MAPI in FACSPI stack |
| **Figure S5** | FACSPI in MAPI stack |
| **Figure S6** | Comparison of pristine and peeled MAPI films |
| **Figure S7** | Operational framework for distinguishing genuine migration from artifacts |
| **Figure S8** | Region-based comparison of summed intensities |
| **Figure S9** | SAM introduced via additive method |
| **Figure S10** | AFM characterization for roughness estimation |
| **Figure S11** | Deconvolution analysis |
| **Figure S12** | Cluster size distribution |
| **Figure S13** | Reference Spiro-OMeTAD profiles |
| **Figure S14** | Reference PCBM profiles |

#### **Miscellaneous** 
Publication statistics (bibliometric motivation) tracks adoption of ToF-SIMS in perovskite research (2014-2025) using Google Scholar data.

---

## Reproducibility

### How to Verify Results

All figures can be exactly reproduced by running the notebook from top to bottom:

1. **Data integrity**: All `.txt` files are unchanged from original SurfaceLab exports
2. **Code determinism**: No randomness or stochastic algorithms
3. **Dependency versions**: Pinned in `requirements.txt` (frozen via `pip freeze`)
4. **Path independence**: All paths are relative; notebook works from any location
5. **Output locations**: Figures automatically save to `output/figures/` subdirectories

### Expected Output

Running the full notebook generates:
- **20 figure files** (PDF + PNG, 1200 DPI)
- **Statistical summaries** (printed to stdout: p-values, other reported values)
- **Data processing logs** (validation of loaded measurements)

**Execution time**: ~5-10 minutes

---

## Data & Code Availability

**Data**: All reported ToF-SIMS measurements (exported from SurfaceLab 7.3) are provided in this repository under the `data/` directory. The raw ToF-SIMS data used in this study is archived on Zenodo:
- DOI: [10.5281/zenodo.19489560](https://doi.org)
- Format: IONTOF proprietary (.itax, .itmx, .itm) and open-standard (.imzML).
- Size: ~38 GB compressed (requires ~320 GB uncompressed).

**Code**: This repository contains the complete analysis pipeline for reproducing all manuscript figures. The code is open-source and freely available for reuse and adaptation.

**Citation**: If you use this code or data, please cite both the manuscript and this code release.

---

## Technical Details

### Python Environment

```
Python 3.10.5+ (via pyenv venv, conda, or system Python)

Required Packages (see requirements.txt):
  - numpy          2.2.1+
  - scipy          1.15.1+
  - matplotlib     3.10.0+
  - ipython        8.31.0+
  - jupyter        (for local notebook server)
```

### Installation Notes

- **macOS/Linux**: Works out-of-the-box with system Python 3.10+
- **Windows**: Use WSL 2 (Windows Subsystem for Linux 2) for best compatibility
- **Google Colab**: Pre-installed dependencies; setup cell installs any missing packages

### Data Format

ToF-SIMS `.txt` files structure:
```
Row 1:  # Profile Smoothing is Disabled
Row 2:  Signal names (tab-separated)
Row 3:  Mass-to-charge ratios (m/z)
Row 4:  Column headers: Data Point, Sputter Time (s), Dose (ions), Fluence (ions/cm²), [100+ signals]
Row 5+: Numeric data
```

The notebook's `extract_depth_profile_txts_to_dataset()` function parses these into nested Python dictionaries for flexible analysis.

---

## Troubleshooting

### "ModuleNotFoundError: No module named 'scipy'"

**Cause**: Dependencies not installed

**Solution**:
```bash
# Ensure you're in the correct virtual environment, then:
pip install -r requirements.txt
```

### "Notebook kernel not found" (VS Code)

**Cause**: VS Code can't find Python interpreter

**Solution**:
1. Click "Select Kernel" in the notebook
2. Choose your venv/conda environment
3. If not listed, click "Python Environments" and find your venv path

### "FileNotFoundError: ../data/main/..."

**Cause**: Notebook run from wrong directory or paths changed

**Solution**:
- Ensure notebook is in `notebooks/` folder
- Run notebook from VS Code or `jupyter notebook` (not just `python`)
- Check paths in data loading cells start with `../data/`

### Google Colab: "git: command not found"

**Note**: Unlikely, but if it occurs:
```python
# In Colab cell:
!apt-get install -y git
```

### Figures not saving / "Permission denied"

**Cause**: `if False:` wraps figure save commands (disabled by default)

**Solution**:
- To enable: Change `if False:` → `if True:` in figure save cells
- Or create `output/figures/` subdirectories manually

---

## Contributing & Feedback

This repository is frozen for the publication. For questions or improvements, contact:

**Corresponding Authors**:
- Nico Fransaert (nico.fransaert@uhasselt.be & nicofransaert@gmail.com)
- Aslihan H. Babayigit (aslihan.babayigit@uhasselt.be)

---

## License

This code and data are provided under the **MIT License**. You are free to use, modify, and distribute for research and commercial purposes, with attribution.  

---

## Acknowledgments

This work was supported by:
- Research Foundation – Flanders (FWO) under mandate grant IDs 11K4324N, 1260022N, 1SA4523N and 1297525N
- BOF-UHasselt grant ID R-12384

---

## References

For detailed methodology, results, and context, see the accompanying manuscript:

> Fransaert et al. (2026). *Joule*. **Disentangling ion migration from artifacts in high-fidelity ToF-SIMS depth profiling of perovskite solar cells**

---

**Last Updated**: April 2026  
**Created By**: Nico Fransaert, X-LAB, Hasselt University
