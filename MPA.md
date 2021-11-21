# Market Pegged Asset

## MPA Input Parameter:
- Feed Producer
- Min. amount of Feed Producer
- Feed Price: The collateral price in the borrowed asset.
- Feed Lifetime
- Core exchange rate (CER): Price to exchange MPA for from BTS asset pool 
- Collateral Ratio (CR) : = DEBT / COLLATERAL
- Maintenance Collateral Ratio (MCR): CR for margin calls.
- Initial Collateral Ratio (ICR): Minimum CR for updating margin position. 
- Target Collateral Ratio (TCR): Sell only enough collateral to reach TCR again.
- Call Price (CP): = DEBT / COLLATERAL * MCR The price at which short/borrowed positions are getting margin called.
- Maximum Short Squeeze Ratio (MSSR): Max. liquidation penalty. Real penalty is dependent on market liquidity.

- Force Settlement Offset (FSO): Fee for MPA settlement to the collateral owner
- Force Settlement Fee (FSF): Fee for MPA settlement to the asset owner
- Force Settlement Daly: Time after requested settlement is processed
- Max. settleable volume each maintance period: Value in percent of the total MPA supply

- Market Fee: Asset Exchange Fee, paid by the asset buyer
- Taker Fee: Percentage of the market fee, paid by the taker
- Market Settlement Options: Handling CR under 1
- Disable Collateral Bidding

## Borrowing & Covering
The BitShares network is capable of minting any MPA, with any collateral, without any interest rate.

A borrow/short position can be closed by hold the same amount of that particular MPA. When the particular debt is payed back to the network, the corresponding supply is reduced and the collateral is released.

## Market Issued Collateral Settlements

### Margin Call
The margin call sells collateral, to buy shares of the borrowed MPA back, to reduce the amount of debt. 
The margin call will occur, when the CR is lower than the MCR and a bid is equal or greater than the SSP.
The borrower is able to add extra collateral or reduce the debt, to increse his CR and prevent further margin calls. 

#### MSSR
- Higher MSSR allows faster liquidation and higher penality. Real liquidation penalty is dependend on market liquidity. 
- An MPA premium reduces the effective MSSR for margin calls.
- Higher MSSR reduces the *effective CR range* (MCR-MSSR) for Market Issued Settlements. 

### Market Settlement Options
When the *effective CR* (MCR-MSSR) is lower than 1, the second settlement starts.

#### Global Settlment (Default)
All debt positions are closed, all or some collateral is moved to a global-settlement fund. Debt asset holders can claim collateral via force-settlement. It is not allowed to create new debt positions when the fund is not empty.

#### No Settlement (Global Settlement Protection)
No debt position is closed, and the derived settlement price is dynamically capped at the collateral ratio of the debt position with the least collateral ratio so that all debt positions are able to pay off their debt when being margin called or force-settled. Able to adjust existing debt positions or create new debt positions.

#### Individual Settlement To Fund
Only the undercollateralized debt positions are closed and their collateral is moved to a fund, which can be claimed via force-settlement. The derived settlement price is capped at the fund's collateral ratio, so that remaining debt positions will not be margin called or force-settled at a worse price.  Able to adjust existing debt positions or create new debt positions.

#### Individual Settlement To Order
Only the undercollateralized debt positions are closed and their collateral is moved to a limit order on the order book which can be bought. The derived settlement price is NOT capped, which means remaining debt positions could be margin called at a worse price. Able to adjust existing debt positions or create new debt positions.

## User Issued Collateral Settlement
When the asset owner, allows the user issued settlement, the MPA can be exchanged at Feed Price + FSO + FSS after the settlement time and max. settlement volume. The settlement closes the borrow/short positions with lowest CR and sells the collateral to the asset settler.
