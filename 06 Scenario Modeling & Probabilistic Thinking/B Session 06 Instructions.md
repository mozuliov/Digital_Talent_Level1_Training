#### This Session
>Explores Monte Carlo simulation techniques to model uncertainty, quantify risk, and build richer, probabilistic views of financial scenarios.

 [![GitHub](https://img.shields.io/badge/GitHub-06_Scenario_Modeling_&_Probabilistic_Thinking-black?logo=github)](https://github.com/mozuliov/Digital_Talent_Level1_Training/tree/main/06%20Scenario%20Modeling%20%26%20Probabilistic%20Thinking)

**Working Environment:** [Google Colab](https://colab.research.google.com/)

Load the following Python libraries at the beginning of your script:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt  

# Set random seed so everyone gets the same random numbers today
np.random.seed(42)
```

Use following **Portfolio Parameters** for the simulation:
```python
# Our Starting Money
INITIAL_VALUE = 1_000_000  # $1,000,000

# Simulation Rules
DAYS = 30           # Let's simulate what happens over the next 30 trading days
SIMULATIONS = 1000  # We will run 1,000 different "what-if" futures

# Portfolio Assumptions (Annual)
EXPECTED_RETURN = 0.07 # 7% average annual return
VOLATILITY = 0.12      # 12% annual volatility (risk)

print(f"Starting with ${INITIAL_VALUE:,.0f}, running {SIMULATIONS} scenarios for {DAYS} days.")
```