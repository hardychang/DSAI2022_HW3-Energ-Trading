# DSAI 2022 HW3 - Energy-Trading

## Overview
### NCKU DSAI HW3 - Energy-Trading


Act as a house owner in this HW3.
The house equipped with appliances and solar power plant.
The house is in a community microgrid with a total 40 households.
You can decide to **buy or sell the power** from the microgrid through a local power trading platform.
You can still consume the power from the main grid by a fixed price.

Goal: Design an agent for bidding power to minimize the electricity bill.

## Data
* 50 households synthetic data
* Hourly Power consumption (kWh)
* Hourly Solar Power generation (kWh)
* Hourly Bidding records
* 12 months of data
 * 8 months for training
 * 1 months for validation
 * 3 months for testing

## Input data
* consumption.csv: 過去七天歷史用電資料
* generation.csv: 過去七天產電資料
* bidresult.csv : 過去七天自己的投標資料

## Output data
* output.csv: 未來一天投標資訊

## Workflow
* Platform inputs the past 7 days of consumption data(consumption.csv), generation data(generation.csv) and bidding records(bidresult.csv) to every agent.
* Agent generates the following day of hourly bidding action(output.csv) and outputs to the specific path.
* Platform crawls the bidding action of all agents and proceeds a bidding match.
* Platform announces the bidding result(bidresult.csv) and outputs it as a file to every agent’s directory.

## Action Type
* Buy
 * Find a seller to buy your power with target_volume and target_price
 * If a transaction succeeds(成交), buyers always get the trade_volume with trade_price
* Sell
 * Find a buyer to buy your power with target_volume and target_price
 * If a seller sells the amount that insufficiently supply to a buyer, seller needs to buy the power from Taipower and supplies it to buyer with the market price (市電單價), annotated as market_price.
* No Action
 * Don’t output any bidding action to output.csv in these hours 

## How to calculate electricity bill
<img src="https://github.com/hardychang/DSAI2022_HW3-Energy-Trading/blob/main/calculate.png" width="600"/><br/>

