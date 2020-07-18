---
description: The gateways for collateral and system coins to join or exit the system
---

# Token Adapters

## 1. Summary <a id="1-introduction-summary"></a>

There are three main token adapter types: `CollateralJoin`, `ETHJoin` and `CoinJoin`: 

* `CollateralJoin` - allows standard ERC20 tokens to be deposited for use with the system. 
* `ETHJoin` - allows native Ether to be used with the system. 
* `CoinJoin` - allows users to withdraw their system coins from the protocol into a standard ERC20 token.

## 2. Contract Variables & Functions <a id="2-contract-details"></a>

* `cdpEngine` - storage of the `CDPEngine`’s address.
* `collateralType` - id of the `CollateralType` for which a `CollateralJoin` is created for.
* `collateral` - the address of the `collateralType` for transferring.
* `systemCoin` - the address of the `Coin` token.
* `ONE` - a 10^27 uint used for math in `CoinJoin`.
* `contractEnabled` - an access flag for the adapter.
* `decimals` - decimals for the collateral type.
* `join` - join tokens into the system
* `exit` - exit tokens from the system
* `disableContract` - disable the adapter and only allow `exit`s

## 3. Walkthrough <a id="3-key-mechanisms-and-concepts"></a>

All adapter contracts serve a similar purpose. They manage the flow of collateral and system coins in and out of the system using `join` and `exit`. `CollateralJoin` is meant to change the `CDPEngine.tokenCollateral` and `CoinJoin` changes `CDPEngine.coinBalance`s.

{% hint style="danger" %}
**CoinJoin Can Be Used to Upgrade the ERC20 System Coin**

`CoinJoin` is a gateway \(like an ATM\) between the `CDPEngine` \(the "bank ledger"\) and the ERC20 representation of the system coin \(cash\). Governance has the power to deploy multiple `CoinJoin`s and `disable` previous `join` contracts. When a `CoinJoin` is disabled, users can only burn ERC20 system coins for `CDPEngine.coinBalance` \(`join` coins into the system\) and can no longer exit their `CDPEngine.coinBalance` in the ERC20 \(thus, the "gateway" only allows for one way transfers\).

If governance wants, they can deploy another ERC20 `Coin` contract \(possibly with blacklisting capabilities\) and also a separate `CoinJoin` for this new token. The previous `CoinJoin` for the old `Coin` contract can be disabled so that old ERC20 tokens can only be `join`ed in the system. The process to upgrade between the old, permissionless `Coin` and the new, permissioned one can be complicated \(although **not** impossible\) because some coin holders may not want to do the switch.

An easy way to avoid this scenario is for governance to remove control over the initial `CoinJoin` and allow system coin holders to use the gateway to `join` and `exit` coins at will.
{% endhint %}


