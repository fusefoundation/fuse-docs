---
description: Build and operate an independent interface for FUSE Protocol on the Internet Computer.
---

# Build on FUSE

Create your own website for FUSE on the Internet Computer. Start by showing public round results, then register your domain if you want to attribute participant contributions to your interface.

<table data-view="cards">
<thead><tr><th width="48"></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead>
<tbody>
<tr><td><i class="fa-bolt"></i></td><td><strong>Read public data</strong></td><td>Show the latest published round. No wallet, account, or bond required.</td><td><a href="quickstart.md">Read public data</a></td></tr>
<tr><td><i class="fa-globe"></i></td><td><strong>Register your website</strong></td><td>Verify your HTTPS domain, fund the bond, and activate your interface.</td><td><a href="register.md">Register your website</a></td></tr>
<tr><td><i class="fa-code"></i></td><td><strong>Build the integration</strong></td><td>Get the Candid contract, JavaScript examples, and Codex skill.</td><td><a href="integration-kit.md">Build the integration</a></td></tr>
<tr><td><i class="fa-circle-check"></i></td><td><strong>Check before launch</strong></td><td>Test attribution and recovery on a test deployment before enabling deposits.</td><td><a href="launch-checklist.md">Check before launch</a></td></tr>
</tbody>
</table>

## How the pieces fit

| Your website | FUSE Root | ckUSDT ledger |
| --- | --- | --- |
| Presents public results and asks the participant to confirm wallet actions. | Records participation, attributes deposits, and publishes round results. | Records ckUSDT transfers. Use its current fee and let FUSE confirm the transfer before showing an accounting credit. |

**Start read-only.** Open the [Quick start](quickstart.md) and compare one published round with the official FUSE app. For copyable production identifiers, see [Mainnet addresses](mainnet.md).

[Official FUSE website](https://fuseprotocol.org/) · [Developer kit on GitHub](https://github.com/burzhuy3/fuse-interface-kit) · [Community and questions](https://t.me/fuseprotocol_en)
