---
description: "Look up FUSE Candid methods for public reads, website registration, bond management, operator earnings, and payout recovery."
---

# FUSE API reference

Use [Mainnet addresses](mainnet.md) for the production Root, ckUSDT ledger, and gateway. Start with [Read-only API](api.md) if you only need public rounds. The [Candid contract](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/api/fuse-interface.did) and [JavaScript bindings](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/api/fuse-interface.idl.mjs) define the exact inputs and results. FUSE Root checks the caller for account-specific requests; there is no partner server API key.

- **Types:** Candid `nat`, `nat64`, and `int` map to `BigInt`; `nat32` maps to `Number`. Options are `[]` or `[value]`. A variant is a single-key object. Root typically returns `{ Ok: value }` or `{ Err: message }`. Handle transport errors separately.
- **Amounts:** 1 ckUSDT is 1,000,000 micro-units. Use integers, serialize large values as decimal strings in JSON, and pass `memo` as raw bytes. Read `icrc1_fee` from the configured ledger before signing.
- **Network:** Use the agent's trusted mainnet root key on ICP. For tests use the test Root, ledger, gateway, and key. `wallet_runtime_capabilities().Ok.deposits` describes API support, not whether deposits are currently open. Root checks admission at operation selection and in `my_incoming_status`.

## Public interface and protocol reads

| Root method | Use |
| --- | --- |
| `interface_info(interface_id)` | Active registration, `controller`, `payout_principal`, `registered_at_ns`. An empty option means no active registration. |
| `interface_deposit_memo(interface_id)` | Assigned memo and registration. It can outlive eligibility for new deposits; cross-check with `interface_info`. |
| `public_interface_deposits(interface_id)` | Confirmed original deposits, bond release threshold, and `history_complete`. If incomplete, show `confirmed_at_least_micro_units` only as a lower bound. |
| `wallet_runtime_capabilities()` | API version, deposit support, and `source.app`, `source.ledger`, `source.local_test`. |
| `public_protocol_status()` | Pause status, round count and `next_cycle_day` when set. |
| `interface_data_capabilities()` | Public API version, publishing capabilities and page limits. |
| `interface_data_automation_status()` | Public data processing status. |
| `project_statistics()` | Aggregates and `progress.caught_up`. Expose the last indexed round if behind. |
| `tour_statistics_page(after, limit)` | Start with `after = []` and continue with `next_after_cycle`. |
| `public_prize_events(after, limit)` | Prize credits. Start with `after = []`, continue with `next_after`, and deduplicate by `event_id`. A credit and a confirmed payout are separate. |

```js
import { readInterface, rootActor, unwrap } from './examples/fuse.mjs';

const binding = await readInterface(process.env.FUSE_INTERFACE_ID);
const progress = unwrap(await rootActor().public_interface_deposits(binding.id));
console.log(binding.memoHex, String(progress.confirmed_at_least_micro_units));
```

Respect `max_page_items` and cache public statistics. Label stale data with the last successful read time. Recheck registration before creating a new operation.

## Registration, bond, and operator earnings

The [interface dashboard](https://int.fuseprotocol.org/site) already implements these flows. Use the table below to map an action to its Root state.

| Action | Root methods | Checks |
| --- | --- | --- |
| Prepare registration | `my_site_claim()`; `request_site_claim_from_view(expected_generation, domain, payout_principal)` | Use `expected_generation = []` for a new claim. Use the current claim binding from `my_site_bond_context()` when replacing it. Refresh on conflict. |
| Approve bond | `bond_approval_quote()`; `my_site_approval_status()`; `choose_site_approval_from_view(revision, claim_binding, expected_allowance, expected_fee)` | Root is the spender. Verify the controller account and exact allowance. Preserve the prepared request and confirmation before funding. |
| Fund bond | `site_bond_action_from_view(claim_id, claim_binding, { Fund: null })` | Requires confirmed approval. Check `my_interface_bond()`; use `scan_pending_interface_bond(16)` to check a previous operation. |
| Verify domain | `verify_site_claim_from_view(claim_binding, last_checked_at_ns)` | Use `claim_binding` from `my_site_bond_context()` and the displayed claim timestamp. Check `valid_until_ns`. |
| Activate | `site_bond_action_from_view(claim_id, claim_binding, { Activate: null })` | Verify the bond and HTTPS proof first, then read `my_interface()` and public configuration. |
| Check earnings | `my_interface_funds()`; `my_income_funds_v3({ Interface: interface_id })` | Check available and reserved amounts, recipient, previous payout, and reconciliation status. |
| Withdraw earnings | `request_income_payout_v3(revision, input, expected_fee)` | From `my_income_funds_v3` use the revision, source, account and kind; include the chosen recipient and gross amount. For `OwnAccount` use `own_recipient`. Display net = gross − fee. |
| Check a previous payout | `my_payout_choice_v3(revision)`; `income_payout_status_v3(request_id)`; `scan_income_payout_v3(request_id, 16)` | Reuse the same request ID. `Paid.ledger_block` confirms payout; `Pending` or `Unknown` retains the reservation. One page with no match does not settle an uncertain payout. |
| Recover bond or close | `site_bond_action_from_view`; `my_interface_bond()` | Use the dashboard for release, closing at the current revision, or release after closure. Check the separate bond account, recipient, and fee. |

Prepare a payout preview with the authenticated controller actor before any withdrawal is submitted:

```js
const kind = { Interface: interfaceId };
const funds = unwrap(await signedRoot.my_income_funds_v3(kind));
const fee = await ledger.icrc1_fee();
const gross = 10_000_000n; // 10 ckUSDT, including the ledger fee
if (funds.needs_reconciliation || funds.pending_payout_id.length ||
    gross <= fee || gross > funds.available) {
  throw new Error('Check the previous payout and available earnings.');
}
const input = {
  account: funds.account, source: funds.source, kind,
  recipient: { OwnAccount: null }, gross,
};
// Show funds.own_recipient, gross, fee, and gross - fee.
// Save the revision and conditions before calling after explicit confirmation.
// signedRoot.request_income_payout_v3(funds.revision, input, fee)
```

For attributed participant deposits and recovery, see [Connect OISY and handle deposits](oisy.md).
