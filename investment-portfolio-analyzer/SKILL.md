---
name: investment-portfolio-analyzer
description: An advanced skill for in-depth analysis and management of investment portfolios using key risk and performance metrics.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Investment Portfolio Analyzer

## Overview
This skill provides a comprehensive and robust toolkit for analyzing, managing, and optimizing investment portfolios. It leverages a wide range of key financial metrics and models to assess performance, evaluate risk, and empower users to make data-driven, informed investment decisions. The skill is meticulously designed for a broad audience, from individual investors seeking to better understand their holdings to seasoned financial professionals requiring sophisticated analytical tools for client reporting and strategy development. By providing a structured workflow and clear explanations, this skill demystifies complex financial analysis, making it accessible and actionable.

## When to Use This Skill
This skill is particularly useful and recommended in the following scenarios:

*   **Routine Portfolio Health Checks:** Conduct periodic and thorough reviews of your portfolio's performance, risk exposure, and overall health. This is essential for long-term investment success.
*   **Due Diligence on New Investments:** Rigorously assess the potential impact of adding a new asset or security to your existing portfolio. This helps in making calculated investment choices.
*   **Comparative Analysis of Investment Strategies:** Systematically analyze and compare different asset allocation models, rebalancing strategies, and their potential long-term outcomes. This allows for strategic adjustments and optimization.
*   **Comprehensive Risk Management:** Proactively identify, quantify, and mitigate potential risks within your portfolio, including market risk, credit risk, and liquidity risk. A robust risk management process is crucial for preserving capital.
*   **Client and Stakeholder Reporting:** Generate detailed, professional, and easy-to-understand reports for clients, stakeholders, or for personal record-keeping and tax purposes. Clear communication is key to maintaining trust and confidence.
*   **Academic and Research Purposes:** Utilize the skill's capabilities for academic research, financial modeling, and backtesting of investment theories and strategies. The skill provides a practical framework for empirical finance studies.
*   **Scenario Analysis and Stress Testing:** Evaluate how your portfolio might perform under various adverse market conditions, helping you to build a more resilient investment strategy.

## Getting Started

Before you can use this skill, you need to have your portfolio data ready. The skill expects a CSV file with historical data for your assets and a JSON file that defines your portfolio's composition.

### Data Requirements

*   **Historical Data (CSV):** This file should contain the historical price and dividend data for each asset in your portfolio. The expected columns are `Date`, `Ticker`, `Adj Close`, `Volume`, and `Dividends`. You can obtain this data from various financial data providers like Yahoo Finance, Alpha Vantage, or Quandl.
*   **Portfolio Definition (JSON):** This file, named `portfolio.json`, defines the structure of your portfolio. It includes the name of the portfolio, the benchmark you want to compare it against, the risk-free rate, and the list of assets with their respective tickers and weights.

### Example Data Files

*   **`portfolio_data.csv`**

```csv
Date,Ticker,Adj Close,Volume,Dividends
2023-01-02,AAPL,125.07,112117500,0.0
2023-01-03,AAPL,125.02,127919900,0.0
...
```

*   **`portfolio.json`**

```json
{
  "name": "My Tech Portfolio",
  "benchmark": "^IXIC",
  "risk_free_rate": 0.02,
  "assets": [
    {"ticker": "AAPL", "weight": 0.4},
    {"ticker": "GOOGL", "weight": 0.3},
    {"ticker": "MSFT", "weight": 0.3}
  ]
}
```

## Core Capabilities

### 1. Performance Analysis
This capability focuses on the granular measurement and evaluation of a portfolio's historical and risk-adjusted performance.

*   **Total Return Calculation:** Accurately calculate the total return of the portfolio over any specified period, including capital gains and dividend income. This is the fundamental measure of performance.
*   **Benchmarking and Peer Comparison:** Compare the portfolio's performance against a wide range of relevant market indices (e.g., S&P 500, NASDAQ Composite, Russell 2000) and peer groups. This provides context to the portfolio's returns.
*   **Performance Attribution Analysis:** Decompose the portfolio's returns to determine the primary sources of performance, such as strategic asset allocation, tactical asset allocation, and individual security selection. This helps in understanding what drives the portfolio's performance.
*   **Rolling Returns:** Analyze the portfolio's performance over various rolling time periods (e.g., 1-year, 3-year, 5-year) to understand its consistency and behavior in different market cycles.
*   **Time-Weighted vs. Money-Weighted Returns:** Differentiate between time-weighted returns (which remove the effects of cash flows) and money-weighted returns (which are affected by the timing of cash flows) to get a clearer picture of performance.

### 2. Risk Assessment and Management
This capability provides a detailed, multi-faceted analysis of the various risks associated with an investment portfolio.

