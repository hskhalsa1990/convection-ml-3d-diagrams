# Convection ML: 3D Diagrams and Explainability Gallery

Visual gallery for a machine learning surrogate that predicts the **Nusselt number (Nu)** of convective heat transfer from the **Reynolds (Re)**, **Rayleigh (Ra)** and **Prandtl (Pr)** numbers.

> **Note on the figures.** The diagrams in this repository are illustrative visuals that show what a convection ML analysis can look like. They were generated as concept graphics and are **not output from a released training pipeline**. The metrics shown in them (for example accuracy, R², latency) are example values, not benchmark results. Code that produces real, reproducible figures is planned (see Roadmap).

## Physics background

| Regime | Dominant effect | Typical correlation |
|---|---|---|
| Forced convection | Pressure-driven flow | Nu = 0.023 Re^0.8 Pr^0.4 (Dittus-Boelter, turbulent pipe flow) |
| Natural convection | Buoyancy-driven flow | Nu ~ 0.59 Ra^0.25 (laminar, vertical surfaces) |
| Mixed convection | Both together | Combined forced and natural contribution |

## Interactive 3D plot

Open [`interactive_3d_convection.html`](interactive_3d_convection.html) in a browser for a rotatable Plotly scatter of Re x Ra x Pr space coloured by Nu. It uses the correlations above on a randomly sampled synthetic dataset (about 10% noise), and needs an internet connection to load Plotly.

## Gallery

### Performance and validation

**Flow regime classification: confusion matrix (laminar, transition, turbulent)**

![Flow regime classification: confusion matrix (laminar, transition, turbulent)](01_confusion_matrix.webp)

**3D surface: Nu as a function of Re and Ra for Pr = 0.7**

![3D surface: Nu as a function of Re and Ra for Pr = 0.7](02_surface_nu_re_ra_3d.webp)

**Serving metrics: inference latency, throughput and error rate**

![Serving metrics: inference latency, throughput and error rate](03_serving_metrics.webp)

**2x2 summary: Nu vs Re, Nu vs Ra, feature correlation matrix, feature importance**

![2x2 summary: Nu vs Re, Nu vs Ra, feature correlation matrix, feature importance](04_model_analysis_summary.webp)

**Input vs output comparison table: analytical Nu against predicted Nu**

![Input vs output comparison table: analytical Nu against predicted Nu](05_input_output_table.webp)

**3D resilience test: pod-kill recovery with auto-scaling**

![3D resilience test: pod-kill recovery with auto-scaling](06_chaos_mesh_3d.webp)

### Training and feature importance

**Training vs validation loss with early stopping**

![Training vs validation loss with early stopping](07_loss_curves.webp)

**Annotated loss curves (rapid learning, plateau, overfitting start)**

![Annotated loss curves (rapid learning, plateau, overfitting start)](09_loss_curves_annotated.webp)

**Loss curves with the learning rate schedule**

![Loss curves with the learning rate schedule](10_loss_lr_schedule.webp)

**SHAP summary: impact of Re, Ra and Pr on predicted Nu**

![SHAP summary: impact of Re, Ra and Pr on predicted Nu](08_shap_summary.webp)

### Statistical checks

**Calibration plot: predicted vs actual Nu**

![Calibration plot: predicted vs actual Nu](11_calibration_plot.webp)

**Residual plot and residual distribution**

![Residual plot and residual distribution](12_residual_plot.webp)

**Q-Q plot for residual normality**

![Q-Q plot for residual normality](13_qq_plot.webp)

**Q-Q plot with 95% confidence bands**

![Q-Q plot with 95% confidence bands](14_qq_plot_ci_bands.webp)

### Explainability (PDP, ICE, ALE)

**Partial dependence: Reynolds number vs Nu**

![Partial dependence: Reynolds number vs Nu](15_pdp_re_nu.webp)

**Partial dependence: Rayleigh number vs Nu**

![Partial dependence: Rayleigh number vs Nu](16_pdp_ra_nu.webp)

**Partial dependence: Prandtl number vs Nu**

![Partial dependence: Prandtl number vs Nu](17_pdp_pr_nu.webp)

**2D partial dependence: Re x Ra interaction heatmap**

![2D partial dependence: Re x Ra interaction heatmap](18_pdp_2d_re_ra_heatmap.webp)

**PDP with ICE curves**

![PDP with ICE curves](19_pdp_ice_curves.webp)

**ALE vs PDP for Re**

![ALE vs PDP for Re](20_ale_vs_pdp_re.webp)

### Advanced 3D visualisations

**3D scatter of Re x Ra x Pr space coloured by Nu**

![3D scatter of Re x Ra x Pr space coloured by Nu](21_scatter_3d_re_ra_pr.webp)

**3D isosurfaces for Nu = 100, 200, 300, 400**

![3D isosurfaces for Nu = 100, 200, 300, 400](22_isosurfaces_3d_nu.webp)

**3D vector field: gradient of Nu in Re x Ra space**

![3D vector field: gradient of Nu in Re x Ra space](23_vector_field_3d_nu_gradient.webp)

**3D streamlines: natural, forced and mixed convection**

![3D streamlines: natural, forced and mixed convection](24_streamlines_3d_flow_regimes.webp)

**3D volume rendering: Nu density cloud**

![3D volume rendering: Nu density cloud](25_volume_rendering_3d_nu.webp)

## Files

All files are in the repository root (flat layout): 25 `.webp` diagrams numbered `01` to `25`, `interactive_3d_convection.html`, `README.md` and `LICENSE`.

## Roadmap

- [ ] Add a Python solver that generates the Nu dataset (links with the `heat-transfer-py` library)
- [ ] Train and publish the surrogate model with a reproducible notebook
- [ ] Regenerate every figure from the real model output, so all numbers are reproducible
- [ ] Add tests and a CI workflow

## License

MIT. See [LICENSE](LICENSE).

Author: H. S. Khalsa
