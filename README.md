# Adaptive RL-enhanced candlestick trading strategy for dynamic markets

**Team TeeChyngWen**

*Innovating at the intersection of finance and deep learning*

---

## 📌 Overview
Financial markets demand strategies that evolve with shifting conditions. This project combines **candlestick pattern analysis** with **reinforcement learning (RL)** to create a dynamic trading system that adapts to unseen market behaviors. By integrating traditional technical indicators with modern deep learning techniques, our solution optimizes entry/exit signals, manages risk, and achieves robust performance across bull and bear markets.

**Key innovation**
- **Hybrid architecture**: Fuses candlestick patterns (Doji, Engulfing, Morning Star) with RL-driven parameter optimization
- **Adaptive risk management**: Uses RL to dynamically adjust stop-loss, take-profit, and position sizing based on market volatility (ATR) and momentum (RSI)
- **Market regime detection**: Employs Markov Switching Models to identify high/low volatility regimes, enhancing strategy responsiveness

---

## 🚀 Features
### 1. **Candlestick pattern recognition**
   - Detects 15+ patterns (e.g., Hammer, Three White Soldiers) using rule-based logic
   - Filters signals with trend (MA50) and momentum (RSI) indicators
### 2. **Reinforcement learning optimization**
   - **RL framework**: Treats hyperparameter tuning as a **multi-armed bandit problem**, where the agent explores parameters (ATR multiplier, risk fraction) and exploits the best-performing combinations
   - **Reward function**: Maximizes a composite score of Sharpe ratio (40%), total return (30%), drawdown (20%), and win rate (10%)
### 3. **Deep learning integration**  
   - **LSTM-based market regime classifier** (future work): Analyzes sequences of returns to predict regime shifts
   - **Transformer for sentiment integration** (future work): Processes news headlines to augment trading signals
### 4. **Advanced backtesting engine**
   - Simulates realistic trading with slippage-free execution, dynamic stop-loss (1.5× ATR), and profit targets (2× risk)

---

## 🛠 Technical architecture
```python
# Simplified RL optimization loop (pseudocode)
for episode in range(n_iter):
    params = agent.choose_parameters()  # RL policy selects parameters
    backtester = Backtester(data, params)
    metrics = backtester.run_backtest()
    reward = calculate_reward(metrics)  # Composite score
    agent.update_policy(reward)         # Q-learning update
```

### Pipeline
1. **Data ingestion**: Fetch OHLCV data from Yahoo Finance (`yfinance`)
2. **Feature engineering**
   - Technical indicators (MA50, ATR, RSI)
   - Candlestick body/wick metrics and pattern detection
3. **Signal generation**
   - Bullish/bearish signals derived from pattern combinations
   - RL-optimized entry/exit filters
4. **Backtesting & risk management**:
   - Monte Carlo simulations for robustness testing
   - Drawdown and VaR analysis

---

## 📈 Performance highlights
### Backtest results (2020–2025)
| Metric                | Value                          |
|-----------------------|--------------------------------|
| **Total return**      | 487,338,356,149,417,142%       |
| **Sharpe ratio**      | 1.97                          |
| **Max drawdown**      | -11.88%                       |
| **Win rate**          | 44.93%                        |
| **Profit factor**     | 1.10                          |

### Stress testing
- **COVID-19 crash (2020)**: +677.56% return | 0% drawdown
- **2022 bear market**: +185,181,423.68% return | -6.30% drawdown

**Equity curve**
<img width="1089" alt="image" src="https://github.com/user-attachments/assets/ea148209-bb79-4975-999b-96508261d8b3"/>
*Strategy vs. buy & hold (cumulative returns)*

---

## 🏆 Alignment with criteria guidelines
### **Innovation**
- **Novel hybrid approach**: First to combine candlestick patterns with RL for parameter optimization
- **Self-adjusting thresholds**: Dynamic ATR-based stops adapt to volatility, avoiding static rules
### **Technical complexity**
- **Multi-model integration**: SARIMAX for factor analysis, Markov Switching for regimes, and RL for decision-making
- **Code scalability**: Modular backtester supports equities, forex, and crypto
### **Impact**  
- **Robustness**: Validated across 50+ hyperparameter iterations and historical crises
- **Real-world relevance**: Achieved a 1.97 Sharpe ratio, outperforming S&P 500
### **Presentation**
- **Interactive visuals**: Heatmaps, Q-Q plots, and autocorrelation analysis
- **Clear documentation**: Readable code with inline comments and Jupyter notebooks

---

## 🛠 Installation & usage
1. **Install dependencies**
   ```bash
   pip install yfinance pandas numpy matplotlib statsmodels scipy seaborn
   ```
2. **Run strategy**
   ```python
   from backtester import Backtester
   data = load_data('AAPL', start='2020-01-01')
   bt = Backtester(data)
   metrics, returns = bt.run_backtest()
   ```
3. **Optimize via RL**
   ```python
   best_params = optimize_strategy(data, n_iter=50)
   ```

---

## 🌟 Future work
- **Incorporate LSTM/transformers**: For sequential pattern detection and news sentiment analysis
- **Live trading API**: Connect to interactive brokers for real-world deployment
- **Federated learning**: Collaborate across asset classes to improve generalizability

---

**🌟 "The market is a pendulum; our AI is the counter-swing." — Team TeeChyngWen**
