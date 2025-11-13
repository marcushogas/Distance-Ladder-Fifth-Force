# Data

This folder contains the machine-readable data underlying *“The paper.”*  
It includes both the proxy-field values used to model environmental effects and the distance-ladder data on which the calibration is based.

---

## Proxy-field data

The file **[`Table_I.txt`](/data/Table_I.txt)** provides the proxy-field values used in the analysis for all Cepheid and TRGB host galaxies across multiple cutoff radii $R_{\max}$.

Each entry corresponds to a galaxy and a chosen cutoff radius $R_{\max}$, with the following columns:

| Column | Description | Unit |
|---------|--------------|------|
| Field | Galaxy identifier | – |
| Phi_low, Phi_mean, Phi_high | Lower, mean, and upper bounds of log₁₀(\|Φ\|/c²) | dex |
| a_low, a_mean, a_high | Lower, mean, and upper bounds of log₁₀(\|a\|/(km s⁻²)) | dex |
| K_low, K_mean, K_high | Lower, mean, and upper bounds of log₁₀(\|K\|/cm⁻²) | dex |
| Rmax | Cutoff radius | Mpc |

These values characterize the large-scale-structure environment of each galaxy and are used to test for screened fifth-force effects in the hierarchical Bayesian recalibration of the distance ladder.

---

## SH0ES distance-ladder data

The SH0ES data form the empirical foundation for the Cepheid-based calibration of the Type Ia supernova distance scale.  
The version included here corresponds to the **fourth SH0ES data release**, originally published by:

- [Riess et al. (2022), *ApJL* 934, L7](https://iopscience.iop.org/article/10.3847/2041-8213/ac5c5b)  
- SH0ES data release repository: [PantheonPlusData GitHub](https://github.com/PantheonPlusSH0ES/DataRelease)

For convenience, we use a **reformatted version** of the same data provided in:

- [Högås et al. (2024), *MNRAS* 538, 883](https://academic.oup.com/mnras/article/538/2/883/8026895)  
- Reformatted dataset: [Cepheid-Distance-Ladder-Data GitHub](https://github.com/marcushogas/Cepheid-Distance-Ladder-Data)

The reformatted data preserve the original SH0ES content but are reorganized to facilitate direct use in alternative distance-ladder calibrations, including the analysis presented in this work.

---

## TRGB distance calibrations

Four TRGB distance measurements are included for comparison and cross-calibration.  
These values are taken from the following works:

- [Freedman et al. (2019), *ApJ* 882, 34](https://iopscience.iop.org/article/10.3847/1538-4357/ab2f73)  
- [Anand et al. (2022), *ApJ* 932, 15](https://iopscience.iop.org/article/10.3847/1538-4357/ac68df)  
- [Li et al. (2024), *ApJ* 976, 177](https://iopscience.iop.org/article/10.3847/1538-4357/ad84f3)  
- [Freedman et al. (2025), *ApJ* 985, 203](https://iopscience.iop.org/article/10.3847/1538-4357/adce78)

These TRGB calibrations provide an independent distance scale that complements the Cepheid-based SH0ES ladder.
