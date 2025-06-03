# BSE-automated-market-making-strategy
# Automated Market Maker in BSE

This repository contains a customized implementation of the **Bristol Stock Exchange (BSE)** simulator featuring a newly developed **Automated Market Maker (AMM)** trading agent.

## Objective

To build a more adaptive and profitable AMM trading strategy (`MMM02`) and compare its performance with the default market-maker `MMM01` in a dynamic, intraday market environment.


## Summary of Work Done

### 1. Custom Strategy in `MMM02`

- Edited the logic in the `TraderMMM02` class to implement a **custom market-making strategy**.
- The agent adaptively places buy and sell orders based on:
  - Recent transaction trends
  - Inventory levels
  - Market price movement using offset data
- Strategy uses a **simple moving average (SMA)** to detect price trends and adjust quote spreads accordingly.
- Ensures long-only constraints: trader can only sell what it owns.

### 2. Integrated Real Intraday Price Data

- Used `offset-copper-1m-170912.csv` as the source of price movement.
- Set up BSE to read the CSV data via the `schedule_offsetfn_read_file(...)` and `schedule_offsetfn_from_eventlist(...)` functions.
- This created a realistic and non-stationary market environment for testing the AMM logic.

### Experimental Evaluation

- Ran multiple market sessions to observe:
  - Bank balance evolution of `MMM02`
  - Comparison of `MMM02` vs `MMM01` profitability
  - Behavior under different trend segments (rising, falling, flat)
- Visualized:
  - Transaction price time-series
  - Trader bank balances over time
  - SMA vs actual price evolution

---

## Files Included

- `BSE-B.py`  
  → Main simulation environment with `MMM02` logic rewritten

- `offset-copper-1m-170912.csv`  
  → Intraday copper price data (1-minute resolution)

---


