# Quick start

Your first version can be a single page that shows a round without asking anyone to sign in.

1. Open the [FUSE app](https://app.fuseprotocol.org/app) as a guest and find the public round results. Use an already published round as a reference.
2. Start with the [read-only API](api.md). Read the day snapshot, then request its latest published round by ID. Keep the current round and the latest published result separate on screen.
3. Check that your page shows the same round ID and result as FUSE. If data is loading, unavailable or not published yet, say so. Do not display a missing amount as zero.

There is no registration or bond for this read-only step. Before adding a participant sign-in or transfer flow, test it in a dedicated test environment without real funds. To receive an operator share, follow [website registration](register.md).
