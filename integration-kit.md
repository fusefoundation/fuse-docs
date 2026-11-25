---
description: >-
  Find the FUSE Candid contract, JavaScript bindings, OISY examples, and the
  Codex skill for building an independent interface.
---

# Integration kit and Codex skill

Start by reading public data with the [read-only API](api.md). An active registration is required for testing your own operators' records, not for reading public round results.

The [FUSE Interface Kit](https://github.com/fusefoundation/fuse-interface-kit) is the companion technical repository. The following links are pinned to the v1.0.0 release:

* [Candid interface](https://github.com/fusefoundation/fuse-interface-kit/blob/v1.0.0/api/fuse-interface.did) and [JavaScript bindings](https://github.com/fusefoundation/fuse-interface-kit/blob/v1.0.0/api/fuse-interface.idl.mjs).
* [Operator registration and troubleshooting](https://github.com/fusefoundation/fuse-interface-kit/blob/v1.0.0/docs/QUICKSTART.md).
* [Full API reference](https://github.com/fusefoundation/fuse-interface-kit/blob/v1.0.0/docs/API.md) and [OISY deposit example](https://github.com/fusefoundation/fuse-interface-kit/blob/v1.0.0/examples/oisy-deposit.mjs).
* [Read-only operator example](https://github.com/fusefoundation/fuse-interface-kit/blob/v1.0.0/examples/read-interface.mjs).
* [Codex skill](https://github.com/fusefoundation/fuse-interface-kit/blob/v1.0.0/skills/fuse-interface/SKILL.md). The kit README explains how to install it in your project.

## Download and run the kit

The [API reference](operator-api.md), [registration guide](register.md), and [OISY walkthrough](oisy.md) are available here without leaving GitBook. Download the release when you want the complete, runnable files.

[Download the latest FUSE Interface Kit release](https://github.com/fusefoundation/fuse-interface-kit/releases/latest). Choose **Source code (zip)** under Assets. The release also links to the [live Round Reader](https://public-round-reader.sergeysolomatin.chatgpt.site/), a read-only browser example that does not require a wallet.

With Node.js 22 or later, run from the kit's root directory:

```bash
npm ci
npm test
read -r -p 'Active interface ID: ' FUSE_INTERFACE_ID
npm run read -- "$FUSE_INTERFACE_ID"
```

The last command queries the public configuration and does not send funds. It needs an existing active interface ID. To read round results without an ID, follow the [read-only quick start](quickstart.md).

## Before you enable participant payments

Use a dedicated test environment and validate your configured network, Root and ledger. Confirm that your site is active and uses the exact `interface_id` and `memo` issued for it. A link to the official participant cabinet does not attribute top-ups made there to your interface.

Make the amount, token, network and fee visible before a participant signs. If confirmation is interrupted, check the original operation before offering a retry. Do not test a payment flow with real funds on mainnet.
