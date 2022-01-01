---
order: 99
label: How it works
icon: question
---
# Interest bearing stablecoin
#### Stable value and fully backed
!!!contrast
1 XUSD = $1
!!!
* $1 of stablecoin backs every XUSD
* XUSD is an [ERC20 token](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/) on the [Avalanche C-chain](https://www.avax.network/)

#### Instantly fungible
* Permissionless [mint](https://app.xusd.fi) using any of supported stablecoins (USDC, DAI, USDT) with no slippage
* Permissionless [redemption](https://app.xusd.fi) for mix of supported stablecoins with no slippage and 0.5% redemption fee
* Support on major DEX and CEX (coming soon).
!!!warning
Redemptions using the XUSD vault incur a 0.5% exit fee and the user doesn't get to pick which stablecoins they receive. Users can often avoid this fee by selling on a DEX or CEX instead.
!!!

#### Supported stablecoins
Currently, XUSD supports these stablecoins:
+++ ![](https://app.xusd.fi/images/currency/usdc-icon-small.svg)  USDC.e
**[Avalanche-bridged USDC](https://snowtrace.io/token/0xa7d7079b0fead91f3e65f86e8915cb59c1a4c664)**

`Avalanche C-chain address: 0xa7d7079b0fead91f3e65f86e8915cb59c1a4c664`
+++ ![](https://app.xusd.fi/images/currency/dai-icon-small.svg)  DAI
**[Avalanche-bridged DAI](https://snowtrace.io/token/0xd586e7f844cea2f87f50152665bcbc2c279d8d70)**

`Avalanche C-chain address: 0xd586e7f844cea2f87f50152665bcbc2c279d8d70`
+++ ![](https://app.xusd.fi/images/currency/usdt-icon-small.svg)  USDT.e
**[Avalanche-bridged USDT](https://snowtrace.io/token/0xc7198437980c041c805a1edcba50c1ce5db95118)**

`Avalanche C-chain address: 0xc7198437980c041c805a1edcba50c1ce5db95118`
+++

#### Automated stablecoin yield farming
* The vault invests in ultra-low volatility, market neutral strategies
* Extensible and configurable strategy set e.g. lending on [Aave](https://app.aave.com/#/markets), stablecoin liquidity providing (curve.fi, Pangolin), and other DeFi strategies.
* Rewards are claimed, collected, swapped, and reinvested automatically at least _once per day_

#### Yield generation strategies


#### Elastic supply
* The amount of XUSD in all wallets increases when gains are realized
* Yield distributed by supply rebasing, so that XUSD remains fully backed: 1 XUSD = $1 USD.

#### Lowest barrier of entry for DeFi yields
* SEC-qualified custodians can hold ERC20 tokens, but cannot give DeFi access
* No self-custody/contract interactions are required to access DeFi yields via XUSD
* Centralized exchanges and custody tools can support XUSD on behalf of users with minimal setup

#### Initial launch on Avalanche C-Chain
* Low gas fees (minting XUSD for around $5 for unlimited amount)
* More than $100 billion of native and ethereum-bridge wrapped stablecoins
* Strong [incentive programs](https://medium.com/avalancheavax/avalanche-foundation-announces-180m-defi-incentive-program-d320fdfafff7)
* Established DeFi protocols operating (Aave, curve.fi, Pangolin, and so many others)
