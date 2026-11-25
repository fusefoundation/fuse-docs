---
description: "Register an HTTPS website with FUSE, confirm the ckUSDT bond, verify your domain, and activate your interface."
---

# Register your website

You need control of your HTTPS domain, an Internet Identity account for managing the interface, and a compatible ICP account to receive your operator earnings.

1. Open the [FUSE page for interface operators](https://int.fuseprotocol.org/interfaces) and sign in to the [operator cabinet](https://int.fuseprotocol.org/site).
2. Enter the domain you control and your intended payout account. Check the exact domain and payout details before continuing.
3. Follow the cabinet’s registration prompts. Activation requires a confirmed **100 ckUSDT refundable bond** and proof that you control the domain. Ledger fees may apply separately. A wallet approval alone does not mean the bond was received.
4. Publish the exact verification file provided by the cabinet at `/.well-known/ccto-verification.txt` on the exact HTTPS domain. Wait for successful verification and confirm the interface status is **Active** before using its ID for attribution.

You can build and test public read-only pages without opening a registration. Do not use a production bond or real participant transfers to test an integration. If a bond transaction has an uncertain status, check the existing operation before trying again.

The verification URL should return HTTP 200 and the verification text from the current claim, without a redirect or login prompt. Keep this URL reachable and check the verification expiry in the cabinet.
