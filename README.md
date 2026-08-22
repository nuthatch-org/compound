# compound

A [nuthatch](https://github.com/nightswatchhq/nuthatch) nest: **Compound III (Comet) USDC on Ethereum**.

Supplies, withdrawals, absorptions and collateral movements.

One binary, one config file, no graph-node, no gateway, no query fees.

## What it indexes

**Chain:** `mainnet`. **1 contract**, **11 tables**.

| alias | address |
|---|---|
| `c0` | `0xc3d688b66703497daa19211eedff47f25384cdc3` |

## Verified

Indexed blocks **25,791,624 to 25,811,560** and sealed **876 events**. Every table below is generated from the vendored ABIs, and the run above is what this nest actually decoded, not an estimate.

## Run it

```sh
nuthatch init --from https://github.com/nightswatchhq/compound
cd compound
nuthatch dev --dir . --backfill 50000 --seal-direct
nuthatch sql --dir . "SELECT count(*) FROM \"c0__absorb_collateral\""
```

The endpoint in `nuthatch.toml` is keyless and public, so this file is publishable: a `nuthatch.toml` is pinned into the nest's content address and must never carry a credential. It is enough to follow the tip. A **backfill** wants archive depth it may not have: pass your own with `--rpc`, and check it first with `nuthatch doctor --rpc <url>`.

## Tables

```
c0__absorb_collateral
c0__absorb_debt
c0__buy_collateral
c0__pause_action
c0__supply
c0__supply_collateral
c0__transfer
c0__transfer_collateral
c0__withdraw
c0__withdraw_collateral
c0__withdraw_reserves
```
