---
description: Find the FUSE Candid contract, JavaScript bindings, OISY examples, and the Codex skill for building an independent interface.
---

# Integration kit

Start by reading public data with the [read-only API](api.md). An active registration is required for testing your own operators' records, not for reading public round results.

The [FUSE Interface Kit](https://github.com/burzhuy3/fuse-interface-kit) is the companion technical repository. The following links are pinned to a known kit revision:

- [Candid interface](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/api/fuse-interface.did) and [JavaScript bindings](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/api/fuse-interface.idl.mjs).
- [Operator registration and troubleshooting](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/docs/QUICKSTART.md).
- [Full API reference](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/docs/API.md) and [OISY deposit example](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/examples/oisy-deposit.mjs).
- [Read-only operator example](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/examples/read-interface.mjs).
- [Codex skill](https://github.com/burzhuy3/fuse-interface-kit/blob/3e2f04ab5e57bd6e5433adf702a6619e67dfda68/skills/fuse-interface/SKILL.md). The kit README explains how to install it in your project.

## Before you enable participant payments

Use a dedicated test environment and validate your configured network, Root and ledger. Confirm that your site is active and uses the exact `interface_id` and `memo` issued for it. A link to the official participant cabinet does not attribute top-ups made there to your interface.

Make the amount, token, network and fee visible before a participant signs. If confirmation is interrupted, check the original operation before offering a retry. Do not test a payment flow with real funds on mainnet.

