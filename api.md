---
description: Read public FUSE round summaries and statistics using production canister queries, with Candid examples.
---

# Read-only API

FUSE Root on Internet Computer mainnet: `ouuix-fyaaa-aaaai-aygia-cai`. See [Mainnet addresses](mainnet.md) for the related ledger and gateway. The following calls are public queries. They do not sign transfers, ask for a key, or require an account.

| Query | What it returns |
| --- | --- |
| `current_tour_summary()` | A day snapshot. `latest_tour` is the last published result, if present; `pending_utc_day` is not a result. |
| `tour_summary(cycle_id : nat64)` | A specific published round, or an error if unavailable. |
| `tour_statistics_page(after_cycle : opt nat64, limit : nat32)` | Indexed statistics. Use the returned `next_after_cycle` for pagination and respect `caught_up`. |

With [DFX installed](https://docs.internetcomputer.org/building-apps/developer-tools/dfx/installing-dfx), run these from a directory outside your DFX project. `anonymous` is DFX's built-in identity:

```bash
ROOT=ouuix-fyaaa-aaaai-aygia-cai
dfx --identity anonymous canister call --network ic --query "$ROOT" current_tour_summary '()'
```

Take the `cycle_id` from `latest_tour` and enter it when prompted:

```bash
read -r -p 'Published cycle ID: ' CYCLE_ID
if [[ "$CYCLE_ID" =~ ^[0-9]+$ ]]; then
  dfx --identity anonymous canister call --network ic --query "$ROOT" tour_summary "($CYCLE_ID : nat64)"
fi
```

Check the same ID in the [official app](https://app.fuseprotocol.org/app). For the display, read `quote.prize` as an integer number of micro-ckUSDT. Preserve Candid `nat` and `nat64` as JavaScript `BigInt`; serialize values as decimal strings in JSON. Handle `Err`, missing option values, and connection errors separately from zero.

These signatures and fields were checked against the release Candid interface. The command output has not been independently compared with the live app for this edition.

See [Integration kit](integration-kit.md) for the operator API, JavaScript bindings, examples and Codex skill.

