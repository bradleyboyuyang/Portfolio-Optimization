# Portfolio-Management
In this project we build a backtesting framework for robust portfolio optimization models for multi-asset classes, including equities, fixed-income, real estate, and commodities. 

### Model

Traditional mean-variance optimization (namely, Markowitz model) is known to have several drawbacks (e.g. sensitivity of parameters, ignorance of higher-order statistics, etc.). We optimize the model by introducing notional control, risk penalty, turnover penalty, and dynamic portfolio rebalancing. The target function is given by:



$$\text{argmax}_w(\mu^{T}w-\cfrac{1}{2}\lambda w^T\Sigma w- \gamma \left|| w - \hat{w} \right||^2)$$

where

- $\sum_i w_i = 1, w_i>0$ are portfolio weights, $\hat{w}$ is the previous weight

- $\mu$: mean asset returns
- $\Sigma$: covariance matrix, portfolio volatility
- $\lambda$: risk penalty parameter (higher $\lambda$ means lower volatility)
- $\gamma$: portfolio turnover penalty parameter (higher $\gamma$ means lower turnover)



### Strategy Pipeline

<img src="./imgs/framework.png" width="750">

### Backtest Framework

<img src="./imgs/backtest.png" width="750">

#### Risk Contribution

<img src="./imgs/risk_contribution.png" width="800">

