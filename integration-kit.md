# Integration kit

Start by reading public data with the [read-only API](api.md). An active registration is required for testing your own operators' records, not for reading public round results.

The [FUSE Interface Kit](https://github.com/burzhuy3/letsdomore/tree/fuse-interface-kit) is the companion technical repository. The following links are pinned to a known kit revision:

- [Candid interface](https://github.com/burzhuy3/letsdomore/blob/d38088bf79d95e6d891cdd113f6c3603eeba44fe/api/fuse-interface.did) and [JavaScript bindings](https://github.com/burzhuy3/letsdomore/blob/d38088bf79d95e6d891cdd113f6c3603eeba44fe/api/fuse-interface.idl.mjs).
- [Operator registration and troubleshooting (Russian)](https://github.com/burzhuy3/letsdomore/blob/d38088bf79d95e6d891cdd113f6c3603eeba44fe/docs/QUICKSTART_RU.md).
- [Read-only operator example](https://github.com/burzhuy3/letsdomore/blob/d38088bf79d95e6d891cdd113f6c3603eeba44fe/examples/read-interface.mjs).
- [Codex skill](https://github.com/burzhuy3/letsdomore/blob/d38088bf79d95e6d891cdd113f6c3603eeba44fe/skills/fuse-interface/SKILL.md). The kit README explains how to install it in your project.

## Before you enable participant payments

Use a dedicated test environment and validate your configured network, Root and ledger. Confirm that your site is active and uses the exact `interface_id` and `memo` issued for it. A link to the official participant cabinet does not attribute top-ups made there to your interface.

Make the amount, token, network and fee visible before a participant signs. If confirmation is interrupted, check the original operation before offering a retry. Do not test a payment flow with real funds on mainnet.

