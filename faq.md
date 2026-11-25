---
description: "Answers to common FUSE integration questions about wallets, website registration, the bond, deposit attribution, and missing results."
---

# Frequently asked questions

## Can I show FUSE results without registering a website?

Yes. Use the [read-only quick start](quickstart.md). You do not need a wallet, an interface ID, or a bond to read published results.

## Do I need to launch my own canister?

No. A read-only site can call FUSE Root from its own frontend. To register for attribution, you need an HTTPS domain you control and a way to host the verification file. See [mainnet addresses](mainnet.md) and [website registration](register.md).

## Who signs the participant transfer?

The participant signs with their wallet. Your frontend presents the terms before asking for confirmation. The [OISY integration guide](oisy.md) shows how to connect, prepare a deposit, and check it afterward.

## Does a link to the FUSE app earn my interface commission?

No. If the user makes a deposit through the official form, it is attributed to the default interface. For your own integration, use the exact `interface_id` and memo shown in your dashboard, and confirm that the site is active. See [how earnings are calculated](earnings.md).

## Can I get the 100 ckUSDT bond back?

Yes, subject to the refund conditions and ledger fee. The dashboard shows whether your bond is eligible. See [costs and fees](costs.md#when-can-i-recover-the-bond).

## The wallet window closed. Should I try the transfer again?

First check the existing operation with the same wallet. A timeout is not proof that the transfer failed. See [troubleshooting](troubleshooting.md) for what to check before another attempt.

## Why might a result or balance be missing?

A round may not have been published yet, or the data source may not be up to date. A ledger-confirmed transfer may also still be awaiting credit in FUSE. Show these states separately from a genuine zero. See the [read-only API](api.md) and [launch checklist](launch-checklist.md).

## Where can I ask questions?

Use the [FUSE Telegram group](https://t.me/fuseprotocol_en) for general questions or email [partners@fuseprotocol.org](mailto:partners@fuseprotocol.org) about an integration. For troubleshooting, share the error and your interface ID if assigned. Never share a seed phrase, private key, or sign-in code.
