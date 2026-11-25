---
description: >-
  Understand FUSE integration terms such as canister, principal, interface ID,
  memo, revision, and credited deposit.
---

# FUSE integration glossary

| Term            | What it means in FUSE                                                                                                                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Canister        | A service on the Internet Computer. FUSE Root handles protocol operations; the separate ckUSDT ledger records token transfers.                      |
| Principal       | An ICP identity for a user or canister. An Internet Identity principal can differ from one site origin to another.                                  |
| Controller      | The Internet Identity principal authorized to manage a registered interface. It can differ from the configured recipient of operator earnings.      |
| Interface ID    | The integer ID of an activated interface. Preserve all digits when moving it between the dashboard, code, and JSON.                                 |
| Memo            | The byte sequence that ties the prepared transfer to the registered interface. A hex representation is not the bytes themselves.                    |
| Revision        | The FUSE number used to locate and check the same prepared operation, including after a reload.                                                     |
| Ledger block    | A ledger record reference for a transfer. A block number helps FUSE locate the operation, but the ledger confirmation and FUSE credit are separate. |
| Round ID        | The protocol identifier for a particular distribution. Use it to find a published result; keep forecasts separate.                                  |
| Refundable bond | The amount required to activate an interface, subject to refund conditions. It is not an operator fee or a participant deposit.                     |

[Mainnet addresses](mainnet.md) · [Costs and fees](costs.md) · [FAQ](faq.md)