*   **Volatility Measurement (Standard Deviation):** Calculate the standard deviation of the portfolio's returns to quantify its historical volatility and price fluctuations. Higher standard deviation implies higher risk.
*   **Beta and Correlation Analysis:** Measure the portfolio's sensitivity to market movements (beta) and the correlation between different assets within the portfolio. Understanding these relationships is key to diversification.
*   **Value at Risk (VaR):** Estimate the potential loss of the portfolio over a specific time horizon with a given confidence level (e.g., 95% or 99% VaR). This metric provides a single number to quantify the portfolio's risk.
*   **Conditional Value at Risk (CVaR):** Also known as Expected Shortfall, CVaR measures the expected loss of the portfolio given that the loss is greater than the VaR. It provides a more complete picture of the tail risk.
*   **Sharpe Ratio:** Calculate the risk-adjusted return of the portfolio by measuring the excess return per unit of total risk (standard deviation). A higher Sharpe ratio is generally better.
*   **Treynor Ratio:** Measure the excess return earned for each unit of systematic risk (beta). This is useful for evaluating diversified portfolios.
*   **Jensen's Alpha:** Determine the portfolio's excess return over its expected return as predicted by the Capital Asset Pricing Model (CAPM), indicating the manager's value-add.
*   **Sortino Ratio:** A modification of the Sharpe ratio that only considers downside volatility, providing a more realistic measure of risk for investors who are more concerned with losses than overall volatility.
*   **Maximum Drawdown:** Calculate the largest peak-to-trough decline in the portfolio's value, which helps in understanding the potential for large losses.
*   **Omega Ratio:** A sophisticated risk-return performance measure that considers all moments of the return distribution, providing a more comprehensive view than Sharpe or Sortino ratios.

### 3. Portfolio Optimization
This capability assists users in constructing and optimizing their portfolios to align with their specific risk tolerance and investment objectives.

*   **Modern Portfolio Theory (MPT):** Employ the principles of MPT to find the optimal asset allocation that maximizes expected return for a given level of risk. This is the foundation of modern portfolio construction.
*   **Efficient Frontier:** Generate and visualize the efficient frontier, which represents the set of optimal portfolios that offer the highest expected return for a defined level of risk. This is a powerful visualization tool.
*   **Monte Carlo Simulation:** Run thousands of simulations to project the potential future performance of the portfolio under a wide range of market conditions and economic scenarios. This helps in understanding the range of potential outcomes.
*   **Backtesting:** Test the historical performance of a given investment strategy to evaluate its viability and potential for future success.
*   **Black-Litterman Model:** A more advanced portfolio optimization model that incorporates an investor's views on the expected returns of different assets, providing a more customized and flexible approach than traditional MPT.

## Step-by-Step Workflow

1.  **Gather and Prepare Portfolio Data:**
    *   Collect historical data for each asset in the portfolio, including daily or monthly prices and dividend payments. This data is crucial for accurate analysis.
    *   The data should be in a CSV format with the following columns: `Date`, `Ticker`, `Adj Close`, `Volume`, `Dividends`.
    *   Ensure the data is clean and free of errors, such as missing values or incorrect prices.

2.  **Define the Portfolio Composition:**
    *   Create a JSON file named `portfolio.json` that clearly defines the portfolio's composition, including the tickers of the assets and their respective weights.
    *   Example `portfolio.json`:

    ```json
    {
      "name": "My Aggressive Growth Portfolio",
      "benchmark": "^GSPC",
      "risk_free_rate": 0.02,
      "assets": [
        {"ticker": "AAPL", "weight": 0.25},
        {"ticker": "GOOGL", "weight": 0.20},
        {"ticker": "MSFT", "weight": 0.20},
        {"ticker": "AMZN", "weight": 0.15},
        {"ticker": "TSLA", "weight": 0.10},
        {"ticker": "NVDA", "weight": 0.10}
      ]
    }
    ```

3.  **Execute the Analysis Script:**
    *   Use the `Read` tool to load the historical portfolio data and the `portfolio.json` file into the agent's memory.
    *   Use the `Bash` tool to execute a Python script that performs the comprehensive analysis. This script will be the core of the skill's execution.
    *   The Python script should leverage powerful libraries such as `pandas` for data manipulation, `numpy` for numerical operations, `scipy` for statistical functions, and `matplotlib` or `plotly` for data visualization.

4.  **Generate a Comprehensive Report:**
    *   The Python script should be designed to generate a detailed report in Markdown format that summarizes all the findings from the analysis.
    *   The report should be well-structured and include tables, charts, and clear explanations of all the key metrics and their implications.

5.  **Review, Interpret, and Act on the Results:**
    *   Use the `Read` tool to carefully review the generated Markdown report.
    *   Interpret the results in the context of your investment goals and risk tolerance to make well-informed decisions about your portfolio.

## Best Practices and Considerations

