# Backtester
Backtester is a simple Python backtesting engine for any strategies to simulate trading on historical market data.


## Features

* Download historical price data via Yahoo Finance (`yfinance`).
* Define and apply simple trading strategies (e.g., SMA crossover).
* Execute simulated trades with position sizing based on a risk percentage.
* Calculate performance metrics:

  * Total returns
  * Annualized returns
  * Annualized volatility
  * Sharpe ratio
  * Total P\&L, average trade return, and win ratio
* Plot portfolio value and buy/sell signals over time.

## Requirements

* Python 3.8+
* pandas
* numpy
* matplotlib
* ta (Technical Analysis library)
* yfinance

Install dependencies:

```bash
pip install pandas numpy matplotlib ta yfinance
```

## Usage

1. **Clone or download the repository**

   ```bash
   ```

git clone  cd backtesting

````

2. **Run the backtester**
   ```bash
python backtester.py
````

3. **Follow the prompts**:

   * Enter the stock symbol you want to backtest (e.g., `AAPL`).
   * Enter the start date (`YYYY-MM-DD`).
   * Enter the end date (`YYYY-MM-DD`).
   * Enter the initial cash amount (e.g., `100000`).
   * Enter the risk percentage (0-1, e.g., `0.02` for 2% risk per trade).

4. **View results**:

   * A plot window will display portfolio value and buy/sell signals.
   * Performance metrics will be printed to the console.

## Code Structure

* \`\`: Main script containing:

  * `get_marktet_data`: Download historical data from Yahoo Finance.
  * `BacktestingEngine` class:

    * `execute_trade`: Simulate trade execution.
    * `run_backtest`: Iterate through data and generate trades based on `signal` column.
    * `calculate_performance`: Compute P\&L, returns, win ratio, and other metrics.
    * `get_portfolio_value`: Calculate portfolio value at a given price.
    * `get_portfolio_returns`: Generate daily portfolio return series.
    * `plot_portfolio_value`: Plot portfolio value and signals.
  * `main`: User prompts, strategy definition (SMA crossover), and orchestration.

## Strategy

A simple **20/50-period SMA crossover**:

* **Buy** when the 20-day SMA crosses above the 50-day SMA.
* **Sell** when the 20-day SMA crosses below the 50-day SMA.

Signal column is created as:

```python
data['signal'] = np.where(sma_short > sma_long, 1, 0)
```

## Customization

* **Strategies**: Replace the SMA crossover logic with your own indicators (EMA, RSI, Bollinger Bands, etc.).
* **Risk management**: Adjust position sizing or add stop-loss/take-profit rules in `run_backtest`.
* **Performance**: Extend `calculate_performance` to include drawdown, max drawdown, and other metrics.

