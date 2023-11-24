---
layout: post
title: The liquidation of DeXian Lending Protocol
subtitle: reliable, up to date, and secure.
# hero_image: /path/to/image.jpg
hero_darken: true
---
## Loan to Value and Liquidation Threshold
Lending is known to be a financial risk product, particularly in the cryptocurrency space where prices are highly volatile. The `Collateral Debt Position` (hereinafter referred to as `CDP`) generated by the DeXian Lending Protocol represents one such risk unit, encapsulating key data on the borrower's collateral, debt, and other relevant information.

```
    debt_token.price = $price_oracle.get_price($debt_token)
    collateral_token.price = $price_oracle.get_price($collateral_token)
    LTV(Loan to Value) = ($debt_token.borrow_amount * $debt_token.price) / $collateral_token.amount * $collateral_token.price
```

Upon creating a `CDP`, the `Loan to Value (LTV)` represents the maximum borrowing ratio accessible to a borrower. However, as the prices of the debt token and collateral token fluctuate, the LTV and, consequently, the health of the CDP, undergo changes. Each collateralized asset is assigned a `Liquidation Threshold`.

```
    CDP.health_factor = ($collateral_token.amount * $collateral_token.price * $collateral_token.liquidation_threshold) / ($debt_token.borrow_amount * $debt_token.price)
```


## Asset Risk Parameter
The liquidation process is initiated when the `CDP.health_factor` falls below 1. The current parameter configurations for the assets supported by DeXian Lending are as follows:

|  Symbol  |  Collateral  |  Loan To Value  |  Liquidation Threshold   |  Liquidation Bonus   | Insurance Ratio | Interest Model          |
| -------- | ------------ | --------------- | ------------------------ | -------------------- | --------------- | ----------------------- |
| XRD      | Yes          | 60%             | 70%                      |  7%                  |  25%            | Default Interest model  |
| USDT     | No           |                 |                          |                      |  10%            | Stable Interest model   | 
| USDC     | Yes          | 85%             | 87%                      |  2%                  |  10%            | Stable Interest model   |


## liquidation call

The components of the DeXian Lending Protocol provide a `liquidation(debt_asset_bucket, debt_to_cover, cdp_id)` method, which can be called by any liquidator participant.

|  name             |     type      |    description                                                    |
| ----------------- | ------------- | ----------------------------------------------------------------- |
| debt_asset_bucket | Bucket        | the underlying borrowed asset to be repaid with the liquidation   |
| debt_to_cover     | Decimal       | the debt amount of borrowed `asset` the liquidator wants to cover |
| cdp_id            | u64           | the #id# of CDP getting liquidated                                |


A liquidation participant is able to receive collateralized assets containing liquidation incentives for the repayment of debts of the liquidated CDP. Liquidators may set `debt_to_cover` to `-1` to represent the maximum share of liquidations they want to participate in, which is currently `50%` of the CDP's total debt per call. The part of the bucket(`debt_asset_bucket`) that exceeds the actual repayment payment amount is refunded to the liquidator.

```
collateral_underlying_asset.amount = [actual_repay_debt.amount * debt_token.price * (1+collateral.liquidation_bonus)] / collateral_underlying_asset.price

```



