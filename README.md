# Curve Finance Vyper Compiler Reentrancy Bug — PoC

> **Educational Purpose Only** — This PoC is created for security research and education
> purposes only. It runs against a fork, not mainnet.

## Quick Start

```bash
git clone https://github.com/NomosLabs-Security/poc-curve-finance-2023
cd poc-curve-finance-2023
forge install foundry-rs/forge-std --no-git
forge test -vvvv
```

## Details

- **Exploit Date:** 2023-07-30
- **Fork Block:** #17807830 (one block prior)
- **Expected Output:** Reentrancy bypassing @nonreentrant due to Vyper compiler bug in storage slot assignment
- **Full Analysis:** [NomosLabs Security Intelligence Archive](https://nomoslabs.io/archive/curve-finance-2023)

## Description

The Vyper compiler versions 0.2.15 through 0.3.0 had a critical bug in the `@nonreentrant`
decorator implementation. When multiple functions used the same lock key, the compiler assigned
different storage slots for the lock variable, making the reentrancy guard useless. Attackers
exploited this to drain ~$70M from multiple Curve stable pools (alETH, msETH, pETH, CRV/ETH).

## RPC Providers

```
Alchemy:   https://eth-mainnet.alchemyapi.io/v2/YOUR_KEY
Infura:    https://mainnet.infura.io/v3/YOUR_KEY
QuickNode: https://YOUR_ENDPOINT.quiknode.pro/YOUR_KEY
```

## License

MIT — For educational use only.
