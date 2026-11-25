---
description: >-
  Add a compact, live FUSE round results widget to your website with one HTML
  snippet.
---

# Embed the FUSE widget

Show the latest published FUSE round on your website. The widget displays the round number, the first recipient's allocation in ckUSDT, and a shortened public principal. When the round has more recipients, it shows how many more there are.

<a href="https://rounds.fuseprotocol.org/embed" class="button primary">Open live preview</a> <a href="https://fuseprotocol.org/" class="button secondary">Visit FUSE</a>

{% embed url="https://rounds.fuseprotocol.org/widget" %}
Latest FUSE round
{% endembed %}

## Add it to your website

Paste this snippet into a custom HTML block or your website template. Put it where you want the card to appear.

```html
<iframe src="https://rounds.fuseprotocol.org/widget"
  title="Latest FUSE round" width="360" height="195"
  style="border:0;max-width:100%" loading="lazy"
  referrerpolicy="no-referrer"
  sandbox="allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox"></iframe>
```

On the published page, check that a round number appears and that **Visit FUSE** opens the official website in a new tab. If your site does not allow iframes, link to the [live preview](https://rounds.fuseprotocol.org/embed) instead. If your site restricts which origins it can embed, allow `https://rounds.fuseprotocol.org` in its frame policy.

## What to expect

* The widget reads public results from ICP mainnet and refreshes while the page is open. No account, wallet, transfer, API key, domain registration, or bond is needed.
* The displayed amount is the first recipient's published allocation, not a record of money withdrawn. Use **Verify results** for the official round results.
* Embedding a widget does not register your website or earn an operator share. To build your own display from the API, follow the [quick start](../quickstart.md).
