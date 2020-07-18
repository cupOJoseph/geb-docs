# Table of contents

* [Introduction to GEB](README.md)
* [Currently Deployed Systems](currently-deployed-systems.md)

## System Overview

* [Core Contracts Naming Transition](system-overview/naming-transition.md)

## System Contracts

* [Core Module](system-contracts/core/README.md)
  * [CDP Engine](system-contracts/core/cdp-engine.md)
  * [Liquidation Engine](system-contracts/core/liquidation-engine.md)
  * [Accounting Engine](system-contracts/core/accounting-engine.md)
* [Auction Module](system-contracts/auction-module/README.md)
  * [Collateral Auction House](system-contracts/auction-module/collateral-auction-house.md)
  * [Debt Auction House](system-contracts/auction-module/debt-auction-house.md)
  * [Surplus Auction House](system-contracts/auction-module/surplus-auction-house.md)
  * [Settlement Surplus Auctioneer](system-contracts/auction-module/settlement-surplus-auctioner.md)
* [Oracle Module](system-contracts/oracle-module/README.md)
  * [Oracle Relayer](system-contracts/oracle-module/oracle-relayer.md)
  * [Medianizer](system-contracts/oracle-module/medianizer/README.md)
    * [DSValue](system-contracts/oracle-module/medianizer/ds-value.md)
    * [Governance Led Median](system-contracts/oracle-module/medianizer/governance-led-median.md)
    * [Chainlink Median](system-contracts/oracle-module/medianizer/chainlink-median.md)
    * [Oracle Network Medianizer](system-contracts/oracle-module/medianizer/oracle-network-medianizer.md)
  * [FSM](system-contracts/oracle-module/fsm/README.md)
    * [Oracle Security Module](system-contracts/oracle-module/fsm/oracle-security-module.md)
    * [FSM Governance Interface](system-contracts/oracle-module/fsm/fsm-governance-interface.md)
* [Token Module](system-contracts/token-module/README.md)
  * [Token Adapters](system-contracts/token-module/token-adapters.md)
  * [System Coin](system-contracts/token-module/system-coin.md)
  * [Protocol Token](system-contracts/token-module/protocol-token.md)
  * [Protocol Token Authority](system-contracts/token-module/protocol-token-authority.md)
* [Money Market Module](system-contracts/money-market-module/README.md)
  * [Tax Collector](system-contracts/money-market-module/tax-collector.md)
* [Feedback Mechanism Module](system-contracts/feedback-mechanism-module/README.md)
  * [Redemption Feedback Mechanism](system-contracts/feedback-mechanism-module/redemption-feedback-mechanism.md)
* [Sustainability Module](system-contracts/sustainability-module/README.md)
  * [Stability Fee Treasury](system-contracts/sustainability-module/stability-fee-treasury.md)
* [Governance Module](system-contracts/governance-module/README.md)
  * [Gnosis Multisig](system-contracts/governance-module/gnosis-multisig.md)
  * [Governance Aggregation](system-contracts/governance-module/governance-aggregation.md)
  * [Vote Quorum](system-contracts/governance-module/vote-quorum.md)
  * [DSPause](system-contracts/governance-module/ds-pause.md)
* [Shutdown Module](system-contracts/shutdown-module/README.md)
  * [Global Settlement](system-contracts/shutdown-module/global-settlement.md)
  * [ESM](system-contracts/shutdown-module/esm.md)
* [Migration Module](system-contracts/migration-module/README.md)
  * [Token Power Delegate](system-contracts/migration-module/restricted-migration.md)

## Proxy Infrastructure

* [DSProxy](proxy-infrastructure/ds-proxy.md)
* [Proxy Registry](proxy-infrastructure/proxy-registry.md)

## Helper Contracts

* [CDP Manager](helper-contracts/cdp-manager.md)
* [Proxy Actions](helper-contracts/proxy-actions.md)
* [Proxy Global Settlement](helper-contracts/proxy-global-settlement.md)
