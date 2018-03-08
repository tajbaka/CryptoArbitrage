# CryptoArbitrage

A rough arbitrage algorithm designed to show executable arbitrage opportunities. We designed an MVP that has been profititable so far. We are still playing around with the current strategy by adding more exchanges and coin pairs to see the rate of profitable arbitrages. If any use cases of a full scale bot present themselves, we will build the automated version.

![2018-03-08](https://gfycat.com/UnselfishMellowInexpectatumpleco.gif)

## Roadmap: 
[Complete] Research and conceptualize our algorithm keeping in mind existing programs such as blackbird etc
[Complete] Create MVP for proof of concept: Use node.js and express to prove algorithm, use Angular4 Web Application to display results.
[To Be Complete] Create Automated Bot to maximize profits.

### Details:
### Phase 1: Gather Data 
* **Goal**: Use Cryptocompare's API to agregate and update coin pairs and prices that exist amonst all relevant exchanges. 
* **Reasoning** To avoid calling the crpytocompare API repeateadly, and allow front end to easily access data.
* **Process**: 
    * Step 1: Recurse through all Coin pairs that exist for each exchange
    * Step 2: Filter by 24 hour minimum volume and update local database.
    * Step 3: Set Up crpytocompare websockets to update these database price pairs in real time.

### Phase 2: Algorithmic Filtering
* **Goal**: Use recursion to find arbitrage opportunities involving coin-fiat and coin-coin pairs 
* **Reasoning** To find all posssible paths, calculate percentage made or lost at each path, and display percentages above minimum threshhold.
* **Process**: 
    * Step 1: Assume starting point at each exchangeX with fiatX
    * Step 2: Assume execution of arbitrage between exchangeX and exchangeX/exchangeY from fiatX to coinY.
    * Step 3: Repeat Step 2 for exchangeX/exchangeY to exchangeX/exchangeY/exchangeZ from coinY to coinZ.
    * Step 4: Repeat process for n number of arbitrages and M coin-fiat/coin-coin pairs and assume O(M^N) computation
    * Step 6: Convert coinX/coinY/coinZ back to fiatX/fiatY/fiatZ.
    * Step 7: Use Exchange Rates to convert coinY/coinZ to coinX
    * Step 8: Calculate Arbitrage Made.

### Phase 3: Manual Execution
* **Goal**: Execute on arbitrages that do not hold our money in a single location for a long time, ie premium exchanges. 
* **Reasoning** We need to execute on arbitrages that will close in a couple days at maximum, so that our fiats can constantly compound without sitting in a premium exchange and needing a wire transfer.
