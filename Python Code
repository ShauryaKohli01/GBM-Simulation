import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Parameters
S0 = 10         # Initial stock price
T = 1           # Time horizon (e.g., 1 year)
dt = 0.002      # Time step
r = 0.02        # Risk-free rate
vol = 0.02      # Volatility
n = 1000        # Number of simulations

tt = np.arange(start=0, stop=T+1e-10, step=dt)
m = len(tt)

# Initialize stock price matrix
S = np.zeros((m, n))
S[0, :] = S0  # First row is initial stock price

# Generate random shocks (Brownian motion increments)
dW = stats.norm.rvs(size=(m-1, n)) * np.sqrt(dt)

# Simulate paths
for i in range(m - 1):
    S[i+1, :] = S[i, :] * np.exp((r - 0.5 * vol**2) * dt + vol * dW[i, :])

# Plotting
fig, ax = plt.subplots()
ax.plot(tt, S)
plt.title('GBM simulations')
plt.xlabel('time')
plt.ylabel('stock prices')
plt.show(block=True)
