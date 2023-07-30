# Portfolio-Management
In this project we build a backtesting framework for robust portfolio optimization models for multi-asset classes, including equities, fixed-income, real estate, and commodities. 

### Models

Traditional mean-variance optimization (namely, Markowitz model) is known to have several drawbacks (e.g. sensitivity of parameters, ignorance of higher-order statistics, etc.). We optimize the model by introducing notional control, risk penalty, turnover penalty, and dynamic portfolio rebalancing. The target function is given by:



$$\text{argmax}_w(\mu^{T}w-\cfrac{1}{2}\lambda w^T\Sigma w- \gamma \left|| w - \hat{w} \right||^2)$$

where

- $\sum_i w_i = 1, w_i>0$ are portfolio weights, $\hat{w}$ is the previous weight

- $\mu$: mean asset returns
- $\Sigma$: covariance matrix, portfolio volatility
- $\lambda$: risk penalty parameter (higher $\lambda$ means lower volatility)
- $\gamma$: portfolio turnover penalty parameter (higher $\gamma$ means lower turnover)

### **Five optimized models**

- v1: standard Markowitz model
- V1.5: mean-variance + outlier winsorization
- V2: mean-variance+ winsorization + Notional Control
- V3: mean-variance+ winsorization + Notional Control + Turnover Control
- V4 (Final model): mean-variance+ winsorization + Notional Control + Turnover Control + Risk Control

### Strategy Pipeline

<img src="./imgs/framework.png" width="700">

<img src="./imgs/backtest.png" width="700">

### Results

#### 1. Optimal Portfolio Weight Dynamics

<img src="./imgs/weights.png" width="700">

#### 2. Portfolio Risk Contribution

<img src="./imgs/risk_contribution.png" width="800">

#### 3. Robustness Check

Check the model robustness for different asset classes, different hyper-parameter values (risk control and turnover control), different backtest windows.

- Change of Sharpe and volatility w.r.t. risk penalty parameter

<img src="./imgs/robust_risk.png" width="650">

- Performance comparison for different backtest windows

<img src="./imgs/robust_window.png" width="650">

#### 4. Model Performance Summary

| Models | Return | Volatility | Sharpe | Max Drawdown | Turnovers |
| ------ | :----: | :--------: | :----: | :----------: | :-------: |
| V1     | 0.0200 |   0.0714   | 0.2799 |   -0.1691    |  0.2518   |
| V1.5   | 0.0163 |   0.0738   | 0.2216 |   -0.1778    |  0.3581   |
| V2     | 0.0475 |   0.1183   | 0.4021 |   -0.2044    |  0.2468   |
| V3     | 0.0479 |   0.1211   | 0.3957 |   -0.2110    |  0.1499   |
| V4     | 0.0542 |   0.1411   | 0.3845 |   -0.2383    |  0.1828   |





