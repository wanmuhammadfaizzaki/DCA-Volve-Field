# DCA-Volve-Field
Decline Curve Analysis on Volve Field real production data — hyperbolic, harmonic and exponential model fitting using SciPy on well 15/9-F-14 with smoothing, visualization, and EUR estimation.

# Decline Curve Analysis — Volve Field

A petroleum engineering project applying **Decline Curve Analysis (DCA)** on real production data from the **Volve Oil Field** (North Sea, Norway). This project fits a hyperbolic decline model to smoothed well production data using Python and SciPy curve fitting.

---

## 📋 Project Overview

Decline Curve Analysis is a fundamental reservoir engineering technique used to:
- Forecast future production rates
- Estimate Estimated Ultimate Recovery (EUR)
- Identify changes in well behavior over time

This project applies DCA to **Well 15/9-F-14** from the Volve dataset — a publicly available real-world field dataset released by Equinor.

---

## 🗂️ Repository Structure

```
DCA-Volve-Field/
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
│
├── data/
│   └── data_source.md          ← How to download the Volve dataset
└── notebooks/
    └── DCA_Volve.ipynb         ← Main analysis notebook
```

---

## ⚙️ Methodology

### 1. Data Preparation
- Load Volve production Excel data
- Filter for target well: `15/9-F-14`
- Remove zero-production entries
- Apply **150-day moving average** to smooth noisy daily production data

### 2. Decline Curve Fitting
- Convert dates to elapsed days
- Fit **Hyperbolic Decline Model** using `scipy.optimize.curve_fit`

**Hyperbolic equation:**

$$q(t) = \frac{q_i}{(1 + b \cdot D_i \cdot t)^{1/b}}$$

| Parameter | Description |
|-----------|-------------|
| `qᵢ` | Initial production rate (Sm³/day) |
| `Dᵢ` | Initial decline rate (1/day) |
| `b` | Hyperbolic exponent (0 < b < 2) |

### 3. Model Evaluation
- Visual comparison of raw, smoothed, and fitted curves
- Distribution analysis of production rates


## 📦 Dependencies

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading and manipulation |
| `numpy` | Numerical computation |
| `matplotlib` | Production curve plotting |
| `seaborn` | Distribution visualization |
| `scipy` | Hyperbolic curve fitting |
| `openpyxl` | Reading Excel data files |

---

## 🛢️ About the Volve Dataset

The Volve field is a decommissioned oil field in the Norwegian North Sea operated by Equinor (formerly Statoil). In 2018, Equinor released the full Volve dataset to the public — making it one of the most complete open petroleum engineering datasets available.

- **Field location:** Norwegian North Sea, Block 15/9
- **Production period:** 2008–2016
- **Data released:** 2018 by Equinor
- **Dataset size:** ~40,000 files including well logs, production data, seismic

---

## 📌 Key Results

| Parameter | Value |
|-----------|-------|
| Well | 15/9-F-14 |
| Decline Model | Hyperbolic, Harmonic and Exponential |
| Smoothing Window | 150 days |

> ⚠️ Results are based on smoothed data for well `15/9-F-14` only. Extend to other wells by modifying the well filter.

---

## 🔭 Future Work

- [ ] Extend analysis to all Volve wells
- [ ] Add EUR (Estimated Ultimate Recovery) calculation
- [ ] Add economic limit cutoff
- [ ] Build interactive Plotly dashboard

---

## 👤 Author

**Wan Muhammad Faizzaki**
- GitHub: [@wanmuhammadfaizzaki](https://github.com/wanmuhammadfaizzaki)

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

The Volve dataset is owned by **Equinor** and released under their open data license.
