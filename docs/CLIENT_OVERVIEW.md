# Who's Behind That? — Client

The public web app at [whosbehindthat.com](https://whosbehindthat.com). Anyone can paste a post or article URL and see whose agenda it serves. No account is required.

For the full system (server, scoring engine, database), see the [architecture doc](https://github.com/haimglikman/whos-behind-that-server/blob/main/docs/ARCHITECTURE.md).

## What users can do

| Tab | Purpose |
|---|---|
| Analyze | Scan a post or article URL (X, Facebook, Instagram, TikTok, YouTube, Telegram, news sites) or paste text manually; optionally research the author |
| Post history | The user's own past scans, with filters by source, entity and actor |
| Investigate | Combine several posts to detect connections, clusters and a shared narrative |
| Clusters history | The user's saved investigations, reopenable and linkable by cluster ID |
| FAQ | Terminology, scanning logic, technical and privacy questions |
| About | Scope, disclaimer, privacy, deployed versions, contact |

## How it works

- **A single file:** `index.html` with no build step, hosted on GitHub Pages under the custom domain.
- **One backend:** all fetching and AI work happens on the WBT server; the client only renders results.
- **Server warm-up:** the server can sleep when idle, so on load the client shows a warm-up screen and retries until the server responds.
- **Anonymous identity:** a random device ID in local storage. It ties together the user's history, their daily quota (10 scans per device) and their scan IDs (`WBT-{XXXX}-…`, where `XXXX` comes from the hashed device ID).
- **Two-layer history:** each scan is stored locally for the user and saved to the shared database (tagged `source: client`), so the operator can monitor quality.
- **Live configuration from the server, on page load:**
  - entities from `/entities/list`, falling back to a built-in default set if the server is unreachable
  - the FAQ from `/faq/list`
  - the client registers its version through `/client/register` for deployment monitoring
- **Version-aware results:** results are displayed according to the server version that produced them (see decision 5).
- **Mobile:** an icon tab bar below the header replaces the desktop navigation.

## Privacy

There is no login, no cookies and no third-party tracking. Users see only their own scans and clusters. Post text is sent to the AI providers only for analysis.
