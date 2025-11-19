# Data

This folder contains the machine-readable data underlying *“The paper.”*  
It includes both the proxy-field values used to model environmental effects and the distance-ladder data on which the calibration is based.

---

## Proxy-field data

The file **[`Table_II.txt`](/data/Table_II.txt)** provides the proxy-field values across multiple cutoff radii $R_{\max}$.

Each entry corresponds to a galaxy and a chosen cutoff radius $R_{\max}$, with the following columns:

| Column | Description | Unit |
|---------|--------------|------|
| Field | Galaxy identifier | – |
| Phi_low, Phi_mean, Phi_high | Lower (68%), median, and upper (68%) bounds of log₁₀(\|Φ\|/c²) | dex |
| a_low, a_mean, a_high | Lower (68%), median, and upper (68%) bounds of log₁₀(\|a\|/(km s⁻²)) | dex |
| K_low, K_mean, K_high | Lower (68%), median, and upper (68%) bounds of log₁₀(\|K\|/cm⁻²) | dex |
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

The reformatted data (**[`C_R22.txt`](/data/C_R22.txt)**, **[`y_R22.txt`](/data/y_R22.txt)**, **[`L_R22.txt`](/data/L_R22.txt)**, **[`q_R22.txt`](/data/q_R22.txt)**) preserve the original SH0ES content but are reorganized to facilitate direct use in alternative distance-ladder calibrations, including the analysis presented in this work.

### Distance-ladder linear model (R22 files)

The `_R22` files contain the data from the fourth-iteration SH0ES calibration [(Riess et al. 2022)](https://iopscience.iop.org/article/10.3847/2041-8213/ac5c5b), formatted for use in the linear model  
$y = Lq$  
with covariance matrix $C$.

- **[`y_R22.txt`](/data/y_R22.txt)** – data vector $y$ with a source label and value for each row.  
- **[`C_R22.txt`](/data/C_R22.txt)** – covariance matrix $C$, ordered consistently with `y_R22.txt`.  
- **[`L_R22.txt`](/data/L_R22.txt)** – design matrix $L$; rows match `y_R22.txt` and columns match `q_R22.txt`.  
- **[`q_R22.txt`](/data/q_R22.txt)** – parameter names defining the components of $q$.

Using these four files you can reproduce the **standard SH0ES calibration** (without fifth-force corrections) by solving the generalized least-squares problem  
$q_{\rm ML} = (L^{\mathsf T} C^{-1} L)^{-1} (L^{\mathsf T} C^{-1} y)$,  
from which  
$H_0 = 10^{q_{\rm ML}(\texttt{5logH0})/5}$.

A minimal Python example:

```python
import numpy as np

# y: second column ("Data") from y_R22.txt
names = ('Source', 'Data')
dtype = {'names': names, 'formats': ('U30', 'f8')}
y_tab = np.loadtxt("data/y_R22.txt", skiprows=1, dtype=dtype)
y = y_tab['Data']

# C: covariance; L: design matrix; q_names: parameter labels
C = np.loadtxt("data/C_R22.txt", delimiter="\t")
L = np.loadtxt("data/L_R22.txt", delimiter="\t")
q_names = np.loadtxt("data/q_R22.txt", dtype="U30")

# GLS solution q_ML = (L^T C^{-1} L)^(-1) L^T C^{-1} y
Cinv = np.linalg.inv(C)         # for production use: Cholesky-based solve
Sigma_inv = L.T @ Cinv @ L
rhs = L.T @ Cinv @ y
q_ML = np.linalg.solve(Sigma_inv, rhs)

# Extract H0 from the component labeled "5logH0"
i_H0 = np.where(q_names == "5logH0")[0][0]
H0 = 10.0**(q_ML[i_H0] / 5.0)
print("H0 (standard SH0ES calibration) =", H0)
```

---

## TRGB distance calibrations

Four TRGB distance measurements are included for comparison and cross-calibration.  
These values are taken from the following works:

- [Freedman et al. (2019), *ApJ* 882, 34](https://iopscience.iop.org/article/10.3847/1538-4357/ab2f73) (**[`TRGB_F19.txt`](/data/TRGB_F19.txt)**)
- [Anand et al. (2022), *ApJ* 932, 15](https://iopscience.iop.org/article/10.3847/1538-4357/ac68df) (**[`TRGB_A22.txt`](/data/TRGB_A22.txt)**)
- [Li et al. (2024), *ApJ* 976, 177](https://iopscience.iop.org/article/10.3847/1538-4357/ad84f3) (**[`TRGB_L24.txt`](/data/TRGB_L24.txt)**)
- [Freedman et al. (2025), *ApJ* 985, 203](https://iopscience.iop.org/article/10.3847/1538-4357/adce78) (**[`TRGB_F24.txt`](/data/TRGB_F24.txt)**)

These provide distance measurements that complement the Cepheid-based ones and are primarily used in our work as part of a single, joint calibration of the full distance ladder.
