---
description: >-
  Copy the production canister IDs and endpoints used by independent FUSE
  interfaces.
---

# Mainnet addresses

Use these values only for production on the Internet Computer. Test deployments use their own Root, ledger, and gateway configuration.

| Service       | Canister ID or endpoint       | Use it for                                                      |
| ------------- | ----------------------------- | --------------------------------------------------------------- |
| FUSE Root     | `ouuix-fyaaa-aaaai-aygia-cai` | Public round data and FUSE-specific operations.                 |
| ckUSDT ledger | `cngnf-vqaaa-aaaar-qag4q-cai` | ckUSDT fees and transfers. This ledger is not operated by FUSE. |
| ICP gateway   | `https://icp-api.io`          | Network endpoint for the ICP agent.                             |
| OISY Signer   | `https://signer.oisy.com/`    | Browser wallet signing in the example integration.              |

These are service identifiers, not instructions for sending funds. For an attributed deposit, use the recipient and memo returned by FUSE for that operation. Do not initiate a raw transfer to the Root ID shown above.

[Read-only API](api.md) · [Full API reference and bindings](https://github.com/fusefoundation/fuse-interface-kit/blob/main/docs/API.md) · [Interface dashboard](https://int.fuseprotocol.org/site)
