# freqtrade-java

Simple High frequency trading bot for crypto currencies in Java. This project is largely inspired by [freqtrade](https://github.com/gcarq/freqtrade) in Python. 
Currently supports trading on Bittrex exchange.

This software is for educational purposes only. Don't risk money which you are afraid to lose.

The command interface is accessible via Telegram (not required).
Just register a new bot on https://telegram.me/BotFather
and enter the telegram `token` and your `chat_id` in `config.json`

Persistence is achieved through hsqldb.

#### Telegram RPC commands:
* /start: Starts the trader
* /stop: Stops the trader
* /status: Lists all open trades
* /profit: Lists cumulative profit from all finished trades
* /forcesell <trade_id>: Instantly sells the given trade (Ignoring `minimum_roi`).
* /performance: Show performance of each finished trade grouped by pair

#### Config
`minimal_roi` is a JSON object where the key is a duration
in minutes and the value is the minimum ROI in percent.
See the example below:

```
"minimal_roi": {
    "2880": 0.005, # Sell after 48 hours if there is at least 0.5% profit
    "1440": 0.01,  # Sell after 24 hours if there is at least 1% profit
    "720":  0.02,  # Sell after 12 hours if there is at least 2% profit
    "360":  0.02,  # Sell after 6 hours if there is at least 2% profit
    "0":    0.025  # Sell immediately if there is at least 2.5% profit
},
```

`stoploss` is loss in percentage that should trigger a sale. 
For example value `-0.10` will cause immediate sell if the
profit dips below -10% for a given trade. This parameter is optional.

The other values should be self-explanatory, if not feel free to raise a github issue.

#### Prerequisites
* Java 8

#### Execute tests

```
$ ./mvnw test
```

