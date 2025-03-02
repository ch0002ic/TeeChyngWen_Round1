# Adaptive RL-enhanced candlestick trading strategy for dynamic markets

**Team TeeChyngWen**
*Innovating at the intersection of computational finance and deep learning*

---

## 📌 Overview
Financial markets demand strategies that evolve with shifting conditions. This project combines **candlestick pattern analysis** with **Reinforcement Learning (RL)** to create a dynamic trading system that adapts to unseen market behaviors. By integrating traditional technical indicators with modern deep learning techniques, our solution optimizes entry/exit signals, manages risk, and achieves robust performance across bull and bear markets.

**Key innovation**:
- **Hybrid architecture**: Fuses candlestick patterns (Doji, Engulfing, Morning Star) with RL-driven parameter optimization.
- **Adaptive risk management**: Uses RL to dynamically adjust stop-loss, take-profit, and position sizing based on market volatility (ATR) and momentum (RSI).
- **Market regime detection**: Employs Markov Switching Models to identify high/low volatility regimes, enhancing strategy responsiveness.

---

## 🚀 Features
### 1. **Candlestick pattern recognition**
   - Detects 15+ patterns (e.g., Hammer, Three White Soldiers) using rule-based logic.
   - Filters signals with trend (MA50) and momentum (RSI) indicators.
### 2. **Reinforcement learning optimization**
   - **RL framework**: Treats hyperparameter tuning as a **multi-armed bandit problem**, where the agent explores parameters (ATR multiplier, risk fraction) and exploits the best-performing combinations.
   - **Reward function**: Maximizes a composite score of Sharpe ratio (40%), total return (30%), drawdown (20%), and win rate (10%).
### 3. **Deep learning integration**
   - **LSTM-based market regime classifier** (future work): Analyzes sequences of returns to predict regime shifts.
   - **Transformer for sentiment integration** (future work): Processes news headlines to augment trading signals.
### 4. **Advanced backtesting engine**
   - Simulates realistic trading with slippage-free execution, dynamic stop-loss (1.5× ATR), and profit targets (2× risk).

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
