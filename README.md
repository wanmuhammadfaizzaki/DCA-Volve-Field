# 📉 Decline Curve Analysis (DCA) — Arps Model

> **Project from the [Petro Analyst YouTube Channel](https://www.youtube.com/@AhmedAbdElgawad-petroAnalyst)**  
> **Production data provided by [Equinor (Volve Field Dataset)](https://www.equinor.com/energy/volve-data-sharing)**

This project implements **Arps Decline Curve Analysis (DCA)** on real oil well production data using Python. It fits three classical decline models — **Exponential**, **Harmonic**, and **Hyperbolic** — and evaluates each using RMSE to identify the best fit.

---

## Overview

Decline Curve Analysis is one of the most widely used methods in petroleum engineering for production forecasting and reserve estimation. This project walks through:

1. Loading and filtering well production data
2. Removing outliers (zero-production days)
3. Smoothing production data using a rolling average
4. Converting dates to elapsed days
5. Fitting all three Arps models using `scipy.optimize.curve_fit`
6. Evaluating model accuracy with RMSE
7. Visualizing and comparing all models

---

## Project Structure

```
DCA-Volve-Field/
│
├── data/
│   └── Volve production data.xlsx      # Equinor Volve dataset (see Dataset section)
│
├── DCA.ipynb                            # Main Jupyter Notebook
├── requirements.txt                     # Python dependencies
├── .gitignore                           # Files to ignore in git
└── README.md                            # This file
```
## Dataset

| Field | Details |
|---|---|
| **Source** | Equinor (formerly Statoil) |
| **Field** | Volve Oil Field, North Sea, Norway |
| **License** | Open / Public |
| **Download** | [Equinor Volve Data Sharing](https://www.equinor.com/energy/volve-data-sharing) |
| **Well Used** | `15/9-F-14` |
| **Production Column** | `BORE_OIL_VOL` (barrels of oil per day) |
| **Date Column** | `DATEPRD` |

---

## Workflow

The notebook is structured as a series of tasks:

| Task | Description |
|---|---|
| **Task 1** | Load and filter data for a specific well |
| **Task 2** | Remove outliers (zero-production rows) |
| **Task 3** | Smooth production using a rolling moving average |
| **Task 4** | Calculate elapsed days from the first production date |
| **Task 5** | Fit Exponential, Harmonic, and Hyperbolic decline models |
| **Final** | Build the full `arps()` pipeline and compare all models |

---

## Models

All three models follow **Arps' decline curve equations**:

### Exponential
```
q(t) = qi * exp(-di * t)
```
Best for reservoirs with constant fractional decline.

### Harmonic
```
q(t) = qi / (1 + di * t)
```
Special case of hyperbolic where b = 1.

### Hyperbolic
```
q(t) = qi / (1 + b * di * t)^(1/b)
```
Most general form. b is between 0 and 1 for most reservoirs.

**Parameters:**

| Symbol | Description |
|---|---|
| `qi` | Initial production rate |
| `di` | Initial decline rate |
| `b` | Hyperbolic exponent (0 = exponential, 1 = harmonic) |

---

## Results

After fitting, each model is evaluated using **Root Mean Square Error (RMSE)**:

```python
RMSE = sqrt( (1/n) * sum((actual - predicted)^2) )
```

The model with the **lowest RMSE** is the best fit for the well's production behavior.

A comparison DataFrame (`params`) is returned with all model parameters and RMSE values side by side.

---

## Credits

| | |
|---|---|
| **Tutorial** | [Petro Analyst YouTube Channel](https://www.youtube.com/@AhmedAbdElgawad-petroAnalyst) |
| **Dataset** | [Equinor Volve Data Sharing Program](https://www.equinor.com/energy/volve-data-sharing) |
| **Implementation** | Based on the Arps (1945) decline curve equations |

---

## License

This project is for **educational purposes only**.  
The Volve dataset is subject to Equinor's data sharing terms. Please review their license before use.
