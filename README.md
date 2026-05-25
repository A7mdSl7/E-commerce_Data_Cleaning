# 🛒 E-Commerce Data Cleaning & Preparation

A professional data cleaning pipeline applied to an E-Commerce Sales & Orders dataset using Python and Pandas. This notebook simulates real-world messy data scenarios and walks through a structured, end-to-end cleaning workflow — from raw ingestion to a fully validated, analysis-ready dataset.

---

## 📌 Project Overview

Raw datasets in production environments are rarely clean. This project demonstrates how to **detect, handle, and document** common data quality issues in an e-commerce context, following professional data engineering practices.

**Dataset:** E-Commerce Sales & Orders (`E-Commerce Sales & Orders.xlsx`)  
**Output:** `cleaned_ecommerce_dataset.xlsx`

---

## 🔄 Workflow

The notebook follows a 9-step structured pipeline:

| Step | Description |
|------|-------------|
| 1 | **Load & Inspect** — Read the raw Excel file, check shape, data types, and summary statistics |
| 2 | **Inject Practice Scenarios** — Simulate real-world issues: duplicates, messy text, invalid values, corrupted dates |
| 3 | **Data Quality Assessment** — Detect missing values, duplicates, and anomalies |
| 4 | **Handle Missing Values** — Fill `CouponCode` NaNs with `'NO_COUPON'` (business-logic-aware) |
| 5 | **Data Cleaning** — Remove duplicates, standardize text formatting, fix dates and negative numbers |
| 6 | **Business Validation** — Enforce `TotalPrice = Quantity × UnitPrice`, validate unique `OrderID` and `TrackingNumber` |
| 7 | **Change Log** — Document every problem detected and the action taken |
| 8 | **Final Validation** — Confirm zero duplicates, nulls, negatives, and logic violations remain |
| 9 | **Export** — Save the cleaned dataset to a new Excel file |

---

## 🧹 Issues Handled

| Problem | Cleaning Action | Result |
|--------|----------------|--------|
| Missing `CouponCode` | Filled with `'NO_COUPON'` | Preserved business logic; no data loss |
| Duplicate rows | `.drop_duplicates()` | Removed identical records |
| Inconsistent text (e.g. `lApToP`, extra spaces) | `.str.strip().str.title()` + regex | Standardized categorical columns |
| Invalid/corrupted dates (e.g. `2023/15/35`) | `pd.to_datetime(errors='coerce')` + drop NaT | Ensured time-series accuracy |
| Negative quantities & prices | `.abs()` | Fixed assumed data-entry errors |
| `TotalPrice` mismatch | Recalculated as `Quantity × UnitPrice` | Enforced financial accuracy |

---

## 🛠️ Technologies Used

- **Python 3**
- **Pandas** — data manipulation and cleaning
- **NumPy** — numerical operations
- **OpenPyXL** — reading and writing Excel files

---

## 📁 File Structure

```
📦 project/
├── ecommerce_data_cleaning.ipynb   ← Main notebook
├── E-Commerce Sales & Orders.xlsx  ← Raw input dataset
├── cleaned_ecommerce_dataset.xlsx  ← Cleaned output dataset
└── README.md
```

---

## 🚀 Getting Started

1. Clone the repository and navigate to the project folder
2. Install dependencies:
   ```bash
   pip install pandas numpy openpyxl
   ```
3. Place `E-Commerce Sales & Orders.xlsx` in the same directory as the notebook
4. Run all cells in `ecommerce_data_cleaning.ipynb`
5. The cleaned output will be saved as `cleaned_ecommerce_dataset.xlsx`

---

## 👤 Author

**Ahmed Salah**
