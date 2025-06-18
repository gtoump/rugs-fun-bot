# 📄 Rugs.Fun Trading Bot — Specification

## 🎯 Objectives
Build an automated trading bot that operates on Rugs.Fun’s free paper mode, using simulated 100 free token to:
- **Test and refine trading strategies** using real-time fake-token charts  
- **Learn market patterns** and execution dynamics  
- Rank on the paper-mode leaderboard purely for performance validation  
- **Prepare** to deploy the same strategies with real SOL

**Performance Goal**: Demonstrate a consistent positive edge (e.g. net +1% SOL P&L per week) in paper mode  
**Uptime**: ≥ 95% bot runtime, 24/7 execution loop

---

## ⚙️ Strategy Approach

### Initial Strategies:
1. **Mean Reversion**  
   - Entry: price dips >1.5% below 1-min SMA  
   - Exit: price reverts to SMA or a 0.5% stop‑loss  

2. **Momentum Breakout**  
   - Entry: price breaks above prior high by +1% in 10s with volume surge  
   - Exit: take-profit at +0.75%, stop‑loss at −0.3%  

3. **Volume Spike Scalping**  
   - Entry: on volume > 3× 1‑min average  
   - Exit: trailing stop (e.g. −0.2%) or quick profit lock-in  

---

## 🛑 Risk Management
- **Max Position Size**: 1 SOL per token  
- **Daily Max Exposure**: 5 SOL  
- **Stop‑Loss (daily)**: −1.5 SOL  
- **Max Trade Duration**: 2 minutes  
- **Anti‑Rug Exit**: force exit if price drops >4% in <5 s  

---

## 🧠 Data & Backtesting
- **Real‑time tick capture** via WebSocket  
- **Storage**: SQLite (or PostgreSQL) via SQLAlchemy  
- **Backtester**: replay historical ticks, simulate fills with slippage & fees  
- **Key Metrics**: P&L, win‑rate, avg trade duration, max drawdown  

---

## 🔨 Tech Stack
| Component   | Tool/Library          |
|-------------|-----------------------|
| Language    | Python 3.10           |
| Container   | Docker                |
| DB          | SQLite + SQLAlchemy   |
| Analysis    | Pandas, Matplotlib    |
| Execution   | Asyncio + websockets  |
| Scheduler   | APScheduler (optional)|
| Monitoring  | Console logs (later Grafana)|

---

## 📊 Success Metrics
| KPI                 | Target by Day 30          |
|---------------------|---------------------------|
| Net Weekly P&L      | ≥ +1% per week (paper)    |
| Max Daily Drawdown  | ≤ 2%                       |
| Bot Uptime          | ≥ 95%                      |
| Pattern Insights    | Documented in EDA reports |

---

## 🧩 Future Enhancements
- **ML‑based signals** (LightGBM, LSTM)  
- **Automated alerts** via Discord/Slack  
- **Real‑SOL deployment** with identical risk rules  
- **Live leaderboard monitoring** and auto‑tuning  
