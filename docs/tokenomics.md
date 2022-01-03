---
order: 96
icon: sync
---
# Tokenomics


### Mint XUSD from Stablecoins

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
    deactivate XUSD Contract
    Wallet->>+XUSD Contract: Get balance
    XUSD Contract->>-Wallet: Increased XUSD Balance
```

### Rebase XUSD balances with gains

```mermaid
    %%{init: { 'theme': dark' } }%%
sequenceDiagram
    actor Wallet
    participant XUSD Contract
    participant Vault
    participant Yield Strategies

    XUSD Contract->>Vault: Periodic Rebase
    activate XUSD Contract
    activate Vault
    Yield Strategies->>Vault: Harvest yield
    Vault->>Yield Strategies: Rebalance
    Vault->>XUSD Contract: Report yield
    deactivate Vault
    XUSD Contract->>XUSD Contract: Mint XUSD for yield
    XUSD Contract->>XUSD Contract: Distribute XUSD among wallets
    deactivate XUSD Contract
    Wallet->>+XUSD Contract: Get balance
    XUSD Contract->>-Wallet: Increased XUSD Balance
```

### Redeem XUSD for Stablecoins

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
    Vault->>Vault: Hold 0.5% for protcol fee
    Vault->>XUSD Contract: Transfer Stablecoins
    deactivate Vault
    XUSD Contract->>XUSD Contract: Burn XUSD
    XUSD Contract->>-Wallet: Transfer Stablecoins
```

### Distribute protocol fee rewards

```mermaid
    %%{init: { 'theme': dark' } }%%
sequenceDiagram
    actor Wallet
    participant Vault
    participant Exchange

    Wallet->>Vault: Option 1: Stake FACT
    Wallet->>Vault: Option 2: Transfer liquidity pool tokens
    note right of Wallet: XUSD/USDT.e, XUSD/USDC.e, XUSD/DAI, XUSD/FACT
    Exchange->>Vault: Harvest liquidity pool rewards
    activate Vault
    Exchange->>Vault: Swap rewards for stablecoins
    Vault->>Vault: Combine with protocol fees
    Vault->>Vault: Hold 90% for redeem or rebase
    Exchange->>Vault: Purchase FACT on open market
    Vault->>-Wallet: Distribute FACT
```

##### XUSD can be minted with or redeemed for stable coins
* Redemption carries nominal fee (0.5%) paid to treasury
##### Stable coins in vault are deposited into strategies
* Adjustable buffer reduces futile cycles
##### Strategies generate yield increasing treasury value
* Deposit-type investments are tracked
* Rewards tokens are periodically sold for stablecoins and reinvested
##### XUSD in wallets (EOAs) are rebased to account for change in vault value
* Adjustable Portion of yield paid to treasury, initially 0%
##### Treasury purchases governance token on open market using treasury funds
##### Treasury distributes governance token to stakers
##### Governance token confers voting rights

### Sequence Diagram


    D --> |Redeem|A
    D --> |Transfer funds | E
    E[Vault] -->|Allocate funds| F(Yield strategies)
    F -->|Harvest gains| E
    E --> |Distribute gains| D
    D --> |rebase supply|D
    E --> |Collect protocol fee| G(Treasury)
    G --> |Buy FACT with collected fee| G
    G --> |Distribute FACT| H(FACT Staking module)

