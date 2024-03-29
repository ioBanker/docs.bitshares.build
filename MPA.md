# Market Pegged Asset (MPA)

## Input Parameter:
- Feed producer
- Min. amount of feed producer
- Backing asset: Any asset, but only one fixed asset can be used as collateral
- Feed price: The collateral price in the borrowed asset.
- Feed lifetime
- Core Exchange Rate (CER): Price to exchange MPA from the asset owner fee pool for BTS.
- Collateral Ratio (CR) : = DEBT / COLLATERAL
- Maintenance Collateral Ratio (MCR): CR for margin call.
- Initial Collateral Ratio (ICR): Minimum CR for updating margin position. 
- Target Collateral Ratio (TCR): Only sell enough collateral to reach TCR again.
- Maximum Short Squeeze Ratio (MSSR): Max. liquidation penalty.
- Margin Call Fee Ratio (MCFR): Paid by the borrower to the asset owner. 

- Force Settlement Offset Percent (FSOP): Fee for MPA settlement to the collateral owner.
- Force Settlement Fee Percent (FSFP): Fee for MPA settlement to the asset owner.
- Force Settlement Delay Seconds (FSDS): Time after requested settlement is processed.
- Max. Force Settleable Volume (MFSV): Value in percent of the total MPA supply for each maintenance period (1h).

- Settlement Response Methods (explained in extra topic)
- Disable Collateral Bidding (prevent outbidding on volataile market)

- Market Fee: Asset exchange fee, paid by the asset buyer.
- Market fee referral reward (excluding taker fee)
- Max. Market Fee
- Taker Fee: Asset exchange fee, paid by the taker.


## Borrowing & Covering
The BitShares network is capable of minting any MPA, with any collateral, without any interest rate.

A borrow/short position can be closed by hold the same amount of that particular MPA. When the particular debt is payed back to the network, the corresponding supply is reduced and the collateral is released.

## Manual Collateral Settlement
When the asset owner allows force settlement, the MPA can be exchanged at Feed Price + FSO + FSS, after the settlement time and max. settlement volume. The settlement closes the borrow/short positions with lowest CR and sells the collateral to the asset settler.

## Automated Collateral Settlements

### Margin Call (First Level Settlement)
The margin call sells collateral, to buy shares of the borrowed MPA back and reduce the amount of debt. 
The margin call will occur, when the CR is lower than the MCR and a bid is equal or greater than the Call Price (CP): = DEBT / COLLATERAL * MCR.
The borrower is able to add extra collateral or reduce the debt, to increse his CR and prevent further margin calls. 

#### MSSR
- Higher MSSR allows faster liquidation and higher penality. Real liquidation penalty is dependend on market liquidity. 
- An MPA premium reduces the effective MSSR.
- Higher MSSR reduces the *effective CR range* (MCR-MSSR) for margin calls. 

### Response Methods (Second Level Settlement)
When the *effective CR* (MCR-MSSR) of the least collaterized position is 1, there are four different options handling the collateralization breaking point.

#### Global Settlement (Default)
All debt positions are closed, all or some collateral is moved to a global-settlement fund. Debt asset holders can claim collateral via force-settlement. It is not allowed to create new debt positions, when the fund is not empty. Collateral redistribution in global-settlement price.

#### No Settlement (Disable Global Settlement)
No debt position is closed, and the derived settlement price is dynamically capped at the collateral ratio of the debt position with the least collateral ratio so that all debt positions are able to pay off their debt when being margin called or force-settled. Able to adjust existing debt positions or create new debt positions. No collateral redistribution.

#### Settlement To Fund
Only the undercollateralized debt positions are closed and their collateral is moved to a fund which can be claimed via force-settlement. The derived settlement price is capped at the fund's collateral ratio so that remaining debt positions will not be margin called or force-settled at a worse price.  Able to adjust existing debt positions or create new debt positions. Collateral redistribution in median price. 

#### Settlement To Order
Only the undercollateralized debt positions are closed and their collateral is moved to a limit order on the order book which can be bought. The derived settlement price is NOT capped, which means remaining debt positions could be margin called at a worse price. Able to adjust existing debt positions or create new debt positions. Collateral redistribution in price range.

## Scripts
- https://github.com/litepresence/Honest-MPA-Price-Feeds
- https://github.com/bitshares/bitshares-pricefeed

## Projects
