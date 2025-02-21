# NL 3.1 Optimized Expert Advisor (EA)

![MetaTrader EA](https://img.shields.io/badge/Platform-MetaTrader%204%2F5-blue) 
![Version](https://img.shields.io/badge/Version-3.1-green) 
![License](https://img.shields.io/badge/License-Proprietary-orange)

**NL 3.1 Optimized** is a sophisticated multi-strategy trading EA designed for Forex and commodities, combining traditional technical analysis with cutting-edge machine learning and quantum-inspired optimization. Optimized for `XAUUSD` (Gold) on the 1-minute timeframe, it dynamically adapts to market conditions while prioritizing robust risk management.

---

## 📌 Key Features

### 🔄 **Multi-Strategy Core**
- **Trend Following**: LWMA crossovers + ATR volatility filter
- **Scalping**: Short-term MA momentum + RSI overbought/oversold zones
- **Statistical Arbitrage**: Multi-symbol correlation matrix analysis
- **Market Making**: Stealth order layering with liquidity detection

### 🧠 **Advanced Technologies**
- **Neural Network**: 5-input MLP (price, volume, volatility, trend, equity) for directional bias
- **Quantum Optimization**: Genetic algorithm with quantum-inspired jumps for parameter tuning
- **Regime Detection**: Kurtosis/skewness analysis (high volatility/trending/mean reversion)

### 🛡️ **Risk Management System**
- Volatility-adaptive position sizing (ATR-based)
- Dynamic trailing stops with breakeven triggers
- Circuit breakers for flash crashes & news events
- Daily loss limits with automatic cooldown

---

## ⚙️ Input Parameters

### 📊 Trading Settings
| Parameter | Description | Default |
|-----------|-------------|---------|
| `InpSymbol` | Trading symbol | `XAUUSD` |
| `InpTimeframe` | Chart timeframe | `PERIOD_M1` |
| `InpMaxTrades` | Maximum simultaneous trades | `3` |

### 📉 Indicators
| Parameter | Description | Default |
|-----------|-------------|---------|
| `InpATRPeriod` | ATR period for volatility | `14` |
| `InpMATrendPeriod` | Long-term MA period | `50` |
| `InpMAScalpPeriod` | Short-term MA period | `20` |
| `InpRSIPeriod` | RSI period | `14` |

### ⚠️ Risk Management
| Parameter | Description | Default |
|-----------|-------------|---------|
| `InpRiskPercent` | Risk per trade (%) | `0.25` |
| `InpMaxDailyLoss` | Daily loss limit (%) | `5.0` |
| `InpMaxSpread` | Maximum allowed spread (pts) | `30.0` |

### 🤖 Advanced Features
| Parameter | Description | Default |
|-----------|-------------|---------|
| `UseNeuralNet` | Enable neural network | `true` |
| `InpQuantumOptimize` | Enable quantum optimization | `true` |
| `InpStealthMode` | Use limit orders for entries | `true` |

---

## 📈 Strategy Logic

### Trend Identification
1. **Primary Trend**: 50-period LWMA slope + position relative to MA
2. **Scalp Signal**: 20-period LWMA crossover + RSI filter
3. **Volatility Filter**: ATR threshold for minimum trade size

### Entry Conditions
- **Bullish**: Price > both MAs + RSI < Overbought + NN confidence > 0.8
- **Bearish**: Price < both MAs + RSI > Oversold + NN confidence < -0.8

### Exit Management
- **TP/SL**: ATR multiples (1.5x/2.0x default) adjusted for market regime
- **Partial Close**: 75% position closure at 50% TP target
- **Trailing Stop**: Activated after 100pts profit, trails at 20pt increments

---

## 🧩 Advanced Systems

### Neural Network Architecture
- **Input Layer**: 
  - Price momentum 
  - Volume profile
  - Normalized volatility 
  - Trend strength
  - Equity curve
- **Hidden Layer**: 10 neurons (tanh activation)
- **Output**: Directional confidence [-1, +1]

### Quantum Optimization
- **Parameters Tuned**:
  - ATR multipliers
  - RSI thresholds
  - MA periods
  - Risk percentage
- **Fitness Function**: 
  ```math
  Fitness = (Profit/Trade) × WinRate − MaxDrawdown/Equity
  ```

### Correlation Matrix
- **Symbols**: 8 major FX pairs + metals
- **Analysis**: Log-returns correlation over 100 bars
- **Arbitrage**: Fade extremes (<-0.8 or >+0.8)

---

## 💻 Installation

1. **Requirements**:
   - MetaTrader 4/5
   - Minimum account balance: $1,000 (recommended)
   - VPS with low latency

2. **Installation Steps**:
   ```bash
   Copy "NL 3.1 Optimized.ex5" to MQL5/Experts/
   Copy included indicators to MQL5/Indicators/
   Restart MT5 terminal
   Attach EA to XAUUSD M1 chart
   ```

3. **Initial Setup**:
   - Enable DLL imports
   - Allow live trading
   - Set proper symbol permissions

---

## ⚠️ Important Notes

- **News Filter**: Requires economic calendar access (IC Markets calendar used)
- **Optimization**: Pre-optimized for XAUUSD but adaptable to other symbols
- **Leverage**: Recommended 1:100-1:200
- **Broker Requirements**: Raw spread account preferred

---

## 📜 Disclaimer

This EA comes with no warranty. Past performance ≠ future results. Test thoroughly in demo before live use. The developer not responsible for trading losses. By using this EA, you agree to assume all risks.

---

**Copyright © 2025 H3NST7** - [www.H3NST7.com](https://www.H3NST7.com)
