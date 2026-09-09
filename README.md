# Active Power Forecasting using Stacked LSTM & SHAP Interpretability

An end-to-end deep learning framework for short-to-medium-term active power forecasting across energy distribution networks. This project utilizes a Stacked Long Short-Term Memory (LSTM) architecture trained on multi-parametric time-series data (historical power demand, meteorological variables, and temporal features) and incorporates SHAP (SHapley Additive exPlanations) for global and local model interpretability.

---

## Key Highlights & Capabilities
* **Deep Sequence Modeling:** Built a multi-layer Stacked LSTM architecture capable of capturing non-linear temporal dependencies across sequential power loads.
* **Feature Engineering:** Integrated weather variables, lag parameters, and rolling statistics to optimize predictive accuracy.
* **Explainable AI:** Integrated SHAP frameworks to unpack the black-box nature of the neural network, identifying critical drivers behind power spike predictions.
* **Regime Evaluation:** Stress-tested model performance across seasonal calendar shifts and grid volatility states to define real-world operational bounds.

---

## Model Architecture & Pipeline

1. **Data Preprocessing & Scaling:** Time-series alignment, and MinMax scaling across sliding window windows.
2. **Model Training:** Stacked LSTM layers with Dropout regularizers to prevent overfitting, optimized using Adam and Early Stopping.
3. **Interpretability Analysis:** SHAP Beeswarm and Force plots to validate feature importance against domain knowledge.

---

## Results & Interpretability

| Metric | Stacked LSTM Performance |
| :--- | :--- |
| **MAE** | 25.13 |
| **RMSE** | 35.23 |
| **MAPE** | **8.87%** |

### Operational Regime Analysis
To evaluate real-world model deployment beyond global averages, forecast accuracy was evaluated across operational regimes based on grid volatility and academic calendar cycles. Comparing the LSTM against a Naive Persistence baseline reveals where deep sequence modeling provides the best performance versus simple persistence.

| Operational Segment | Sample Count ($n$) | LSTM MAPE | Persistence MAPE | Dominant Model (Margin) |
| :--- | :---: | :---: | :---: | :--- |
| **Calm Window** ($\ge$ 2025-07-14) | 1,896 | **7.65%** | 9.66% | **LSTM** (+2.01%) |
| **Volatile Window** (< 2025-07-14) | 882 | 11.50% | **7.04%** | **Persistence** (+4.46%) |
| **Term-Time** | 2,568 | **8.65%** | 9.01% | **LSTM** (+0.36%) |
| **Vacation Period** | 210 | 11.53% | **6.64%** | **Persistence** (+4.89%) |

#### Regime Insights
* **Pattern Learning in High-Volume Windows:** The LSTM excels during regular load behavior (**Term-Time** and **Calm Windows**), successfully capturing daily seasonality and non-linear trends to outperform persistence by up to 2.01% MAPE.
* **Operational Boundary:** During sudden structural shifts (**Vacation Periods** and **Volatile Windows**), sharp step-changes in consumption favor short-term persistence.

---

## Repository Contents

* `notebook/`: Complete data cleaning, feature engineering, model training, and evaluation pipeline.
* `docs/`: Full dissertation report and final defense presentation.
* `assets/`: Generated visual outputs, training loss plots, and SHAP interpretability graphs.

---

## Author
**Saad Abdullah**  
* [LinkedIn](https://www.linkedin.com/in/muhammadsaadabdullah/)
