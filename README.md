# btc-algo
This project focuses on creating a basic momentum algorithm for trading bitcoin (can eventually be applied to any crypto). This README file will provide a thorough overview of the project, and markdown cells and documentation within the notebook provide further details.

## Abstract


## Introduction
I started this project because I wanted to learn how to create a working trading algorithm, and I chose to use cryptocurrencies because Coinbase Pro has a very user-friendly and free API for retreiving data about cryptos. After reading about popular trading algorithms, I chose to experiment with a momentum algorithm due to its simplicity and flexibility. I read that a good way to implement a momentum based algo is to choose two different interval moving averages (e.g. 5 minutes and 20 minutes), and to buy the crypto when the shorter average is higher than the longer average and sell if the opposite occurs. I first coded this algorithm, and then applied it to historic bitcoin data in attempt to optimize the algorithm using the best possible intervals for the moving averages.

## Methods and Results
### Moving Averages Algorithm
The trading algorithm is very simple: it takes the two different moving average intervals and the time to wait before updating as parameters. Each time the loop updates, it calculates the two moving averages, and if the shorter interval has a greater average price than the larger interval, any money in USD will be used to purchase BTC (although it can easily be adjusted to work for any crypto). If the shorter interval has a lower average price than the larger interval *and* the value of BTC is greater than when it was last purchased, it will be sold for USD. The reason this works is that when a shorter moving average has a higher value than a longer one, it is indication that the crypto is trending upward and is likely to continue moving up and vice versa. After testing some different moving averages in real time with the Sandbox API, I wondered if I could find specific moving averages that would result in more profit.

### Historical Moving Average Analysis of BTC
#### Methods
To correctly backtest the algorithm I created, I first wrote methods that iterate through a dataframe of historic minutely data of a crypto and create new columns
for any given length moving averages. I also wrote a simple method that factors in the fees that Coinbase charges for transactions for as much accuracy as possible. These methods are helpers for the backtest method, which takes two intervals in minutes, historic data, and a starting amount of USD, then returns the final amount in USD. The method backtest is then used in the method returns_many, which returns a dataframe that contains the final balance of many different moving average lengths chosen by the user. This allowed me to test hundreds of different moving average pairs and look for patterns within that data.

#### Analysis


## Conclusion
