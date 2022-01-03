---
order: 96
icon: sync
---
# Tokenomics


### XUSD can be minted with or redeemed for stable coins
* Redemption carries nominal fee (0.5%) paid to 
* Stable coins in vault are deposited into strategies
* Adjustable buffer reduces futile cycles

```mermaid
    %%{init: { 'theme': dark' } }%%
sequenceDiagram
    actor Wallet
    participant XUSD Contract
    participant Vault
    participant Yield Strategies

    Wallet->>+XUSD Contract: Convert Stablecoins
    XUSD Contract->>+Vault: Transfer
    Vault->>-Yield Strategies: Allocate
    XUSD Contract->>XUSD Contract: Mint XUSD for wallet
    XUSD Contract->>Wallet: Increased XUSD Balance
    deactivate XUSD Contract
```

### Strategies generates yield and XUSD increases supply
* Deposit-type investments are tracked
* Rewards tokens are periodically sold for stablecoins and reinvested
* XUSD in wallets (EOAs) are rebased to account for change in vault value
* Adjustable Portion of yield paid to treasury, initially 0%

```mermaid
    %%{init: { 'theme': dark' } }%%
sequenceDiagram
    actor Wallet
    participant XUSD Contract
    participant Vault
    participant Yield Strategies

    note over Vault: Periodic Rebase
    Vault->>Yield Strategies: Harvest yield
    activate Vault
    Vault->>Yield Strategies: Rebalance
    Vault->>XUSD Contract: Report yield
    activate XUSD Contract
    deactivate Vault
    XUSD Contract->>XUSD Contract: Mint XUSD for yield
    XUSD Contract->>XUSD Contract: Distribute XUSD among wallets
    XUSD Contract->>Wallet: Increased XUSD Balance
    deactivate XUSD Contract
```

### XUSD is always fully redeemable for stablecoins
* Redemption always possible for full value of XUSD
* Backing assets are liquidated from yield strategies if necessary

```mermaid
    %%{init: { 'theme': dark' } }%%
sequenceDiagram
    actor Wallet
    participant XUSD Contract
    participant Vault

    Wallet->>+XUSD Contract: Convert XUSD
    XUSD Contract->>+Vault: Initiate Redeem
    Vault->>+Yield Strategies: Divest
    Yield Strategies->>-Vault: Transfer Stablecoins
    Vault->>Vault: Hold 0.5% protcol fee
    Vault->>XUSD Contract: Transfer Stablecoins
    deactivate Vault
    XUSD Contract->>XUSD Contract: Burn XUSD
    XUSD Contract->>-Wallet: Transfer Stablecoins
```

### Reward governance token (FACT) from protocol fees & liquidity pools
* FACT is [not yet launched](/roadmap#table-stakes)
* Vault purchases governance token on open market using collected protocol fees
* Vault distributes governance token to FACT stakers and XUSD liquidity providers
* Governance token confers voting rights

```mermaid
    %%{init: { 'theme': dark' } }%%
sequenceDiagram
    actor Wallet
    participant Vault
    participant Exchange

    Wallet->>Vault: Option 1: Stake FACT
    Wallet->>Vault: Option 2: Transfer liquidity pool tokens
    note right of Wallet: XUSD/USDT.e, XUSD/USDC.e, XUSD/DAI, XUSD/FACT
    Vault->>Exchange: Harvest liquidity pool rewards
    activate Vault
    Vault->>Exchange: Swap rewards for stablecoins
    Vault->>Vault: Combine with protocol fees
    Vault->>Vault: Hold 90% for redeem or rebase
    Vault->>Exchange: Purchase FACT on open market
    Vault->>-Wallet: Distribute FACT
```


