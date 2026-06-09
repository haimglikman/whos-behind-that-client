# whos-behind-that-client

### v1.10.2 — bug fix (client) | Server: v1.15.1 | Admin: v2.9.4
- FAQ: moved "Is login or identification required?" and "Is Who's Behind That? free?" from Technical → Privacy
- FAQ: moved "What platforms are supported?" and "What languages are supported?" from Scanning logic → Technical

### v1.10.1 - bug fix (client) | Server: v1.15.1 | Admin: v2.9.4
- bug fix: FAQ items appearing across all tabs — rebuilt FAQ page structure from scratch

### v1.10.0 (client) | Server: v1.15.1 | Admin: v2.9.4
- New FAQ: What is Hidden Convergent Interest? (Terminology)
- New FAQ: What platforms are supported? (Scanning logic)
- New FAQ: Is login or identification required? (Technical)
- New FAQ: Is Who's Behind That? free? (Technical)
- "Who's Behind That?" now italicized everywhere it appears in app text

### v1.9.3 — bug fix (client) | Server: v1.15.0 | Admin: v2.8.0
- Fixed URL input bar dropping below sidebar — caused by incorrect flex-direction on page layout
- Fixed FAQ and About text confined to left half — removed max-width constraint
- Fixed stale hardcoded version in topbar

### v1.9.2 — bug fix (client) | Server: v1.15.0 | Admin: v2.8.0
- Fixed URL input bar dropping down — caused by incorrect flex-direction on page layout
- Fixed FAQ and About text confined to left half of screen — removed max-width constraint

### v1.9.1 — bug fix (client) | Server: v1.14.0 | Admin: v2.7.0
- Fixed bottom bar (server status, app version, server version) CSS missing — now displays correctly
- Fixed FAQ and About pages cut off — now scroll to full content
- Contact us button now opens mailto directly instead of navigating to About tab
- Added Clear button next to Open post in results header

### v1.9.0 (client) | Server: v1.13.0 | Admin: v2.7.0
- New FAQ tab with 20 questions across four categories: Terminology, Scanning logic, Technical, Privacy
- FAQ questions are collapsible/expandable
- Mobile bottom tab bar now has 4 tabs: Analyze, History, FAQ, About

### v1.8.1 — bug fix (client) | Server: v1.13.0 | Admin: v2.7.0
- Analysis no longer cancels when switching tabs — runs in background and results appear when returning to Analyze tab
- About tab: added news and media website coverage
- About tab: added public content only disclaimer (no paywalls, no private/friends-only posts)
- About tab: added Israeli domestic politics to scope description
- About tab: actor research mentioned in How it works section
- About tab: daily credit limit noted as beta — subject to change

### v1.8.0 (client) | Server: v1.13.0 | Admin: v2.7.0
- News website support: analyze articles from Ynet, Haaretz, BBC, NYT, and 60+ other outlets
- Actor research on news articles: profiles both the author and the publication (editorial line, ownership, agenda)
- Actor research now uses web search for better results
- Actor searches saved to server DB with scan ID — visible in admin
- News platform icon (📰) in history

### v1.7.0 (client) | Server: v1.12.4 | Admin: v2.4.0
- Expanded About tab with full Disclaimer section covering AI results, accuracy limitations, non-endorsement, editorial neutrality, scope, and intended use
- Added Anthropic third-party data processing disclosure
- Updated contact email to contact@whosbehindthat.com

### v1.6.0 (client) | Server: v1.12.4 | Admin: v2.3.1
- Actor research now counts against the daily scan limit — only on success, not on failed requests

### v1.5.1 — bug fix (client) | Server: v1.12.2 | Admin: v2.3.1
- Same URL normalization fix as admin

### v1.5.0 (client) | Server: v1.12.0 | Admin: v2.3.0
- Server warm-up screen on load: shows spinner while server wakes from sleep, retries 3 times, fades out when ready
- Fixed scan ID and Open Post button not appearing in results — now shown prominently after every analysis

### v1.4.0 (client) | Server: v1.12.0 | Admin: v2.3.0
- Browser tab now shows "Who's Behind That? — Client"
- Analyze tab: scan ID shown prominently with "Scan ID" label
- Analyze tab: "↗ Open post" button next to URL

### v1.3.0 (client) | Server: v1.11.1 | Admin: v2.2.1
- Post text now shown in results view and when replaying a scan from history
- Removed technical scoring summary — admin-only detail

### v1.2.1 — bug fix (client) | Server: v1.11.1 | Admin: v2.2.1
- Client now sends WBT scan ID (not numeric timestamp) as primary DB key — fixes ID mismatch with admin
- Back button from history entry overlay now correctly closes the overlay

### v1.2.0 (client) | Server: v1.11.0 | Admin: v2.2.0
- Scan IDs now include user prefix: WBT-{XXXX}-{date}-... where XXXX is last 4 of hashed device ID
- Retroactive migration: old IDs upgraded to include user prefix
- Browser back/forward buttons now navigate between tabs within the app

### v1.1.3 — bug fix (client) | Server: v1.11.0 | Admin: v2.1.1
- Fixed dial percentage position on mobile — explicit SVG dimensions prevent layout collapse
- Versions (app + server) now shown in top-right corner on mobile since bottom bar is hidden behind tab bar
- Bottom bar hidden on mobile to avoid overlap with tab bar

### v1.1.2 — bug fix (client) | Server: v1.11.0 | Admin: v2.1.1
- Fixed dial percentage centering on mobile — reverted to flex centering which is reliable across browsers
- Analyze tab no longer clears immediately after scan — results stay visible, tab clears when navigating away
- Cleaned up stale references to removed actor handle input

### v1.1.1 — bug fix (client) | Server: v1.11.0 | Admin: v2.1.1
- Fixed dial percentage appearing top-left on mobile — now properly centered
- History entries now open inline as an overlay within My history tab instead of switching to Analyze tab
- Analyze tab auto-clears after a successful scan and shows a toast with the scan ID pointing to My history

### v1.1.0 (client) | Server: v1.11.0 | Admin: v2.1.1
- Mobile: sidebar hidden on small screens, replaced with bottom tab bar (Analyze / History / About)
- Fixed actor research prompt incorrectly showing Instagram/Facebook detection message for all platforms — now shows a generic "Would you like to research this account?" prompt
- Fallback message when fetch fails is now platform-agnostic: no mention of specific platforms, just a clear message about public post access with paste option

### v1.0.1 (client) | Server: v1.11.0 | Admin: v2.0.0
**Server: v1.10.4**
- Client scans now saved to shared database — visible in admin history
- Scans tagged with source:'client' and anonymous device ID

## v1.0.0
**Server: v1.10.4**
- Initial client release
- Full narrative alignment analysis: primary and secondary matches, convergent interest detection, AI text score
- Personal history: scans stored locally per device, visible only to the user
- Anonymous device ID: no login required, history persists across sessions on the same device
- Daily rate limit: 10 scans per device per 24 hours, resets at midnight
- Actor research: profile any social media account after a scan
- Supports X (auto-fetch), Facebook (auto-fetch), Instagram (manual text paste)
- Privacy policy and contact email in the About tab
- Status bar shows app version, server version, and live server status
- Powered by the same server and entity database as the admin version
