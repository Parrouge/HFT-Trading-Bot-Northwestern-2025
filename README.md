# Northwestern Algorithmic Trading Competition 2025  
### Team Submission — All Cases (HFT, Crypto Market-Making, and Manual Trading)  
**Team:** Parry Nall & Ayush Chandra  
**Ranking:** Top 10 / 50 (20%) in High Frequency Trading (HFT) Case  
**Language:** C++  
**Platform:** NU Fintech Exchange (Proprietary Simulation Environment)  

---

## Overview  
This repository contains our team’s submission for the **Northwestern Algorithmic Trading Competition 2025**, organized by **NU Fintech**. We participated in **all three competition cases** — **High Frequency Trading (HFT)**, **Crypto Market-Making**, and **Manual Trading**.  

Our primary success came from the **HFT case**, where we developed a **C++ adaptive market-making algorithm** that achieved a **top 10 finish (top 20%)** out of 50 teams. The algorithm was designed to handle high volatility, optimize order placement, and maintain consistent profitability through dynamic risk and inventory control.  

---

## Core Features  
- **Multi-Asset Market Making:** Operates across BTC, ETH, and LTC with separate orderbooks, inventory management, and capital tracking.  
- **Adaptive Quoting Logic:** Continuously refines bid/ask levels relative to the market spread, improving competitiveness and liquidity capture.  
- **Inventory-Aware Control:** Dynamically biases quotes to reduce directional exposure when inventory deviates from balance.  
- **Dynamic Order Sizing:** Adjusts trade sizes proportionally to capital and exposure, stabilizing performance during market swings.  
- **Emergency Unwind Mechanism:** Triggers position reduction when exposure breaches defined safety limits using immediate-or-cancel limit orders.  
- **Aggressive Quote Refreshing:** Refreshes all outstanding quotes on a set frequency to maintain optimal placement during volatility.  

---

## Technical Design  
The algorithm was implemented within the official **NU Fintech C++20 simulation framework** and interacted directly with the live orderbook API.  

**Main Components**  
- `on_orderbook_update()` — Updates market data and triggers quote placement or refresh.  
- `on_account_update()` — Tracks balance, inventory, and PnL; invokes unwind logic if overexposed.  
- `on_trade_update()` — Records fills and updates realized/unrealized profits.  
- `_quote()` — Places limit orders based on adaptive spread and market conditions.  
- `_calculate_size()` — Determines appropriate order quantity based on risk tolerance.  
- `_unwind_positions()` — Safely exits open positions to rebalance exposure.  
- `_cancel_orders()` — Cancels all open orders to prevent stale activity before re-quoting.  

---

## Hyperparameters  
| Parameter | Default | Description |
|------------|----------|-------------|
| `base_order_size` | 25–30 | Default limit order size per asset. |
| `spread_improvement` | 0.01 | Adjusts quotes closer to midprice for tighter spreads. |
| `max_position` | 150–200 | Maximum allowed position per asset. |
| `inventory_skew` | 0.01 | Controls how strongly inventory affects quoting direction. |
| `quote_frequency` | 150–250 | Determines how frequently orders are refreshed. |

These parameters were optimized through simulation runs to balance aggressiveness and risk management under various volatility scenarios.  

---

## Competition Context  
**Event:** Northwestern Algorithmic Trading Competition 2025  
**Organized by:** Northwestern Fintech (NUFT)  
**Sponsors:** IMC Trading, Hudson River Trading (HRT), Five Rings, Chicago Trading Company, All Options  

**Competition Cases:**  
- **High Frequency Trading (HFT)** — Developed adaptive C++ market-making strategies for multi-asset trading under volatility (Placed Top 10 / 50).  
- **Crypto Market-Making** — Focused on liquidity provision and arbitrage stability across simulated crypto exchanges.  
- **Manual Trading** — Real-time human-driven case emphasizing technical analysis, execution timing, and behavioral finance.  

Our **HFT algorithm** was recognized for its performance, stability, and effective position management under fast-changing market conditions.  

---

## Results  
- **Participated in:** All three cases (HFT, Crypto Market-Making, Manual Trading)  
- **HFT Ranking:** Top 10 / 50 (20%)  
- **Evaluation Metric:** Final Net PnL (Capital + Portfolio Value)  
- **Execution Environment:** Live NU Fintech Exchange at The Hive, Northwestern University  

---

## Technical Notes  
- Built entirely in **C++20** within NUFT’s provided framework.  
- Uses only standard STL libraries (no external dependencies).  
- Operates within competition limits (1GB memory, 0.5 CPU core).  
- Prioritized consistent order management, low-latency execution, and deterministic behavior.  

---

## Acknowledgements  
We thank the **NU Fintech Organizing Committee** and competition sponsors — **IMC Trading**, **Hudson River Trading**, **Five Rings**, **Chicago Trading Company**, and **All Options** — for providing an exceptional platform to learn, experiment, and apply quantitative trading strategies in a real-world simulation environment.  

---

## Authors  
**Parry Nall**  
**Ayush Chandra**  
