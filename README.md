# Distance-Ladder-Fifth-Force

Machine-readable data and analysis files accompanying the study  
**“The paper.”**

This repository provides the proxy-field values, supporting scripts *(optional)*, and related materials *(optional)* used in the hierarchical Bayesian recalibration of the Cepheid–TRGB distance ladder under screened modified-gravity models. The data enable independent verification and reuse of the environmental proxy fields employed in the paper.

---

## Contents

- **[data/](/data/)** — Machine-readable tables of proxy-field values (`Table_I.txt`) for Cepheid and TRGB host galaxies across five cutoff radii $R_{\max} = \{0.4, 1.4, 5.1, 18.1, 50\} \mathrm{Mpc}$.
- **code/** *(optional)* — Python script for calibrating the distance ladder
- **figures/** *(optional)* — Selected plots or figure data used in the paper
- **results/** *(optional)* — Posterior samples or summary statistics produced in the analysis

---

## Overview

This work investigates whether screened fifth forces—possible deviations from General Relativity active in low-density environments—could influence the calibration of the local distance ladder. Using environmental proxy fields for the external gravitational potential ($\Phi$), acceleration ($a$), and curvature ($K$), we recalibrate the Cepheid–TRGB distance ladder within a hierarchical Bayesian framework and quantify the resulting impact on the inferred Hubble constant.

The proxy-field values ($\Phi, a, K$) represent large-scale-structure environments of galaxies hosting Cepheids and TRGB stars.  
They are derived from external potential, acceleration, and curvature maps following the *screened fifth-force* formalism used to test departures from General Relativity.

---

## Usage

All tables are distributed as plain text files readable by standard tools.

Example (Python):
```python
import pandas as pd
df = pd.read_csv("data/machine_readable_Table1_proxy_fields.txt", sep="\t", comment="#")
