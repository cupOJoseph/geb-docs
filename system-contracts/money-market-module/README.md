---
description: The interest rate setters
---

# Money Market Module

**Relevant smart contracts:**

* [TaxCollector](https://github.com/reflexer-labs/geb/blob/master/src/TaxCollector.sol)

## 1. Overview

The **Money Market Module** contains the components that governance \(or an autonomous rate setter\) can use to set and collect stability fees.

## 2. Component Descriptions

* The `TaxCollector` imposes fees on all collateral types and distributes them to various parties. Compared to MCD, the system can automatically use fees to fund its operations such as paying for oracle calls or adding liquidity to DEXs \(in addition to accruing surplus in the `AccountingEngine`\). Each collateral's stability fee is composed out of a `globalStabilityFee` \(a base fee applied to all collaterals\) and its own, unique `CollateralType.stabilityFee`.

## 3. Risks

### Smart Contract Bugs <a id="coding-errors"></a>

* `TaxCollector` - a bug in the collector would make it so that the system could no longer accrue surplus \(which is used to settle bad debt and pay for other system operations\) and thus components that depend on a constant stream of fees to work properly would likely dry up

### Improper Maintenance

The `TaxCollector` depends on external actors that call `taxSingle` or `taxAll` in order to collect stability fees. In theory, protocol token holders are incentivized to call the collector as often as possible \(in order to gather and ultimately use surplus to burn `PROT`\) although in the early days of the system the calls may be more infrequent. The main caveat is that any CDP that is opened and closed between two fee collections will not be subject to taxation.

Another major risk is related to malicious governance setting extremely high or extremely low stability fees. If the fees are extremely high, CDPs may be unjustly liquidated. On the other hand, if they are too low, the system may not be able to collect enough fees to become sustainable.

## 4. Governance Minimization

Depending on whether governance wants to expand the basket of accepted collateral types over time, they may keep control over the `TaxCollector` or choose to add only a few assets and then completely remove their permissions.

Governance may also keep their power to change stability fees within certain limits. For example, the `globalStabilityFee` may only be changed a certain percentage every week or every `CollateralType.stabilityFee` can have strict bounds over what values it can be set to.
