# Market Pegged Asset

## MPA Input Parameter:
- Feed Price: The collateral price in the borrowed asset.
- Collateral Ratio (CR) : = DEBT / COLLATERAL
- Maintenance Collateral Ratio (MCR): CR for margin calls.
- Initial Collateral Ratio (ICR): Minimum CR for updating margin position. 
- Target Collateral Ratio (TCR): Sell only enough collateral to reach TCR again.
- Call Price (CP): = DEBT / COLLATERAL * MCR The price at which short/borrowed positions are getting margin called.
- Maximum Short Squeeze Ratio (MSSR): Max. liquidation penalty. Real penalty is dependent on market liquidity.


- Force Settlement Offset (FSO): Fee for MPA settlement for the collateral owner
- Force Settlement Fee (FSF): Fee for MPA settlement for the asset owner
- Max. settleable volume each maintance period


- Market Fee: Orderbook Exchange Fee
- Taker Fee: Percentage of the market fee paid by the taker


## Borrowing
The BitShares network is capable of minting any MPA, with any collateral, without any interest rate.

## Margin Call
The margin call sells collateral, to buy shares of the borrowed MPA back, to reduce the amount of debt. 
The margin call will occur, when the CR is lower than the MCR and a bid is equal or greater than the SSP.
The borrower is able to add extra collateral or reduce the debt, to increse his CR and prevent further margin calls. 

### MSSR
Higher MSSR allows faster liquidation and higher penality on less liquid markets. Market MPA discounts does reduce the effective MSSR.

## Settlement
When the asset owner, allows a settlement, the MPA can be exchanged at Feed Price + FSO + FSS after the settlement time and max. settlement volume. The settlement closes the borrow/short positions with lowest CR and sells the collateral to the asset settler.

## Covering
A borrow/short position can be closed by hold the same amount of that particular MPA. When the particular debt is payed back to the network, the corresponding supply is reduced and the collateral is released.
