# Data Source

## Dataset
- **Name:** Volve Field Production Data
- **File needed:** `Volve production data.xlsx`
- **Rename to:** `Volve_production_data.xlsx`
- **Place in:** `data/` folder

---

## Source

- **Owner:** Equinor (formerly Statoil)
- **Released:** 2018 (open data)
- **License:** Equinor Open Data License
- **Official page:** [https://www.equinor.com/energy/volve-data-sharing](https://www.equinor.com/energy/volve-data-sharing)

---

## How to Download

1. Go to [https://www.equinor.com/energy/volve-data-sharing](https://www.equinor.com/energy/volve-data-sharing)
2. Register for free access
3. Download the **Production Data** package
4. Extract the Excel file: `Volve production data.xlsx`
5. Rename it to `Volve_production_data.xlsx`
6. Place it in the `data/` folder of this repository

---

## About the Volve Field

| Detail | Info |
|--------|------|
| Location | Norwegian North Sea, Block 15/9 |
| Operator | Equinor (Statoil) |
| Production period | 2008 – 2016 |
| Data released | 2018 |
| Well used in this project | 15/9-F-14 |

---

## Columns Used in This Project

| Column | Description |
|--------|-------------|
| `NPD_WELL_BORE_NAME` | Well identifier |
| `DATEPRD` | Production date |
| `BORE_OIL_VOL` | Daily oil production volume (Sm³/day) |

---

## Important Notes

- The raw data contains multiple wells — this project filters for `15/9-F-14`
- Zero-production days are removed before analysis
- The dataset is **not included** in this repository due to Equinor's licensing terms
- Always download fresh data from the official Equinor source
