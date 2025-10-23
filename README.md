# Northwestern Algorithmic Trading Competition 2025  
### High Frequency Trading (HFT) Case — Team Submission  
**Team:** Parry Nall & Ayush Chandra  
**Ranking:** Top 10 / 50 (20%)  
**Language:** C++  
**Platform:** NU Fintech Exchange (Proprietary Simulation Environment)  

---

## Overview  
This repository contains our final submission for the **Northwestern Algorithmic Trading Competition 2025**, organized by **NU Fintech**. We developed an **adaptive market-making algorithm** in C++ for the **High Frequency Trading (HFT)** case, where participants built autonomous trading systems that operated in a live simulated exchange against institutional, retail, and market-making bots under high volatility and zero trading fees.  

Our strategy focused on **dynamic quoting**, **inventory management**, and **real-time risk control**, achieving a **top 10 finish (top 20%)** based on final PnL performance. The algorithm continuously adjusted its orders based on changing market conditions while maintaining capital discipline and minimizing exposure.  

---

## Core Features  
- **Multi-Asset Market Making:** Handles BTC, ETH, and LTC simultaneously, maintaining independent orderbooks, positions, and active orders.  
- **Adaptive Quoting System:** Adjusts limit prices using a configurable spread-improvement factor to maintain competitiveness within the market.  
- **Inventory-Aware Positioning:** Incorporates a skew parameter to bias quotes away from overexposed positions, reducing directional risk.  
- **Dynamic Order Sizing:** Scales order quantities based on current inventory levels to balance capital use and market impact.  
- **Emergency Unwind Protocol:** Detects when exposure exceeds safe limits and automatically reduces risk using IOC (immediate-or-cancel) limit orders.  
- **Aggressive Quote Refreshing:** Periodically cancels and replaces quotes to avoid stale orders, ensuring up-to-date participation in the market.  

---

## Technical Design  
The algorithm runs within the NUTC-provided C++20 framework and interacts with the exchange via the following callbacks:  

- **`on_orderbook_update()`** — Updates best bid/ask data and triggers the quoting logic after a defined number of updates.  
- **`on_trade_update()`** — Receives notifications of trades that occur on the exchange (informational only).  
- **`on_account_update()`** — Updates internal records of inventory and capital, triggers unwind logic if positions exceed risk limits.  
- **Private Helper Methods:**  
  - `_aggresive_quote()` — Places and manages limit orders for both bid and ask sides.  
  - `_calculate_size()` — Computes order sizes based on exposure and capital.  
  - `_emergency_unwind()` — Quickly reduces positions during abnormal inventory conditions.  
  - `_cancel_all()` — Cancels all open orders for a given ticker to prevent duplication or stale activity.  

---

## Hyperparameters  
| Parameter | Default | Description |
|------------|----------|--------------|
| `base_order_size` | 25–30 | Base size for new limit orders. |
| `spread_improvement` | 0.01 | How aggressively to tighten the bid-ask spread. |
| `max_position` | 150–200 | Maximum position size allowed per asset. |
| `inventory_skew` | 0.01 | Strength of inventory-based quote bias. |
| `quote_frequency` | 150–250 | How frequently to refresh limit orders. |

These hyperparameters can be tuned to balance between risk, profitability, and trading frequency depending on volatility and competition dynamics.  

---

## Competition Context  
**Event:** Northwestern Algorithmic Trading Competition 2025  
**Organized by:** Northwestern Fintech (NUFT)  
**Sponsors:** IMC Trading, Hudson River Trading (HRT), Five Rings, Chicago Trading Company, All Options  
**Categories:**  
- High Frequency Trading (HFT)  
- Crypto Market-Making  
- Manual Trading Game  

Our team participated in the **HFT case**, which simulated an ultra-low-latency, multi-asset exchange environment. Competitors were ranked based on total **Profit and Loss (PnL)** after a full-day live session.  

---

## Results  
- **Case:** High Frequency Trading (HFT)  
- **Ranking:** Top 10 / 50 (20%)  
- **Performance Metric:** Final Net PnL (Capital + Portfolio Value)  
- **Execution:** Live on NUFT exchange platform during the in-person competition at Northwestern University  

---

## Technical Notes  
- Fully implemented within the **C++20 NUFT competition framework**.  
- Utilizes standard C++ STL only (no external libraries).  
- Designed to operate within exchange rate limits and memory constraints (≤1GB RAM, ≤0.5 CPU core).  
- Emphasized stability, risk mitigation, and deterministic order handling under high-frequency updates.  

---

## Acknowledgements  
We thank the **Northwestern Fintech Organizing Committee** and sponsors including **IMC Trading**, **Hudson River Trading**, **Five Rings**, **Chicago Trading Company**, and **All Options** for supporting this event and promoting hands-on algorithmic trading experience.  

---

## Authors  
**Parry Nall**  
**Ayush Chandra** 
