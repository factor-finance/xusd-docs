---
icon: zap
order: 97
---

# Risks of owning XUSD

Knowledge is power. Do not invest funds you cannot afford to lose.

==- Smart Contract Risks
Risk  | Mitigation
---   | ---
A bug or open exploits in the Vault contract could allow attacker to withdraw funds.| We can reduce by auditing by multiple, top-tier security firms, formal verification of contract code, and a lucrative Bug Bounty, however, this risk can never be fully removed.
An attacker could manipulate price oracles to redeem for more than $1/XUSD.  | Chainlink [oracles](https://data.chain.link/avalanche/mainnet) for approved stablecoin prices are resistent to manipulation. A redemption fee for XUSD prevents exploiting manipulations smaller than the 0.5% fee.


==- Private key compromise
Risk  | Mitigation
---   | ---
The Private keys of deployer account can be compromised by attackers or inadvertantly. | By design, the XUSD token, the treasury vault, and vault strategies cannot be compromised by loss of developer deployment keys. Contract updates, strategy changes, capital pause & unpase, and operations are all subject to a [3-day timelock governor contract](https://github.com/factor-finance/xusd-contracts/blob/main/contracts/timelock/Timelock.sol). Changes must be executed by a [Gnosis multisignature wallet](https://github.com/gnosis/MultiSigWallet) than controls the timelock.


==- Impermanent Loss (IL)
Risk  | Mitigation
---   | ---
Many DeFi strategies are subject to impermanent loss delivering real returns lower than advertised APYs | XUSD operates using only using stable coin investments, so _impermanent losses are nonexistent._


==- Negative APY
Risk  | Mitigation
---   | ---
If the value of the vault decreases, XUSD holders could experience a rebase that *decreases* holdings or devalues XUSD. | By investing in stablecoins rather than volatile coins and avoiding impermanent loss, negative APYs are less likely.
Gas costs of investing newly minted XUSD or divesting from strategies could produce negative yields | The low gas costs of Avalanche C-Chain, 0.5% XUSD redemption fee, and a buffer of stablecoins held in the vault reduce the cost of transactions to XUSD holders.
Short-term holders may experience no or irregular yield from rebasing. | Hodl, at least until a harvest and rebase has occurred (several times a day).


==- Loss of funds in underlying strategy
Risk  | Mitigation
---   | ---
prop1 | type1
prop2 | type2


==- Low-or-no exchange liquidity (CEX or DEX)
Risk  | Mitigation
---   | ---
prop1 | type1
prop2 | type2


==- Departure from $1 Peg
Risk  | Mitigation
---   | ---
prop1 | type1
prop2 | type2
===
