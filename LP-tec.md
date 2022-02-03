# Liquidity Pools Technical
Liquidity Pools are part of the bitshares-core 5.0, which are providing a fully automated and autonomous onchain liquidity.
Always holding an equal amount of value in both assets, at the current pool price

## Functions

### Exchange
The exchange rate is defined by: 
- constant product model: `k = amount_x * amount_y` 
- pool taker fee, contributed to the pool token holders

### Deposit
Both assets are needed in equal amounts at the current pool price. A deposit increases the amount of pool tokens. 

### Withdraw
Withdrawing funds from the pool, burns the pool token, which reduces the pool token supply. Withdraw fees are shared to the remaining pool token holders.

### Create
A new UIA needs to be created in the first place, which can be upgraded to the pool token. The asset ID A is by definiton smaller, than the asset ID B. After the inital pool deposit by the creator, the invariant `k` is defined and the liquidity pool is active. 

## Interfaces
- https://dex.iobanker.com/poolmart/liquidity-pools
- https://app.xbts.io/#/pools
- https://blocksights.info/#/pools
- https://github.com/bitshares/PoolTool

## Sources:
- https://news.iobanker.com/2021/04/02/bitshares-blockchain-liquidity-pools-defi-god-mode-is-now-enabled-at-iobanker-dex/
- https://github.com/bitshares/bitshares-core/releases/tag/5.0.0

## Index

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