*   **Data Quality is Paramount:** The accuracy and reliability of the analysis are directly dependent on the quality of the input data. Always use clean, accurate, and reliable sources for historical price and dividend data.
*   **Select an Appropriate Benchmark:** The choice of benchmark is critical for meaningful performance comparison. Select a benchmark that closely mirrors the portfolio's asset allocation, investment style, and geographic focus.
*   **Acknowledge the Limitations of Historical Data:** Remember that all analysis is based on historical data and past performance is not a guarantee of future results. Use the skill's outputs as a guide for decision-making, not as a definitive prediction of the future.
*   **The Power of Diversification:** Diversification is a fundamental principle of sound risk management. A well-diversified portfolio across different asset classes, geographies, and sectors can help to reduce risk without necessarily sacrificing returns.
*   **The Importance of Regular Reviews:** Financial markets are dynamic and constantly evolving. It is essential to review your portfolio on a regular basis and make adjustments as needed to stay on track with your financial goals.
*   **Consider Transaction Costs and Taxes:** The analysis provided by this skill does not typically account for transaction costs and taxes, which can have a significant impact on real-world returns. Always consider these factors in your investment decisions.
*   **Understand the Assumptions:** Be aware of the assumptions underlying the financial models used in this skill, such as the assumption of normal distribution of returns in some models. These assumptions may not always hold true in the real world.
*   **Behavioral Biases:** Be mindful of your own behavioral biases, such as loss aversion and overconfidence, which can lead to suboptimal investment decisions. This skill provides objective data to help you counteract these biases.

## Troubleshooting

*   **Data Errors:** If you encounter errors related to data, double-check the format and quality of your input CSV file. Ensure that there are no missing values or incorrect data types.
*   **Library Issues:** If you get errors related to Python libraries, make sure that all the required libraries (`pandas`, `numpy`, `scipy`, `matplotlib`, `plotly`) are installed in your environment.
*   **Incorrect Weights:** If the portfolio weights in your `portfolio.json` file do not sum to 1, the analysis may produce incorrect results. Always ensure that the weights are properly normalized.
*   **Benchmark Not Found:** If the specified benchmark is not found, you may need to use a different ticker or source for the benchmark data.
*   **API Rate Limits:** When fetching data from financial data providers, be mindful of any API rate limits to avoid being blocked.

## Advanced Examples and Code Snippets

### Example 1: Comprehensive Portfolio Return Calculation

```python
import pandas as pd
import json

# Load historical portfolio data
data = pd.read_csv('portfolio_data.csv', index_col='Date', parse_dates=True)

# Load portfolio definition
with open('portfolio.json') as f:
    portfolio = json.load(f)

# Calculate daily returns for each asset
returns = data.pct_change()

# Calculate weighted daily returns for the portfolio
asset_weights = [asset['weight'] for asset in portfolio['assets']]
weighted_returns = (returns * asset_weights).sum(axis=1)

# Calculate cumulative portfolio returns
cumulative_returns = (1 + weighted_returns).cumprod() - 1

# Plot the cumulative returns
import matplotlib.pyplot as plt
plt.figure(figsize=(12, 6))
plt.plot(cumulative_returns.index, cumulative_returns.values)
plt.title('Portfolio Cumulative Returns')
plt.xlabel('Date')
plt.ylabel('Cumulative Returns')
plt.grid(True)
plt.show()
```

### Example 2: Calculating and Interpreting Multiple Risk Metrics

```python
import numpy as np

# Calculate annualized return
annualized_return = weighted_returns.mean() * 252

# Calculate annualized volatility (standard deviation)
annualized_volatility = weighted_returns.std() * np.sqrt(252)

# Assume a risk-free rate from the portfolio definition
risk_free_rate = portfolio['risk_free_rate']

# Calculate the Sharpe Ratio
sharpe_ratio = (annualized_return - risk_free_rate) / annualized_volatility

# Calculate downside deviation for Sortino Ratio
downside_returns = weighted_returns[weighted_returns < 0]
downside_deviation = downside_returns.std() * np.sqrt(252)

# Calculate the Sortino Ratio
sortino_ratio = (annualized_return - risk_free_rate) / downside_deviation

print(f'Annualized Return: {annualized_return:.2%}')
print(f'Annualized Volatility: {annualized_volatility:.2%}')
print(f'Sharpe Ratio: {sharpe_ratio:.2f}')
print(f'Sortino Ratio: {sortino_ratio:.2f}')
```

### Example 3: Monte Carlo Simulation for Future Projections

