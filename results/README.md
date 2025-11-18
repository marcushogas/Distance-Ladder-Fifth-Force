# Results

This folder contains the numerical results produced by the hierarchical Bayesian recalibration of the Cepheid–TRGB distance ladder under screened fifth-force models.  
For each analysis configuration, three output files are provided, summarizing the inferred fifth-force parameters, model comparison statistics, and diagnostics of the MCMC sampling.

The folder structure is:

- **[SH0ES_plus_TRGB/](/results/SH0ES_plus_TRGB/)** — Results for calibrations including TRGB distances (subfolders F19, A22, F24, L24).  
- **[SH0ES_only/](/results/SH0ES_only/)** — Results for calibrations based on Cepheids only.  
- **[H0prior/](/results/H0prior/)** — Results obtained when including an external Planck $H_0$ prior.

Each dataset–model combination includes the following files:

- **`results_*.txt`**  
  Contains the posterior estimates of the fifth-force parameters $(p_0, \Delta G / G_\mathrm{N}|_\mathrm{max})$, their uncertainties (68% CL), and model-selection metrics ($\chi^2$, $\Delta\mathrm{AIC}$, $\Delta\mathrm{BIC}$).

- **`diagnostics_*.txt`**  
  Reports MCMC diagnostics, including runtime, number of walkers, effective sample sizes, and auto-correlation estimates.

- **`H0_diagnostics_*.txt`**  
  Summarizes the inferred Hubble constant for the standard calibration (no fifth force) and fifth-force models, including uncertainties and differences in $\chi^2$.
