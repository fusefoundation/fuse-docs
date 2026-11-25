---
description: Verify the independent interface from its first public query to test deposit recovery.
---

# Launch checklist

Use a dedicated test deployment for payment paths. Passing this checklist does not require sending funds on mainnet.

| Check | What success looks like |
| --- | --- |
| Public data | In a signed-out browser, a completed round shows the expected ID and prize fund. Loading, an unavailable result, and a true zero are distinguishable. |
| Site configuration | The registered hostname, active interface ID, and exact memo bytes match the dashboard. Test and mainnet configurations are separate. |
| Confirmation | Before the participant signs, the site displays the wallet account, token, amount, destination, fee, and total. |
| Interrupted submission | Close the signer after submitting. Reload the page with the same wallet and check the original operation. The flow does not send a second transfer. |
| Accounting | The UI distinguishes a ledger-confirmed transfer from one credited in FUSE. |
| Operator view | The interface dashboard shows the expected attribution and earnings from applicable daily contributions, not from the top-up alone. |

For a network or payment error, record the environment and the existing operation reference for recovery. Do not collect keys, seed phrases, or signed envelopes in support tickets.

[Connect a website](register.md) · [Integration kit](integration-kit.md) · [Troubleshooting](troubleshooting.md)
