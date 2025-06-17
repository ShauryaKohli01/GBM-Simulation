# 📈 Stock Price Simulation & Risk Analysis in Python

Simulate stock price behavior using **Geometric Brownian Motion (GBM)** and **Monte Carlo simulations**, with risk metrics like **Value at Risk (VaR)** and **Probability of Loss**.

---

## 🚀 What This Project Does
- Simulates GBM-based stock price paths
- Uses Monte Carlo methods for thousands of simulations
- Plots stock paths, histogram of outcomes
- Calculates financial risk (VaR, loss probability)

---

## 📘 What is Geometric Brownian Motion?
GBM is used to model stock prices under two assumptions:
- Constant average return (μ)
- Constant volatility (σ)
- Log-normal distribution of prices

Formula:
```python
S[t] = S[t-1] * exp((μ - 0.5 * σ²) * Δt + σ * √Δt * Z[t])
```
Where:
- `S[t]`: stock price at time t
- `Z[t]`: standard normal random variable

---

## 📊 Monte Carlo Simulation
Monte Carlo runs GBM many times with random paths:
- Helps estimate risk and possible future outcomes

Key parameters:
```python
S0 = 100        # initial stock price
mu = 0.1        # expected return
sigma = 0.1123  # volatility
T = 1           # time in years
N = 252         # steps (daily)
M = 10,000      # simulation runs
```

Simulation:
```python
Z = np.random.normal(0, 1, size=(M, N))
price_paths = np.zeros((M, N+1))
price_paths[:, 0] = S0

for t in range(1, N+1):
    price_paths[:, t] = price_paths[:, t-1] * np.exp(
        (mu - 0.5 * sigma**2) * dt + sigma * np.sqrt(dt) * Z[:, t-1]
    )
```

---

## 📉 Risk Analysis
- **Histogram of final simulated prices**
- **Value at Risk (VaR)** at chosen confidence level
- **Probability of Loss** below your threshold

---

## 📎 Output Examples
- Price path plots
- Histograms
- CSV export for further analysis

---

## 🛠️ Built With
- `numpy`, `matplotlib`, `pandas`
- `streamlit` for web app (optional)

