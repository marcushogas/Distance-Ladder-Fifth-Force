# Distance-Ladder-Fifth-Force

Machine-readable data and analysis files accompanying the study  
**“The paper.”**

This repository provides all data required to reproduce the distance-ladder calibration presented in the paper, together with selected figures and result files.

---

## Overview

This work investigates whether screened fifth forces—possible deviations from General Relativity active in low-density environments—could influence the calibration of the local distance ladder. Using environmental proxy fields for the external gravitational potential ($\Phi$), acceleration ($a$), and curvature ($K$), we recalibrate the local distance ladder within a hierarchical Bayesian framework and quantify the resulting impact on the inferred Hubble constant.

---

## Contents

- **[data/](/data/)** — Machine-readable tables of proxy-field values for Cepheid and TRGB host galaxies across five cutoff radii $R_{\max} = \{0.4, 1.4, 5.1, 18.1, 50\} \mathrm{Mpc}$, together with the SH0ES distance-ladder data (fourth release) and four TRGB distance calibrations.
- **[figures/](/figures/)** — Posterior distributions of the fifth-force parameters for all datasets and model configurations
- **[results/](/results/)** — Summary statistics and diagnostics produced in the analysis
---

## Usage

All tables are distributed as plain text files readable by standard tools.

Example (Python):
```python
import pandas as pd
df = pd.read_csv("data/Table_I.txt", sep="\t", comment="#")
```
---

## Attribution
If you use the data or method presented in this work, please cite: 
> arXiv:251X.XXXXX

This repository compiles both original data products and external datasets gathered for reproducibility.  
If you make use of specific external components, please also cite the corresponding original sources:

- **SH0ES distance-ladder data:**  
  [Riess et al. (2022), *ApJL* 934, L7](https://iopscience.iop.org/article/10.3847/2041-8213/ac5c5b) — main SH0ES publication
  
  SH0ES data release: [PantheonPlusData GitHub](https://github.com/PantheonPlusSH0ES/DataRelease)
  
  Reformatted dataset used here: [Högås et al. (2024), *MNRAS* 528, 2](https://academic.oup.com/mnras/article/538/2/883/8026895), [Cepheid-Distance-Ladder-Data GitHub](https://github.com/marcushogas/Cepheid-Distance-Ladder-Data)

- **TRGB distance calibrations:**  
  [Freedman et al. (2019), *ApJ* 882, 34](https://iopscience.iop.org/article/10.3847/1538-4357/ab2f73)
  
  [Anand et al. (2022), *ApJ* 932, 15](https://iopscience.iop.org/article/10.3847/1538-4357/ac68df)
  
  [Li et al. (2024), *ApJ* 976, 177](https://iopscience.iop.org/article/10.3847/1538-4357/ad84f3)
  
  [Freedman et al. (2025), *ApJ* 985, 203](https://iopscience.iop.org/article/10.3847/1538-4357/adce78)    

