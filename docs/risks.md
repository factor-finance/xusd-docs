---
label: Risks
icon: zap
order: 97
---

# Risks of owning XUSD

Knowledge is power. Do not invest funds you cannot afford to lose.

==- Smart Contract Risks
Risk  | Mitigation
---   | ---
A bug or open exploits in the Vault contract could allow attacker to withdraw funds.| We can reduce by auditing by multiple, top-tier security firms (in progress), formal verification of contract code (in progress), and a lucrative Bug Bounty (to be established), however, this risk can never be fully removed.
An attacker could manipulate price oracles to redeem for more than $1/XUSD.  | Chainlink [oracles](https://data.chain.link/avalanche/mainnet) for approved stablecoin prices are resistent to manipulation. A redemption fee for XUSD prevents exploiting manipulations smaller than the 0.5% fee.


==- Private key compromise
Risk  | Mitigation
---   | ---
The Private keys of deployer account can be compromised by attackers or inadvertantly disclosed. | By design, the XUSD token, the treasury vault, and vault strategies (all the contracts holding user funds) cannot be compromised by loss of developer deployment keys. Contract updates, strategy changes, capital pause & unpase, and operations are all subject to a [3-day timelock governor contract](https://github.com/factor-finance/xusd-contracts/blob/main/contracts/timelock/Timelock.sol). After the timelock, proposed changes must be executed by a [Gnosis multisignature wallet](https://github.com/gnosis/MultiSigWallet).


==- Impermanent Loss (IL)
Risk  | Mitigation
---   | ---
Many DeFi strategies are subject to impermanent loss delivering real returns lower than advertised APYs | XUSD vault strategies are stablecoin-only, and as such _impermanent losses are diminimous to nonexistent._

==- Negative APY
Risk  | Mitigation
---   | ---
If the value of vault funds decrease, XUSD holders could experience a rebase that *decreases* holdings or devalues XUSD. | By investing in stablecoins rather than volatile coins and avoiding impermanent loss, negative APYs are less likely. Further, allocating the same coins used to mint XUSD directly into strategies reduces potential for market shocks of XUSD redemptions larger than the current vault buffer.
Gas costs of investing newly minted XUSD or divesting from strategies could produce negative yields | The low gas costs of Avalanche C-Chain, 0.5% XUSD redemption fee, and a buffer of stablecoins held in the vault reduce the cost of transactions to XUSD holders.
Short-term holders may experience 0 or lower-than-average yield from rebases. | Hodl until a harvest & rebase occurs (at least once per day). Intra-day yields can be volatile, but average to reported values.


==- Loss of funds in underlying strategy
Risk  | Mitigation
---   | ---
Vault funds backing XUSD are in contracts controlled by other DeFi protocols (e.g. Aave, Curve, etc). These funds could be stolen, lost, or devalued. | We choose strategies carefully and believe them to have exceptional risk-vs-return. You can read more about their risks [here](https://docs.aave.com/risk/liquidity-risk/introduction), [here](https://curve.fi/risks), or [here](https://alphafinancelab.gitbook.io/alpha-homora-v2/ibeth-alpha/tbd-risks-and-mitigation-1). To avoid exposure to any new strategies, look for strategy update announcements and redeem XUSD during the timelock period.


==- Low-or-no exchange liquidity
Risk  | Mitigation
---   | ---
If centralized exchange (CEX), decentralized exchange (DEX), and/or OTC liquidity disappeared (i.e. "rug pull"), XUSD holder could be unable to sell. | XUSD is *always* fully redeemable for the underlying stablecoins by calling the `redeem` method on the vault contract, which makes liquidity unnecessary to redeem XUSD for stablecoins DAI/USDC/USDT, although selling XUSD on an exchange may be preferable or more convienant.

==- Departure from $1 Peg
Risk  | Mitigation
---   | ---
XUSD could break $1 peg trading at less than $1 on one or more central or decentralized exchanges | Providing low-friction, permissionless mint and redeem functionality, XUSD can always be purchased (minted) for $1 and sold (redeemed) for $0.995 worth of stablecoins ($1 - 0.5% redeem fee). As such, arbitrageurs will act on transient peg depatures to keep DEX/CEX prices close to $1.
===

