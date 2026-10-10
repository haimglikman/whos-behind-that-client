# Who's Behind That? — Client Decisions

Key decisions behind the public client. Each entry covers the problem, what was chosen, and the result. Version numbers refer to the client changelog; `-dev` versions were built in the development repo.

---

## 1. Anonymous by design
**v1.0.0, v1.2.0**

**Problem:** The tool should be usable instantly, and a tool that analyzes political content should not collect identities. AI calls still cost money, so usage has to be bounded.

**Decision:** No accounts. A random device ID in local storage drives each user's history, a daily quota (10 scans per device) and their scan IDs. The server stores only a hashed form of the ID. Actor research counts toward the quota only when it succeeds.

**Outcome:** Zero sign-up friction, predictable AI cost, and a privacy story that fits on one FAQ line: no login, no cookies, no tracking.

---

## 2. Design around a sleeping server
**v1.5.0, v1.11.1**

**Problem:** The hosting tier lets the server sleep when idle, so a user's first request could hang or fail.

**Decision:** Show a warm-up screen on load: a spinner, three retries, then fade out once the server responds. When `AbortSignal.timeout()` turned out to be unsupported on iOS before 16, the timeout was rewritten with a manual `AbortController`.

**Outcome:** Cold starts became a visible loading state instead of an error, on every device.

---

## 3. The server as the single source of truth
**v1.16.2, v1.17.3**

**Problem:** Entities were hard-coded in the client, so every change in admin required a client release, and client and admin could drift apart.

**Decision:** Load entities (and the FAQ) from the server on every page load, keeping a built-in default set as a fallback. The client also reports its version to the server, so admin can see which versions are live and on how many devices.

**Outcome:** Entity and FAQ changes reach users without a deploy, and version rollout is observable.

---

## 4. Clusters that look the same on every device
**client-dev v1.14.2–v1.15.10 · shipped in v1.16.0**

**Problem:** A cluster reopened from history, on another device or in admin, looked different from the original: post numbers (P1, P2…) were scrambled, connection lines were missing, and dates were wrong. Reconstruction depended on whatever scans happened to be in the viewer's local history.

**What was tried:** Fixes one symptom at a time: restoring connection lines, placeholder timestamps for unknown posts, and re-sorting.

**Decision:** Make the saved cluster self-contained. Each cluster stores its full post data, its isolated post IDs and its connections, with the post array built from the investigation basket rather than from local history. Reconstruction keeps the original post order instead of re-sorting by timestamp.

**Outcome:** The same cluster renders identically on any device and in admin. A related privacy fix made Clusters history show only the current device's clusters.

---

## 5. Version-aware result display
**v1.19.0**

**Problem:** The v2 scoring engine (Jev + Claude Opus) produces calibrated verdicts, while older scans used a fixed 85% cut-off. Showing both under one rule would misrepresent one of them.

**Decision:** Display each result according to the engine that produced it. Server 2.x results use the judge's verdict (primary from 60%, up to 3; secondary from 50%, up to 2); server 1.x results keep the 85% rule. Summary messages explain which rule applied.

**Outcome:** Old and new scans coexist in history and both read correctly. The engine changed without rewriting past results.

---

## 6. Mobile navigation
**v1.1.0, v1.17.4–v1.17.8**

**Problem:** Adding the Investigate and Clusters history tabs meant six tabs no longer fit the original bottom tab bar.

**Decision:** After trying a smaller bottom bar and a scrolling top bar, settle on an icon tab bar directly below the header, in the same position as the desktop navigation.

**Outcome:** One navigation position across desktop and mobile, with room to add more tabs.
