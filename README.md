
# GanTrade - Automated trading

<a href="http://makeapullrequest.com">
 <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" />
</a>

This repository contains a trading bot. The bot implements some strategies (RSI+EMA, Stochastic Oscillator, ATR) and works on the Binance currency exchange.

## Installation

Clone the repository and add at least one API key to the `application.yaml` file. 

Configuration example:

```yaml
app:
    binance:
        api-key: <API-KEY>
        secret-key: <API-SECRET>
    bot:
        rsi-ema-bot:
            sma-period-1: <MOVING-AVARAGE-PERIOD>
            sma-period-2: <MOVING-AVARAGE-PERIOD>
            sma-period-3: <MOVING-AVARAGE-PERIOD>
            stop-loss-threshold: <STOP-LOSS-THRESHOLD>
            stop-gain-threshold: <STOP-GAIN-THRESHOLD>
            rsi-period: <RSI-PERIOD>
            rsi-threshold: <RSI-THRESHOLD>
    telegram:
        username: <TELEGRAM-BOT-USERNAME>
        token: <TELEGRAM-BOT-TOKEN>
        chat-id: <TELEGRAM-BOT-CHAT-ID>
```

After the configuration is done, you can start the `RsiEmaBot` via api (see api.yaml) or via telegram.

# Strategies
GanTradeBot contains many major trend following strategies (RSI+EMA, Stochastic Oscillator, ATR) 

## RsiEmaBot
The RsiEmaBot bot uses three simple moving averages with different lengths. A buy is triggered when `ema short > ema middle > ema long` and a sell is triggered when the `ema short < ema middle` or `ema short < ema long` or `price bought descrease 3%`. A RSI (Relative Strength Index) filter can be applied, buys only executed when the RSI indicator confirms a trend (`RSI >= 50`).
