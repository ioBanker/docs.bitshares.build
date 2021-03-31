# Liquidity Pools
Liquidity Pools are part of the bitshares-core 5.0, which are providing a fully automated and autonomous onchain liquidity.

## Functions

### Exchange
The exchange rate is defined by: 
- constant product model: `k = amount_x * amount_y` 
- exchange fees, paid by the taker and contributed to the pool token holders

### Deposit
Both assets are needed in equal amounts at the current pool price. 
Liquidity Pools, which use a (Market Pegged Asset)/Collateral pair, can be used to stake a long, neutral or short position.

#### Example: 1.19.66 - HONEST.BTCBTSMM
- **HONEST.BTC Long - BTS Short:** Sell 50% of the BTS for the HONEST.BTC part.
- **HONEST.BTC\/BTS Neutral:** Borrow the 50% HONEST.BTC and add an extra 50% BTS.
- **HONEST.BTC Short - BTS Long:** Use all BTS for borrowing. Sell 50% of your HONEST.BTC for the BTS part.

### Witdraw
Withdrawing funds from the pool burns the pool token and reduces the pool token supply. Withdraw fees are shared to the remaining pool token holders.

## Interfaces
- https://dex.iobanker.com/poolmart/liquidity-pools
- https://blocksights.info/#/pools
- https://github.com/bitshares/PoolTool

### Functions
 - liquidity_pool_create_operation
 - liquidity_pool_delete_operation
 - liquidity_pool_deposit_operation
 - liquidity_pool_withdraw_operation
 - liquidity_pool_exchange_operation
 
 ### Object
 - asset_a
 - asset_b
 - balance_a
 - balance_b
 - share_asset
 - taker_fee_percent
 - virtual_value
