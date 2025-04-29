# Modeling and Forecasting USD-JPY FX Rates Using Stochastic Simulation

## Overview

This project implements stochastic simulation techniques to model and forecast the USD-JPY foreign exchange rate.  
Three stochastic models were used:

- **Geometric Brownian Motion (GBM)**
- **Ornstein-Uhlenbeck (OU) Process**
- **GARCH(1,1) Model**

Numerical implementation was based on discretization methods, primarily the **Euler-Maruyama method** for continuous-time stochastic differential equations (SDEs).

---

## Data Source

Historical daily closing prices of the USD-JPY exchange rate were collected using the `yfinance` Python module, covering the period from **January 1, 2020** to **March 31, 2025**.

Data cleaning included:
- Retaining only the closing price and date columns.
- Removing missing values corresponding to non-trading days.

---

## Stochastic Models and Methods

### 1. Geometric Brownian Motion (GBM)

**Stochastic Differential Equation:**

<img width="806" alt="Image" src="https://github.com/user-attachments/assets/513923d0-ed31-467d-b344-877ce7e2be39" />

**Euler-Maruyama Discretization:**

<img width="806" alt="Image" src="https://github.com/user-attachments/assets/b7ed1c8f-c28b-460f-a5a3-575c6480b9b3" />

---

### 2. Ornstein-Uhlenbeck (OU) Process

**Stochastic Differential Equation:**

<img width="806" alt="Image" src="https://github.com/user-attachments/assets/830bec9f-a9ae-4a75-92ed-9d81cea79721" />

**Euler-Maruyama Discretization:**

<img width="806" alt="Image" src="https://github.com/user-attachments/assets/dc603515-9253-4a84-8dd7-b0cbed5b83ad" />

---

### 3. GARCH(1,1) Model

**Time Series Equations:**

Conditional variance evolution:

<img width="806" alt="Image" src="https://github.com/user-attachments/assets/957758b1-4882-4f81-aca0-4e3aa3e93f06" />

---

## Simulation Procedure

For each stochastic model:

1. **Initialization**:  
   Parameters were estimated from historical USD-JPY closing price data.

2. **Simulation**:  
   10 independent trajectories were generated for each model.  
   The final forecast trajectory was computed as the mean across all simulations to reduce stochastic noise.

3. **Evaluation**:  
   Visual comparison between actual exchange rate data and simulated paths.  
   Attempts to apply formal statistical evaluation methods (e.g., R² metric, chi-squared goodness-of-fit) were made, but inconsistencies in data structures limited robust validation.

---

## Technical Summary

- **GBM** models simple stochastic exponential growth with constant drift and volatility, assuming log-normal price distributions.
- **OU Process** models mean-reverting behavior typical for FX rates influenced by macroeconomic equilibria.
- **GARCH(1,1)** models conditional heteroskedasticity to capture volatility clustering.

All continuous-time stochastic differential equations were discretized using the **Euler-Maruyama method**.  
The GARCH model was implemented through standard time series recursion methods.
