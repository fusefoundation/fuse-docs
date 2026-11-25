---
description: "Learn how to connect OISY, preview and confirm a ckUSDT deposit, then recover the original operation if the wallet response is interrupted."
---

# Connect OISY and handle deposits

Start after [registering your website](register.md) on the intended test network. Use the same wallet account throughout an operation. **Prepare**, **confirm**, and **check** are separate user actions.

The [browser example](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/examples/oisy-deposit.mjs) uses `@icp-sdk/core` and `@icp-sdk/signer`. Include it in a build that resolves npm imports. Offer an account selection when OISY returns more than one primary account.

Serve the page over HTTPS and preserve the `postMessage` channel to the signer popup. If the page sets `Cross-Origin-Opener-Policy`, use `same-origin-allow-popups` for that page. If it sets CSP, permit `https://icp-api.io` in `connect-src`. Call `connectOisy()` directly from a click so the browser permits the popup.

```js
import {
  connectOisy, prepareDeposit, sendPreparedDeposit, recoverDeposit,
} from './examples/oisy-deposit.mjs';

// Connect OISY.
const connection = await connectOisy();
const session = connection.select(chosenPrincipal); // From connection.accounts.

// Prepare a deposit and display the conditions.
const preview = await prepareDeposit(session, configuredInterfaceId, '10.25');
// Show preview.owner, preview.receiver, preview.id, preview.amount,
// preview.fee, and preview.total. Keep the preview until confirmation.

// Submit only after the participant explicitly confirms.
const payment = await sendPreparedDeposit(session, preview);
console.log(payment.state, payment.row.revision);

// Check the previous deposit, including after a reload.
const restored = await recoverDeposit(session);
console.log(restored.state);
// For awaiting-confirmation, show restored.preview for explicit confirmation.
```

1. `my_incoming_status()` returns `next_revision` and the previous request. `choose_wallet_incoming_from_view(revision, { Deposit: { interface_id, amount } }, fee)` prepares the request without moving funds.
2. Verify `owner`, source, interface ID, amount, fee, destination, and memo. `content` contains the prepared CBOR ingress for `icrc1_transfer`. The example checks it, passes `arg` unchanged, and uses `operation_id` as the signing nonce. `SignerAgent` checks that the certified response belongs to the expected participant, ledger, and call.
3. If the ledger returns `Ok(block)` or `Err.Duplicate.duplicate_of`, pass that block to `confirm_incoming_block(revision, block)`. Root verifies the operation against the ledger.
4. If the popup closes, transport fails, or confirmation is delayed, keep the same revision. Read `my_incoming_choice(revision)`, search with `scan_incoming_choice(revision, 16)`, or confirm a known block again. On another device, call `recoverDeposit(session, revision)` with the verified revision and the same principal.

| Example state | Meaning |
| --- | --- |
| `credited` | `Ledger.credited = true`: the deposit is recorded in FUSE accounting. |
| `confirmed` | Root confirmed the transfer; accounting is pending. Recent Root versions can expose `confirmed_pending_micro_units`. |
| `checking` | Credit is not established. If `Ledger.unattributed = true`, investigate the same operation rather than starting another. |
| `awaiting-confirmation` | A saved request exists but this site has not started sending it. Show its conditions and wait for explicit confirmation. |
| `not-sent` | Root established the request did not produce a transfer. A new deposit requires a fresh user action. |

The example stores a pointer in `localStorage`, without keys, delegations, or signed envelopes. Web Locks prevent duplicate clicks across tabs of the same origin. It records `checking` before submitting the ledger transfer and only checks the old operation if the response is lost. Keep the revision for support. Before using this in production, connect every state to your UI and test recovery with the same account in a test environment.

## Internet Identity and the participant account

The [interface dashboard](https://int.fuseprotocol.org/site) uses Internet Identity for management. Participants can also use it in the [official account](https://app.fuseprotocol.org/account). An account is identified by its ICP principal; Internet Identity principals are origin-specific unless separately configured and verified for the intended origin relationship.

A custom participant client that uses Internet Identity can sign prepared ingress via `choose_incoming_from_view` and `arm_incoming_choice`, then check it via `observe_incoming_choice`, `confirm_incoming_block`, and `scan_incoming_choice`. Check the signed request ID and conditions against the prepared request. A link to the official participant dashboard does not transfer your interface's attribution. Use the OISY example for your first integration.

[API reference](operator-api.md) · [Launch checklist](launch-checklist.md) · [Troubleshooting](troubleshooting.md)
