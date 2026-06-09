# Capstone Project: Dynamic Pricing Prediction for Parking

## Overview

This project implements a **predictive pricing system** for parking lots using historical and time-based data. Developed entirely in **Google Colab**, it combines structured preprocessing, multiple modeling techniques, and rich visual analytics. The project explores two pricing models — one baseline and one context-aware — for improving revenue predictability and operational decisions.

---

## Tech Stack

- **Python 3**
- **Google Colab** – Notebook-based development
- **Pandas** – Data preprocessing
- **NumPy** – Numerical operations
- **Matplotlib & Seaborn** – Plotting and EDA
- **Scikit-learn** – Modeling and evaluation
- **XGBoost** – Advanced model
- **Pathway** – For stream simulation and file handling
- **Pathlib** – Clean file I/O handling

---

## Architecture Diagram
---

<img src="https://github.com/ar-yansingh/images/blob/main/Untitled%20diagram%20_%20Mermaid%20Chart-2025-07-09-161810.png" alt="Architecture Diagram" height="720" />

---


## Project Workflow

### 1. **Data Preprocessing**

- Mounted Google Drive for file access
- Cleaned timestamps, missing values, and encoded vehicle and lot-level variables
- Mapped numeric weights to variables like `VehicleType`, `TrafficCondition`, etc.

---

## Pricing Models

### Model 1: Historical Average Pricing

A baseline model that predicts prices using historical averages or medians for each lot and hour segment.

```python
Price = base_price + α * (avg_occupancy) + β * vehicle_weight
```

Pros:
- Simple and fast  
Cons:
- Ignores real-time context like traffic or demand spikes

**Model 1 Output (Static Plot):**  
![Model 1 Prediction](https://github.com/ar-yansingh/images/blob/main/Dynamic%20parking%20price%20over%20time(model1).png)

---

### Model 2: Context-Aware Dynamic Model

Incorporates temporal and environmental variables such as occupancy ratio, time of day, and vehicle type.

```python
Price = BASE + α * (Occupancy / Capacity)
              + β * TimeWeight
              + γ * VehicleWeight
              + δ * IsWeekend
```

Pros:
- Responds to real-time behavior and context  
Cons:
- Needs more preprocessing and tuning

**Model 2 Output (Static Plot):**  
![Model 2 Prediction](https://github.com/ar-yansingh/images/blob/main/Dynamic%20parking%20price%20over%20time(model2).png)

---

## Sample Visualization

**Lot-wise Pricing Over Time (Historical):**  
![Historical Lot Prices](https://github.com/ar-yansingh/images/blob/main/Price%20Comparison%20across%20lots(model2).png)

---

## Pathway Integration

- **Used for**: Organizing output directories (`/notebooks/visuals`), managing filepaths, and controlling runtime storage
- **Tool**: `pathlib.Path` and Colab drive mount
- **Benefit**: Clean reproducible structure, enabling consistent saving of plots, processed data, and outputs

---

## Project Structure

```bash
.
├── notebooks/
│   ├── preprocessing_and_eda.ipynb         # Data wrangling and exploration
│   └── modeling_and_visualization.ipynb    # Model training and evaluation
│
├── data/
│   ├── parking_raw.csv
│   └── parking_processed.csv
│
├── visuals/
│   ├── model1_prediction.png
│   ├── model2_prediction.png
│   └── price_comparison.png
│
├── README.md
└── report.pdf (optional)
```

---
## System Extensibility

The system is modular and can be extended with:

- ** Real-Time Map Visualization**: Live display of parking availability.
- ** API Integration with Sensors**: Connect to smart parking sensors for real-time data.
- ** ML-Based Demand Prediction**: Use machine learning to forecast demand using historical and contextual data.

## Pricing Logic

Currently rule-based, but can be hybridized with:

- Historical usage data  
- Real-time trends  
- ML-driven dynamic pricing


## Future Enhancements

- Real-time pricing integration using sensors or live APIs
- ML-based demand forecasting (ARIMA, LSTM)
- Integration into a dashboard or mobile app

---



## Author

- Built and tested in Google Colab

