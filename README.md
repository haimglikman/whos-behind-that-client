# whos-behind-that-client

### v1.11.0 (server) | Admin v2.0.0 / Client v1.0.1
- source and device_id columns added to scans table
- history/save accepts and stores source + deviceId
- history/list supports source and deviceId filter params
- Device IDs hashed to usr_XXXX for privacy
- clientUsers array returned for admin filter dropdown

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
