# Simple Breakout Strategy (QuantConnect / Python)

This project implements a basic **breakout trading strategy** using the QuantConnect algorithmic trading platform. It is designed to trade the SPY ETF based on breakout levels over a dynamic lookback window, adjusted using recent volatility.

## 📈 Strategy Overview

- Trades **SPY** on a **daily resolution**
- Uses a **breakout signal** based on the highest high over a lookback period
- Adjusts lookback length dynamically based on changes in volatility
- Implements a **trailing stop-loss** for risk management
- Only enters one position at a time

## 🧠 Core Logic

- **Breakout Entry**: Enters a long position when the current close price exceeds the highest high over the past `lookback` days.
- **Dynamic Lookback**: `lookback` period adjusts daily depending on changes in 30-day price volatility.
- **Trailing Stop**: A stop-loss order is placed after entry and is updated if price moves in favor, trailing the peak price.

## ⚙️ Key Parameters

| Parameter           | Description                              |
|---------------------|------------------------------------------|
| `lookback`          | Initial lookback period (20 days)        |
| `ceiling`, `floor`  | Bounds for lookback period (10-30 days)  |
| `initialStopRisk`   | Stop-loss multiplier from breakout level (0.98) |
| `trailingStopRisk`  | Trailing stop-loss multiplier (0.90)     |

## 📅 Scheduling

The strategy runs logic **20 minutes after market open** using `Schedule.On`, ensuring that intraday volatility has settled before signals are evaluated.

## 🛠 Requirements

- [QuantConnect](https://www.quantconnect.com/) environment
- Python 3
- NumPy

## 📊 Plotting

The algorithm generates plots for:
- Asset price (`SPY`)
- Active trailing stop price (`Stop Price`)

## 🚀 How to Use

1. Upload the script to QuantConnect's Research or Algorithm Lab.
2. Set the backtest period and initial capital.
3. Run the backtest and review performance, logs, and charts.

## 🤝 Credits

Developed using the QuantConnect Lean Algorithm Framework.

---

Feel free to modify the parameters or symbols to suit your trading ideas!
