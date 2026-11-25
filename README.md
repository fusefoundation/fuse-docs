---
description: >-
  Explore FUSE Protocol and build an independent interface on the Internet
  Computer. Find costs and fees, setup guides, canister IDs, and the developer
  kit.
---

# Build on FUSE

FUSE is a charity-focused lottery protocol on the Internet Computer. Use this guide to understand how it works, see what it costs to register a website, or build an independent interface. You can start by showing public round results without connecting a wallet.

[About FUSE](about.md) · [Costs and fees](costs.md) · [FAQ](faq.md)

**Are you a creator or publisher?** [How to earn with FUSE](how-to-earn-with-fuse.md) before opening the technical guides.

## Choose where to start

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><i class="fa-bolt">:bolt:</i></td><td><strong>Read public data</strong></td><td>Show the latest published round. No wallet, account, or bond required.</td><td><a href="quickstart.md">quickstart.md</a></td></tr><tr><td><i class="fa-globe">:globe:</i></td><td><strong>Register your website</strong></td><td>Verify your HTTPS domain, fund the bond, and activate your interface.</td><td><a href="register.md">register.md</a></td></tr><tr><td><i class="fa-code">:code:</i></td><td><strong>Build the integration</strong></td><td>Read the full API reference and follow a wallet integration from preparation to recovery.</td><td><a href="integration-kit.md">integration-kit.md</a></td></tr><tr><td><i class="fa-circle-check">:circle-check:</i></td><td><strong>Check before launch</strong></td><td>Test attribution and recovery on a test deployment before enabling deposits.</td><td><a href="launch-checklist.md">launch-checklist.md</a></td></tr></tbody></table>

## How the pieces fit

| Your website                                                                | FUSE Root                                                                | ckUSDT ledger                                                                                                        |
| --------------------------------------------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| Presents public results and asks the participant to confirm wallet actions. | Records participation, attributes deposits, and publishes round results. | Records ckUSDT transfers. Use its current fee and let FUSE confirm the transfer before showing an accounting credit. |

**Start read-only.** Open the [Quick start](quickstart.md) and compare one published round with the official FUSE app. For copyable production identifiers, see [Mainnet addresses](mainnet.md).

## Read the full integration here

[Register and verify your website](register.md) · [Connect OISY and handle deposits](oisy.md) · [FUSE API reference](operator-api.md) · [Glossary](glossary.md)

GitHub is optional for reading this guide. Use the [downloadable kit](integration-kit.md#download-and-run-the-kit) when you need the complete example files, tests, or Codex skill.

[Official FUSE website](https://fuseprotocol.org/) · [Developer kit on GitHub](https://github.com/fusefoundation/fuse-interface-kit) · [Community and questions](https://t.me/fuseprotocol_en)