```python
# Set up the Monte Carlo simulation parameters
num_simulations = 1000
num_days = 252  # 1 year

# Create a DataFrame to hold the simulation results
simulation_df = pd.DataFrame()

# Run the simulation
for x in range(num_simulations):
    count = 0
    daily_vol = weighted_returns.std()
    
    price_series = []
    
    price = cumulative_returns.iloc[-1]
    price_series.append(price)
    
    for i in range(num_days):
        price = price_series[count] * (1 + np.random.normal(0, daily_vol))
        price_series.append(price)
        count += 1
    
    simulation_df[x] = price_series

# Plot the simulation results
plt.figure(figsize=(12, 6))
plt.plot(simulation_df)
plt.title('Monte Carlo Simulation of Portfolio Performance')
plt.xlabel('Day')
plt.ylabel('Portfolio Value')
plt.show()
```

### Example 4: Efficient Frontier Optimization

```python
import numpy as np
import pandas as pd
from scipy.optimize import minimize

# Function to calculate portfolio performance
def portfolio_performance(weights, mean_returns, cov_matrix):
    returns = np.sum(mean_returns * weights) * 252
    std = np.sqrt(np.dot(weights.T, np.dot(cov_matrix, weights))) * np.sqrt(252)
    return returns, std

# Function to minimize (negative Sharpe Ratio)
def neg_sharpe_ratio(weights, mean_returns, cov_matrix, risk_free_rate):
    p_returns, p_std = portfolio_performance(weights, mean_returns, cov_matrix)
    return -(p_returns - risk_free_rate) / p_std

# Asset returns and covariance
mean_returns = returns.mean()
cov_matrix = returns.cov()
num_assets = len(mean_returns)

# Constraints and bounds
args = (mean_returns, cov_matrix, risk_free_rate)
constraints = ({'type': 'eq', 'fun': lambda x: np.sum(x) - 1})
bounds = tuple((0, 1) for asset in range(num_assets))

# Initial guess
initial_guess = num_assets * [1. / num_assets,]

# Optimize for maximum Sharpe Ratio
result = minimize(neg_sharpe_ratio, initial_guess, args=args,
                    method='SLSQP', bounds=bounds, constraints=constraints)

# Optimal weights
optimal_weights = result['x']
print('Optimal Weights:')
for ticker, weight in zip(returns.columns, optimal_weights):
    print(f'{ticker}: {weight:.2%}')
```

## Glossary of Terms

*   **Alpha:** A measure of the active return on an investment, the performance of that investment compared with a suitable benchmark.
*   **Beta:** A measure of the volatility, or systematic risk, of a security or a portfolio in comparison to the market as a whole.
*   **Correlation:** A statistical measure that expresses the extent to which two variables are linearly related, meaning they change together at a constant rate.
*   **Covariance:** A measure of the joint variability of two random variables.
*   **Diversification:** A risk management strategy that mixes a wide variety of investments within a portfolio.
*   **Efficient Frontier:** The set of optimal portfolios that offer the highest expected return for a defined level of risk or the lowest risk for a given level of expected return.
*   **Modern Portfolio Theory (MPT):** A theory on how risk-averse investors can construct portfolios to optimize or maximize expected return based on a given level of market risk.
*   **Sharpe Ratio:** A measure of risk-adjusted return, calculated as the average return earned in excess of the risk-free rate per unit of volatility or total risk.
*   **Standard Deviation:** A measure of the dispersion of a set of data from its mean.
*   **Value at Risk (VaR):** A statistic that quantifies the extent of possible financial losses within a firm, portfolio, or position over a specific time frame.

## Disclaimer

The information and tools provided by this skill are for educational and informational purposes only and do not constitute financial advice. The skill is not a substitute for professional financial advice from a qualified financial advisor. Investment decisions should be made based on your own personal financial situation and investment objectives. The author and publisher of this skill are not liable for any losses or damages arising from the use of this information.

## References and Further Reading

*   [Investopedia: A Guide to Modern Portfolio Theory (MPT)](https://www.investopedia.com/terms/m/modernportfoliotheory.asp)
*   [Investopedia: Measuring a Portfolio's Performance](https://www.investopedia.com/articles/08/performance-measure.asp)
*   [CION Investments: 5 Key Metrics to Benchmark a Portfolio](https://cioninvestments.com/insights/portfolio-benchmarks-key-metrics/)
*   [Portfolio Visualizer: An advanced online tool for portfolio analysis](https://www.portfoliovisualizer.com/)
*   ["A Random Walk Down Wall Street" by Burton Malkiel](https://www.amazon.com/Random-Walk-Down-Wall-Street/dp/0393358380)
*   ["The Intelligent Investor" by Benjamin Graham](https://www.amazon.com/Intelligent-Investor-Definitive-Investing-Essentials/dp/0060555661)
*   ["Fooled by Randomness" by Nassim Nicholas Taleb](https://www.amazon.com/Fooled-Randomness-Hidden-Chance-Markets/dp/0812975219)
*   [Python for Finance: Cookbook](https://www.oreilly.com/library/view/python-for-finance/9781492024329/)

---

*This skill was created by an AI agent and has been reviewed by a human.*
