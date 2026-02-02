'''markdown
---
name: crypto-tracker
description: "Use this skill to track cryptocurrency prices, market trends, and manage crypto portfolios. Triggers: crypto, cryptocurrency, bitcoin, ethereum, BTC, ETH, price, value, portfolio, market cap, blockfolio, cotação, criptomoeda, valor, preço."
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Crypto Tracker: Real-Time Cryptocurrency Tracking and Analysis

## Overview

## Automatic Triggers

**ALWAYS activate this skill when user mentions:**
- Keywords: crypto, cryptocurrency, bitcoin, ethereum, BTC, ETH, altcoin, token, price, value, cotação, preço, valor, market cap, portfolio, blockfolio
- Phrases: "what's the price of", "how is the crypto market", "track my crypto", "crypto portfolio value", "qual o preço de", "valor do bitcoin", "mercado de cripto"
- Context: Any discussion about monitoring cryptocurrency prices, managing a crypto investment portfolio, or analyzing market trends.

**Example user queries that trigger this skill:**
- "What is the current price of Bitcoin in USD?"
- "Can you track my crypto portfolio for me?"
- "Qual a cotação do Ethereum em Reais?"
- "Show me the top 10 cryptocurrencies by market cap."

The Crypto Tracker skill empowers Manus to monitor cryptocurrency markets, providing real-time price data, customizable alerts, and basic market analysis. It leverages browser automation and data extraction to gather information from reliable financial data sources (e.g., CoinMarketCap, CoinGecko, Binance). This skill is designed for users who need to stay updated on cryptocurrency movements, whether for trading, investment monitoring, or research purposes. It can fetch current prices, track portfolio values, notify users of significant price changes, and provide summaries of market trends.

## When to Use This Skill

This skill is particularly useful in the following scenarios:

*   **Active Trading:** When you need to make quick decisions based on real-time price action and require immediate alerts for specific price targets.
*   **Investment Monitoring:** To keep track of the value of your long-term cryptocurrency portfolio without manually checking prices constantly.
*   **Market Research:** To gather data on historical performance, trading volume, and market capitalization for various cryptocurrencies.
*   **Automated Reporting:** To generate regular reports on the status of your favorite cryptocurrencies or overall market trends.
*   **Risk Management:** To set alerts for sudden price drops (stop-loss alerts) or significant market volatility.
*   **General Interest:** For enthusiasts who want to follow the crypto market and learn more about different digital assets.

## Core Capabilities

### 1. Real-Time Price Fetching

The skill can retrieve the current price of any specified cryptocurrency from major data providers. It can handle multiple pairs (e.g., BTC/USD, ETH/BRL) and fetch data with minimal delay.

*   **Functionality:** Fetches the latest price, 24h change, and trading volume.
*   **Tools Used:** `Browser`, `Read`
*   **Example:** "Get the current price of Bitcoin in USD."

### 2. Customizable Price Alerts

Users can set up alerts to be notified when a cryptocurrency reaches a specific price target, goes above or below a threshold, or changes by a certain percentage.

*   **Functionality:** Creates, manages, and triggers alerts based on user-defined conditions.
*   **Tools Used:** `Write`, `Edit`, `Bash` (for scheduled checks)
*   **Template:**
    ```json
    {
      "alert_name": "BTC_Above_70k",
      "asset": "Bitcoin",
      "condition": "above",
      "target_price_usd": 70000,
      "notification_method": "email", // or 'sms', 'log'
      "status": "active"
    }
    ```

### 3. Portfolio Tracking

The skill can monitor a user-defined portfolio of cryptocurrencies, calculating the total value in a specified fiat currency and tracking its performance over time.

*   **Functionality:** Aggregates the value of multiple assets and reports the total.
*   **Tools Used:** `Read`, `Write`, `Edit`
*   **Template (portfolio.json):**
    ```json
    {
      "portfolio_name": "My HODL Stash",
      "base_currency": "USD",
      "assets": [
        {"symbol": "BTC", "amount": 0.5},
        {"symbol": "ETH", "amount": 10},
        {"symbol": "SOL", "amount": 150}
      ]
    }
    ```

### 4. Basic Market Analysis

The skill can provide a summary of market conditions, including top gainers and losers, overall market capitalization, and Bitcoin dominance.

*   **Functionality:** Scrapes and synthesizes key market indicators.
*   **Tools Used:** `Browser`, `Read`
*   **Example:** "What are the top 5 performing altcoins today?"

## Step-by-Step Workflow

This workflow outlines how to use the Crypto Tracker skill for a common task: setting a price alert for Ethereum (ETH).

1.  **Initiate the Task:**
    *   **User Prompt:** "Manus, I want to set a price alert for Ethereum. Notify me when it drops below $3,000."

2.  **Information Gathering (Internal):**
    *   Manus identifies the core intent: create a price alert.
    *   It parses the key parameters: Asset (Ethereum), Condition (below), Target Price ($3,000).

3.  **Define the Alert Structure:**
    *   Manus uses the `Write` tool to create a JSON file to store the alert configuration. This ensures persistence and allows for easy management.
    *   **Action:** `file.write('alerts.json', '[{"asset": "Ethereum", "symbol": "ETH", "condition": "below", "target_price_usd": 3000, "status": "active"}]')`

4.  **Create the Monitoring Script:**
    *   Manus writes a shell script (`check_price.sh`) that will be executed periodically. This script will:
        a.  Use the `Browser` tool (via shell commands like `curl` or a headless browser script) to navigate to a reliable crypto data website (e.g., `https://api.coingecko.com/api/v3/simple/price?ids=ethereum&vs_currencies=usd`).
        b.  Extract the current price of ETH.
        c.  Use the `Read` tool to load the `alerts.json` file.
        d.  Compare the current price with the target price and condition.
        e.  If the condition is met, trigger a notification.

    *   **Action (`check_price.sh`):**
        ```bash
        #!/bin/bash
        
        # Read alert configuration
        ALERT_CONFIG=$(cat alerts.json)
        TARGET_PRICE=$(echo $ALERT_CONFIG | jq -r '.[0].target_price_usd')
        
        # Fetch current price from an API
        CURRENT_PRICE=$(curl -s 'https://api.coingecko.com/api/v3/simple/price?ids=ethereum&vs_currencies=usd' | jq -r '.ethereum.usd')
        
        # Check condition (using bc for floating point comparison)
        if (( $(echo "$CURRENT_PRICE < $TARGET_PRICE" | bc -l) )); then
            echo "ALERT: Ethereum has dropped below $TARGET_PRICE! Current price: $CURRENT_PRICE"
            # Here, you would add a command to send an email, log, or other notification
            # For now, we just print to stdout and update the alert status
            
            # Deactivate the alert to avoid repeated notifications
            UPDATED_CONFIG=$(echo $ALERT_CONFIG | jq '.[0].status = "triggered"')
            echo $UPDATED_CONFIG > alerts.json
        else
            echo "Condition not met. Current price: $CURRENT_PRICE"
        fi
        ```

5.  **Schedule the Check:**
    *   Manus uses `Bash` with `cron` or a simple `watch` command to run the `check_price.sh` script at a regular interval (e.g., every 5 minutes).
    *   **Action:** `shell.exec('chmod +x check_price.sh && watch -n 300 ./check_price.sh')`
    *   *Note: For a true background task, a `cronjob` would be more robust.* `(crontab -l ; echo "*/5 * * * * /home/ubuntu/check_price.sh") | crontab -`

6.  **Report to User:**
    *   Manus confirms that the alert has been set up successfully.
    *   **Response:** "I have set an alert for Ethereum to notify you if the price drops below $3,000. I will monitor it every 5 minutes."

## Best Practices

*   **Use Reliable Data Sources:** Always prefer official APIs (like CoinGecko, Binance) over scraping consumer-facing websites. APIs are more stable and provide structured data. If scraping is necessary, target specific, stable HTML elements.
*   **Persist Configuration:** Store user configurations like alerts and portfolios in files (e.g., `config.json`). This makes the skill stateful and robust across sessions.
*   **Handle Errors Gracefully:** Network requests can fail. Implement retry logic and clear error messages. If a price can't be fetched, inform the user and try again later.
*   **Avoid Over-Polling:** Be mindful of API rate limits. Do not check prices too frequently (e.g., every second). A check every 1-5 minutes is sufficient for most non-critical use cases.
*   **Use `jq` for JSON Processing:** When working with JSON data in shell scripts, the `jq` utility is indispensable for parsing and manipulation. It's more reliable than using `grep` or `awk`.
*   **Parameterize Scripts:** Write your scripts to be reusable. Instead of hardcoding "Ethereum", pass the asset name or symbol as an argument to the script.
*   **Security:** Never ask for or store private keys or exchange API keys with write/trade access. The skill should only require public addresses for tracking or read-only API keys.

## Examples

### Example 1: Get the price of multiple cryptocurrencies

*   **User Prompt:** "What are the current prices of Solana, Cardano, and Polkadot?"
*   **Action Flow:**
    1.  Manus constructs a single API call if the source supports it (e.g., `https://api.coingecko.com/api/v3/simple/price?ids=solana,cardano,polkadot&vs_currencies=usd`).
    2.  It uses `curl` to fetch the data.
    3.  It parses the JSON response using `jq`.
    4.  It formats the output into a user-friendly table or list.
*   **Response:**
    ```
    Here are the current prices:
    - Solana (SOL): $150.25
    - Cardano (ADA): $0.45
    - Polkadot (DOT): $7.10
    ```

### Example 2: Track a simple portfolio

*   **User Prompt:** "I have a portfolio with 2 BTC and 30 ETH. What is its total value in USD?"
*   **Action Flow:**
    1.  Manus creates a temporary `portfolio.json` file using the `Write` tool.
    2.  It fetches the current prices for BTC and ETH.
    3.  It calculates the total value: `(2 * price_btc) + (30 * price_eth)`.
    4.  It presents the final calculation to the user.
*   **Response:** "Based on current prices, your portfolio with 2 BTC and 30 ETH is valued at approximately $200,500 USD."

### Example 3: Find the top gainer of the day

*   **User Prompt:** "Which crypto in the top 100 has gained the most in the last 24 hours?"
*   **Action Flow:**
    1.  Manus uses the `Browser` tool to navigate to CoinMarketCap or CoinGecko's "Top Gainers" page.
    2.  It uses `Read` or a scraping script to extract the list of cryptocurrencies and their 24h percentage change.
    3.  It identifies the top performer from the list.
*   **Response:** "Today's top gainer in the top 100 is XYZ coin, with a 45% increase in the last 24 hours."

## References

*   **[CoinGecko API Documentation](https://www.coingecko.com/en/api/documentation):** A comprehensive and free API for cryptocurrency data.
*   **[CoinMarketCap API](https://coinmarketcap.com/api/):** Another widely used source for market data.
*   **[jq Manual](https://stedolan.github.io/jq/manual/):** The official documentation for the `jq` JSON processor.
*   **[Bash Scripting Guide](https://tldp.org/LDP/abs/html/):** An in-depth guide to shell scripting for more complex logic.
*   **[Crontab Generator](https://crontab.guru/):** A helpful tool for creating `cron` scheduling expressions.

'''
