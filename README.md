# portfolio-simulation-weights-loop

Simulation that tests different weights of each security in portfolio.

It converts all data to a specified **analysis currency** to facilitate the analysis.

It is mainly intended for portfolios consisting of ETFs (Exchange Traded Funds). Therefore, I will use ETFs in examples below.

The data for analysis comes from Yahoo Finance, and it is retrieved using the yfinance library.

## Table of contents

1. [Overview](#Overview)
2. [Results](#Results)
3. [Simulation parameters](#Simulation-parameters)
4. [Examples](#Examples)

## Overview

Generate a random list of transaction dates based on specified parameters and test all combinations of weights that sum up to 1 (100%). Store the results in dictionaries, and subsequently utilize them for analyzing outcomes.

## Results

The simulation generates an HTML file containing the described statistics as its output.

### Profit statistics

#### Profits for each iteration

- **Description:** A dictionary containing statistics of profit for each iteration.
- **Variable:** `results_profit_describe`
- **Usage:** This dictionary provides a comprehensive overview of the profit statistics observed in each simulation iteration.

#### Profit percentage for each iteration

- **Description:** A dictionary with statistics of profit percentage for each iteration.
- **Variable:** `results_profit_percentage_describe`
- **Usage:** This dictionary captures the percentage change in profit for each simulation iteration, offering insights into relative performance.

### Drawdown statistics

#### Drawdown for each iteration

- **Description:** A dictionary with statistics of drawdown for each iteration.
- **Variable:** `results_drawdown_describe`
- **Usage:** This dictionary provides insights into the depth of decline from a peak in the value of the portfolio for each simulation iteration.

## Simulation parameters

- `analysis_currency` - Currency in which the simulation is run.
- `start_date` - Start date of simulation data. If start_date is before the first available date of the securities, the first available date will be used.
- `end_date` - End date of simulation data.
- `tickers_and_currencies` - A dictionary where the keys are for securities tickers and the values are for currencies for the corresponding securities.
- `expense` - Amount of expense (transaction fee) for each transaction.
- `amount` - Approximate amount of money to invest in each transaction.
- `precision` - Step accuracy in percentage points when testing different weights (precision = 1 means 0%, 1%, 2% etc., precision = 3 means 0%, 3%, 6% etc.)
- `ohlc` - Which column to use for open, high, low, close prices.
- `n_months` - A number representing the interval between transactions starting from the month specified in the start_date variable.

## Examples

The code already includes predefined sample parameters.

### Predefined portfolio strategy

Each calendar month we buy specified securities (ETFs) in the corresponding weights for ~1000 euro. Therefore, out analysis currency will be `EUR`.

We will invest in the securities (ETFs) below:

- `VWCE.DE` - Vanguard FTSE All-World UCITS ETF - currency: `EUR`
- `ISAC.L` - iShares MSCI ACWI UCITS ETF USD - currency: `USD`
- `VAGP.L` - Vanguard Global Aggregate Bond UCITS ETF - currency: `GBP`
- `AGGH.MI` - iShares Core Global Aggregate Bond UCITS ETF - currency: `EUR`
- `4GLD.DE` - Xetra-Gold - currency: `EUR`
- `IGLN.L` - iShares Physical Gold ETC - currency: `USD`

The precision will be set to 10, indicating consideration only for weights within the sequence: 0, 0.1, 0.2, ..., 1.

### Results

Overall number of iterations when sum of weights was equal to 1 was exactly 2486.

Columns:

- **profit_mean_to_std**: Mean profit to standard deviation ratio.
- **min_drawdown**: Minimum drawdown [%].
- **mean_drawdown**: Mean drawdown [%].
- **mean_profit_percentage**: Mean profit percentage [%].
- **max_profit_percentage**: Maximum profit percentage [%].
- **min_profit_percentage**: Minimum profit percentage [%].

Screenshot with the first 21 rows of the table from the HTML file.

![image](https://github.com/mrkyc/portfolio-simulation-monte-carlo/assets/82812493/07bee911-840e-429c-b54c-b642a96221c2)
